# Especificación Técnica y Matemática: Motor de Análisis de Telemetría GPX para Regatas (Clase Optimist)

**Autor:** Especialista en Ingeniería Naval y Telemetría de Regatas  
**Plataforma de Aplicación:** Análisis cinemático de embarcaciones monotipo IOD95 (Optimist)  
**Lenguaje de Implementación:** JavaScript (ES6+)

---

## 1. Preprocesamiento y Filtrado Cinemático de Datos GPX

Un receptor GPS embarcado registra trayectorias con fluctuaciones de frecuencia ($0.5\text{--}2\,\text{Hz}$), imprecisiones posicionales (DOP) e interferencias por escora y movimiento del tripulante. Para realizar análisis micro-telemétricos (como pérdida en metros en virada), es obligatorio normalizar el vector de entrada.

```
       RAW GPX DATA                    1 Hz RE-SAMPLED                  EMA SMOOTHED TRACK
[t_i, lat_i, lon_i] (irregular) ---> [Interpolación Lineal] ---> [EMA en SOG y COG (Circular)]
```

### 1.1 Interpolación Temporal Uniforme a $1\,\text{Hz}$
Dado un conjunto de puntos crudos $P_i = (t_i, \phi_i, \lambda_i)$ donde $t_i$ es el timestamp Unix en milisegundos, $\phi_i$ es la latitud en grados y $\lambda_i$ la longitud en grados, se define una grilla temporal uniforme $t_k = t_0 + k \cdot 1000\,\text{ms}$.

Para cualquier $t_k \in [t_i, t_{i+1}]$, los factores de interpolación $f$ vienen dados por:

$$f = \frac{t_k - t_i}{t_{i+1} - t_i}$$

$$\phi(t_k) = \phi_i + f \cdot (\phi_{i+1} - \phi_i)$$

$$\lambda(t_k) = \lambda_i + f \cdot (\lambda_{i+1} - \lambda_i)$$

### 1.2 Cálculo Geodésico de SOG (Speed Over Ground) y COG (Course Over Ground)
A partir de la posición interpolada a $1\,\text{Hz}$, la distancia ortodrómica $d$ entre $P_k(\phi_k, \lambda_k)$ y $P_{k-1}(\phi_{k-1}, \lambda_{k-1})$ se calcula mediante la fórmula de **Haversine**:

$$\Delta \phi = \frac{(\phi_k - \phi_{k-1}) \cdot \pi}{180}, \quad \Delta \lambda = \frac{(\lambda_k - \lambda_{k-1}) \cdot \pi}{180}$$

$$a = \sin^2\left(\frac{\Delta \phi}{2}\right) + \cos\left(\frac{\phi_{k-1} \cdot \pi}{180}\right) \cdot \cos\left(\frac{\phi_k \cdot \pi}{180}\right) \cdot \sin^2\left(\frac{\Delta \lambda}{2}\right)$$

$$c = 2 \cdot \arctan2\left(\sqrt{a}, \sqrt{1-a}\right), \quad d = R \cdot c \quad (R = 6\,371\,000\,\text{m})$$

La velocidad instantánea sobre el fondo $\text{SOG}_k$ en nudos ($\text{kt}$) es:

$$\text{SOG}_k = \left(\frac{d}{\Delta t}\right) \cdot 1.94384 \quad (\text{donde } \Delta t = 1.0\,\text{s})$$

El rumbo instantáneo sobre el fondo $\text{COG}_k$ en grados azimuth ($0^\circ \le \text{COG} < 360^\circ$) se obtiene mediante:

$$y = \sin(\Delta \lambda) \cdot \cos\left(\frac{\phi_k \cdot \pi}{180}\right)$$

$$x = \cos\left(\frac{\phi_{k-1} \cdot \pi}{180}\right) \cdot \sin\left(\frac{\phi_k \cdot \pi}{180}\right) - \sin\left(\frac{\phi_{k-1} \cdot \pi}{180}\right) \cdot \cos\left(\frac{\phi_k \cdot \pi}{180}\right) \cdot \cos(\Delta \lambda)$$

$$\text{COG}_k = \left( \left( \arctan2(y, x) \cdot \frac{180}{\pi} \right) + 360 \right) \pmod{360}$$

