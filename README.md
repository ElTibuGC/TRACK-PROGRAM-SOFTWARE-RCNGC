# ⛵ Visor y Analizador de Regatas (Optimist / Vela Ligera)

¡Bienvenido al proyecto! Este programa es una herramienta web pensada para entrenadores y regatistas de vela (inicialmente enfocada en la clase Optimist, pero adaptable a cualquier otra clase). Permite cargar los archivos GPS de los barcos de un entrenamiento o regata para verlos navegar juntos en un mapa interactivo, comparar velocidades, analizar viradas y ver quién va ganando en cada momento.

---

## 🎯 ¿Qué hace este programa?

En las regatas y entrenamientos, cada regatista suele llevar un reloj GPS (como Amazfit/Zepp), un móvil o un dispositivo de seguimiento (como Traccar). Al terminar el día, tienes un montón de archivos sueltos con puntos geográficos y horas.

Este programa soluciona ese problema:
1. **Junta todos los barcos en una misma pantalla**: Cargas la carpeta con los archivos y el programa los coloca a todos navegando a la vez.
2. **Reproduce la regata paso a paso**: Puedes darle al botón de reproducir, avanzar rápido, pausar y ver exactamente qué decisión tomó cada barco en el agua.
3. **Mide el rendimiento**: Calcula automáticamente la velocidad en nudos, la distancia recorrida, las viradas que ha hecho cada barco y el tiempo que ha tardado en completar el recorrido.
4. **Funciona sin internet y con total privacidad**: Todo se procesa directamente en tu propio navegador. Ningún dato ni track sale de tu ordenador ni se sube a servidores externos.

---

## 📂 Archivos del Repositorio

Actualmente el proyecto cuenta con los siguientes archivos:

* 📄 **`Visor Regata Optimist_Entrenadores v1.html`**: Es el programa completo. Contiene toda la aplicación en un único archivo (el diseño visual, los botones, el mapa y el sistema que lee los archivos GPS).
* 📄 **`README.md`**: Este documento, que explica qué es el proyecto, cómo funciona y el historial de cambios.
* 📄 **`AGENT.md`**: Las instrucciones y normas sobre cómo debe comunicarse y trabajar el asistente de inteligencia artificial contigo.

---

## 📘 Guía Rápida e Instrucciones para Entrenadores

Esta guía está redactada para que cualquier entrenador del **Real Club Náutico de Gran Canaria** pueda abrir el programa y sacarle el máximo partido en las sesiones de análisis y debriefing de Optimist.

### 1. 🚀 Abrir el programa y cargar los tracks
1. **Abrir**: Haz doble clic en el archivo `Visor Regata Optimist_Entrenadores v1.html`. Se abrirá en tu navegador (Chrome, Edge, Firefox, Safari) sin necesidad de conexión a internet.
2. **Cargar archivos**:
   * **Por carpeta**: Pulsa el botón azul **«Elegir carpeta»** y selecciona la carpeta donde hayas descargado los archivos de los regatistas.
   * **Por archivos sueltos**: Pulsa **«Elegir archivos»** o arrástralos directamente con el ratón al recuadro de bienvenida.
   * **Formatos soportados**: GPX (relojes GPS de pulsera, Garmin, Apple Watch, Zepp, etc.), KML, o tablas Excel/CSV exportadas desde Traccar.
3. **Modo de tiempo (Hora real vs Desde el inicio)**:
   * Si todos los barcos entrenaron a la vez, se sincronizarán automáticamente en **«Hora real»**.
   * Si quieres comparar mangas corridas a horas distintas o en días separados, usa el selector **«Tiempo → Desde el inicio»** en la barra inferior para superponerlos desde su primer segundo.

---

### 2. ⛵ Identificación y gestión de la flota (Pestaña «Barcos»)
* **Poner números de vela**: Haz clic en el recuadro del número de vela de cada barco para poner su vela real (ej. *ESP 3140*). Al pulsar Enter o hacer clic fuera, se actualiza en el mapa y la clasificación.
* **Color distintivo**: Haz clic en la pastilla de color del barco para asignarle un color personalizado.
* **Eliminar un track subido por error**: A la derecha de cada barco verás un botón **✕**. Púlsalo para descartar ese barco (por ejemplo, si subiste por error el track de una neumática o lancha de apoyo).
* **Sumar más barcos a la sesión**: Puedes añadir tracks adicionales en cualquier momento usando el botón **«+ Añadir más archivos»** sin perder el trabajo ya hecho.

---

### 3. 📍 Configuración del Campo de Regatas (Pestaña «Recorrido»)
* **Dirección del viento**: En el control *«Viento · de dónde sopla»*, pulsa en **−10° / +10°** o introduce directamente los grados (ej. *020°*). La flecha de la rosa de los vientos en el mapa apuntará en la dirección hacia donde corre el viento.
* **Marcar salida**: Desplaza la barra grande de tiempo inferior hasta el segundo exacto del bocinazo de salida y pulsa **«Marcar salida»**.
* **Modalidades de recorrido**:
  * **Libre / Tradicional**: Pulsa *«+ Añadir baliza»* y haz clic sobre el mapa para situar boyas libres (B1, B2, etc.).
  * **Trapecio Oficial IODA (Optimist)**: Pulsa **«📍 Añadir recorrido paso a paso»**. El asistente te irá pidiendo hacer clic en el mapa para fijar en orden:
    1. **B1** (Barlovento).
    2. **B2** (Desmarque / Través a 60°).
    3. **Puerta 3s** (Boya de estribor de la puerta).
    4. **Puerta 3p** (Boya de babor de la puerta).
    5. **Pin de Llegada** (Boya de meta).
    6. **Comité de Llegada** (Barco de llegada).
    * *Nota*: Puedes reposicionar cualquier baliza suelta en cualquier momento con sus botones individuales (`📍 B1`, `📍 B2`, etc.).

---

### 4. 📐 Pizarra Táctica y Explicaciones (Pestaña «Táctica»)
Diseñada específicamente para debriefings y explicaciones tácticas en pantalla grande o proyector:
* **Laylines automáticas**: Pulsa **«📐 Laylines de barlovento»** para proyectar las líneas de layline a 45° a ambos bordos de la baliza 1 y de la línea de llegada.
* **Círculo de 3 esloras (7,08 m)**: Pulsa **«⭕ 3 esloras (7,08 m)»** para activar el círculo reglamentario de 3 esloras de Optimist ($3 \times 2,36\text{ m} = 7,08\text{ m}$) alrededor de todas las balizas y de la línea de llegada (tanto en la boya de Pin como en el barco Comité de llegadas, conforme a la Regla 18 del RRV; excluyendo la línea de salida donde no aplica zona de espacio en baliza).
* **Línea de salida táctica con parrilla de esloras (hasta 45 m)**: Pulsa **«🚩 Marcar Pin y Comité»**, haz 1 clic en la boya de Pin y otro en el barco Comité. Se dibuja la línea de salida con su zona de aproximación a sotavento hasta los 45 metros: los primeros 20 metros medidos con precisión en esloras de Optimist (línea de puntos diferenciada cada 2,36 m de 1 a 8 esloras en naranja cálido) y referencias métricas a 20 m, 30 m, 40 m y límite exterior de 45 m.
* **Medición de rumbo y distancia**: Pulsa **«📏 Línea recta»** y haz 2 clics en el mapa. Una etiqueta central te indicará el rumbo exacto (ej. *045°*) y la distancia en metros (ej. *185 m*).
* **Flechas de rachas y corrientes**: Pulsa **«➡️ Flecha táctica»** y arrastra en el mapa para señalar roles, zonas de presión o corrientes marinas.
* **Barcos tácticos interactivos**: Añade barcos adicionales con vela personalizada y oriéntalos fácilmente amurados a estribor o babor (en ceñida a 45°, popa a 140° o rumbo libre).
* **Cancelar o deseleccionar**: Pulsa la tecla **Escape (`Esc`)** en el teclado o el botón flotante **«✕ Cancelar / Salir (Esc)»** en la parte inferior para volver al cursor normal.

---

### 5. ⏱️ Reproducción y Análisis de Rendimiento
* **Barra de reproducción inferior**: Controla el tiempo con la barra deslizante. Dispones de botones de velocidad rápida (**1x**, **5x**, **10x**, **30x**, **60x**, **120x**) y longitud de estelas (**30s**, **1m**, **3m**, **5m** o **completa**).
* **Gráfica de velocidad individual**: Al hacer clic sobre cualquier barco, verás su ficha técnica y su gráfica de velocidad. Puedes cambiar la escala de tiempo (**5 min**, **15 min**, **30 min** o **Toda la regata**) y verás marcas verticales con las horas exactas de paso por cada baliza.
* **Resumen de la sesión**: Al pie de la página encontrarás la tabla completa con distancia navegada, velocidad media, velocidad punta, viradas y trasluchadas de cada regatista, junto con el botón **«Copiar para Excel»**.

---

### 6. 💾 Memoria Automática y Nueva Sesión
* **Memoria a prueba de F5**: Todos los barcos, nombres de vela, balizas del recorrido y dibujos tácticos se guardan solos en el navegador. Si actualizas la página con **F5** o cierras el navegador, todo se restaura al instante.
* **Empezar una nueva regata**: Para borrar los datos actuales y empezar un nuevo entrenamiento desde cero, pulsa el botón **«Nueva sesión»** en la cabecera superior derecha.
* **Guía en pantalla**: En cualquier momento puedes pulsar el botón **«📖 Guía de uso»** en la cabecera para consultar estas instrucciones directamente en el visor.

---

