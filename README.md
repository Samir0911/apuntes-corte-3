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


# Dimensionamiento y Cálculo de un Servomotor (Servo Sizing)

---

## Pasos a seguir para el cálculo

En el ejemplo del video, se dimensiona el accionamiento de un **repartidor de pasada** para la fabricación de bobinas.

### 1. Modelar el sistema mecánico del eje
- Se escoge el modelo más cercano al sistema real en el software de cálculo.
- Se introducen datos físicos y dinámicos.

### 2. Definir el perfil de movimiento
- El repartidor se mueve de **0 a 42 mm y regresa a 0 mm**, sincronizado con el giro del núcleo.
- Por cada vuelta del núcleo, el carro del repartidor se desplaza **1 mm** (ancho del hilo).
- Cálculo del número de vueltas necesarias:

  $$\frac{42\ \text{mm (ancho núcleo)}}{1\ \text{mm (hilo/vuelta)}} = 42\ \text{vueltas}$$

- A una velocidad de:

  $$10{,}000\ \text{RPM} = \frac{10{,}000}{60} \approx 166.66\ \text{rev/s}$$

- El tiempo disponible para hacer un ciclo (ida y regreso):

  $$\frac{1\ \text{s}}{166.66 / 42} \approx 0.504\ \text{segundos} = 504\ \text{ms}$$

### 3. Calcular
- Se define la gama del producto (motor, reductor, tensión de red, etc.).
- Se calcula el par y la inercia total del sistema.

### 4. Optimizar
- Se obtienen múltiples resultados y se selecciona la opción más eficiente.
- Se ajustan parámetros como:
  - Relación de reducción
  - Paso del husillo
  - Diámetro de poleas
  - Perfil de movimiento

---

## Optimización del Accionamiento

Para **optimizar el par eficaz del motor**, se analizan:

- **Relaciones de reducción**:
  
  Minimizar el torque modificando la relación de engranajes. Por ejemplo:

  - Con $\( i = 1.2 \)$: par alto.
  - Con $\( i = 5 \)$: par reducido al mínimo.

- **Paso del husillo**:
  
  - Un paso mayor (ej. 5 mm) aumenta el par requerido.
  - Un paso menor (ej. 2 mm) reduce el par.

- **Perfil de aceleración y jerk**:
  
  - El "jerk" (derivada de la aceleración) impacta negativamente en la mecánica si no se suaviza el perfil.
  - Optimizar curvas de posición, velocidad y aceleración para minimizarlo.

---

## Herramientas de Cálculo - Motion Sizer

- Calcular manualmente el sistema completo puede ser tedioso y propenso a errores.
- Existen softwares como **Motion Sizer** que permiten:
  - Ingresar parámetros físicos y cinemáticos.
  - Acceder a bases de datos de componentes (motores, reductores).
  - Obtener resultados optimizados automáticamente.
  - Generar listas de referencias para compras.

---

## Sistemas Inestables

En algunos casos, los sistemas inestables pueden ser identificados en **lazo abierto**, aunque con ciertas limitaciones. Un ejemplo común es un **motor inestable en posición**. En estos casos:

- El modelo obtenido es una **aproximación**.
- El **controlador** debe asumir el margen de error.

---

## Modelado en Lazo Abierto

### Modelo: Primer orden + tiempo muerto + factor integrante

Para este tipo de sistemas, se utiliza el siguiente modelo de función de transferencia:

$$G = \frac{K e^{-s t_o}}{(\tau s + 1)s}$$

### Metodología

1. Captura de la **curva de reacción** en lazo abierto.
2. Derivación de la curva (numéricamente o por simulación).
3. Ajuste del resultado a un sistema de primer orden más tiempo muerto (FOPDTI).

---

## Aproximación FOPDTI - Ejemplo

- Se deriva la curva de reacción.
- Se aproxima con un sistema de primer orden más tiempo muerto.

Datos del método de Smith:

$$t_2 = 1.9 \quad t_1 = 1.24$$

---

## Aproximación IPDT

Este modelo considera un **factor integrante** más un **tiempo muerto**:

$$G = \frac{K e^{-s t_o}}{s}$$

### Metodología

1. Captura de la curva de reacción en lazo abierto.
2. Ubicación de puntos característicos de la curva.
3. Cálculo de los parámetros $K$ y $t_o$.