### 1.3 Filtrado por Media Móvil Exponencial (EMA)
Para aislar el ruido GPS sin introducir desfase de fase excesivo, se aplica un filtro EMA con factor de suavizado $\alpha = 1 - e^{-\Delta t / \tau}$ ($\tau = 1.5\,\text{s}$, $\alpha \approx 0.486$).

Para la magnitud escalar de velocidad:

$$\text{SOG}_{\text{EMA}}[k] = \alpha \cdot \text{SOG}_k + (1 - \alpha) \cdot \text{SOG}_{\text{EMA}}[k-1]$$

Para la magnitud circular $\text{COG}$, para evitar la discontinuidad entre $0^\circ$ y $360^\circ$, se descompone en componentes vectoriales cartesianas:

$$X[k] = \alpha \cdot \sin\left(\frac{\text{COG}_k \cdot \pi}{180}\right) + (1 - \alpha) \cdot X[k-1]$$

$$Y[k] = \alpha \cdot \cos\left(\frac{\text{COG}_k \cdot \pi}{180}\right) + (1 - \alpha) \cdot Y[k-1]$$

$$\text{COG}_{\text{EMA}}[k] = \left( \left( \arctan2(X[k], Y[k]) \cdot \frac{180}{\pi} \right) + 360 \right) \pmod{360}$$

```javascript
// Módulo de Filtrado Cinemático en JavaScript
class GPXKinematicFilter {
  constructor(tau = 1.5) {
    this.R = 6371000; // Radio terrestre en metros
    this.tau = tau;
    this.alpha = 1 - Math.exp(-1.0 / tau);
  }

  toRad(deg) { return (deg * Math.PI) / 180; }
  toDeg(rad) { return (rad * 180) / Math.PI; }

  haversine(lat1, lon1, lat2, lon2) {
    const dLat = this.toRad(lat2 - lat1);
    const dLon = this.toRad(lon2 - lon1);
    const a = Math.sin(dLat / 2) ** 2 +
              Math.cos(this.toRad(lat1)) * Math.cos(this.toRad(lat2)) * Math.sin(dLon / 2) ** 2;
    return this.R * 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
  }

  calculateBearing(lat1, lon1, lat2, lon2) {
    const dLon = this.toRad(lon2 - lon1);
    const y = Math.sin(dLon) * Math.cos(this.toRad(lat2));
    const x = Math.cos(this.toRad(lat1)) * Math.sin(this.toRad(lat2)) -
              Math.sin(this.toRad(lat1)) * Math.cos(this.toRad(lat2)) * Math.cos(dLon);
    return (this.toDeg(Math.atan2(y, x)) + 360) % 360;
  }

  processTrack(rawPoints) {
    if (rawPoints.length < 2) return [];

    // 1. Interpolación temporal a 1 Hz
    const startTime = rawPoints[0].timestamp;
    const endTime = rawPoints[rawPoints.length - 1].timestamp;
    const uniformPoints = [];
    let rawIdx = 0;

    for (let t = startTime; t <= endTime; t += 1000) {
      while (rawIdx < rawPoints.length - 2 && rawPoints[rawIdx + 1].timestamp < t) {
        rawIdx++;
      }
      const p1 = rawPoints[rawIdx];
      const p2 = rawPoints[rawIdx + 1];
      if (!p2) break;

      const factor = (t - p1.timestamp) / (p2.timestamp - p1.timestamp);
      const lat = p1.lat + factor * (p2.lat - p1.lat);
      const lon = p1.lon + factor * (p2.lon - p1.lon);
      uniformPoints.push({ timestamp: t, lat, lon });
    }

    // 2. Cálculo de SOG, COG y filtrado EMA
    const processed = [];
    let prevSogEma = 0;
    let prevX = 0;
    let prevY = 0;

    for (let i = 0; i < uniformPoints.length; i++) {
      if (i === 0) {
        processed.push({ ...uniformPoints[i], sog: 0, cog: 0, sogEma: 0, cogEma: 0 });
        continue;
      }

      const pPrev = uniformPoints[i - 1];
      const pCurr = uniformPoints[i];
      const dist = this.haversine(pPrev.lat, pPrev.lon, pCurr.lat, pCurr.lon);
      const rawSog = (dist / 1.0) * 1.94384; // nudos
      const rawCog = this.calculateBearing(pPrev.lat, pPrev.lon, pCurr.lat, pCurr.lon);

      // EMA SOG
      const sogEma = (i === 1) ? rawSog : (this.alpha * rawSog + (1 - this.alpha) * prevSogEma);
      prevSogEma = sogEma;

      // EMA COG Vectorial
      const radCog = this.toRad(rawCog);
      const sinC = Math.sin(radCog);
      const cosC = Math.cos(radCog);
      const xEma = (i === 1) ? sinC : (this.alpha * sinC + (1 - this.alpha) * prevX);
      const yEma = (i === 1) ? cosC : (this.alpha * cosC + (1 - this.alpha) * prevY);
      prevX = xEma;
      prevY = yEma;

      const cogEma = (this.toDeg(Math.atan2(xEma, yEma)) + 360) % 360;

      processed.push({
        timestamp: pCurr.timestamp,
        lat: pCurr.lat,
        lon: pCurr.lon,
        sog: rawSog,
        cog: rawCog,
        sogEma,
        cogEma
      });
    }
    return processed;
  }
}
```