### 7. ☁️ Nube Central RCNGC (Base de Datos SQLite en Turso)
Diseñada para compartir entrenamientos y regatas entre entrenadores y regatistas desde cualquier dispositivo con el enlace público de GitHub:
* **Acceso directo**: Pulsa el botón **«☁️ Nube RCNGC»** en la cabecera superior o el botón azul en la pantalla de bienvenida.
* **Biblioteca de regatas guardadas**: Lista interactiva con fecha, barcos, viento, autor y notas de cada manga. Cualquier usuario puede pulsar **«📥 Cargar en el mapa»** para abrir y reproducir la regata de inmediato con un solo clic.
* **Búsqueda en tiempo real**: Casilla de búsqueda para encontrar regatas por fecha, título, notas o entrenador.
* **Publicar sesión actual**: En la pestaña *«Guardar sesión actual»*, introduce el título, fecha y notas.
* **Protección con PIN de Entrenador**: Para evitar que personas ajenas borren o sobreescriban datos del club, se solicita el PIN de entrenador (por defecto: `RCNGC2026`).
* **Ajustes de conexión**: Pestaña para comprobar latencia o configurar credenciales de la base de datos Turso SQLite.

---

## ✨ Características y Funciones Clave

* **Mapa interactivo en 2D**:
  * Dibuja los barcos con su orientación real y una vela simulada según el ángulo con el viento.
  * Muestra estelas de recorrido (de 1 minuto, 5 minutos o toda la sesión).
  * Incluye controles para acercar, alejar, encuadrar toda la flota y seguir a un barco en particular.
  * Flechas de viento y cuadrícula de escala en metros/kilómetros.
* **Sincronización de tiempos inteligente**:
  * **Hora real**: Si los barcos estaban en el agua a la misma hora, los ves competir en paralelo.
  * **Desde el inicio**: Si los barcos salieron a horas diferentes o en días distintos, el programa los alinea para que todos empiecen a la vez desde su primer punto y puedas comparar sus tiempos.
* **Clasificación y tramos en tiempo real**:
  * Detecta si un tramo es **Ceñida**, **Popa** o **Través** en función del viento.
  * Muestra la posición (1º, 2º, 3º...), velocidad actual en nudos y la distancia o tiempo de diferencia con el líder.
* **Detección de viradas**:
  * Cuenta automáticamente las viradas por cambio de amura respecto al viento cuando el barco navega contra el viento (en ceñida).
* **Control de calidad del GPS**:
  * Avisa si algún reloj o móvil tuvo mala señal, si faltan datos durante varios segundos o si hay saltos extraños producidos por fallos del GPS.

---

## 🛠️ Tecnologías Utilizadas

* **HTML5 y CSS3**: Estructura de la página y diseño visual moderno, adaptable a ordenadores y pantallas más pequeñas (móviles/tablets), con soporte para modo claro y modo oscuro.
* **JavaScript**: El motor que realiza todos los cálculos matemáticos, la interpolación segundo a segundo (1 Hz) y la lógica de clasificación.
* **HTML5 Canvas**: El motor gráfico que dibuja el mapa, los barcos y las animaciones de forma fluida.
* **SheetJS (xlsx.full.min.js)**: Librería incluida a través de internet para poder leer archivos de Excel y hojas de cálculo sin complicaciones.

---

## 📋 Changelog (Registro de Cambios)

Aquí se irán anotando todas las novedades, mejoras y correcciones que se hagan en el programa:

### [v1.3.6] - Perfil del Regatista con Asignación de Nombre en Modo Entrenador, Histórico de Resultados (Puestos y Podios) y Evolución de Tiempos de Salida
* **Gestión de Nombres de Regatistas y Seguridad de Configuración**:
  * **Ocultación de la Pestaña «⚙️ Conexión y Seguridad» en Modo Regatista**: La pestaña de configuración de conexión de Turso SQLite y parámetros de seguridad queda ahora completamente oculta en Modo Regatista (solo lectura). Únicamente se hace visible cuando se desbloquea el `Modo Entrenador` mediante el PIN de seguridad. Si se cierra la sesión de entrenador mientras se consulta dicha pestaña, el sistema redirige automáticamente al usuario a la lista de regatas.
  * **Asignación y Edición de Nombre en la Ficha del Barco**: En el perfil de cada regatista (pestaña «Big Data»), los entrenadores con permisos activos (`Modo Entrenador`) disponen de un botón `✏️ Asignar / Editar Nombre` para asociar el nombre y apellidos completos al número de vela.
  * **Directorio Central en Turso SQLite (`regatistas_club`)**: Nueva tabla relacional que persiste la asociación entre vela, nombre y categoría del regatista en la base de datos central en la nube.
  * **Protección y Acceso Rápido**: En `Modo Regatista`, el nombre asignado se muestra claramente (ej: `⛵ 0614 · Lucía Cabrera`), y el botón de edición muestra un candado `🔒`. Al pulsar sobre él, se solicita el PIN de entrenador para desbloquear la sesión en 1 clic y proceder con la edición.
  * **Desplegables Enriquecidos**: Tanto el filtro de barcos en la nube como el selector del histórico muestran ahora el número de vela acompañado del nombre real del regatista (ej: `⛵ 0614 · Lucía Cabrera (2 sesiones)`).
* **Histórico de Resultados, Puestos y Podios de Competición**:
  * **KPI Resumen de Puestos & Podios**: Muestra el mejor puesto alcanzado en regatas oficiales y entrenamientos (ej: `1º 🥇` o `Mejor: 2º`), indicando el recuento total de podios y desglose de medallas (`X podios (🥇 oro, 🥈 plata, 🥉 bronce)`).
  * **Columna «🏆 Puesto» en la Tabla de Sesiones**: Incorpora el puesto final conseguido por cada barco en cada sesión con distintivos de medalla dorada (`1º 🥇`), plateada (`2º 🥈`), bronceada (`3º 🥉`) o puesto numérico.
  * **Cálculo Automático de Puesto al Guardar**: Al guardar un entrenamiento o regata en la nube, el visor computa automáticamente la posición final de cada barco en la clasificación de la flota y la almacena en `posicion_final`.
* **Evolución de Tiempos en Cruzar la Línea de Salida ($\Delta t = t_{cruce} - t_{salida}$)**:
  * **Métrica Clave de Salida**: Registra los segundos transcurridos desde el bocinazo de salida oficial hasta el instante exacto en que la proa del regatista corta la línea de salida con rumbo a la baliza 1.
  * **KPI «⏱️ Tiempo Medio Salida»**: Indicador destacado con la media de retraso a la salida, mejor marca alcanzada y número de salidas de alta calidad ($\le 3.0\text{ s}$).
  * **Selector Interactivo de Gráficos [⏱️ Tiempos de Salida] / [📈 Velocidad SOG]**:
    * **Gráfico de Evolución de Salidas**: Barras verticales que representan el tiempo en cruzar la línea en cada sesión con código de semáforo de alto rendimiento:
      * 🟢 **Verde ($\le 3.0\text{ s}$)**: Salida excelente (arrancada pegada a la línea con velocidad).
      * 🟡 **Ámbar ($3.1 - 6.0\text{ s}$)**: Salida estándar / media.
      * 🔴 **Rojo ($> 6.0\text{ s}$)**: Salida tardía o penalizada.
      * **Línea de Referencia Objetivo RCNGC**: Marca discontinua verde a los $3.0\text{ s}$ como referencia de calidad del club.
    * **Gráfico de Evolución de Velocidad**: Alternancia instantánea al gráfico de velocidad media SOG y marcas máximas en 5 segundos.
  * **Columna «⏱️ Salida (+s)» en la Tabla de Sesiones**: Cada fila muestra la etiqueta de salida con su código de color correspondiente (ej: `+1.4s` en verde, `+3.8s` en ámbar).

### [v1.3.5] - Desplegable de Barcos Analizados, Filtro por Regatista y Módulo Big Data del Club (Histórico Deportivo)
* **Desplegable de Barco / Vela en el Menú de la Nube**:
  * **Selector «⛵ Mi Barco / Vela»**: Desplegable dinámico en la cabecera de filtros que lista todas las velas y barcos que han sido analizados en la nube central, indicando el número de regatas en las que ha participado cada uno (ej: `⛵ 0614 (2 regatas)`).
  * **Filtrado Instantáneo de Regatas**: Al seleccionar su número de vela, la lista se reduce en tiempo real para mostrar únicamente las regatas y entrenamientos donde ese regatista fue trackeado.
  * **Banner Activo y Resaltado en Tarjetas**: Aparece una barra informativa interactiva indicando el barco activo con acceso directo a su ficha histórica, y cada tarjeta de regata resalta con un distintivo verde `✓ Tu barco participa (XXXX)` junto con el listado completo de barcos analizados en la sesión.
  * **Búsqueda por Vela en el Buscador**: El buscador general de texto ahora busca también por número de vela en el campo `barcos_lista`.
* **Estructura para Histórico y Estadísticas del Regatista (Big Data del Club)**:
  * **Nueva Tabla Relacional en Turso SQLite (`regatas_barcos_stats`)**: Almacena de forma ligera y optimizada métricas individuales por barco y sesión (`sog_media`, `sog_max`, `distancia_m`, `duracion_s`, `tacks_count`, `viento_dir`, `viento_kts`) indexada por número de vela y fecha para consultas ultrarrápidas sin descargar gigabytes de telemetría GPS.
  * **Pestaña «📊 Histórico y Big Data» en la Nube**: Nuevo panel accesible tanto para regatistas como entrenadores con:
    * **Dashboard de 6 KPIs Acumulados**: Total de sesiones disputadas, horas acumuladas en el agua, millas navegadas (NM), récord personal de velocidad (SOG máx), velocidad media global histórica y volumen total de viradas.
    * **Gráfico de Evolución Temporal (Progreso Deportivo)**: Gráfico interactivo que muestra la progresión de velocidad media y marcas máximas a lo largo de las semanas, junto con la línea de referencia de su media global.
    * **Tabla Cronológica de Sesiones**: Desglose sesión a sesión con fecha, título, categoría, condiciones de viento, velocidades y botón `📥 Cargar en mapa` para abrir directamente cualquier entrenamiento del pasado.
  * **Auto-Backfill Automático**: Las regatas previamente existentes en la base de datos se analizan y enriquecen de forma automática para que todos los regatistas históricos aparezcan disponibles de inmediato.