Fórmulas:

$$K = \frac{O_2 - O_1}{(I_2 - I_1)(T_3 - T_2)}$$

$$t_o = T_2 - T_1$$

---

## Ejemplo Práctico

Valores:

- $T_3 = 5.86$
- $T_2 = 2.19$
- $T_1 = 1.02$
- $O_2 = 3.47$
- $O_1 = 0$
- $I_2 - I_1 = 1$

Aplicando las fórmulas:

$$K = \frac{3.47 - 0}{(1)(5.86 - 2.19)} = 0.94$$

$$t_o = 2.19 - 1.02 = 1.17$$

Función de transferencia estimada:

$$G = \frac{0.94 e^{-s 1.17}}{s}$$

---

## Ejercicio 1: Método IPDT

Se ha obtenido la siguiente información de una curva de reacción de un sistema:

- $T_3 = 6.0 \ \text{s}$
- $T_2 = 2.5 \ \text{s}$
- $T_1 = 1.0 \ \text{s}$
- $O_2 = 4.0$
- $O_1 = 0$
- $I_2 - I_1 = 1$

Determina la función de transferencia aproximada del sistema.

### Solución:

Calculamos $K$:

$$K = \frac{O_2 - O_1}{(I_2 - I_1)(T_3 - T_2)} = \frac{4.0 - 0}{(1)(6.0 - 2.5)} = \frac{4.0}{3.5} = 1.14$$

Calculamos $t_o$:

$$t_o = T_2 - T_1 = 2.5 - 1.0 = 1.5$$

Función de transferencia aproximada:

$$G(s) = \frac{1.14 \cdot e^{-s 1.5}}{s}$$

---

## Ejercicio 2: Método FOPDTI

Se registra una curva de reacción de un sistema inestable. Se aproxima por derivación a un sistema de primer orden más tiempo muerto. Se obtienen los siguientes parámetros:

- $K = 2$
- $\tau = 4$
- $t_o = 1.2$

Encuentra la función de transferencia aproximada.

### Solución:

Usamos el modelo FOPDTI:

$$G(s) = \frac{K \cdot e^{-s t_o}}{(\tau s + 1)s}$$

Sustituimos:

$$G(s) = \frac{2 \cdot e^{-s 1.2}}{(4s + 1)s}$$


## Conclusiones

- Es posible obtener una función de transferencia aproximada para sistemas de orden superior.
- Los métodos basados en la curva de reacción en lazo abierto presentan limitaciones.
- En la industria son comunes los sistemas sobreamortiguados.
- Con los métodos de dos puntos se pueden modelar incluso sistemas de segundo orden.

---

#Sintonización de Controladores PID en Lazo Cerrado

## Fundamento General

La sintonización PID en lazo cerrado consiste en hacer pruebas directamente sobre el sistema en operación, sin romper el lazo de control. El objetivo es ajustar los parámetros del controlador PID (Proporcional, Integral, Derivativo) observando la respuesta del sistema.

A partir de la respuesta, se identifican características clave como la frecuencia de oscilación y la ganancia crítica, que permiten calcular los parámetros del PID.

---

## Método de Ziegler-Nichols (Ciclo Último)

Este método busca obtener los parámetros PID a partir de una oscilación sostenida en la salida del sistema.

### Pasos:

1. Poner las ganancias del controlador PID en cero.
2. Aumentar $K_p$ (proporcional) hasta lograr una **oscilación sostenida y estable**.
3. Medir el **período de oscilación** ($P_u$).
4. Registrar la **ganancia proporcional** que causó dicha oscilación ($K_u$).

---

## Ejemplo Analítico

Se da un sistema con función de transferencia:

$$G = \frac{1}{s^3 + 6s^2 + 11s + 6}$$

La función de transferencia del sistema en lazo cerrado es:

$$G_o = \frac{K_p \cdot \frac{1}{s^3 + 6s^2 + 11s + 6}}{1 + K_p \cdot \frac{1}{s^3 + 6s^2 + 11s + 6}} = \frac{K_p}{s^3 + 6s^2 + 11s + 6 + K_p}$$

Se analiza para $s = j\omega$ y se igualan parte real e imaginaria a cero para encontrar $K_u$ y $P_u$.

