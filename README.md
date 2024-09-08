# Timbre inteligente

**Alumno**: Leandro Murillo.

**Objetivo**: Desarrollar un prototipo que implemente la lógica de un timbre programado por mensajes.

## Descripción:

Este sistema tiene como objetivo implementar un prototipo con las funcionalidades de un timbre programable mediante mensajes. Para ello, se utilizarán los LEDs de la placa de desarrollo para simular acciones del sistema, como la captura de una imagen o la grabación de un mensaje de voz, mientras que el botón de la placa funcionará como el botón del timbre. Además, se empleará un potenciómetro que servirá para simular la entrada analógica que detectaría un micrófono.

El timbre se activa al presionar el botón _doorBellButton_, lo que provoca que el LED _CameraLed_ parpadee durante unos segundos para simular que se ha tomado una foto de la persona en la entrada. Luego, la terminal UART mostrará el siguiente mensaje:

```
Hola! tenes a una nueva visita en la puerta.
```

Para evitar la repetición del mensaje cada vez que se presione el botón _doorBellButton_ de forma seguida, el sistema debe asegurar que el LED _CameraLed_ solo parpadee una única vez en cada ejecución o hasta que expire un timer de espera.

Después de que comience el timer de espera, el LED _CameraLed_ permanece encendido hasta que se complete alguna de las secuencias de eventos del sistema o hasta que el timer expire.

El timer de espera también se activará cada vez que se solicite una entrada por el teclado de la computadora para evitar bloqueos, pudiendo asignarse timers diferentes según el caso.

A continuación, la terminal UART solicitará al usuario que introduzca uno de los siguientes comandos:

```
Elija una de las opciones disponibles:
Presione '1' para enviar una respuesta pre-grabada
Presione '2' para enviar un mensaje de voz
```

Si no se introduce ninguna opción válida, la terminal mostrará:

```
El caracter '%c' no es una opción válida
```

---
Si el usuario selecciona la opción '1', la terminal UART mostrará:

```
Usted ha elegido la opción 1. Elija una de las respuestas disponibles:
'1' - Buen día, si ¿qué necesita?
'2' - El señor #### lo atenderá en un momento
'3' - La señora #### lo atenderá en un momento
'0' - VOLVER AL MENU PRINCIPAL
```

* Si se selecciona la opción '1', '2' o '3', el LED _playingAudioLed_ parpadeará durante unos segundos y se terminará la ejecución del sistema apagando todos los LEDs.
* Si se selecciona la opción '0', se volverá al menú anterior.
* Si se selecciona cualquier otra opción, se mostrará un mensaje de error similar al mostrado en el menú principal.

---
Si el usuario selecciona la opción '2', la terminal UART le pedirá que presione la tecla '0' para continuar:
 
```
Ha seleccionado la opción '2'. Presione la tecla '0' para grabar un mensaje.
```

Para simular la grabación de un mensaje de voz, el usuario deberá girar la perilla del potenciómetro hacia la derecha para indicar que la operación fue exitosa, o hacia la izquierda para indicar que la acción falló. Una vez hecho esto, deberá presionar '0' para confirmar su elección. El LED _recordingAudioLed_ parpadeará mientras dure esta operación o hasta que expire el timer de espera.

La terminal UART mostrará el mensaje correspondiente a cada situación:
```
Su mensaje de voz ha sido enviado.
```

```
Lo siento, no se ha podido grabar el mensaje de voz
```

También se procederá de la misma manera para simular la grabación de un mensaje de voz en la entrada:

```
Se ha habilitado el microfono del otro lado. Presione la tecla '0' para conocer la respuesta.
```
```
Tiene un nuevo mensaje de voz en bandeja de entrada.
```

```
No se ha escuchado nada al grabar el mensaje de voz en la entrada.
```

Finalmente, la terminal UART mostrará un mensaje de despedida y se apagarán todos los LEDs del sistema.

### Plataforma de desarrollo: NUCLEO-F439ZI

### Periféricos a utilizar:

- **doorBellButton:** se utiliza el botón BUTTON1 de la placa como botón del timbre.

- **CameraLed:** se utiliza el led LED1 de la placa para simular la captura de imágenes mediante una cámara.

- **playingAudioLed:** se utiliza el led LED2 de la placa para simular que se está reproduciendo un mensaje de voz pregrabado por un altavoz.

- **recordingAudioLed:** se utiliza el led LED3 de la placa para simular que se está grabando un mensaje de voz por micrófono. 

- **potentiometer**: Se utiliza para simular la entrada analógica de un micrófono.

- **UART:** Se utiliza para enviar notificaciones desde el microcontrolador hacia la computadora y también para enviar comandos del menú de opciones desde la computadora hacia el microcontrolador.

### Diagrama en Bloques:

![[Diagrama de bloques TP1 (1) 1.jpg]]