### [v1.3.4] - Categorización Oficial RCNGC (Grupos A, B, C y Vela Ligera), Tipos de Sesión y Protección por PIN (Modo Entrenador vs Modo Regatista)
* **Categorización Oficial RCNGC y Grupos de Flota (Paso 3)**:
  * **Clasificación por Grupo de Flota**: Selector desplegable configurado con las opciones oficiales del club:
    * `Grupo A Optimist`
    * `Grupo B Optimist`
    * `Grupo C Optimist`
    * `Vela ligera RCNGC`
  * **Tipo de Sesión**:
    * `🎯 Entrenamiento`
    * `🏁 Regata`
    * `📊 Análisis de otras regatas`
  * **Etiquetas y Badges Cromáticos**: Cada tarjeta de la biblioteca muestra badges distintivos con códigos de color náutico para identificar la flota (`.grupo-a`, `.grupo-b`, `.grupo-c`, `.vela-ligera`) y el tipo de sesión (`.entrenamiento`, `.regata`, `.analisis`) a simple vista.
  * **Filtros Rápidos Interactivos**: Barra de navegación con botones píldora (`cat-pill`) para filtrar instantáneamente por categoría (`Todas`, `Grupo A Optimist`, `Grupo B Optimist`, `Grupo C Optimist`, `Vela ligera RCNGC`) y desplegable para filtrar por Tipo de Sesión, combinables con el buscador textual en tiempo real.
* **Control de Acceso y Protección de Roles (Paso 4)**:
  * **Modo Regatista (Público / Solo Lectura)**: Modo predeterminado seguro para regatistas y familias. Los botones de borrado (`🗑️`) quedan completamente ocultos del visor y el formulario de subida a la nube permanece bloqueado tras una pantalla de protección para evitar modificaciones o sobreescrituras accidentales en la base de datos central.
  * **Modo Entrenador (Escritura y Gestión Completa)**: Desbloqueable mediante PIN de seguridad (por defecto `RCNGC2026`, configurable en local). Muestra el distintivo `🔓 Modo Entrenador` en la cabecera, desbloquea los botones de eliminación de regatas con doble confirmación de seguridad y habilita el formulario completo de publicación a la nube con pre-rellenado automático del PIN.
  * **Gestión de Sesión Intuitiva**: El entrenador puede bloquear o desbloquear su sesión cómodamente desde el botón superior del modal o desde la pestaña de «Conexión y Seguridad».
  * **Esquema de Base de Datos Dinámico y Retrocompatible**: La tabla `regatas_club` en Turso SQLite se actualiza automáticamente con las nuevas columnas `categoria` y `tipo_manga` con protección de fallos y fallback transparente si la base de datos tiene esquemas heredados.

### [v1.3.3] - Enlaces Directos para Compartir Regatas por URL y Compresión GZIP en la Nube
* **Enlaces Directos para Compartir por URL (`?regata=ID`)**:
  * **Botón «🔗 Compartir» en la Cabecera**: Aparece en la barra superior al cargar o guardar una regata de la nube, permitiendo copiar en un clic el enlace directo para enviar por WhatsApp o guardar.
  * **Botón «🔗 Compartir» en la Lista de Regatas**: Cada tarjeta de regata en la ventana modal de la nube incluye ahora un botón para copiar directamente su enlace web con confirmación visual interactiva (`✅ ¡Copiado!`).
  * **Auto-carga Instantánea al Abrir el Enlace**: Si cualquier regatista, padre o entrenador abre una URL con el parámetro `?regata=ID`, el visor detecta la regata automáticamente, la descarga de la base de datos de Turso SQLite y la reproduce en el mapa sin pasos intermedios.
  * **Sincronización con la Barra de Direcciones**: Al cargar o guardar una regata, la dirección del navegador se actualiza limpiamente (`history.replaceState`) reflejando la ID de la regata activa sin recargar la página. Al pulsar «Nueva sesión», se limpia la URL automáticamente.
* **Compresión Nativa GZIP en el Cliente (`CompressionStream` / `DecompressionStream`)**:
  * **Ahorro de hasta el 85% en Espacio**: Antes de subirse a la base de datos de Turso SQLite, el payload JSON de la regata se comprime automáticamente mediante la API nativa de streams GZIP del navegador y se codifica en Base64 con prefijo `gz:`.
  * **Carga Acelerada**: Al reducir drásticamente el peso de las pistas GPS, las descargas y aperturas de regatas son notablemente más veloces incluso en redes móviles 4G/5G.
  * **100% Retrocompatible**: El motor de descompresión detecta automáticamente si el registro proviene del formato antiguo (texto plano JSON) o del nuevo formato comprimido, garantizando que todas las regatas previamente almacenadas sigan abriéndose a la perfección.

### [v1.3.2] - Corrección de Polares Empíricas Optimist y Reactivación de Gráficos de Métricas Avanzadas
* **Definición de Polares Empíricas Calibradas (`getOptimistPolarTarget`)**:
  * Implementado el modelo de interpolación lineal continua de polares para la clase Optimist (IOD95) en base a las tablas empíricas de 6, 10, 14 y 18+ nudos:
    * **Ceñida (Upwind)**: TWA 43°–42°, SOG objetivo 3.25–4.35 kn, VMG objetivo 2.35–3.18 kn.
    * **Través (Reach)**: SOG objetivo 3.80–6.10 kn.
    * **Popa (Downwind)**: TWA 152°–146°, SOG objetivo 3.50–5.75 kn, VMG objetivo 2.90–4.65 kn.
  * Solucionado el fallo `ReferenceError: getOptimistPolarTarget is not defined` que detenía la ejecución del módulo táctico al detectar maniobras o analizar tramos IODA.
* **Restauración Completa de los Gráficos de Dinámica de Regata y Tablas**:
  * **Gráfico Polar del Regatista**: Vuelve a dibujar los círculos concéntricos de 1 a 6 kn, rayos radiales cada 15°, la curva de referencia discontinua azul y la nube de puntos GPS con la curva empírica del regatista junto al indicador `% Rendimiento Polar`.
  * **Pérdida de Velocidad y Ángulo en Maniobras**: Vuelve a graficar el perfil temporal [-5s, 0s, +5s] con las curvas de velocidad máxima (verde), mínima (roja), media (azul) y evolución angular de TWA (violeta), así como la tira de indicadores superiores (V. Entrada, V. Mín Ápex, V. Salida, Caída/Recup., TWA Entrada/Salida).
  * **Métricas Tácticas por Tramo (Recorrido IODA)**: Vuelve a poblar la tabla con el desglose de tramos, tiempos, distancias, eficiencia de derrota, viradas/trasluchadas y Polar Target %.
  * **Diagnóstico Micro-Telemétrico de Maniobras**: Vuelve a registrar cada virada y trasluchada con segundo de ápex, velocidad previa, velocidad mínima, ratio de timón y pérdida en metros (Tack Loss).
  * **Tarjetas KPI Vectoriales del Barco**: Vuelve a renderizar las tarjetas superiores con viento TWD del track vs entrenador, SOG máx/ceñida, VMG ceñida/popa, pérdida media en viradas y ratio de frenado de timón.
* **Protección Defensiva de Renderizado**:
  * Incorporada gestión de errores y bloques `try/catch` defensivos en `renderTacticalAnalysis()`, garantizando que cualquier anomalía en un tramo o dato no bloquee el resto de la interfaz.

### [v1.3.1] - Unificación de Línea de Salida en Recorrido, Detección de Cruce de Salida y Estelas por Tramo
* **Línea de Salida Unificada en la Pestaña «Recorrido»**:
  * Eliminado el botón y la sección de línea de salida de la pestaña «Táctica» para evitar duplicidades o incoherencias entre módulos.
  * Centralización completa de la línea de salida en la pestaña «Recorrido» (tanto para Trapecio IODA como para Recorrido Libre/Tradicional):
    * Botón **«🚩 Marcar Pin y Comité (2 clics)»**: Permite situar el Pin y el Comité en el mapa sucesivamente de forma rápida.
    * Botones individuales **«📍 Mover Pin»** y **«📍 Mover Comité»** para ajustes finos e independientes.
    * Botón **«🗑️ Quitar salida»** para reiniciar la línea de salida.
    * Indicador de estado con la longitud en metros y esloras equivalentes de Optimist (ej. `✓ Definida (78 m · 33 esloras)`).
    * Casilla integrada para activar o desactivar la **«Parrilla de salida hasta 45 m (por esloras en primeros 20 m)»**.
* **Detección Geométrica de Salida de la Flota y de Cada Barco**:
  * Nuevo algoritmo cinemático que analiza el cruce efectivo de la línea de salida hacia el campo de regatas (hacia barlovento / B1).
  * Auto-detección del momento oficial de salida de la flota (`D.detectedStartT`) a partir de la mediana de cruces de los barcos, con opción de fijación manual por el entrenador (`D.startT`).
* **Estelas por Tramo («Tramo») Ancladas a la Salida**:
  * Corregido el inicio del tramo 0 (`Ceñida a B1`): ahora el tramo de ceñida comienza estrictamente en el instante exacto en que el barco cruza la línea de salida.
  * Todo el tiempo previo se etiqueta como pre-salida (`-1`), evitando que la estela arrastre la navegación previa desde el puerto, la rampa de varada o la espera de flota.
  * Al navegar en el primer tramo, la estela se proyecta limpiamente desde la línea de salida hasta la posición actual del barco.
* **Marcas de Salida en la Línea de Tiempo y Gráficas de Velocidad**:
  * En la barra de reproducción inferior se muestra de forma garantizada el indicador vertical **«Salida»** en el segundo de la señal.
  * En la tarjeta del barco y su gráfica de velocidad individual (sparkline) se dibuja la línea discontinua de **«Salida (+Xs)»** indicando el segundo y retraso exacto del barco con respecto al bocinazo.