---

## 2. Descomposición Vectorial de Rendimiento: VMG y VMC

El rendimiento cinemático de un barco de regata se mide proyectando su vector velocidad $\vec{V}_{\text{SOG}}$ sobre el viento o sobre la boya de destino.

```
                  Eje Viento (TWD)
                         ^
                         |   / Vector Vel. (SOG, COG)
                         |  /
                  VMG -> | / 
                         |/  
                         +------------------> Ortogonal
```

### 2.1 Velocity Made Good (VMG) al Viento Real
La VMG al viento cuantifica la velocidad de ganancia efectiva directamente a barlovento (ceñida) o a sotavento (empopada). Dado el rumbo $\text{COG}$ y la dirección del viento real $\text{TWD}$:

$$\text{TWA} = \text{COG} - \text{TWD} \quad (\text{True Wind Angle})$$

$$\text{VMG}_{\text{wind}} = \text{SOG}_{\text{EMA}} \cdot \cos\left(\frac{\text{TWA} \cdot \pi}{180}\right)$$

* Si $\text{VMG}_{\text{wind}} > 0$: El barco gana distancia hacia barlovento (ceñida).
* Si $\text{VMG}_{\text{wind}} < 0$: El barco gana distancia hacia sotavento (empopada/largos).

### 2.2 Velocity Made on Course (VMC) a Boya
La VMC cuantifica la velocidad de aproximación a una coordenada geográfica fija $P_{\text{mark}}(\phi_m, \lambda_m)$. Se calcula mediante la marcación o demarcación objetivo $\text{BRG}_{\text{mark}} = \text{bearing}(P_{\text{boat}}, P_{\text{mark}})$:

$$\text{VMC} = \text{SOG}_{\text{EMA}} \cdot \cos\left( \frac{(\text{COG}_{\text{EMA}} - \text{BRG}_{\text{mark}}) \cdot \pi}{180} \right)$$

```javascript
class VectorDecomposition {
  static calculateVMG(sog, cog, twd) {
    const twaRad = ((cog - twd) * Math.PI) / 180;
    return sog * Math.cos(twaRad);
  }

  static calculateVMC(sog, cog, markLat, markLon, boatLat, boatLon, filterInstance) {
    const brgMark = filterInstance.calculateBearing(boatLat, boatLon, markLat, markLon);
    const angleRad = ((cog - brgMark) * Math.PI) / 180;
    return sog * Math.cos(angleRad);
  }
}
```

---

## 3. Algoritmo de Estimación Automática de la Dirección del Viento (TWD)

Dado que las embarcaciones Optimist carecen de sensores de viento anemo-veleta conectados a la telemetría, el viento real ($\text{TWD}$) debe derivarse de la **simetría del ángulo de ceñida** de la flota o del propio regatista durante los bordos sostenidos.

```
Amura Estribor (COG_stbd)          Amura Babor (COG_port)
          \                               /
           \       TWD (Bisectriz)       /
            \            |              /
             \           |             /
              \--------->|<-----------/
                    TWA     TWA
```

