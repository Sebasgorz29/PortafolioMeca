#  🛠️ KiCad

---

## Autores del Proyecto

- **Sebastian Gomez Rodriguez**
  <img src="recursos/foto_sebastian.jpg" alt="Foto Sebastian Gomez Rodriguez" width="200" />

- **Erik Andre Zepeda Tapia**
  <img src="recursos/foto_erik.jpg" alt="Foto Erik Andre Zepeda Tapia" width="200" />

---

## Evidencia y Fotografías de la Placa

- **Vista de la Placa PCB**
  <img src="recursos/pcb.jpg" alt="Vista PCB" width="400" />

- **Circuito Ensamblado**
  <img src="recursos/pcb_ensamblada.jpg" alt="Circuito Ensamblado" width="400" />

---

## Tabla de Contenidos
1. Autores del Proyecto
2. Evidencia y Fotografías de la Placa
3. Flujo de Trabajo General
4. Fase 1: Captura Esquemática - Eeschema
5. Fase 2: Verificación Eléctrica y Asignación de Huellas
6. Fase 3: Diseño Físico de la PCB - PCB Editor
7. Fase 4: Ruteo y Planos de Cobre
8. Fase 5: DRC y Exportación de Archivos de Fabricación - Gerber
9. Puntos Ciegos y Lista de Chequeo Anti-Errores

---

## Flujo de Trabajo General

Esquemático Eeschema > Check ERC > Asignación de Footprints
         |
PCB Layout PCB Editor > Definir Edge.Cuts > Ruteo + Plano GND
         |
Check DRC > Vista 3D > Exportar Gerber / Drill .zip

---

## Fase 1: Captura Esquemática - Eeschema

1. **Creación del Proyecto:**
   - Abre KiCad > File > New Project.
   - Guarda el proyecto en un directorio dedicado. Ejemplo: mi_proyecto_pcb/

2. **Inserción de Componentes:**
   - Abre la librería de símbolos.
   - Busca componentes pasivos R, C, LED e integrados ATmega328P, ESP32, LM7805, etc.

3. **Cableado Eléctrico:**
   - Conecta los pines de los componentes usando la herramienta de cableado.
   - Usa Net Labels para señales repetitivas o largas como TX, RX, SDA, SCL para mantener el esquemático limpio y legible.

4. **Desacoplo de Alimentación:**
   - Coloca condensadores de desacoplo de 100 nF en paralelo entre VCC/VDD y GND, lo más cerca posible de cada pin de alimentación de los integrados.
   - Añade símbolos de alimentación GND y VCC.

---

## Fase 2: Verificación Eléctrica y Asignación de Huellas

1. **Anotación de Componentes:**
   - Haz clic en el icono Annotate Schematic para asignar identificadores numéricos automáticos: R1, R2, C1, U1.

2. **Electrical Rules Check - ERC:**
   - Corre el test ERC.
   - Solución a errores comunes:
     - Pin connected to other pins but not driven by any pin: Añade la etiqueta PWR_FLAG a la línea de entrada de VCC y GND.
     - Unconnected pin: Si un pin no se usará, márcalo explícitamente con la herramienta No Connect Flag.

3. **Asignación de Footprints - Huellas Físicas:**
   - Abre el Footprint Assignment Tool.
   - Asigna el encapsulado real a cada símbolo:
     - Componentes Through-Hole THD: Resistor_THT:R_Axial_DIN0207...
     - Componentes Surface Mount SMD: Resistor_SMD:R_0805_2012Metric o R_0603_1608Metric.
   - Verificación doble: Confirma el pitch - espaciado de pines en mm - consultando la hoja de datos datasheet del fabricante.

---

## Fase 3: Diseño Físico de la PCB - PCB Editor

1. **Importación desde el Esquemático:**
   - Abre el editor de PCB y actualiza la PCB desde el esquemático.
   - Haz clic en Update PCB y coloca la red de componentes ratsnest en el área de trabajo.

2. **Definición del Contorno de la Placa - Edge.Cuts:**
   - Selecciona la capa Edge.Cuts en el panel derecho.
   - Dibuja el borde cerrado de la PCB usando las herramientas de línea o rectángulo.
   - Nota: El contorno debe ser una figura geométrica completamente cerrada sin líneas superpuestas.

3. **Ubicación Estratégica de Componentes:**
   - Coloca los conectores como Micro-USB, Bornieres o Headers en los bordes de la placa.
   - Coloca los capacitores de desacoplo inmediatamente al lado del pin de alimentación correspondiente del IC.
   - Orienta los componentes para minimizar el cruce de líneas guía ratsnest.

---

## Fase 4: Ruteo y Planos de Cobre

1. **Reglas de Ancho de Pista - Traces:**
   - Ve a File > Board Setup > Design Rules > Net Classes.
   - Configura anchos según la corriente estimada:
     - Señales digitales / de datos: 0.2 mm a 0.25 mm
     - Alimentación VCC / GND: 0.5 mm a 1.0 mm o más si la corriente supera 1A.

2. **Ruteo Manual:**
   - Inicia el trazado en la capa superior F.Cu color rojo o inferior B.Cu color verde.
   - Regla de oro: Evita ángulos de 90°. Usa siempre cambios de dirección a 45° para reducir reflexiones de señal y prevenir trampas de ácido en la fabricación.
   - Para cambiar de capa durante el ruteo, inserta una Vía.

3. **Plano de Masa - Filled Zone:**
   - Selecciona la herramienta Add Filled Zone.
   - Elige la capa B.Cu y asígnala a la red GND.
   - Dibuja un rectángulo envolviendo toda la placa.
   - Rellena la zona de masa.

---

## Fase 5: DRC y Exportación de Archivos de Fabricación - Gerber

1. **Design Rules Check - DRC:**
   - Ejecuta el DRC - Inspect > Design Rules Checker.
   - Resuelve todos los errores y advertencias como untrack disconnects o clearance violations. Debe quedar en 0 Errores / 0 Advertencias.

2. **Inspección Visual 3D:**
   - Abre el visor 3D para verificar colisiones mecánicas, altura de componentes y serigrafía.

3. **Exportación de Archivos Gerber:**
   - Ve a File > Fabrication Outputs > Gerbers .gbr
   - Capas necesarias a incluir:
     - F.Cu - Cobre superior
     - B.Cu - Cobre inferior
     - F.Silkscreen - Serigrafía superior
     - B.Silkscreen - Serigrafía inferior
     - F.Mask - Máscara antisoldante superior
     - B.Mask - Máscara antisoldante inferior
     - Edge.Cuts - Contorno de la placa
   - Haz clic en Plot.
   - Haz clic en Generate Drill Files... para exportar los taladros en formato Excel / NC Drill.
   - Comprime todos los archivos .gbr y .drl generados en un único archivo .zip.

---