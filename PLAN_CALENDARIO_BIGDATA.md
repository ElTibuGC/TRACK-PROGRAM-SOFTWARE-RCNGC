# 📅 PLAN MAESTRO: Calendario Deportivo & Big Data del Regatista RCNGC

## 🎯 Objetivo
Crear una nueva aplicación independiente dentro de la **RCNGC Suite** dedicada exclusivamente a la gestión de **Calendario Deportivo**, **Convocatorias & Asistencia** y **Portal 360° de Histórico y Big Data del Regatista**.

---

## 📂 Archivos y Rutas del Software
* **Archivo de raíz**: `Calendario e Historico Optimist.html`
* **Subcarpeta web**: `calendario-historico/index.html` (copia espejo sincronizada)
* **Copia de distribución**: `TRACK PROGRAM SOFTWARE RCNGC/Calendario e Historico Optimist.html`

---

## 🔗 Integración con la RCNGC Suite
1. **Menú de Usuario / Entrenador**:
   * En el Visor de Regatas y en el Analizador de Entrenamientos, la opción `📅 Calendario` del menú desplegable del usuario redirige a esta aplicación en la misma pestaña.
2. **Botón Principal**:
   * El botón `📊 Histórico & Big Data` de la pantalla principal de los visores redirige directamente a la sección de Big Data de esta app.
3. **Navegación de retorno**:
   * Botón destacado `🏠 Inicio` en la cabecera superior para regresar al Visor de Regatas en 1 clic.
   * Botón `⚡ Ver en Visor` en cada regata del calendario para abrir el track y análisis táctico.

---

## ☁️ Base de Datos Compartida (Turso Serverless SQLite)
La aplicación utiliza la misma conexión Turso ya configurada en la suite:
* **Tablas existentes compartidas**:
  * `usuarios_club`: Control de acceso y sesiones (Admin / Entrenadores).
  * `regatas_club`: Histórico de mangas y regatas oficiales guardadas con tracks.
  * `regatistas_club`: Perfiles de regatistas, categorías (Grupo A, B, C, Vela Ligera), números de vela, pesos y notas.
  * `regatas_barcos_stats`: Estadísticas de rendimiento de cada barco en cada regata disputada.
* **Nueva tabla añadida**:
  * `calendario_rcngc`:
    * `id`: Identificador único (UUID / timestamp).
    * `titulo`: Nombre del evento (ej: *Trofeo AECIO*, *Entrenamiento en el agua*, *Preparación Física*).
    * `tipo`: `regata_oficial`, `entrenamiento_mar`, `fisico`, `teoria`, `concentracion`.
    * `fecha_inicio`: `YYYY-MM-DD` o `YYYY-MM-DD HH:MM`.
    * `fecha_fin`: `YYYY-MM-DD` o `YYYY-MM-DD HH:MM`.
    * `categoria`: `Optimist Grupo A`, `Grupo B`, `Grupo C`, `Vela Ligera`, `Todos`.
    * `lugar`: Ubicación (ej: *Bahía de Las Palmas*, *Gimnasio RCNGC*, *Aula de Vela*).
    * `descripcion`: Objetivos del día, notas para familias o regatistas.
    * `convocados`: Lista JSON de números de vela / IDs convocados.
    * `asistencia`: Registro de presentes / ausentes / justificados.
    * `regata_club_id`: Enlace opcional a la regata guardada en `regatas_club`.
    * `creado_por`: Entrenador / Admin autor.

---

## 📐 Módulos de la Aplicación

### Módulo 1: Calendario Deportivo & Convocatorias
* **Selector de Vistas**:
  * 📅 **Vista Mensual**: Cuadrícula de mes completo con badges de colores según tipo de evento.
  * 📆 **Vista Semanal**: Detalle de horas y sesiones de lunes a domingo.
  * 📋 **Vista Agenda / Próximos eventos**: Lista cronológica limpia con tarjetas detalladas.
* **Filtros rápidos**:
  * Por categoría (Todos, Grupo A, Grupo B, Grupo C).
  * Por tipo de actividad (Regatas oficiales, Agua, Físico, Teoría).
* **Modal de Creación / Edición de Eventos** (Solo Entrenadores / Admin):
  * Título, fecha, tipo, categoría, lugar, horario y selector de regatistas convocados.
* **Control de Asistencia**:
  * Marcar asistencia con un clic (`Presente`, `Falta`, `Justificado`).

### Módulo 2: Portal 360° Big Data & Historial del Regatista
* **Buscador de Regatista**: Desplegable o buscador predictivo por número de vela o nombre.
* **Ficha Personal y Deportiva**:
  * Foto / Emoji de perfil, categoría, número de vela, club y peso registrado.
  * Cuaderno técnico del entrenador: objetivos de mejora y notas privadas.
* **Panel de KPIs de Temporada**:
  * Horas totales navegadas y número de sesiones.
  * Porcentaje de asistencia.
  * Regatas disputadas, podios (1º, 2º, 3º) y porcentaje en top 5.
* **Gráficas de Evolución Temporal**:
  * Evolución de puestos a lo largo del año.
  * Rendimiento respecto a la Polar VPP Optimist (IOD95).
  * Eficiencia de salidas (segundo 0 en parrilla).
* **Historial Detallado de Regatas del Barco**:
  * Tabla con cada manga corrida, viento del día, velocidad media, puesto y botón para abrir directamente en el visor.

---

## 🎨 Identidad Visual y Estilo
* **Tema Oscuro Náutico RCNGC**:
  * Fondo principal: `#071318`
  * Contenedores y tarjetas: `#0b1a20` / `#0f232b`
  * Bordes y líneas: `#16333f`
  * Acentos principales: Cian náutico `#00f0ff` y azul eléctrico `#38bdf8`
  * Acentos de aviso / destacados: Ámbar `#f59e0b` y oro `#fbbf24`
  * Éxito / Presente: Esmeralda `#10b981`
* **Diseño Responsive**: Adaptable a ordenador de despacho, portátil y tablet de entrenador.