### Parte imaginaria:

$$-\omega^2 + 11 = 0 \Rightarrow \omega = \sqrt{11}$$

$$P_u = \frac{2\pi}{\omega} = \frac{2\pi}{\sqrt{11}} \approx 1.894 \ \text{segundos}$$

### Parte real:

$$-6\omega^2 + 6 + K_p = 0 \Rightarrow K_p = 6\omega^2 - 6$$

Sustituyendo $\omega = \sqrt{11}$:

$$K_p = 6 \cdot 11 - 6 = 60 = K_u$$

---

## Fórmulas de Sintonización (Ziegler-Nichols)

| Tipo | $K_p$       | $T_i$             | $T_d$           |
|------|-------------|-------------------|------------------|
| P    | $0.5 K_u$   | —                 | —                |
| PI   | $0.45 K_u$  | $\frac{P_u}{1.2}$ | —                |
| PID  | $0.6 K_u$   | $\frac{P_u}{2}$   | $\frac{P_u}{8}$  |

Tabla 1. Fórmulas de Sintonización (Ziegler-Nichols).


---

## Método del Relé

Este método mejora el de Ziegler-Nichols evitando saturar el sistema. Consiste en usar un **relé con histéresis** como controlador para inducir una oscilación controlada.

### Pasos:

1. (Opcional) Medir el tiempo para alcanzar el régimen estacionario en lazo abierto.
2. Cerrar el lazo usando un relé con histéresis.
3. Medir el **período de oscilación** ($P_u$) y la **amplitud** ($A_u$).
4. Calcular la **ganancia crítica** $K_c$:

$$K_c = \frac{4d}{\pi (A_u^2 - \varepsilon^2)}$$

---

## ¿Qué es el Método del Relé?

El método del relé es una técnica de sintonización PID **empírica** y **segura**, diseñada para obtener los parámetros del controlador sin necesidad de alcanzar condiciones de operación peligrosas o inestables, como ocurre con el método de Ziegler-Nichols.

Este método utiliza un **relé (controlador ON-OFF)** en lugar de una ganancia proporcional variable, generando una **oscilación sostenida** en la salida del sistema. A partir de esta respuesta se extraen parámetros útiles para el diseño del controlador PID.

---

## Objetivos del Método

- Obtener la **ganancia crítica** ($K_c$) de manera segura.
- Medir el **período de oscilación** ($P_u$).
- Evitar saturaciones o inestabilidades excesivas.
- Permitir la manipulación de la señal durante la prueba.

---

## Procedimiento

1. (Opcional) Verifica el tiempo necesario para que el sistema alcance el estado estacionario en lazo abierto.
2. Cierra el lazo e implementa un **controlador tipo relé con histéresis**.
3. Registra la respuesta del sistema: una **oscilación sostenida**.
4. Mide:
   - **Amplitud de la salida** ($A_u$)
   - **Histéresis del relé** ($\varepsilon$)
   - **Altura del relé** ($d$)
   - **Período de oscilación** ($P_u$)

---

## Cálculo de la Ganancia Crítica $K_c$

Se utiliza la siguiente fórmula para calcular la **ganancia equivalente** al obtener la oscilación con el relé:

$$K_c = \frac{4d}{\pi (A_u^2 - \varepsilon^2)}$$

Donde:

- $d$: altura del relé (amplitud de la señal de control ON/OFF)
- $A_u$: amplitud de oscilación de la salida
- $\varepsilon$: histéresis
- $\pi$: constante matemática (≈ 3.1416)

---

## Sintonización del Controlador

Con los valores de $K_c$ y $P_u$, se pueden usar **fórmulas adaptadas** similares a Ziegler-Nichols para obtener los parámetros del controlador. Ejemplo para un controlador **PI**:

- $$K_p = \frac{5K_c}{6}$$
- $$T_i = \frac{P_u}{5}$$

> Para controladores PID, se pueden usar fórmulas ampliadas según el diseño o la literatura utilizada.

---

## Ventajas del Método del Relé

- No se requiere llevar el sistema a una condición de oscilación por ganancia elevada.
- Permite observar y controlar la respuesta durante la prueba.
- Mayor seguridad para el sistema real.
- Es compatible con implementaciones en microcontroladores o sistemas digitales.

---