* **Integración en «Métricas Avanzadas»**:
  * La tabla de métricas avanzadas detecta de forma fiable la salida de cada regatista, mostrando su hora real y retraso (`Salida: hh:mm:ss (+Xs)`).
  * Las métricas de distancia navegada, velocidad media y viradas se computan desde el cruce real de la salida hasta la llegada.

### [v1.3.0] - Nube Central Compartida (Turso Serverless SQLite) y Biblioteca de Regatas del Club
* **Integración Nativa con Base de Datos SQLite en la Nube (Turso)**:
  * Conexión directa mediante HTTP pipeline con la base de datos oficial del club en Turso (`rcngc-regatas-eltibugc.aws-eu-west-1.turso.io`), permitiendo que el visor en GitHub Pages funcione como una plataforma multiusuario compartida con coste 0 € y sin servidores intermedios.
  * Creación y gestión automática de la tabla `regatas_club` (título, fecha, viento, barcos, autor, notas, telemetría y metadatos).
* **Biblioteca de Regatas Compartidas**:
  * Botón **«☁️ Nube RCNGC»** en la barra superior (accesible en todo momento) y botón destacado en la pantalla de bienvenida.
  * Ventana modal con el catálogo completo de entrenamientos y mangas guardadas, ordenadas de más reciente a más antigua.
  * Tarjetas informativas con fecha, número de barcos participantes, dirección e intensidad del viento, autor y observaciones.
  * **Carga instantánea en 1 clic («📥 Cargar en el mapa»)**: Descarga la sesión desde Turso, reconstruye toda la cinemática a 1 Hz, las balizas del recorrido y las herramientas tácticas, y la pone a reproducir inmediatamente.
  * **Búsqueda reactiva**: Filtro en tiempo real por título, fecha o notas del día.
* **Publicación y Guardado de Entrenamientos**:
  * Pestaña dedicada para publicar la sesión activa actual en la base de datos central.
  * Formulario intuitivo con título, fecha, autor, notas y resumen automático de la flota cargada.
* **Sistema de Seguridad y Permisos (PIN de Entrenador)**:
  * **Lectura abierta**: Cualquier regatista, padre o entrenador que acceda al enlace de GitHub puede consultar y reproducir libremente las regatas de la biblioteca.
  * **Acciones protegidas**: Para guardar nuevas regatas o eliminar una sesión de la nube se solicita el PIN de entrenador (por defecto: `RCNGC2026`), impidiendo modificaciones accidentales o no autorizadas.
* **Panel de Configuración y Diagnóstico**:
  * Pestaña para comprobar la latencia de la base de datos (`SELECT 1`), visualizar o personalizar la URL de la base de datos, el Token y almacenar el PIN de entrenador en la memoria local del navegador.

### [v1.2.7] - Parrilla de Salida por Esloras (Zona 45 m) y Ajuste Reglamentario de Zonas de 3 Esloras (Llegada vs Salida)
* **Zona de Salida hasta 45 Metros hacia Sotavento**:
  * Rediseñada la zona de aproximación de salida táctica, reduciendo el área activa desde los 75 m previos hasta **45 metros**, delimitada por líneas laterales de encuadre y sombreado suave de campo.
* **Primeros 20 Metros Medidos por Esloras de Optimist (Línea de Puntos Diferenciada)**:
  * En los primeros 20 metros desde la línea de salida, la parrilla se mide en **esloras de Optimist ($1\text{ eslora} = 2,36\text{ m}$)**.
  * Trazado con **línea de puntos diferenciada (`setLineDash([2, 3])`)** en color ámbar/naranja de alto contraste (`#f97316`) desde $1\text{ esl}$ ($2,36\text{ m}$) hasta $8\text{ esloras}$ ($18,88\text{ m}$).
  * Etiquetas adaptadas dinámicamente al zoom (`1 esl`, `2 esl`... o `X esl (Y.Ym)` al acercar).
  * Zona de esloras (0 a 20 m) resaltada con fondo cálido suave para distinguirla de la zona métrica exterior.
* **Referencias Métricas Exteriores (20 m, 30 m, 40 m y Límite 45 m)**:
  * Línea de transición a $20\text{ m}$ (`20m (8.5 esl)`).
  * Líneas discontinuas métricas a $30\text{ m}$ y $40\text{ m}$.
  * Línea límite reforzada a $45\text{ m}$ (`45m (límite)`).
* **Eliminación de la Zona Roja de 3 Esloras en la Salida (START)**:
  * Eliminado el círculo rojo de 3 esloras que aparecía erróneamente en el punto de START. Conforme a la Regla 18 del Reglamento de Regatas a Vela (RRV), las balizas de salida no confieren derecho a espacio en baliza (*mark-room*) en la aproximación para salir.
* **Incorporación de la Zona de 3 Esloras en Pin de Llegada y Barco Comité de Llegadas**:
  * Ahora el círculo reglamentario de 3 esloras de Optimist ($7,08\text{ m}$) se dibuja tanto en la **Boya Pin de llegada** como en el **Barco Comité de llegadas**, donde la Regla 18 sí aplica con total rigor reglamentario.
  * Añadidos además los rótulos identificativos `PIN Llegada` y `RC Llegada` sobre la línea de llegada.

### [v1.2.6] - Orientación del Campo de Regatas: North Up vs Wind Up y Cuadrícula Táctica a 45° del Viento
* **Modo de Visualización Dual: «North Up» vs «Wind Up»**:
  * **North Up (Norte arriba)**: Vista geográfica estándar donde el Norte geográfico ($0^\circ$) apunta hacia la parte superior de la pantalla. Ideal para ubicar la posición geográfica real del campo en la costa o bahía.
  * **Wind Up (Viento arriba)**: Vista orientada al viento en la que todo el campo de regatas se rota automáticamente para situar **Barlovento en la parte superior** (arriba) y **Sotavento en la inferior** (abajo).
  * **Solución para vientos de Este o Sur**: Elimina la necesidad de ver recorridos ladeados o invertidos cuando el viento sopla del Este ($90^\circ / 120^\circ$) o del Sur ($180^\circ$). Las ceñidas se visualizan siempre avanzando verticalmente hacia arriba y las empopadas descendiendo hacia abajo, tal como se enseña en la pizarra técnica y en los sistemas tácticos profesionales de navegación (B&G, Expedition, RaceFoxx).
* **Cuadrícula Táctica de Fondo Orientada a 45° del Viento**:
  * Las cuadrículas del fondo del mapa se trazan ahora **alineadas a $\pm 45^\circ$ respecto a la dirección del viento real**:
    * Un conjunto de líneas paralelas coincide de forma exacta con el rumbo de **ceñida a estribor ($TWD + 45^\circ$)**.
    * El conjunto ortogonal perpendicular coincide con el rumbo de **ceñida a babor ($TWD - 45^\circ$)**.
  * **Análisis táctico visual inmediato**: Permite a entrenadores y regatistas comprobar al instante la ganancia de VMG (*escalones tácticos*), verificar si los barcos navegan por encima o debajo de la layline a las boyas, y observar cómo las viradas se alinean con las diagonales del campo.
  * **Densidad Triplicada de Cuadrícula**: Se ha ajustado la función de escala métrica (`niceStep`) con un objetivo base de 30 px (frente a los 90 px originales), haciendo que cada celda sea **el triple de pequeña** y generando el triple de líneas de cuadrícula para una referencia táctica milimétrica, manteniendo su adaptación continua al nivel de zoom.
  * **Anclaje rígido geográfico**: Las líneas de la cuadrícula están matemáticamente fijadas a coordenadas reales del agua; al arrastrar (*pan*) o hacer zoom, la cuadrícula se desplaza solidaria al agua y las marcas sin flotar ni deslizarse.
* **Controles Interactivos de Orientación y Tipografía Limpia (Sin Emoticonos)**:
  * **Botón en Herramientas del Mapa**: Selector limpio `[ Norte ]` / `[ Viento ]` en la barra flotante de herramientas del mapa (junto a `+`, `−`, `Flota` y `Seguir`), que se ilumina en naranja al activar Wind Up.
  * **Rosa de los Vientos Interactiva**:
    * Al hacer clic directo sobre la rosa de los vientos en la esquina superior izquierda, se alterna instantáneamente entre North Up y Wind Up.
    * En **Wind Up**, la flecha del viento sopla recta desde arriba hacia abajo, y la aguja roja de **Norte (`N`)** rota con precisión para indicar hacia dónde queda el Norte geográfico real.
    * Rótulo limpio junto a la rosa: `· Wind Up` / `· North Up` (sin emoticonos añadidos).
  * **Pestaña Táctica**: Botones limpios en el panel lateral de Táctica: `[ Norte arriba (North Up) ]` y `[ Viento arriba (Wind Up) ]`.
  * **Atajos de Teclado**: Pulsar la tecla `W` activa el modo Wind Up y pulsar la tecla `N` regresa a North Up.
* **Transformación Geométrica Rigurosa y Rótulos Horizontales**:
  * **Encuadre automático (`fit`)**: El zoom y encuadre de la flota recalculan la caja envolvente rotada para asegurar que el recorrido aproveche al máximo el espacio de pantalla sin cortes en ningún extremo.
  * **Rotación y arrastre 1:1**: El movimiento de arrastre (pan) y el zoom con la rueda del ratón responden de forma natural en la dirección del cursor físico.
  * **Contrarrotación de textos (`drawTextLabel`)**: Todos los números de vela, identificadores de baliza (B1, B2, 3s, 3p, Salida, Llegada) y rótulos de maniobras se contrarrotan automáticamente para mantenerse siempre horizontales y perfectamente legibles en pantalla.
  * **Persistencia en memoria**: La orientación seleccionada se guarda automáticamente en la memoria del navegador y se restaura al reabrir la sesión.
  * **Estabilidad y corrección de carga en refresco (F5)**: Corregida una errata tipográfica en la definición de propiedades de rótulos que impedía la inicialización completa de la base de datos de sesión y los eventos de carga de archivos tras refrescar la página.

