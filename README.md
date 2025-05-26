# apuntes-corte-3
# Apuntes de Control de Movimiento – Ingeniería Mecatrónica

---

## Torque Reflejado

El torque reflejado es el torque observado en el eje del motor debido a la carga externa, teniendo en cuenta el sistema de transmisión. Este torque depende de la relación de transmisión y del tipo de mecanismo utilizado.

### Factores que afectan el torque reflejado:
- Relación de transmisión (ej. engranajes, poleas)
- Eficiencia del mecanismo
- Pérdidas mecánicas por fricción, desalineaciones, deformaciones
- Masa y geometría de la carga acoplada

---

## Eficiencia y Calidad del Mecanismo

La eficiencia del mecanismo determina qué porcentaje de la potencia de entrada se transfiere útilmente a la salida.

### Causas comunes de pérdida de eficiencia:
- Fricción en rodamientos o guías
- Juegos mecánicos (backlash)
- Flexión o deformación de componentes
- Alineamiento incorrecto

---

## Relación de Inercia

La relación de inercia es la fracción de la inercia total que afecta al eje motriz, considerando todos los elementos acoplados, incluyendo:

- Acoples
- Cargas móviles
- Poleas o engranajes

Una relación de inercia adecuada mejora el control del sistema y previene sobreesfuerzos del motor.

---

## Sistema Polea–Correa

Sistema de transmisión que convierte el movimiento rotacional de un eje a otro, mediante una o más poleas conectadas por una correa.

### Ventajas:
- Transmisión a distancia
- Bajo costo
- Fácil mantenimiento

### Desventajas:
- Posible deslizamiento
- Menor precisión
- Dependencia del tensado adecuado

---

## Tornillo Sin Fin y Tornillo Guía

Este mecanismo convierte movimiento rotacional en lineal, usando un tornillo (husillo) y una tuerca deslizante (cápsula).

### Tipos de rosca:
- Trapezoidal: Más comunes, más fricción, más capacidad de carga.
- Cuadrada: Más eficientes, pero más costosas y difíciles de fabricar.

### Ventajas:
- Buena transmisión de fuerza
- Capacidad de autobloqueo

### Desventajas:
- Pérdidas por fricción
- Posible backlash

---

## Tornillo ACME y Tornillo de Esferas

### Tornillo ACME
- Rosca trapezoidal
- Alta resistencia y durabilidad
- Menor eficiencia por mayor fricción
- Ideal para sistemas que requieren autobloqueo

### Tornillo de Esferas (Ball Screw)
- Utiliza esferas recirculantes para reducir fricción
- Alta eficiencia (hasta 90%)
- Mayor precisión
- No tiene capacidad de autobloqueo, se necesita freno externo

---

## Backlash

El backlash es el juego o espacio muerto que existe entre dos componentes acoplados mecánicamente, y genera errores de posicionamiento en sistemas de control.

### Ejemplo práctico:
En un motor de avión PT6, antes se usaban tres palancas con guayas (cables mecánicos). Si una palanca se movía un poco, el movimiento no se reflejaba en el motor debido al juego mecánico. Esto causaba errores y poca precisión.

Solución: Se reemplazó el sistema mecánico por un encoder electrónico, eliminando el backlash y mejorando el control del motor.

---

# Ejercicios

**Ejercicio 1: Torque Reflejado**
Una carga lineal de 10 kg se mueve con un sistema tornillo-guía de paso 5 mm/rev acoplado directamente a un motor. Si el coeficiente de eficiencia del tornillo es del 80 %, calcula el torque reflejado en el eje del motor cuando la carga se mueve con una aceleración de 1 m/s². Desprecia fricción adicional.

**Datos:**

- Masa: $\( m = 10 \, \text{kg} \)$
- Aceleración: $\( a = 1 \, \text{m/s}^2 \)$
- Paso del tornillo: $\( p = 5 \, \text{mm/rev} = 0.005 \, \text{m/rev} \)$
- Eficiencia: $\( \eta = 0.8 \)$

**Fórmula del torque reflejado:**

$$
T = \frac{F \cdot p}{2\pi \cdot \eta}
$$

Donde:

$$
F = m \cdot a = 10 \cdot 1 = 10 \, \text{N}
$$

Sustituyendo:

$$
T = \frac{10 \cdot 0.005}{2\pi \cdot 0.8} = \frac{0.05}{5.0265} \approx 0.00994 \, \text{Nm}
$$

**Respuesta:**
El torque reflejado es aproximadamente **0.00994 Nm**.

---

**Ejercicio 2: Relación de Inercia**
Un sistema de polea-correa conecta un motor a una carga. La polea del motor tiene un radio de 5 cm y la de la carga 15 cm. La inercia de la carga es de 0.09 kg·m². Calcula la inercia reflejada al eje del motor.


**Datos:**