### 3.1 Proceso de Estimación por Bisectriz
1. **Filtrado de Bordo Estable:** Se seleccionan segmentos de la traza donde la velocidad de giro angular sea baja ($\left|\frac{d\text{COG}}{dt}\right| < 1.5^\circ/\text{s}$) y la velocidad esté en rango competitivo ($\text{SOG} \ge 3.0\,\text{kt}$).
2. **Agrupación Cíclica:** Se separan los rumbos en dos clústeres angulares principales (Amura de Estribor $\text{COG}_{\text{stbd}}$ y Amura de Babor $\text{COG}_{\text{port}}$).
3. **Cálculo de Bisectriz Promedio Circular:**
   Dados los ángulos promedios en radianes $\bar{\theta}_{\text{stbd}}$ y $\bar{\theta}_{\text{port}}$:

$$\vec{V}_{\text{stbd}} = (\sin \bar{\theta}_{\text{stbd}}, \cos \bar{\theta}_{\text{stbd}}), \quad \vec{V}_{\text{port}} = (\sin \bar{\theta}_{\text{port}}, \cos \bar{\theta}_{\text{port}})$$

$$\vec{V}_{\text{wind}} = \vec{V}_{\text{stbd}} + \vec{V}_{\text{port}} = (\sin \bar{\theta}_{\text{stbd}} + \sin \bar{\theta}_{\text{port}}, \cos \bar{\theta}_{\text{stbd}} + \cos \bar{\theta}_{\text{port}})$$

$$\text{TWD} = \left( \left( \arctan2(V_{\text{wind}, x}, V_{\text{wind}, y}) \cdot \frac{180}{\pi} \right) + 360 \right) \pmod{360}$$

$$\text{TWA}_{\text{base}} = \frac{|(\bar{\theta}_{\text{stbd}} - \bar{\theta}_{\text{port}} + 540) \pmod{360} - 180|}{2}$$

*(Nota: En el Optimist, un $\text{TWA}_{\text{base}}$ típico oscila entre $40^\circ$ y $45^\circ$, lo que equivale a un ángulo de virada total de $80^\circ\text{--}90^\circ$)*.

```javascript
class TWDEstimator {
  static estimateTWD(processedPoints) {
    const stbdAngles = [];
    const portAngles = [];

    // Filtrar puntos en bordos estables de ceñida
    for (let i = 1; i < processedPoints.length - 1; i++) {
      const p = processedPoints[i];
      const rateOfTurn = Math.abs((processedPoints[i + 1].cogEma - processedPoints[i - 1].cogEma + 540) % 360 - 180) / 2.0;

      if (p.sogEma >= 2.8 && rateOfTurn < 1.5) {
        // Asignación preliminar por cuadrantes para agrupar amuras
        if (stbdAngles.length === 0) {
          stbdAngles.push(p.cogEma);
        } else {
          const meanStbd = stbdAngles.reduce((a, b) => a + b, 0) / stbdAngles.length;
          const diff = Math.abs((p.cogEma - meanStbd + 540) % 360 - 180);
          if (diff < 30) {
            stbdAngles.push(p.cogEma);
          } else if (portAngles.length === 0) {
            portAngles.push(p.cogEma);
          } else {
            const meanPort = portAngles.reduce((a, b) => a + b, 0) / portAngles.length;
            const diffPort = Math.abs((p.cogEma - meanPort + 540) % 360 - 180);
            if (diffPort < 30) portAngles.push(p.cogEma);
          }
        }
      }
    }

    if (stbdAngles.length === 0 || portAngles.length === 0) return { twd: 0, twaBase: 42 };

    const avgStbd = TWDEstimator.circularMean(stbdAngles);
    const avgPort = TWDEstimator.circularMean(portAngles);

    const radS = (avgStbd * Math.PI) / 180;
    const radP = (avgPort * Math.PI) / 180;

    const wx = Math.sin(radS) + Math.sin(radP);
    const wy = Math.cos(radS) + Math.cos(radP);

    const twd = ((Math.atan2(wx, wy) * 180) / Math.PI + 360) % 360;
    const twaBase = Math.abs((avgStbd - avgPort + 540) % 360 - 180) / 2.0;

    return { twd, twaBase, avgStbd, avgPort };
  }

  static circularMean(angles) {
    let sinSum = 0, cosSum = 0;
    for (let a of angles) {
      sinSum += Math.sin((a * Math.PI) / 180);
      cosSum += Math.cos((a * Math.PI) / 180);
    }
    return ((Math.atan2(sinSum, cosSum) * 180) / Math.PI + 360) % 360;
  }
}
```