### [v1.2.5] - Distancias en Millas Náuticas (NM), Selector de Velocidad 1×, Salto Temporal por Teclado y Estela por Tramo
* **Unidades Náuticas Oficiales en Tablas (Millas Náuticas y Kilómetros)**:
  * **Distancia Real por Tramo (Recorrido IODA)**: La columna de distancia de cada tramo se expresa ahora en **millas náuticas** (ej. `0,64 NM`).
  * **Distancia Navegada (Tabla de Flota)**: Se establece como unidad principal la **milla náutica** con los kilómetros en tamaño reducido entre paréntesis (ej. `2,11 NM (3,91 km)`), facilitando la lectura náutica directa para los entrenadores.
* **Ajuste de Velocidad de Reproducción: Incorporada opción 1× (eliminada 10×)**:
  * El selector de velocidad de reproducción en la barra inferior pasa a ofrecer: **`1×`**, **`5×`**, **`30×`**, **`60×`** y **`120×`**, permitiendo reproducir en tiempo real ($1\text{ s}$ de reloj = $1\text{ s}$ de regata) para debriefings minuciosos de maniobras o salidas.
* **Entrada Manual de Tiempo por Teclado (`Hora: hh:mm:ss`)**:
  * Nuevo control interactivo en la barra de reproducción para escribir a teclado la hora exacta deseada de la simulación.
  * Admite formatos de hora real (`14:35:20` o `14:35`) y tiempos relativos (`25:30`).
  * Al pulsar `Enter`, el reproductor salta de forma instantánea al segundo indicado y actualiza todos los barcos en el mapa.
  * Al hacer clic sobre el reloj de la cabecera superior, el cursor se sitúa automáticamente en la casilla para escribir.
* **Estela Dinámica por Tramo de Recorrido (`Tramo`)**:
  * Incorporado el modo **`Tramo`** en los botones de longitud de estela: `[ 1 min | 5 min | Tramo | Toda ]`.
  * Al activarlo, la estela de cada barco se confina de forma estricta al tramo que está navegando en ese instante. En cuanto el barco cruza una baliza oficial (B1, B2, Puerta 3 o Línea de Llegada), la estela del tramo anterior se retira automáticamente y comienza a dibujarse únicamente la traza del nuevo tramo desde el paso por boya.

### [v1.2.4] - Viento del Track en Grande (Naranja), TWA Entrada vs Salida en Gráfico de Maniobras y Doble Eje Angular
* **Prioridad Visual al Viento Analizado por el Track**:
  * Invertida la jerarquía en la tarjeta KPI superior de viento:
    * En **número grande naranja** se muestra el viento calculado a partir del track con la etiqueta **`TRACK`** (ej. `116° TRACK`).
    * En la línea secundaria en tamaño reducido se indica la referencia del entrenador y la desviación neta (ej. `Entrenador: 120° (desviación -4°) · Optimist`), manteniendo el cálculo de delta $\Delta$.
* **Evolución y Variación de Ángulo en Maniobras (TWA Entrada vs Salida)**:
  * Incorporado un eje secundario derecho en violeta para el ángulo respecto al viento (`TWA (°)`) en el gráfico de diagnóstico de maniobras.
  * **Curva de evolución de ángulo $|TWA|$ (violeta punteada)**: Muestra de forma continua cómo el barco orza desde la ceñida inicial ($TWA_{\text{entrada}}$ a $-5\text{s}$), pasa por el eje del viento en el ápex ($0\text{s}$) y arriba a la nueva amura de ceñida ($TWA_{\text{salida}}$ a $+5\text{s}$).
  * Rótulos flotantes automáticos en la gráfica indicando **`TWA In: XX.X°`** y **`TWA Out: YY.Y°`**.
  * Cuadro resumen ampliado con tarjetas de **TWA Entrada (-5s)** y **TWA Salida (+5s)** con su desviación angular ($\Delta TWA$), permitiendo detectar de inmediato salidas sobreviradas (arribadas excesivas) o barcos que salen atrancados contra el viento.
  * Tooltips interactivos actualizados mostrando en cada segundo la velocidad media, mín-máx y el ángulo TWA exacto.

### [v1.2.3] - Comparación Dual de Viento (Entrenador vs Track), Gráfico Polar del Regatista y Curva Temporal de Maniobras (-5s a +5s)
* **Visualización Dual de Viento de Regata (Entrenador vs Track)**:
  * La tarjeta KPI de viento ahora muestra de forma explícita y simultánea:
    * El **Viento fijado por el entrenador** (fuente de verdad maestra de la sesión, ej. `120° Entrenador`).
    * El **Viento calculado por el track** mediante bisectriz circular de los bordos estables de ceñida a estribor y babor, mostrando la desviación angular exacta (ej. `Track: 118° (Δ -2°)`).
* **Gráfico Polar Empírico del Regatista (Estilo SailTimerApp)**:
  * Nuevo diagrama polar interactivo de alta resolución:
    * Flecha violeta y rótulo de «True Wind» en la parte superior central ($0^\circ$).
    * Círculos concéntricos de velocidad de $1$ a $6\text{ nudos}$ en cian con números en ámbar en el eje vertical.
    * Rayos radiales cada $15^\circ$ delimitando las amuras de Estribor (derecha) y Babor (izquierda).
    * **Polar teórica de referencia de Optimist (IOD95)** en línea discontinua azul (`#0284c7`).
    * **Curva real del regatista** en rojo sólido (`#ef4444`), calculada por sectores de TWA a 1 Hz, acompañada por la nube de puntos GPS.
    * Indicador de eficiencia polar general (`XX% Rendimiento Polar`) y tooltip interactivo al pasar el cursor (TWA, amura, SOG real, polar teórica y segundos navegados).
* **Gráfico de Pérdida de Velocidad en Maniobras (Perfil Temporal de $-5\text{s}$ a $+5\text{s}$)**:
  * Gráfico temporal de evolución de velocidad en las viradas y trasluchadas:
    * Eje X: Tiempo relativo segundo a segundo desde la aproximación ($-5\text{s}$), cruce del eje del viento / ápex ($0\text{s}$) y relanzamiento a velocidad de crucero ($+5\text{s}$).
    * Eje Y: Velocidad en nudos ($0$ a $5+\text{ kn}$).
    * **Verde (`#10b981`)**: Velocidad Máxima en cada segundo (la maniobra óptima / mejor ejecutada).
    * **Azul (`#0284c7`)**: Velocidad Media (promedio del regatista con etiquetas de valor en $-5\text{s}$, $0\text{s}$ y $+5\text{s}$).
    * **Rojo (`#ef4444`)**: Velocidad Mínima (la maniobra más lenta / frenazo con timón).
    * Banda sombreada de dispersión entre curvas máximas y mínimas.
    * Selector interactivo para alternar entre **Viradas (Ceñida)** y **Trasluchadas (Popa)**.
    * Cuadro resumen con $V_{\text{entrada}}$, $V_{\min}$ en ápex, $V_{\text{salida}}$ y caída neta ($\Delta V$ y $\%$ recuperado).
    * Tooltips flotantes con fase de la maniobra, media, rango mín-máx y total de maniobras evaluadas.
* **Integración Completa con la Impresión de Informes**:
  * Ambos gráficos se formatean automáticamente en `@media print` para exportar informes individuales completos en papel o PDF con calidad de debriefing profesional.

### [v1.2.2] - Corrección de Clasificación de Maniobras, Geometría de Laylines, Pérdida Neta (Tack Loss) e Informe Táctico Imprimible
* **Corrección de Clasificación de Maniobras (Viradas vs Trasluchadas)**:
  * Resuelto el problema por el cual las viradas en ceñida se clasificaban erróneamente como trasluchadas.
  * **Causa y solución**: El algoritmo anterior intentaba adivinar el viento mediante bisectriz de rumbos GPS automáticos; si el track contenía rumbos dominantes de popa o pre-salida, invertía el viento $180^\circ$ y veía los giros de proa como si fueran de popa. Ahora el motor utiliza el viento de referencia fijado por el entrenador (`D.windRef`) como fuente de verdad canónica. Además, el clasificador incorpora conocimiento del tramo: en ceñida (`UPWIND`) cualquier cambio de amura se clasifica como virada (*Tack*); en popa (`DOWNWIND`) siempre como trasluchada (*Jibe*). Se filtra además el guiñado por olas ($< 40^\circ$).
* **Cálculo Geométrico Preciso de Desviación de Laylines (Overstanding)**:
  * Sustituida la fórmula anterior por la distancia ortogonal exacta hacia el cono de laylines: $d_{\perp} = R \cdot \sin(\Delta \theta - 43^\circ)$ respecto a la baliza de barlovento o meta.
  * Registra los metros máximos navegados por fuera del cono óptimo de $43^\circ$ de Optimist y los segundos perdidos en "overstanding" (ej. `+24 m (18s)` o `✓ 0 m (Óptimo)`).
* **Diagnóstico de Pérdida en Maniobras (Tack / Jibe Loss)**:
  * Cálculo de pérdida neta en metros frente a la VMG teórica óptima de la polar de Optimist (valores realistas de $6\,\text{m}$ a $14\,\text{m}$ por virada en Optimist).
  * En la tabla de tramos IODA, la columna de maniobras detalla con claridad el conteo y los metros perdidos: ej. `4 viradas (-34 m)` en ceñida o `2 trasluchadas (-18 m)` en popa.
* **Limpieza de Interfaz Táctica**:
  * Eliminada la columna «Ver en mapa» de la tabla táctica por tramo (ahora basta con hacer clic en cualquier fila de la tabla para resaltar su traza en el mapa Canvas).