## Ejemplo Práctico

Se utiliza un relé de $d = 1.2$, se obtiene una oscilación de $A_u = 2.5$, con histéresis $\varepsilon = 0.3$, y un período de $P_u = 2.8$ s.

Se calcula:

$$K_c = \frac{4 \cdot 1.2}{\pi (2.5^2 - 0.3^2)} = \frac{4.8}{\pi (6.25 - 0.09)} = \frac{4.8}{\pi (6.16)} \approx \frac{4.8}{19.35} \approx 0.248$$

Luego, si se desea un controlador PI:

$$K_p = \frac{5 \cdot 0.248}{6} = 0.206 \quad ; \quad T_i = \frac{2.8}{5} = 0.56$$


---

## Fenómeno Wind-Up

Cuando el actuador alcanza sus límites, la acción integral del PID puede seguir acumulando error, lo que genera tiempos de respuesta excesivos y riesgo de saturación prolongada.

### Soluciones Anti-Windup

1. **Saturación de la acción integral**: Detiene la acumulación al alcanzar el límite.
2. **Integración condicional**: Pausa la integración cuando la salida se satura.
3. **Re-cálculo con seguimiento**: Se estima el comportamiento del actuador y se modula suavemente la acción integral.

Fórmula del tiempo de transición anti-windup:

$$T_t = T_i T_d$$

---

# Ejercicios: Sintonización PID en Lazo Cerrado

## Ejercicio 1: Método de Ziegler-Nichols (Ciclo Último)

Se realiza una prueba en lazo cerrado a un sistema. Se incrementa $K_p$ hasta que la salida presenta una **oscilación sostenida**. Se obtienen los siguientes datos:

- Ganancia última: $K_u = 48$
- Período último: $P_u = 2.5$ segundos

Determina los parámetros del controlador **PID** usando la tabla de Ziegler-Nichols.

### Solución:

Usamos las fórmulas del método:

- $$K_p = 0.6 K_u = 0.6 \cdot 48 = 28.8$$
- $$T_i = \frac{P_u}{2} = \frac{2.5}{2} = 1.25$$
- $$T_d = \frac{P_u}{8} = \frac{2.5}{8} = 0.3125$$

**Resultado**:

Controlador PID:
- $K_p = 28.8$
- $T_i = 1.25$
- $T_d = 0.3125$

---

## Ejercicio 2: Método del Relé

Durante una prueba con **controlador tipo relé con histéresis**, se obtienen los siguientes datos:

- Altura de histéresis: $d = 1.5$
- Amplitud de oscilación: $A_u = 2.0$
- Histéresis: $\varepsilon = 0.3$
- Período de oscilación: $P_u = 3.2$ segundos

Determina la ganancia crítica $K_c$ y calcula los parámetros del **controlador PI**.

### Solución:

#### Paso 1: Calcular la ganancia crítica $K_c$

Usamos la fórmula:

$$
K_c = \frac{4d}{\pi (A_u^2 - \varepsilon^2)} = \frac{4 \cdot 1.5}{\pi (2.0^2 - 0.3^2)} = \frac{6}{\pi (4 - 0.09)} = \frac{6}{\pi (3.91)} \approx \frac{6}{12.29} \approx 0.488
$$

#### Paso 2: Calcular parámetros del PI

Según el método del relé:

- $$K_p = \frac{5 K_c}{6} = \frac{5 \cdot 0.488}{6} \approx 0.407$$
- $$T_i = \frac{P_u}{5} = \frac{3.2}{5} = 0.64$$

**Resultado**:

Controlador PI:
- $K_p \approx 0.407$
- $T_i = 0.64$



## Conclusiones

- Las pruebas en lazo cerrado permiten diseñar controladores PID directamente sobre el sistema.
- El método de Ziegler-Nichols, aunque antiguo, sigue siendo útil en la industria.
- El método del relé ofrece una alternativa más segura y manipulable.
- Implementar estrategias anti-windup es crucial en aplicaciones reales.

---

# Ejemplo paso a paso: Modelo en Espacio de Estados con ADRC

## 1. Ecuación diferencial del sistema

Dado un sistema mecánico masa-resorte-amortiguador con entrada $u(t)$ y salida $y(t)$:

$$u(t) - K y(t) - B \dot{y}(t) = M \ddot{y}(t)$$