---

## 4. Detección Automática y Análisis Cuantitativo de Maniobras

El análisis micro-telemétrico de las viradas (*tacks*) y trasluchadas (*jibes*) evalúa la eficacia cinética del regatista y el impacto hidrodinámico de la pala del timón (evitando el freno excesivo).

```
SOG ^
    |       Punto Entrada (t_entry)
V_target-----\                                  /----- Recuperación (t_recovery)
    |         \                                /
    |          \                              /
V_min------------\----- Apex (t_apex) -------/
    |
    +----------------------------------------------------> Tiempo (t)
```

### 4.1 Criterios Cinemáticos de Fases de la Maniobra
1. **Umbral de Caída Angular ($\omega_{\text{threshold}}$):**
   Una maniobra inicia cuando el cambio de rumbo $\left|\frac{\Delta \text{COG}}{\Delta t}\right| \ge 4.5^\circ/\text{s}$ durante al menos $2\,\text{s}$ consecutivos.
2. **Punto de Entrada ($t_{\text{entry}}$):** Instante $t$ antes del inicio de la rotación donde $\text{SOG}$ comienza a caer por debajo del $95\%$ de la velocidad objetivo sostenida ($V_{\text{target\_pre}}$).
3. **Punto Ápex / Paso por el Viento ($t_{\text{apex}}$):**
   * **Virada:** Instante exacto en que el rumbo cruza el viento real: $\text{COG}(t_{\text{apex}}) = \text{TWD}$.
   * **Trasluchada:** Instante en que el rumbo cruza la empopada: $\text{COG}(t_{\text{apex}}) = (\text{TWD} + 180^\circ) \pmod{360}$.
   * **Velocidad Mínima ($V_{\min}$):** Registra $V_{\min} = \text{SOG}(t_{\text{apex}})$. En Optimist, $V_{\min} / V_{\text{target}} < 0.35$ indica una maniobra defectuosa por frenado excesivo de timón.
4. **Tiempo de Recuperación ($t_{\text{recovery}}$):**
   Instante posterior al ápex en que la velocidad recupera el $90\%$ del valor de velocidad de entrada o del nuevo target ($V_{\text{target\_post}}$) y el rumbo se estabiliza ($\left|\frac{\Delta \text{COG}}{\Delta t}\right| < 1.5^\circ/\text{s}$).
   El tiempo total de recuperación es:

$$t_{\text{rec}} = \frac{t_{\text{recovery}} - t_{\text{entry}}}{1000} \quad [\text{segundos}]$$

### 4.2 Pérdida Métrica Neta (*Tack Loss*)
Mide la distancia neta perdida a barlovento durante la maniobra en comparación con la distancia que se habría recorrido manteniendo la $\text{VMG}_{\text{óptima}}$ teórica constante:

$$d_{\text{real}} = \sum_{k = t_{\text{entry}}}^{t_{\text{recovery}}} \left( \text{SOG}[k] \cdot 0.514444 \cdot \cos\left(\frac{(\text{COG}[k] - \text{TWD}) \cdot \pi}{180}\right) \right) \cdot \Delta t$$

$$d_{\text{teórico}} = \text{VMG}_{\text{target}} \cdot 0.514444 \cdot \left( \frac{t_{\text{recovery}} - t_{\text{entry}}}{1000} \right)$$

$$\text{Tack Loss } (\Delta d) = d_{\text{teórico}} - d_{\text{real}} \quad [\text{metros}]$$

