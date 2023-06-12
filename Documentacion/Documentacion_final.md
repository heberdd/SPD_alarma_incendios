# Documentación del Código

## Descripción
Este código en C++ controla un sistema que monitorea la temperatura y activa una alarma en caso de detectar un incendio. El sistema utiliza un sensor de temperatura, un control remoto IR, un display LCD, un servomotor y LEDs para indicar el estado del sistema.

## Dependencias
- [IRremote](https://github.com/z3t0/Arduino-IRremote): Biblioteca para controlar el receptor IR.
- [LiquidCrystal](https://www.arduino.cc/en/Reference/LiquidCrystal): Biblioteca para el control del display LCD.
- [Servo](https://www.arduino.cc/en/Reference/Servo): Biblioteca para controlar el servomotor.

![Dependencias](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/1_dependencias.png)



## Configuración de Hardware
El código utiliza los siguientes pines para conectar los componentes:
- Sensor de temperatura: A0
- Receptor IR: 11
- Display LCD:
  - RS: 0
  - E: 1
  - D4: 6
  - D5: 7
  - D6: 8
  - D7: 9
- Servomotor: 10
- LEDs:
  - LED verde: 12
  - LED rojo: 13

![Configuracion de Hardware](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/2_configuracion_hardware.png)


## Funcionamiento
El código realiza las siguientes acciones en el bucle principal (`loop()`):
1. Lee la temperatura del sensor analógico.

![Funcionamiento](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/3.png)

2. Procesa los comandos recibidos del control remoto IR.

![Procesa los comandos](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/4.png)


3. Verifica la temperatura para activar o desactivar la alarma y mover el servomotor.

![Verifica Temperatura](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/5.png)

4. Muestra la temperatura y la estación del año en el display LCD.

![Muestra temperatura](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/6.png)

5. Controla los LEDs para indicar el estado del sistema.

![Controla Leds](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/7.png)

El código también contiene las siguientes funciones:

### `readTemperature()`
Lee la temperatura del sensor analógico y la retorna en grados Celsius.

![Lee Temperatura](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/8.png)

### `processRemoteCommand(unsigned long command)`
Procesa los comandos recibidos del control remoto IR. Actualmente, los comandos `0x12345678` y `0x87654321` activan y desactivan el sistema de incendio, respectivamente.

![Procesa comandos control](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/9.png)

### `activateFireSystem()`
Activa el sistema de incendio y realiza acciones personalizadas.

![Activa sistema de incendios](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/10.png)

### `deactivateFireSystem()`
Desactiva el sistema de incendio y realiza acciones personalizadas.

![Desativa sistema incendios](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/11.png)

### `activateAlarm()`
Activa la alarma cuando se detecta un incendio. Mueve el servomotor, muestra un mensaje de alarma en el display LCD y enciende el LED rojo.

![Activa servomotor](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/12.png)

### `deactivateAlarm()`
Desactiva la alarma. Vuelve el servomotor a la posición inicial, muestra un mensaje en el display LCD y enciende el LED verde.

![Desactiva servomotor](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/13.png)

### `displayTemperature(float temperature)`
Muestra la temperatura actual en el display LCD.

![Muestra temperatura](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/14.png)

### `displaySeason(int season)`
Muestra la estación del año en el display LCD basado en un código numérico de estación.

![Muestra Estacion](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/15.png)

### `getSeason(float temperature)`
Determina la estación del año basado en la temperatura actual y retorna un código 
numérico de estación.

![Determina Estacion](https://github.com/heberdd/SPD_alarma_incendios/blob/main/Img_code/16.png)

## Uso
1. Conecta los componentes según los pines especificados en la configuración de hardware.
2. Carga el código en tu placa Arduino.
3. Verifica que las bibliotecas `IRremote`, `LiquidCrystal` y `Servo` estén instaladas en tu entorno de desarrollo.
4. Sube el código a tu placa Arduino y observa el comportamiento del sistema.

## Consideraciones Adicionales
- Asegúrate de tener las bibliotecas necesarias instaladas en tu entorno de desarrollo.
- Puedes personalizar las acciones en las funciones `activateFireSystem()` y `deactivateFireSystem()` según tus necesidades.
- Ajusta el umbral de temperatura (`TEMPERATURE_THRESHOLD`) según tus requisitos.

## Notas
- Este código es una demostración y puede requerir modificaciones para adaptarse a tu configuración específica.


