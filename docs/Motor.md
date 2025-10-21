# ⚙️ Control de Giro, Velocidad y Posición con ESP32

## 🎯 Propósito
Explorar el control de motores mediante el ESP32, aplicando técnicas de cambio de giro, variación de velocidad con PWM y posicionamiento de servo motores.

## 🧭 Meta de la práctica
Poder comprender cómo llegar a controlar motores DC y servos utilizando programación en ESP32, aplicando conceptos de lógica digital, modulación por ancho de pulso (PWM) y mapeo de valores para posicionamiento.

### 👥 Organización del Equipo
El equipo se dividió en dos áreas principales:
- Desarrollo del código de programación
- Desarrollo electrónico

### 🧰 Materiales Utilizados
- ESP32  
- Motor DC  
- Servo motor  
- Protoboard  
- Cables de conexión (jumpers)  
- Fuente de alimentación  
- Cable USB para cargar el programa  

### 🧪 Tecnologías Utilizadas
- **Lenguajes:** Python  
- **Hardware:** ESP32, Arduino  
- **Software:** Arduino IDE  

### ⚡ Sistema Electrónico
- **Cambio de giro del motor DC:** Se conectaron dos pines digitales al motor, alternando su estado para cambiar la dirección de giro (adelante y atrás).  
- **Control de velocidad del motor DC:** Se utilizó un pin PWM configurado para incrementar la velocidad del motor.  
- **Control de posición de un servo motor:** Se configuró un canal PWM con frecuencia de 50 Hz y resolución de 12 bits. Se usó la función `map()` para convertir grados (0° a 180°) en valores de duty cycle entre 205 y 410, que corresponden al rango de operación del servo.

## 🧠 Programación
- **Cambio de giro:** Alterna los pines `in1` e `in2` para cambiar la dirección del motor.  
- **Velocidad progresiva:** Usa `ledcWrite()` para aumentar gradualmente la velocidad del motor en pasos del 20%.  
- **Servo motor:** Utiliza PWM de 12 bits para mover el servo a posiciones específicas (0°, 90°, 180°), mostrando los valores en el monitor serial.

## 📈 Resultados y Observaciones
El motor DC respondió correctamente al cambio de giro, alternando entre avance y retroceso.  
El control de velocidad fue progresivo y estable, mostrando cómo el PWM puede modificar la potencia entregada al motor.  
El servo motor se posicionó con precisión en los ángulos programados, y los valores de duty cycle se reflejaron correctamente en el monitor serial.  
No se presentaron errores de conexión ni fallas en la ejecución de los códigos.


## 🧩 Reflexiones Finales
Esta práctica permitió comprender tres aspectos fundamentales del control de motores con ESP32: dirección, velocidad y posición.  
Se reforzó el uso de PWM en diferentes resoluciones y frecuencias, y se evidenció cómo la programación puede traducirse en movimientos físicos precisos.  
Además, se aprendió a mapear valores para controlar servos, y se observó la importancia de los retardos (`delay`) para estabilizar los cambios.

## 📹 Evidencias
[Evidencias en video aquí.]()