```javascript
class ManeuverDetector {
  constructor(twd) {
    this.twd = twd;
  }

  detectManeuvers(points) {
    const maneuvers = [];
    let inManeuver = false;
    let entryIdx = 0;

    for (let i = 2; i < points.length - 2; i++) {
      const rotRate = Math.abs((points[i + 1].cogEma - points[i - 1].cogEma + 540) % 360 - 180) / 2.0;

      if (!inManeuver && rotRate >= 4.5) {
        inManeuver = true;
        entryIdx = Math.max(0, i - 2);
      } else if (inManeuver && rotRate < 1.5) {
        // Fin potencial de rotación
        const exitIdx = i + 2;
        const maneuverSegment = points.slice(entryIdx, Math.min(points.length - 1, exitIdx + 10));

        const analysis = this.analyzeSegment(maneuverSegment, points[entryIdx].sogEma);
        if (analysis) maneuvers.push(analysis);

        inManeuver = false;
        i = exitIdx; // Salto de ventana
      }
    }
    return maneuvers;
  }

  analyzeSegment(segment, vTargetPre) {
    if (segment.length < 4) return null;

    let minSog = Infinity;
    let apexIdx = 0;
    let type = 'TACK';

    for (let k = 0; k < segment.length; k++) {
      if (segment[k].sogEma < minSog) {
        minSog = segment[k].sogEma;
        apexIdx = k;
      }
    }

    // Clasificación por ángulo del ápex respecto al TWD
    const apexAngleDiff = Math.abs((segment[apexIdx].cogEma - this.twd + 540) % 360 - 180);
    if (apexAngleDiff > 90) {
      type = 'JIBE';
    }

    // Identificar tiempo de recuperación (SOG vuelve a 90% de vTargetPre)
    let recoveryIdx = segment.length - 1;
    for (let k = apexIdx; k < segment.length; k++) {
      if (segment[k].sogEma >= 0.90 * vTargetPre) {
        recoveryIdx = k;
        break;
      }
    }

    const tEntry = segment[0].timestamp;
    const tApex = segment[apexIdx].timestamp;
    const tRecovery = segment[recoveryIdx].timestamp;
    const durationSec = (tRecovery - tEntry) / 1000.0;

    // Cálculo de Tack Loss Métrica
    const vmgTargetMs = vTargetPre * 0.514444 * Math.cos((42 * Math.PI) / 180); // TWA base 42°
    const dTeorico = vmgTargetMs * durationSec;

    let dReal = 0;
    for (let k = 0; k < recoveryIdx; k++) {
      const sogMs = segment[k].sogEma * 0.514444;
      const twaRad = ((segment[k].cogEma - this.twd) * Math.PI) / 180;
      dReal += sogMs * Math.cos(twaRad) * 1.0; // dt = 1s
    }

    const tackLossMeters = dTeorico - dReal;

    return {
      type,
      timestampEntry: tEntry,
      timestampApex: tApex,
      timestampRecovery: tRecovery,
      vTargetPre: Number(vTargetPre.toFixed(2)),
      vMin: Number(minSog.toFixed(2)),
      vMinRatio: Number((minSog / vTargetPre).toFixed(2)),
      durationSec: Number(durationSec.toFixed(1)),
      tackLossMeters: Number(tackLossMeters.toFixed(2))
    };
  }
}
```

---

## 5. Segmentación de Tramos e Informe JSON Final

### 5.1 Máquina de Estados para Clasificación Cinemática
Cada punto interpolado $P_k$ se clasifica en uno de los 4 tramos tácticos en función de su Ángulo respecto al Viento Real ($\text{TWA} = |\text{COG}_{\text{EMA}} - \text{TWD}|$) y su tiempo relativo a la señal de salida ($t_{\text{start}}$):

* **Pre-Salida (`PRE_START`):** Intervalo $t < t_{\text{start}}$ o patrón de maniobra en caja con $\text{SOG} < 2.0\,\text{kt}$.
* **Ceñida (`UPWIND`):** $30^\circ \le \text{TWA} \le 60^\circ$ de forma continuada durante $> 10\,\text{s}$.
* **Empopada (`DOWNWIND`):** $135^\circ \le \text{TWA} \le 180^\circ$ de forma continuada durante $> 10\,\text{s}$.
* **Través (`REACH`):** $60^\circ < \text{TWA} < 135^\circ$.