* **Botón «🖨️ Imprimir Análisis Táctico» (sustituye a «Descargar JSON»)**:
  * Sustituido el botón de descarga de JSON por un botón directo de impresión optimizado para papel o PDF con cabecera oficial del club, datos del regatista, fecha, viento, tabla de tramos IODA y resumen de maniobras.
* **Verificación de Telemetría GPS vs Viento Real**:
  * Confirmación técnica de que los relojes GPS de pulsera no disponen de sensores de viento (veleta / anemómetro), por lo que la dirección e intensidad deben ser validadas siempre por el entrenador mediante los controles manuales de la aplicación.

### [v1.2.1] - Ventana de Regata Estricta (Salida a Meta), Cruce Geométrico de Línea y Polares Empíricas Optimist
* **Filtro Estricto de Regata («Start to Finish»)**:
  * Todas las métricas de la pestaña «Métricas avanzadas» (velocidad media, velocidad máxima sostenida en 5s, distancia navegada, conteo de viradas, tiempo navegado y desglose por tramos IODA) se calculan de forma exclusiva **desde que el barco cruza la línea de salida hasta que corta la línea de llegada**.
  * Se descartan automáticamente las esperas previas, maniobras de calentamiento y el traslado de vuelta al club o remolque.
  * La tabla de la flota muestra claramente el estado de cada barco (`✓ Meta: hh:mm:ss` o `⛵ En regata`) y la hora de corte de salida (`Salida: hh:mm:ss (+Xs)`).
* **Detección Geométrica de Paso por Meta (Corte de Línea)**:
  * El algoritmo analiza segundo a segundo la intersección vectorial entre el desplazamiento del barco $[P_{s-1}, P_s]$ y el segmento entre el Pin y el Comité de llegada.
  * Al cortar la línea en dirección a barlovento, se fija de inmediato su timestamp exacto de llegada (`finishT`).
* **Modelo de Polares Empíricas de Referencia para la Clase Optimist (IOD95)**:
  * Explicación y parametrización basada en las referencias de alto rendimiento para Optimist (ante la ausencia de archivo ORC VPP rígido debido a la variación de peso del regatista de 35 a 52 kg y dinámica con ola):
    * **Ceñida (TWA 42°-44°)**: SOG objetivo de 3.25 kn (6 kn TWS), 3.85 kn (10 kn TWS), 4.20 kn (14 kn TWS) y 4.35 kn (18+ kn TWS). VMG objetivo a barlovento de 2.35 kn a 3.18 kn.
    * **Través (TWA 85°-95°)**: SOG objetivo de 3.80 kn (6 kn TWS) a 6.10 kn (18+ kn TWS).
    * **Popa (TWA 146°-152°)**: SOG objetivo de 3.50 kn (6 kn TWS) a 5.80 kn (18+ kn TWS). VMG objetivo a sotavento de 2.90 kn a 4.90 kn.
* **Modal Interactivo de Consulta («📖 Polares Optimist»)**:
  * Nuevo botón y modal en la cabecera de «Métricas avanzadas» con la tabla completa de polares de referencia y directrices de medición para entrenadores.
* **Aviso Visual de Filtro Activo**:
  * Banner informativo en la parte superior del panel de telemetría confirmando que los datos se calculan únicamente en tiempo de regata.

### [v1.2.0] - Motor Cinemático Avanzado, Análisis Táctico de Recorrido IODA, Diagnóstico de Maniobras y Exportación JSON
* **Motor Cinemático y Filtrado de Telemetría (EMA)**:
  * Interpolación uniforme a frecuencia de 1 Hz.
  * Suavizado continuo de velocidad sobre el fondo (SOG) y rumbo (COG) mediante Media Móvil Exponencial ($\tau = 1.5\,\text{s}$, $\alpha \approx 0.486$), con descomposición cartesiana vectorial ($X = \sin, Y = \cos$) para eliminar cualquier salto o discontinuidad en $0^\circ / 360^\circ$.
* **Estimación Automática de Viento (TWD) y Métricas Vectoriales**:
  * Algoritmo de bisectriz de rumbos circulares promedios en bordos estables ($|\frac{d\text{COG}}{dt}| < 1.5^\circ/\text{s}$ y $\text{SOG} \ge 2.8\,\text{kt}$).
  * Cálculo en tiempo real de Ángulo de Viento Real (TWA), ganancia a barlovento/sotavento (VMG) y aproximación a boya (VMC).
* **Diagnóstico Micro-Telemétrico de Maniobras (Viradas y Trasluchadas)**:
  * Detección algorítmica de puntos críticos de cada giro: entrada $t_{\text{entry}}$ (caída al 95% de velocidad), ápex $t_{\text{apex}}$ (cruce del rumbo por el viento / velocidad mínima $V_{\min}$) y recuperación $t_{\text{recovery}}$ (retorno al 90% de velocidad).
  * Métricas calculadas: ratio de frenado de timón ($V_{\min} / V_{\text{target\_pre}}$, con alerta visual si es $< 0.35$), duración neta en segundos y pérdida métrica agregada (*Tack Loss* neto en metros frente a la VMG óptima teórica).
* **Tabla Independiente: «Métricas Tácticas por Tramo (Recorrido IODA)»**:
  * Segmentación cinemática por balizas oficiales: Ceñida 1, Través, Popa a Puerta 3 y Ceñida a Llegada (o segmentación angular automática si no se han fijado balizas).
  * Columnas calculadas por tramo:
    * **Duración y Distancia**: Tiempo neto navegado (`mm:ss`) y distancia real recorrida (`m`).
    * **Eficiencia de Derrota (% Rhumbline)**: Relación entre la distancia directa a la boya y la distancia real navegada.
    * **Desglose de Maniobras**: Conteo exacto de viradas y trasluchadas por tramo y pérdida agregada en metros ($\Delta d$).
    * **Polar Target %**: Comparación porcentual entre la velocidad/VMG real y la polar teórica de referencia de Optimist según la intensidad del viento.
    * **Bordo Favorecido (% VMC)**: Porcentaje del tiempo que el regatista navegó en la amura de mayor velocidad de aproximación a la baliza.
    * **Desviación de Laylines**: Metros y segundos navegados en "overstanding" fuera del cono de 42°.
* **Conexión Interactiva con el Mapa Canvas**:
  * Al hacer clic en cualquier tramo o pulsar «🎯 Ver en mapa», el mapa resalta la traza con un halo brillante naranja y dibuja sobre el mapa los puntos de viradas y trasluchadas con sus metros de pérdida.
* **Descarga de Informe JSON `TelemetryPerformanceReport`**:
  * Botón para exportar el informe completo de telemetría conforme al estándar formal de ingeniería naval de `performance_knowledge.md` (metadatos, viento estimado, métricas globales, detalle de maniobras y tramos).

### [v1.1.0] - Inicio V2: Navegación por pestañas («Visualizar el track» / «Métricas avanzadas»), Tabla de Telemetría e Impresión de Informes
* **Sistema de navegación principal por pestañas**:
  * Dos vistas principales en la parte superior: **«Visualizar el track»** y **«Métricas avanzadas»**, con indicador de pestaña activa subrayada en naranja e integración con el tema visual del club.
  * Vista «Visualizar el track»: Conserva el mapa interactivo, la línea de tiempo, el reproductor y el panel lateral de clasificación, barcos, recorrido y táctica.
  * Vista «Métricas avanzadas»: Nuevo espacio dedicado al análisis cuantitativo, tablas comparativas y telemetría de rendimiento de la flota de Optimist.
* **Tabla de Métricas Avanzadas**:
  * **Posición**: Puesto en la regata o sesión con distintivo visual (`1º`, `2º`, `3º`...).
  * **Nombre del barco**: Vela real del regatista con su muestra/barrita de color distintivo y nombre secundario.
  * **Velocidad media**: En nudos con dos decimales de precisión, calculada durante los períodos de navegación activa.
  * **Velocidad máxima (5s)**: Pico de velocidad sostenido en ventana móvil de 5 segundos para suprimir ruidos del GPS.
  * **Distancia navegada**: Distancia ortodrómica total recorrida en metros y su equivalencia en millas náuticas (NM).
  * **Número de viradas**: Total de viradas computadas en ceñida mediante cambio de amuras respecto al viento.
  * **Tiempo navegado**: Duración total en el agua en formato claro de horas, minutos y segundos (ej. `1h 05m 48s`).
* **Ordenación interactiva por columnas**: Posibilidad de hacer clic en cualquier columna de la tabla para ordenar la flota de forma ascendente o descendente según la métrica deseada.
* **Resumen rápido con tarjetas KPI**: Bloques superiores con barcos analizados, viento de la sesión, velocidad media de la flota, velocidad punta y total de viradas registradas.
* **🖨️ Impresión y exportación de informes**:
  * Botón «🖨️ Imprimir informe» con estilos optimizados `@media print` para papel A4 o guardar en PDF, con cabecera oficial del club, fecha, tarjetas de resumen, tabla formateada y zona de observaciones/firma del entrenador.
  * Botón «📋 Copiar para Excel» para pegar directamente los datos en hojas de cálculo.

### [v1.0.11] - Inversión de amuras en ceñida, Borrador táctico selectivo y Colores individuales
* **Corrección de amuras de barcos tácticos en ceñida**: Invertida la orientación para barcos en ceñida («Estribor» y «Babor»). Ahora «Estribor (ceñida)» sitúa el barco con el viento entrando por su costado de estribor (rumbo `w − 45°`) con la botavara a babor, y «Babor (ceñida)» con el viento entrando por babor (rumbo `w + 45°`) con la botavara a estribor, reflejando con exactitud la física de navegación. La popa se mantiene inalterada.
* **Herramienta de Borrador táctico selectivo (`🧽 Borrador`)**:
  * Nuevo botón «🧽 Borrador» en la pizarra táctica.
  * Permite hacer clic directamente sobre cualquier elemento del mapa (barco táctico, línea de rumbo, flecha, zona manual o línea de salida) para borrar **únicamente** la figura pulsada, sin tener que borrar todo ni empezar desde cero.
  * Incluye avisos interactivos y cursor específico tipo puntero para facilitar la selección.
