# Timbre inteligente

**Alumno**: Leandro Murillo.

**Objetivo**: Desarrollar un prototipo que implemente la lógica de un timbre programado por mensajes.

## Descripción:

> **OBSERVACIÓN IMPORTANTE:** En esta primera versión del proyecto, no se conectarán dispositivos periféricos analógicos. En su lugar, se simularán estos periféricos mediante el encendido o parpadeo de los LEDs del microcontrolador. Asimismo, aunque en la descripción se menciona la posibilidad de comunicación con el microcontrolador mediante dispositivos móviles, en esta versión se implementará la transmisión de mensajes a través de una interfaz UART USB entre el microcontrolador y la computadora.

 El sistema notifica al usuario cuando alguien presiona el timbre de la puerta. Al activarse, el sistema toma una fotografía de la persona en la puerta y la envía al teléfono del usuario junto con una notificación.

 Para evitar la repetición de notificaciones seguidas, el sistema enviará una nueva notificación solo si ha transcurrido el tiempo definido para la atención de la visita, configurado mediante una constante del tipo `#define`.

 A continuación, el sistema desplegará un menú de opciones que permitirá al usuario decidir cómo proceder. 
``` 
Hay alguien en la entrada principal. ¿Qué desea hacer?
- Presione '1' para enviar una respuesta pregrabada.
- Presione '2' para enviar un mensaje de voz.
```
``` 
El caracter '#' no es una opción válida
```
 El usuario podrá elegir entre responder con un mensaje pregrabado, almacenado en una tarjeta SD y reproducido por el altavoz del timbre, o grabar una nueva respuesta en tiempo real para enviarla a la persona en la puerta.
```
Ha seleccionado la opción '1'. Elija una respuesta pregrabada para enviar:
- '1' - "Hola, buen día! Por favor aguarde un momento"
- '2' - "El señor ##### lo atenderá en un momento"
- '3' - "La señora ##### lo atenderá en un momento"
- '0' - VOLVER AL MENU PRINCIPAL
```
 Si se elige la opción de grabar una respuesta, se reproducirá un mensaje de bienvenida por el altavoz del timbre, informando al visitante que puede grabar un mensaje de voz que será escuchado por el usuario.
```
Ha seleccionado la opción '2'. Grabando mensaje de voz...
Su mensaje de voz ha sido enviado.
Se ha habilitado el microfono del otro lado. Esperando respuesta...
Ha recibido un nuevo mensaje de voz.
```
Luego de haber finalizado cualquier secuencia de acciones o luego de vencido el tiempo de atención prestablecido el LED1 se apagará. 

---
### Plataforma de desarrollo: NUCLEO-F439ZI

### Periféricos a utilizar:

- **USER BUTTON:** Se utiliza para simular el botón del timbre.

- **LED 1:** Parpadea para indicar que la cámara se ha activado y luego permanece encendido hasta que se venza el tiempo de atención a la visita.

- **LED 2:** Parpadea mientras se reproduce un mensaje pregrabado. Se mantiene encendido si se reproduce una respuesta grabada en el momento.

- **LED 3:** Parpadea para indicar que el usuario está grabando una respuesta. Se mantiene encendido si el micrófono en la puerta está activo y está grabando una respuesta.

- **ANALOG IN:** Se utiliza para simular el micrófono.

- **ANALOG OUT:** Se utiliza para simular el altavoz.

- **UART:** Se utiliza para enviar notificaciones desde el microcontrolador hacia la computadora y también para enviar comandos del menú de opciones desde la computadora hacia el microcontrolador.

### Diagrama en Bloques:
![Diagrama de bloques TP1](https://github.com/user-attachments/assets/0e3860ed-4dfc-4697-9eb2-e8b575989c55)
