# 🚗 Vehículo Controlado por Bluetooth con Motores DC

## 🎯 Propósito
Este proyecto consistió en el diseño y construcción de un vehículo a control remoto, utilizando motores de corriente directa (DC), un puente H para el control de dirección, y un microcontrolador ESP32 para la comunicación vía Bluetooth.  
El objetivo principal fue aplicar conocimientos básicos de electrónica, mecánica y programación para competir en una dinámica de robótica.

## 🧭 Metas del Proyecto
**Meta General:**  
Desarrollar un prototipo funcional de un coche a control remoto que pueda participar en una competencia de robótica, demostrando habilidades de diseño, integración de sistemas y trabajo en equipo.

**Metas Específicas:**
- Implementar un sistema de control que permita maniobrar el vehículo con precisión y velocidad.  
- Diseñar una pala frontal que facilite la interacción con objetos (como pelotas) durante la competencia.  
- Optimizar el rendimiento del coche para lograr una ventaja competitiva en el juego.

## 📐 Alcance del Proyecto
El proyecto abarcó desde la conceptualización del diseño hasta la implementación completa del sistema electrónico y mecánico.  
Se trabajó con materiales accesibles y se estableció un límite de dos semanas para su desarrollo.

Incluye:
- Diseño estructural del vehículo  
- Integración de componentes electrónicos  
- Programación del sistema de control  
- Pruebas funcionales previas a la competencia

## 🔄 Proceso del Trabajo

### 👥 Organización del Equipo
El equipo se dividió en dos áreas principales:
- Desarrollo del código de programación
- Desarrollo electrónico
- Diseño

Mientras algunos miembros se encargaron de la estructura del coche, otros se enfocaron en la programación y conexiones.

### 🧰 Materiales Utilizados
- 2 motores DC  
- Puente H  
- ESP32  
- Protoboard  
- Jumpers  
- LED  
- Batería de 9V  
- MDF para la base  
- PLA para impresión 3D de la pala frontal

### 🧪 Tecnologías Utilizadas
- **Lenguajes:** Python, C++  
- **Hardware:** ESP32, Arduino  
- **Software:** SolidWorks, PSeInt  
- **Otros:** CircuitVerse

### ⚡ Sistema Electrónico
- Se conectaron los motores al puente H, asegurando una correcta polaridad y conexión a tierra.  
- Los pines IN1 a IN4 se configuraron para controlar la dirección de giro de los motores.  
- La ESP32 se integró como unidad de control, con especial atención a la asignación de pines y la protección contra cortocircuitos.

## 🧠 Programación
Se desarrolló un programa en Arduino IDE que permite controlar el coche mediante una aplicación Bluetooth.

Funciones principales:
- Avanzar  
- Retroceder  
- Girar a la izquierda/derecha  
- Detenerse  
- Ajustar velocidad mediante PWM  

La lógica de movimiento se basó en la manipulación de los motores: por ejemplo, para girar, se detiene una rueda mientras la otra sigue girando.  
El código para controlar el coche se encuentra al final del artículo.

## 📈 Resultados y Observaciones
Antes de la competencia, el coche mostró un buen desempeño:
- Respondía a los comandos  
- La pala funcionaba correctamente  
- El diseño era estable  

Durante el evento surgieron algunos inconvenientes:
- Uno de los motores se desprendió tras un choque con una silla  
- El control Bluetooth presentaba cierto retraso en la respuesta  
- Los movimientos eran algo bruscos, lo que dificultaba la precisión  

A pesar de estos detalles, el coche cumplió con los objetivos técnicos del proyecto.

## 🧩 Reflexiones Finales
El proyecto fue una excelente oportunidad para aplicar conocimientos teóricos en un entorno práctico.  
Se logró integrar electrónica, mecánica y programación en un sistema funcional.

Áreas de mejora identificadas:
- Realizar más pruebas antes de la competencia  
- Mejorar el montaje de los motores  
- Optimizar el control desde la app  

Esta experiencia reforzó la importancia de la planificación, el trabajo colaborativo y la iteración constante para lograr un producto funcional y competitivo.

## 📹 Evidencias
[Evidencias en video aquí.]()