Este modelo representa la Segunda Ley de Newton para un sistema masa-resorte-amortiguador.

---

## 2. Despeje de la aceleración

Se despeja $\ddot{y}(t)$ (segunda derivada de la salida) para convertirlo en una forma apta para el espacio de estados:

$$\ddot{y}(t) = \frac{u(t)}{M} - \frac{K}{M} y(t) - \frac{B}{M} \dot{y}(t)$$

---

## 3. Definición de variables de estado

Se define:

- $x_1 = y(t)$ (posición)
- $x_2 = \dot{y}(t)$ (velocidad)

Por lo tanto:

- $\dot{x}_1 = x_2$
- $\dot{x}_2 = \ddot{y}(t)$

Entonces:

$$\dot{x}_2 = \frac{u(t)}{M} - \frac{K}{M} x_1 - \frac{B}{M} x_2$$

---

## 4. Forma matricial del sistema

Se reescribe el sistema como:

### Ecuación de estado:

$$\dot{x} = \begin{bmatrix} \dot{x}_1 \\ \dot{x}_2\end{bmatrix}=\begin{bmatrix}0 & 1 \\-\frac{K}{M} & -\frac{B}{M}\end{bmatrix}\begin{bmatrix}x_1 \\x_2\end{bmatrix}+\begin{bmatrix}0 \\\frac{1}{M}\end{bmatrix}u(t)$$

### Ecuación de salida:

$$y = \begin{bmatrix}1 & 0\end{bmatrix}\begin{bmatrix}x_1 \\x_2\end{bmatrix}+ 0 \cdot u(t)$$

---

## 5. Inclusión de perturbación generalizada en ADRC

La ecuación dinámica incluye una perturbación $\varepsilon(t)$:

$$
\ddot{y} = \frac{u(t)}{M} - \frac{K}{M} y(t) - \frac{B}{M} \dot{y}(t)
$$

Se reescribe como:

$$
y^{(n)} = \mathbb{K} u + \varepsilon(t)
$$

Donde:

- $\mathbb{K} = \frac{1}{M}$
- $\varepsilon(t) = -\frac{K}{M} y(t) - \frac{B}{M} \dot{y}(t)$

---

## 6. Modelo extendido de estados (ESO - Observador de estados extendido)

Se construye el modelo incluyendo la perturbación $\varepsilon$ y su derivada como nuevos estados:

- $x_1 = y$
- $x_2 = \dot{y}$
- $x_3 = \varepsilon$
- $x_4 = \dot{\varepsilon}$

Entonces el sistema se modela como:

$$
\begin{aligned}
\dot{x}_1 &= x_2 \\
\dot{x}_2 &= \mathbb{K} u + x_3 \\
\dot{x}_3 &= x_4 \\
\dot{x}_4 &= \ddot{\varepsilon}
\end{aligned}
$$

---

## 7. Implementación del observador (estimación de estados)

Se define el error de observación:

$$
e = x_1 - \hat{x}_1
$$

Donde $\hat{x}_i$ son las estimaciones del observador.

El observador se plantea como:

$$
\begin{aligned}
\dot{\hat{x}}_1 &= \hat{x}_2 + \lambda_3 e \\
\dot{\hat{x}}_2 &= \mathbb{K} u + \hat{x}_3 + \lambda_2 e \\
\dot{\hat{x}}_3 &= \hat{x}_4 + \lambda_1 e \\
\dot{\hat{x}}_4 &= 0 + \lambda_0 e
\end{aligned}
$$

---

## 8. Ley de control del ADRC

Una vez estimados los estados y la perturbación, se define la ley de control para el seguimiento de una trayectoria deseada $y^*$:

$$u = (1 / K) * [ y^(n)* - k1*(ŷ̇ - ẏ*) - k0*(ŷ - y*) - ε̂ ]$$


Donde:

- $k_1$, $k_0$ son ganancias del controlador
- $\hat{\varepsilon}$ es la perturbación estimada

---

## 9. Polinomio característico para el error de seguimiento

Para garantizar estabilidad y buena respuesta dinámica, se define el siguiente polinomio de error:

$$
P_e(s) = s^2 + k_1 s + k_0
$$