```javascript
class LegSegmenter {
  static segmentTrack(points, twd, tStartGun = null) {
    return points.map(p => {
      const twa = Math.abs((p.cogEma - twd + 540) % 360 - 180);
      let leg = 'REACH';

      if (tStartGun && p.timestamp < tStartGun) {
        leg = 'PRE_START';
      } else if (twa >= 30 && twa <= 60) {
        leg = 'UPWIND';
      } else if (twa >= 135 && twa <= 180) {
        leg = 'DOWNWIND';
      }

      const vmg = VectorDecomposition.calculateVMG(p.sogEma, p.cogEma, twd);
      return { ...p, twa, leg, vmg };
    });
  }
}
```

### 5.2 Esquema JSON Final de Salida (`TelemetryPerformanceReport`)

A continuación se muestra la especificación JSON resultante generada por el motor para su renderizado en paneles de rendimiento de vela de alta competición:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "TelemetryPerformanceReport",
  "type": "object",
  "properties": {
    "metadata": {
      "type": "object",
      "properties": {
        "class": { "type": "string", "enum": ["Optimist IOD95"] },
        "sailorWeightKg": { "type": "number", "example": 45.0 },
        "mastRakeMeters": { "type": "number", "example": 2.81 },
        "totalDurationSec": { "type": "number" },
        "sampleRateHz": { "type": "number", "example": 1.0 }
      }
    },
    "windEnvironment": {
      "type": "object",
      "properties": {
        "estimatedTwdDeg": { "type": "number", "example": 215.4 },
        "estimatedTwaBaseDeg": { "type": "number", "example": 42.1 }
      }
    },
    "overallMetrics": {
      "type": "object",
      "properties": {
        "maxSogKnots": { "type": "number" },
        "avgUpwindSogKnots": { "type": "number" },
        "avgUpwindVmgKnots": { "type": "number" },
        "avgDownwindSogKnots": { "type": "number" },
        "avgDownwindVmgKnots": { "type": "number" }
      }
    },
    "maneuversSummary": {
      "type": "object",
      "properties": {
        "totalTacks": { "type": "integer" },
        "totalJibes": { "type": "integer" },
        "avgTackDurationSec": { "type": "number" },
        "avgTackLossMeters": { "type": "number" },
        "avgVMinRatio": { "type": "number", "description": "Ratio Vmin / VtargetPre" }
      }
    },
    "maneuversDetail": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "type": { "type": "string", "enum": ["TACK", "JIBE"] },
          "timestampEntry": { "type": "integer" },
          "timestampApex": { "type": "integer" },
          "timestampRecovery": { "type": "integer" },
          "vTargetPre": { "type": "number" },
          "vMin": { "type": "number" },
          "vMinRatio": { "type": "number" },
          "durationSec": { "type": "number" },
          "tackLossMeters": { "type": "number" }
        }
      }
    },
    "legsDetail": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "legIndex": { "type": "integer" },
          "type": { "type": "string", "enum": ["PRE_START", "UPWIND", "DOWNWIND", "REACH"] },
          "durationSec": { "type": "number" },
          "avgSogKnots": { "type": "number" },
          "avgVmgKnots": { "type": "number" },
          "distanceTraveledMeters": { "type": "number" }
        }
      }
    }
  }
}
```

---

## 6. Integración Estratégica en el Marco SOAD

Este motor numérico traduce los datos puros en decisiones directamente aplicables al marco de entrenamiento **SOAD** de la clase Optimist:

1. **S (Speed / Velocidad):** Permite verificar si los ajustes de trimado (como la caída o inclinación del mástil entre $2.80\text{--}2.83\,\text{m}$ o la tensión del pujamen/*outhaul*) mantienen la $\text{VMG}_{\text{wind}}$ máxima objetivo en el rango de $3.6\text{--}4.2\,\text{kt}$.
2. **A (Agility / Agilidad):** Analiza la fluidez cinética del tripulante en la virada a través del ratio $V_{\min} / V_{\text{target}}$ y el tiempo de recuperación $t_{\text{rec}}$, penalizando los giros donde el timón actúa excesivamente como freno por descontrol de escora (virada por balanceo / *roll tack* deficiente).
3. **O (Offense) & D (Defense):** Evalúa la eficacia de la navegación en cancha libre y el costo en metros ($\Delta d_{\text{tack}}$) al realizar viradas defensivas para cubrir rivales o buscar rachas de viento.
