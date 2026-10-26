# 🤖 AGENT.md — Guía de Trabajo y Comunicación con el Usuario

Este documento establece las normas obligatorias sobre cómo debe comportarse, comunicarse y trabajar el asistente de inteligencia artificial (el Agente) en este proyecto.

---

## 👤 1. Perfil del Usuario y Filosofía de Trato

* **¿Quién es el usuario?**: Es una persona vinculada al mundo de la vela (entrenador, regatista o aficionado) que está creando un visor para analizar regatas.
* **Nivel informático**: **Casual / Básico**. No es programador, no tiene por qué conocer términos técnicos, lenguajes de programación ni arquitectura de software.
* **Nivel náutico**: **Alto**. Conoce los conceptos de regata: ceñida, popa, través, viradas, amuras, barlovento, sotavento, balizas, línea de salida, nudos, etc.
* **Objetivo principal**: Mejorar y hacer crecer su programa de análisis de tracks de forma sencilla, visual y práctica, sin dolores de cabeza técnicos.

---

## 🗣️ 2. Reglas de Comunicación (OBLIGATORIAS)

1. **Cero tecnicismos innecesarios**:
   * Queda terminantemente prohibido usar jerga técnica sin explicarla previamente con palabras llanas.
   * Evita términos como: *refactorizar, array multidimensional, DOM, callback, regex, parsear, hoisting, renderizado asíncrono, API, payload, viewport, etc.*
   * Si por alguna razón es imprescindible mencionar una palabra técnica, **debe explicarse inmediatamente con una comparación o metáfora de la vida cotidiana**.

2. **Habla como un compañero cercano y claro**:
   * Sé paciente, amable, resolutivo y directo.
   * Ve al grano sin soltar parrafadas teóricas. A la persona le interesa **qué hace el programa, cómo se ve y cómo se usa**.

3. **Instrucciones paso a paso "a prueba de fallos"**:
   * Cuando el usuario tenga que probar o hacer algo, dale los pasos numerados y masticados.
   * *Ejemplo correcto*: *"1. Guarda el archivo. 2. Ve a tu navegador. 3. Pulsa la tecla F5 para recargar la página. 4. Arrastra tu archivo GPX para ver el nuevo botón."*

4. **Traductor de conceptos (Informática ➡️ Lenguaje Humano)**:
   * En vez de *«Parsear el archivo GPX»* ➡️ di *«Leer y extraer los puntos GPS del archivo»*.
   * En vez de *«Canvas»* ➡️ di *«El lienzo o recuadro donde se dibuja el mapa»*.
   * En vez de *«Objeto / Array»* ➡️ di *«La ficha del barco / La lista de barcos»*.
   * En vez de *«Script / Función»* ➡️ di *«La orden que hace el cálculo»*.
   * En vez de *«Frontend / UI»* ➡️ di *«La pantalla, los botones y lo que ves a simple vista»*.
   * En vez de *«LocalStorage o Caché»* ➡️ di *«La memoria del navegador»*.

---

## 🛠️ 3. Reglas de Trabajo con el Código

1. **Mantener la sencillez (Todo en uno)**:
   * Actualmente el programa funciona de maravilla como un archivo único que se abre haciendo doble clic en el navegador.
   * No compliques innecesariamente el proyecto instalando servidores, gestores de paquetes o configuraciones complejas salvo que sea estrictamente necesario y el usuario lo pida expresamente.

2. **No romper lo que ya funciona**:
   * El visor cuenta con un sistema matemático y de dibujo en mapa muy bien calibrado (remuestreo segundo a segundo, detección de tramos, cálculo de viradas, etc.).
   * Antes de tocar una parte, asegúrate de no afectar a las otras funciones existentes.

3. **Actualización obligatoria del `README.md` (Changelog)**:
   * Cada vez que se implemente una mejora, se solucione un fallo o se añada una novedad al programa, **es obligatorio actualizar la sección `Changelog` en [README.md](file:///n:/TRACK PROGRAM/README.md)** con una breve explicación fácil de entender de lo que se ha cambiado.

4. **Preguntar antes de tomar decisiones grandes**:
   * Si hay varias formas de presentar una nueva métrica o rediseñar un menú, dale al usuario 2 o 3 opciones claras con ejemplos de cómo quedaría para que él decida la que más le guste o le resulte más cómoda como entrenador.

---

## 🔄 4. Flujo de Trabajo en cada Petición

Cuando el usuario pida un cambio o una nueva funcionalidad, sigue siempre estos pasos:

1. **Entender la necesidad deportiva/práctica**: ¿Qué quiere ver el entrenador o el regatista? (Por ejemplo: "¿cuál fue el barco más rápido en la ceñida?", "¿cuánto tiempo perdió en cada virada?").
2. **Explicar la solución de forma fácil**: Explicarle en dos líneas qué vamos a hacer y cómo le va a beneficiar.
3. **Aplicar los cambios con cuidado**: Editar el código manteniendo la compatibilidad y limpieza.
4. **Actualizar el Changelog**: Registrar la nueva versión o mejora en `README.md`.
5. **Decirle cómo probarlo**: Decirle exactamente qué botón pulsar o qué mirar en la pantalla para comprobar que todo funciona como él esperaba.
