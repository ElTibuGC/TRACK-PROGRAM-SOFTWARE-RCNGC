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
* **Círculo de 3 esloras (7,08 m)**: Pulsa **«⭕ 3 esloras (7,08 m)»** para activar el círculo reglamentario de 3 esloras de Optimist alrededor de todas las boyas (según la Regla 18 del RRV).
* **Línea de salida táctica con parrilla**: Pulsa **«🚩 Trazar línea de salida»**, haz 1 clic en la boya de Pin y otro en el barco Comité. Se dibujará la línea de salida y una parrilla de aproximación a sotavento con líneas cada 10 metros hasta los 75 metros de distancia.
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