* **Colores personalizados e individuales por elemento**:
  * **Barcos tácticos**: Selector de color para elegir el color del barco antes de colocarlo, y selector de color individual en la lista de barcos colocados para cambiar el color de cualquier barco en cualquier momento.
  * **Líneas y flechas**: Selectores de color dedicados junto a los botones de línea y flecha para trazar mediciones y vectores tácticos en el color que prefieras (azul, verde, naranja, etc.).
* **Persistencia total**: Los colores asignados y los borrados selectivos se guardan automáticamente en la memoria del navegador y persisten tras pulsar F5.

### [v1.3.7] - Suite Completa de Analítica Avanzada, Big Data del Regatista y Gamificación RCNGC
* **Análisis Profundo de Salidas**:
  * **Velocidad en el bocinazo ($V_{gun}$)**: Medición exacta en nudos de la velocidad de arrancada en el segundo cero de la salida (Objetivo RCNGC $\ge 3,5\text{ kn}$).
  * **Distribución táctica de la línea**: Cálculo porcentual de elecciones de salida repartidas entre **Pin**, **Centro** y **Comité** con barra visual tricromática y etiquetas.
  * **Distancia y tiempo de corte**: Estimación métrica de la distancia a la línea a 0s y tiempo medio de cruce tras el bocinazo.
* **Matriz de Rendimiento por Rango de Viento**:
  * Desglose automático de todas las regatas del regatista en tres regímenes meteorológicos clave:
    1. 🍃 **Viento Suave (< 10 kn)**: Sesiones, velocidad media, VMG ceñida y puesto medio.
    2. 💨 **Viento Medio (10–15 kn)**: Rendimiento en condiciones estándar de regata.
    3. 🌊 **Viento Fuerte (> 15 kn - Alisios RCNGC)**: Análisis de potencia y gobierno en las condiciones habituales de la bahía de Las Palmas.
* **Calidad de Maniobras (Telemetría de Viradas)**:
  * **Pérdida en el ápex ($\Delta V$)**: Medición de la caída de velocidad en nudos durante la virada por avante.
  * **Tiempo de aceleración ($t_{rec}$)**: Tiempo en segundos necesario para recuperar el 90% de la velocidad objetivo tras cambiar de bordo.
  * **Coste en metros y esloras**: Conversión métrica directa del coste de cada virada en distancia y en esloras de Optimist ($2,36\text{ m}$).
* **Tramos, VMG y Eficiencia de Derrota**:
  * **VMG Ceñida vs Popa**: Desglose de la velocidad neta de ascenso contra el viento frente a la velocidad de descenso a sotavento.
  * **Eficiencia de derrota**: Ratio porcentual de progreso respecto a la derrota óptima de ceñida.
* **Estrategia y Remontadas (Flota RCNGC)**:
  * **Paso en Baliza 1 (B1 Barlovento) vs Puesto Final en Meta**: Comparación de rendimiento en la primera ceñida frente al resultado global.
  * **Índice de Remontada**: Puestos ganados o perdidos de promedio desde el paso por Barlovento hasta cortar la línea de llegada.
  * **Gap al líder**: Diferencia media en segundos respecto al primer barco que cruzó la meta.
* **Insignias y Gamificación Deportiva**:
  * 🚀 **«Salida Cañón»**: Otorgada por clavar la salida en $\le 2,0\text{ s}$ con velocidad $V_{gun} \ge 3,5\text{ kn}$.
  * 🔄 **«Virada Fina»**: Otorgada por promediar una pérdida de velocidad en virada $\le 1,8\text{ kn}$.
  * ⚓ **«Millas de Oro»**: Otorgada al superar las 10 Millas Náuticas de telemetría acumulada en el club.
  * 📈 **«Remontador»**: Otorgada al mantener un índice positivo de remontada ($\ge +0,5$ puestos ganados).
  * ⚡ **«Récord SOG Histórico»**: Muestra la velocidad punta absoluta del regatista acompañada de la fecha exacta de la manga.
* **Gráfica Multieje SVG con 4 Modos Interactivos**:
  * Pestañas superiores para alternar instantáneamente entre:
    1. `⏱️ Tiempos Salida (+s)`: Con línea de objetivo RCNGC ($\le 3,0\text{ s}$) y código semafórico.
    2. `🚀 Vel. Bocinazo (kn)`: Con línea de objetivo $\ge 3,5\text{ kn}$.
    3. `📈 Velocidad SOG (kn)`: Velocidad media y pico máximo en 5s.
    4. `🧭 VMG Ceñida (kn)`: Velocidad de ascenso a barlovento con línea de media histórica.
* **Seguridad y Jerarquía de Accesos**:
  * La pestaña **«Conexión y Seguridad»** permanece 100% oculta en modo regatista (`display: none`) y solo se hace visible al autenticarse como entrenador.
  * La asignación y edición del nombre de regatistas, así como el borrado de regatas en la nube, exige el PIN de entrenador (`RCNGC2026`).

### [v1.0.10] - Cierre V1: Equipo de Regatas RCNGC, Rosa de Viento, Memoria F5, Nueva Sesión y Guía del Entrenador
* **Identificación oficial «Equipo de Regatas RCNGC · Optimist»**: Actualizados todos los textos de cabecera y títulos de sesión para mostrar siempre «Equipo de Regatas RCNGC · Optimist».
* **Dirección del viento en el mapa**: Corregida la rotación de la flecha en la rosa de los vientos para reflejar con exactitud la dirección del flujo de viento (si el viento entra de 0°, la flecha apunta hacia 180°; si entra de 10°, apunta a 190°, etc.).
* **Restauración total de memoria tras F5 (IndexedDB)**: Reorganizada la inicialización de la base de datos interna para garantizar que al pulsar F5 o cerrar y reabrir el navegador, la sesión completa (barcos, números de vela, recorrido y dibujos tácticos) se restaure al instante.
* **Botón «Nueva sesión» restaurado**: Visible en la cabecera superior derecha para permitir a los entrenadores vaciar la sesión actual y comenzar un nuevo día de entrenamiento desde cero cuando lo deseen.
* **Guía interactiva integrada («📖 Guía de uso»)**: Nuevo botón en la cabecera accesible en todo momento que abre una ventana con las instrucciones completas explicadas paso a paso para cualquier entrenador.
* **Manual de uso para entrenadores en el repositorio**: Incorporada en este documento la guía completa y detallada de uso para debriefing y análisis en el club.

### [v1.0.9] - Corrección en la carga de archivos (GPX / Excel / CSV)
* **Desbloqueo de la pantalla de carga de archivos**: Se ha solucionado una llamada interna en la función de sincronización de datos que provocaba que la aplicación se quedara congelada en el mensaje de «Leyendo 1 de 1: archivo.gpx».
* **Carga fluida e inmediata**: Ahora al subir archivos GPX de relojes o trackers, hojas de cálculo Excel/CSV o archivos KML, el programa procesa y alinea las trayectorias al instante, retirando la pantalla de carga e iniciando directamente la visualización del mapa, la clasificación y el panel de control.

### [v1.0.8] - Corrección integral de tildes, Recorrido IODA manual paso a paso y botón de Cancelar (Esc)
* **Corrección total de tildes y caracteres en toda la interfaz**: Revisión exhaustiva y saneamiento de todos los textos del programa. Se han corregido todas las palabras con tildes, signos y símbolos especiales (`Nueva sesión`, `Clasificación`, `Táctica`, `Trapecio IODA`, `−10°`, `1º`, `Posición`, `Velocidad`, `Viradas`, `Navegado`, `Llegada`, `Salida`, etc.), eliminando cualquier carácter extraño o mal codificado.
* **Recorrido IODA 100% manual (sin generación automática)**:
  * Tal y como se solicitó, se ha quitado la generación automática del campo de regatas IODA.
  * **Asistente guiado paso a paso**: Nuevo botón «📍 Añadir recorrido paso a paso» que solicita al entrenador hacer clic directamente sobre el mapa para situar en orden cada punto oficial del recorrido: B1 (Barlovento) ➔ B2 (Desmarque) ➔ Puerta 3s (Estribor) ➔ Puerta 3p (Babor) ➔ Boya de Llegada (Pin) ➔ Barco de Llegada (Comité).
  * **Colocación y ajuste individual**: Botones dedicados para colocar o reubicar cualquier baliza suelta en cualquier momento (`📍 B1`, `📍 B2`, `📍 3s`, `📍 3p`, `📍 Pin Llegada`, `📍 Comité Llegada`, `📍 Salida`), con indicadores de estado («✓ Colocada» o «Pendiente») y botón para borrar las marcas IODA si se quiere empezar de nuevo.
  * **Cálculo dinámico de tramos**: El programa calcula automáticamente los tramos (ceñida a B1, través a B2, popa a la puerta 3 con paso libre por 3s o 3p, y ceñida a la llegada) y proyecta los laylines limpios en B1 y Llegada.
* **Botón visual de cancelación y mejora de la tecla Escape**:
  * En el cuadro flotante blanco inferior que aparece al activar cualquier herramienta de dibujo o baliza, se ha integrado un botón claro y directo: `[ ✕ Cancelar / Salir (Esc) ]`.
  * La tecla Escape del teclado ahora funciona de manera inmediata y garantizada desde cualquier punto de la pantalla, gracias a un detector en fase prioritaria que evita bloqueos.