Los valores de $k_1$ y $k_0$ se eligen para colocar los polos en el semiplano izquierdo (criterio de Hurwitz).

---

## 10. Parámetros numéricos del ejemplo

Se dan:

- $K = 0.5$
- $B = 0.2$
- $M = 0.5$
- Entonces $\mathbb{K} = \frac{1}{0.5} = 2$

---

# Fórmulas del Método ADRC (Active Disturbance Rejection Control)

## 1. Modelo Dinámico del Sistema

### Ecuación diferencial base:
$$
u(t) - K y(t) - B \dot{y}(t) = M \ddot{y}(t)
$$

### Despeje de la aceleración:
$$
\ddot{y}(t) = \frac{u(t)}{M} - \frac{K}{M} y(t) - \frac{B}{M} \dot{y}(t)
$$

---

## 2. Espacio de Estados

### Definición de estados:
$$
x_1 = y \quad ; \quad x_2 = \dot{y}
$$

### Derivadas:
$$
\dot{x}_1 = x_2
$$
$$
\dot{x}_2 = \frac{u(t)}{M} - \frac{K}{M} x_1 - \frac{B}{M} x_2
$$

### Forma matricial:
$$
\dot{X}(t) = A X(t) + B u(t)
$$
$$
y(t) = C X(t) + D u(t)
$$

Donde:

$$
A =
\begin{bmatrix}
0 & 1 \\
-\frac{K}{M} & -\frac{B}{M}
\end{bmatrix}, \quad
B =
\begin{bmatrix}
0 \\
\frac{1}{M}
\end{bmatrix}, \quad
C =
\begin{bmatrix}
1 & 0
\end{bmatrix}, \quad
D = [0]
$$

---

## 3. Modelo ADRC

### Forma general:
$$\ddot{y} = \mathbb{K} u + \varepsilon(t)$$

Donde:
$$\mathbb{K} = \frac{1}{M}$$

$$\varepsilon(t) = -\frac{K}{M} y(t) - \frac{B}{M} \dot{y}(t)$$

---

## 4. Estados Extendidos (ESO)

### Nuevos estados:
$$
x_3 = \varepsilon \quad ; \quad x_4 = \dot{\varepsilon}
$$

### Modelo extendido:
$$
\begin{aligned}
\dot{x}_1 &= x_2 \\
\dot{x}_2 &= \mathbb{K} u + x_3 \\
\dot{x}_3 &= x_4 \\
\dot{x}_4 &= \ddot{\varepsilon}
\end{aligned}
$$

---

## 5. Observador de Estados Extendidos

### Error de observación:
$$
e = x_1 - \hat{x}_1
$$

### Ecuaciones del observador:
$$
\begin{aligned}
\dot{\hat{x}}_1 &= \hat{x}_2 + \lambda_3 e \\
\dot{\hat{x}}_2 &= \mathbb{K} u + \hat{x}_3 + \lambda_2 e \\
\dot{\hat{x}}_3 &= \hat{x}_4 + \lambda_1 e \\
\dot{\hat{x}}_4 &= 0 + \lambda_0 e
\end{aligned}
$$

---

## 6. Ley de Control ADRC

### General:

$$
u = (1/𝕂) * [ y⁽ⁿ⁾* - k₁ (ŷ̇ - ẏ*) - k₀ (ŷ - y*) - ε̂ ]
$$

---

## 7. Polinomio Característico del Error

$$
P_e(s) = s^2 + k_1 s + k_0
$$

---

## 8. Condiciones Numéricas del Ejemplo

$$K = 0.5, \quad B = 0.2, \quad M = 0.5$$

$$\mathbb{K} = \frac{1}{M} = 2$$

---

## 9. Aproximación del Observador

### Derivadas observadas:
$$
\dot{x}_1 = x_2 + \lambda_3 e_1 \\
\dot{x}_2 = \mathbb{K} u + x_3 + \lambda_2 e_1 \\
\dot{x}_3 = x_4 + \lambda_1 e_1 \\
\dot{x}_4 = 0 + \lambda_0 e_1
$$

### Dinámica del error del observador:
$$
e^{(4)} + \lambda_3 \dddot{e}_1 + \lambda_2 \ddot{e}_1 + \lambda_1 \dot{e}_1 + \lambda_0 e_1 = \ddot{\varepsilon}
$$


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
