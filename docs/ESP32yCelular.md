# 📶 Comunicación Bluetooth entre ESP32 y Celular

## 🎯 Propósito
Establecer una comunicación inalámbrica entre un ESP32 y un teléfono celular mediante Bluetooth, para enviar mensajes desde la app de Arduino y visualizar los textos recibidos en el monitor serial de la computadora.

## 🧭 Meta de la práctica
Lograr que el ESP32 reciba mensajes escritos desde una app móvil y los muestre en el monitor serial de la computadora a través de una conexión Bluetooth.

### 👥 Organización del Equipo
La organización fue eficaz: el equipo se dividió en dos áreas principales:
- Desarrollo del código de programación
- Desarrollo electrónico

### 🧰 Materiales Utilizados

- ESP32  
- Protoboard  
- Cables de conexión (jumpers)  
- Cable USB para cargar el programa  
- Aplicación *Arduino Bluetooth Controller* (en celular Android)  
- Computadora con Arduino IDE  

#### 🧪 Tecnologías Utilizadas

- **Lenguajes:** Python  
- **Hardware:** ESP32, Arduino  
- **Software:** Arduino IDE  
- **Sistema Electrónico:** Comunicación Bluetooth sin sensores ni actuadores externos

### 🧠 Función del ESP32
El ESP32 se conectó a la computadora mediante USB. No se utilizaron sensores ni actuadores, ya que el enfoque fue exclusivamente en la comunicación Bluetooth. Se configuró como servidor Bluetooth para que el celular pudiera detectarlo y conectarse.

## 📡 Programación

Este proyecto permite establecer una comunicación inalámbrica entre un ESP32 y un teléfono celular mediante Bluetooth. El objetivo es recibir mensajes escritos desde una app móvil y mostrarlos en el monitor serial de la computadora.

### 🔧 Flujo del código

1. **Librería Bluetooth**
   - Se incluye `BluetoothSerial.h` para habilitar la comunicación Bluetooth.
   - Se crea el objeto `SerialBT` para manejar la conexión.

2. **Configuración inicial (`setup()`)**
   - Se inicia la comunicación serial con `Serial.begin(115200)`.
   - Se activa el Bluetooth con `SerialBT.begin("ESP32AÑ")`.
   - Se imprime un mensaje indicando que el Bluetooth está listo.

3. **Ciclo principal (`loop()`)**
   - Se verifica si hay datos disponibles con `SerialBT.available()`.
   - Si se detecta un mensaje:
     - Se lee con `SerialBT.readString()`.
     - Se muestra en el monitor serial con `Serial.println()`.
   - Se incluye un retraso de 1 segundo (`delay(1000)`) para evitar sobrecarga.

### 📲 Aplicación

Este código convierte al ESP32 en un receptor Bluetooth que recibe texto desde un celular y lo muestra en tiempo real en la computadora. Es útil para proyectos de:
- Comunicación inalámbrica
- Monitoreo de datos
- Control remoto básico

## 📈 Resultados y Observaciones

- La conexión Bluetooth fue exitosa y estable.  
-  Los mensajes enviados desde el celular se reflejaron correctamente en el monitor serial.  
-  El ESP32 respondió de forma inmediata.  
- No se presentaron errores de transmisión ni desconexiones durante la prueba.

### Codigo
```cpp
#include "BluetoothSerial.h"   

BluetoothSerial SerialBT;      
void setup() {
  Serial.begin(115200);       
  SerialBT.begin("ESP32AÑ");   
  Serial.println("Bluetooth listo. Esperando conexión...");
}

void loop() {
  if (SerialBT.available()) {                
    String mensaje = SerialBT.readString();  
    Serial.println("Recibido: " + mensaje);  
  delay(1000);  
}
```

## 📹 Evidencias
[Evidencias en video aquí.](https://youtube.com/shorts/FjRERy2lNNs?si=2Luq59n9TTcmMw0b)