### [v1.0.7] - Recorrido Trapecio IODA, escala real de balizas y ajustes tácticos
* **Recorrido oficial Trapecio IODA (Optimist)**: Se añade en la pestaña «Recorrido» la opción de alternar entre el recorrido «Libre / Tradicional» y el «Trapecio IODA (Optimist)»:
  * **Generación automática en un clic**: Botón «⚡ Generar Trapecio IODA automático» que calcula y coloca al instante todo el campo de regatas oficial orientado a la dirección del viento y adaptado al área de navegación de la flota.
  * **Elementos oficiales del Trapecio**: Baliza 1 (B1 barlovento), Baliza 2 (B2 través a 60°), Puerta 3 (dos balizas: 3s y 3p), Línea de Llegada (Pin y Comité azules) y Línea de Salida (Pin y Comité naranjas).
  * **Puerta 3 inteligente**: El sistema detecta automáticamente si el barco toma la baliza 3s o la 3p para completar el tramo de popa.
  * **Laylines en B1 y Llegada**: Los laylines se calculan automáticamente tanto para la baliza de barlovento (B1) como para la línea de llegada.
  * **Reposicionamiento individual**: Botones para mover y reubicar de forma independiente cada baliza o línea en el mapa.
  * **Tramos y cronología**: Visualización de los tramos en la clasificación, en la barra de tiempo («1º B1», «1º B2», «1º Puerta 3», «1º Llega») y en la gráfica de velocidad individual.
* **Escala real de las balizas al hacer zoom**: Ajustado el tamaño de las balizas para que coincida con el diámetro real de una baliza reglamentaria de regata (1 metro de diámetro = 0,5 m de radio). Al hacer zoom para ver aproximaciones y pasos en detalle, las balizas mantienen una proporción perfecta con los cascos de Optimist (2,30 m de eslora) sin verse desmesuradamente grandes.
* **Línea de salida con parrilla de 10 m a 75 m**: La parrilla de aproximación a sotavento ahora marca distancias de 10 en 10 metros hasta 75 metros (`10m`, `20m`, `30m`, `40m`, `50m`, `60m`, `70m`, `75m`).
* **Laylines limpios**: Eliminadas las descripciones de texto («Layline Estribor / Babor») y el arco verde superior para una visualización táctica despejada y limpia.
* **Zona de 3 esloras sin etiquetas**: Eliminado el rótulo de texto («3 esloras (7,08 m)») en el mapa, manteniendo el círculo reglamentario punteado en rojo suave alrededor de todas las balizas.
* **Persistencia total en memoria**: El tipo de recorrido (Libre o IODA), las posiciones de todas las marcas y los ajustes tácticos se guardan automáticamente y se restauran íntegramente al recargar con F5.

### [v1.0.6] - Pizarra Táctica completa (laylines, 3 esloras, salida con parrilla, barcos y herramientas)
* **Nueva pestaña «Táctica» en el panel lateral**: Se incorpora una pizarra táctica interactiva pensada para explicaciones de regata, análisis de maniobras, aproximaciones y debriefing de entrenamientos.
* **Líneas rectas (Regla de rumbo y distancia)**: Herramienta interactiva para trazar líneas en el mapa con 2 clics. Muestra en el centro una placa con el rumbo exacto en grados (ej. `045°`) y la distancia navegada en metros o kilómetros (ej. `185 m` o `1.2 km`).
* **Flechas tácticas**: Herramienta para dibujar flechas orientadas en el mapa, ideal para señalar rachas de viento, corrientes, tácticas o maniobras.
* **Zona invisible de balizas y zonas manuales**: Se han hecho invisibles las líneas punteadas que antes se mostraban por defecto alrededor de las balizas. Ahora puedes dibujar tus propias zonas a mano con el radio que desees alrededor de cualquier baliza o punto del campo de regatas.
* **Zona automática de 3 esloras de Optimist (7,08 m)**: Botón de un solo clic que dibuja al instante el círculo reglamentario de 3 esloras de Optimist (7,08 metros según la Regla 18 del Reglamento de Regatas a Vela) en todas las balizas del recorrido y en la llegada.
* **Línea de salida táctica con parrilla de aproximación**: Herramienta para marcar la salida indicando la boya de Pin y el barco Comité (RC). Dibuja la línea en rojo vivo con el texto «START» y genera la parrilla de distancia a sotavento con líneas paralelas a 100 m, 200 m y 300 m de la salida, siguiendo el estándar de los visores de regata profesionales.
* **Barcos tácticos interactivos**: Menú para colocar barcos adicionales en el mapa. Permite elegir número de vela, color distintivo, y orientarlos rápidamente amurados a estribor o a babor (en ceñida a 45°, popa a 140° o rumbo libre). Cada barco se dibuja con el casco de Optimist, la botavara abierta a sotavento según su amura y una placa con su número de vela.
* **Laylines automáticas de barlovento**: Botón para trazar automáticamente desde las balizas de barlovento las líneas de layline a 45° del viento hacia sotavento, junto con el arco sombreado superior que delimita el sector de barlovento.
* **Deshacer y persistencia total**: Botones para deshacer el último dibujo o borrar toda la pizarra. Todos los dibujos, barcos y configuraciones tácticas se guardan en la memoria del navegador y se conservan al pulsar F5 o recargar la página.
* **Corrección en la vista previa del barco táctico**: Se ha resuelto una errata en la fórmula de orientación en vivo que bloqueaba el inicio del programa, restaurando el funcionamiento inmediato de los botones de carga («Elegir carpeta» / «Elegir archivos») y la recuperación de la sesión con F5.

### [v1.0.5] - Detección inteligente de balizas y sincronización de memoria
* **Detección robusta de balizas (sin bloqueos)**: Se ha mejorado el sistema de paso por baliza. Ahora utiliza el punto de máxima aproximación del barco y un radio efectivo más generoso (60 m por defecto). Si una baliza queda un poco desplazada del track o el regatista pasa abierto, el programa no se queda atascado y continúa registrando todas las balizas y la meta con total fiabilidad.
* **Restauración completa de recorrido tras F5**: Corregido el orden de carga desde la memoria del navegador para que las balizas, el viento y la salida se recuperen de forma íntegra antes de calcular los tramos, garantizando que siempre se muestren las marcas de paso tanto en la barra grande inferior como en la gráfica de velocidad.

### [v1.0.4] - Selector de período y marcas de baliza en la gráfica de velocidad
* **Selector de período de tiempo**: Botones para elegir la ventana temporal en la gráfica de velocidad del barco: «5 min» (vista estándar), «15 min» (para analizar un tramo completo), «30 min» (para mangas largas) o «Toda» (para ver el perfil de velocidad de toda la regata de principio a fin).
* **Marcas de balizas y salida en la gráfica**: Marcas verticales con sus nombres («Salida», «B1», «B2», «Meta») en el momento exacto en que ese barco pasó cada baliza, con sistema anticolisión para que los textos nunca se pisen entre sí si dos balizas se toman muy seguidas.

### [v1.0.3] - Guardado automático y gestión de archivos (borrar y añadir)
* **Memoria automática (a prueba de F5)**: Los archivos cargados, números de vela personalizados, dirección del viento, balizas y salida se guardan automáticamente en la memoria interna del navegador. Si pulsas F5 o cierras la ventana, la sesión se restaura de forma instantánea sin perder nada.
* **Eliminar barcos individuales**: Añadido un botón «✕» al lado de cada barco en la pestaña «Barcos» para borrar tracks subidos por error. Al pulsar, pide confirmación y recalcula la clasificación y el mapa al momento.
* **Añadir más barcos sobre la marcha**: Ahora puedes sumar barcos a la sesión actual arrastrando nuevos archivos o usando el nuevo botón «+ Añadir más archivos».
* **Botón «Nueva sesión»**: Nuevo botón en la cabecera superior para limpiar los datos actuales y empezar un nuevo entrenamiento desde cero cuando tú quieras.

### [v1.0.2] - Corrección de la orientación de la botavara
* **Posición de la botavara**: Corregido el ángulo de la botavara en la silueta de los barcos. Ahora rota 90º hacia la popa y se abre hacia sotavento (el lado opuesto al viento), reflejando con total fidelidad la posición real de la vela según el rumbo y la dirección del viento.

### [v1.0.1] - Corrección de textos y orientación de la flecha de viento
* **Identificación del equipo**: Actualizado el texto de cabecera a «Equipo de Regatas RCNGC» tanto en la pantalla inicial como tras cargar los archivos de una sesión.
* **Corrección de la flecha de viento**: Corregida la rotación de la flecha en la rosa de los vientos del mapa. Ahora apunta en la dirección hacia donde sopla el viento (por ejemplo, con viento de 0º la flecha apunta hacia el Sur / 180º; con viento de 10º apunta a 190º).

### [v1.0.0] - Versión Inicial (Base del Proyecto)
* **Visualizador completo**: Implementación de la primera versión del visor en `Visor Regata Optimist_Entrenadores v1.html`.
* **Soporte multiformato**: Lectura de tracks en GPX, KML, CSV y hojas de cálculo Excel (XLSX, XLS, ODS).
* **Lector rápido de GPX**: Algoritmo optimizado para leer archivos grandes de reloj (sesiones de 5 horas o más de 20.000 puntos).
* **Remuestreo a 1 Hz**: Estandarización de todas las posiciones segundo a segundo para permitir reproducción simultánea y cálculos exactos.
* **Modo de alineación**: Capacidad de sincronizar barcos por hora real o superpuestos desde su punto de inicio.
* **Recorrido y balizas**: Creación interactiva de balizas sobre el mapa, cálculo automático de tramos (ceñida/popa/través) y radio de paso personalizable.
* **Métricas y telemetría**: Cálculo de velocidad en nudos, rumbo en grados, distancias navegadas y contador automático de viradas.
* **Gráfica de velocidad (Sparkline)**: Mini-gráfico de rendimiento del barco seleccionado en los últimos 5 minutos.
* **Resumen para entrenadores**: Tabla final con métricas completas y botón para copiar directamente a Excel.
* **Documentación inicial**: Creación de `README.md` (manual y contexto) y `AGENT.md` (guía de trabajo y comunicación).