- Radio de polea motriz: $\( r_1 = 5 \, \text{cm} \)$
- Radio de polea conducida: $\( r_2 = 15 \, \text{cm} \)$
- Inercia de la carga: $\( J_{\text{carga}} = 0.09 \, \text{kg·m}^2 \)$

**Relación de transmisión:**

$$
N = \frac{r_2}{r_1} = \frac{15}{5} = 3
$$

**Inercia reflejada al motor:**

$$
J_{\text{reflejada}} = \frac{J_{\text{carga}}}{N^2} = \frac{0.09}{3^2} = \frac{0.09}{9} = 0.01 \, \text{kg·m}^2
$$

**Respuesta:**
La inercia reflejada al eje del motor es **0.01 kg·m²**.


---

**Ejercicio 3: Análisis de Backlash**
Un sistema de posicionamiento tiene un backlash de 0.3°. Si el sistema realiza 100 ciclos de avance y retroceso por hora, ¿cuánto error acumulado puede presentar en una jornada de 8 horas si no se corrige el backlash?


**Datos:**

- Backlash por ciclo: $\( 0.3^\circ \)$
- Ciclos por hora: 100
- Horas de trabajo: 8

**Cálculo del error total:**

$$
\text{Error total} = 0.3^\circ \cdot 100 \cdot 8 = 240^\circ
$$

**Respuesta:**
El sistema puede acumular hasta **240° de error angular** por backlash en una jornada de 8 horas si no se corrige.

---

# Gemelos Digitales con MATLAB y Quanser – Servo 3

---

## ¿Qué es un Gemelo Digital?

Un **gemelo digital** es una réplica virtual de un sistema físico que simula su comportamiento en tiempo real. Se utiliza para **análisis**, **diagnóstico**, **predicción de fallas** y **optimización del rendimiento** del sistema original.

### Características:
- Replica dinámica del sistema real
- Actualización en tiempo real con datos sensoriales
- Interacción directa con el sistema físico (control bidireccional)

---

## MATLAB y Simulink para Gemelos Digitales

**MATLAB** y **Simulink** permiten construir modelos físicos detallados que pueden actuar como gemelos digitales.

### Herramientas clave:
- **Simulink**: entorno de modelado y simulación en tiempo continuo y discreto.
- **Simscape / Simscape Multibody**: para modelado físico.
- **Stateflow**: para lógica de control.
- **Instrument Control Toolbox**: para comunicación con hardware real.
- **Digital Twin Toolbox (opcional)**: para aplicaciones industriales avanzadas.

---

## Quanser Servo 3 y su Uso como Plataforma de Gemelo Digital

El **Quanser SRV03 (Servo 3)** es una planta didáctica de control rotacional usada en laboratorios de ingeniería para diseño y prueba de sistemas de control.

### Componentes del SRV03:
- Motor DC con encoder óptico
- Disco inercial acoplado
- Amplificador de potencia
- Carga variable
- Sensores de posición

### Aplicaciones con gemelos digitales:
1. **Modelado del sistema SRV03** en Simulink usando ecuaciones dinámicas.
2. **Validación del modelo** mediante comparación con datos reales.
3. **Implementación del control** desde el gemelo digital.
4. **Monitoreo en tiempo real** usando tarjetas de adquisición (DAQ) conectadas al hardware real.

---

## Simulaciones en MATLAB y Simulink

### Pasos típicos:

1. **Modelado matemático del Servo 3**:
   - Ecuaciones del motor DC:
   - 
     $$V(t) = L\frac{di(t)}{dt} + Ri(t) + K_b \omega(t)$$
     
     $$J\frac{d\omega(t)}{dt} + B\omega(t) = K_t i(t)$$

2. **Implementación del modelo en Simulink**:
   - Uso de bloques de:
     - Ganancias
     - Integradores
     - Sumas
     - Bloques de transferencia

3. **Diseño del controlador** (P, PI o PID)

4. **Comparación entre el modelo y la planta real** conectando el Servo 3 por medio de una tarjeta Quanser Q2-USB o similar.

5. **Interacción en tiempo real**:
   - El sistema físico y el gemelo digital se sincronizan
   - Se puede predecir el comportamiento ante fallas o cambios de parámetros

---

## Ventajas del uso de Gemelos Digitales en Ingeniería

- Reducción de costos por pruebas físicas
- Detección anticipada de fallos
- Validación de diseños sin riesgos
- Entrenamiento seguro de operadores
- Desarrollo ágil de controladores

---

## Ejemplo de Práctica con el Servo 3

1. **Objetivo**: Diseñar un gemelo digital del SRV03 y validarlo con el sistema físico.
2. **Pasos**:
   - Crear el modelo dinámico en Simulink
   - Calibrar parámetros (masa, fricción, constante del motor)
   - Implementar control PID
   - Comparar salida del modelo con medición real
3. **Resultados esperados**:
   - Error bajo entre gemelo digital y planta física
   - Respuesta del controlador óptima en ambos entornos

---


