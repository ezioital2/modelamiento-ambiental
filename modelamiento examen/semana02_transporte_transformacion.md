# Semana 02 — Transporte y transformación de contaminantes asistida por IA

> Fuente: *MODELACIÓN AMBIENTAL semana 02.pptx* (46 diapositivas). Título completo: *Modelación del transporte y transformación de contaminantes asistida por Inteligencia Artificial: formulación, simulación y análisis de escenarios ambientales.*
> Transcripción limpia; las infografías se pasaron a texto. Las notas ⚠️ señalan errores de las diapositivas; su corrección está en [FORMULARIO.md](FORMULARIO.md).

---

## 1. Clasificación de contaminantes y tipos de fuentes

La modelación comienza identificando **(1) el tipo de contaminante, (2) su fuente de emisión y (3) el medio receptor**. Estas características determinan qué procesos de transporte y transformación hay que representar matemáticamente.

La **IA** apoya esta etapa (análisis de datos, patrones, selección de variables, escenarios), pero **la definición del modelo conceptual sigue siendo responsabilidad del ingeniero ambiental**.

**Secuencia (infografía, diap. 3):** Contaminante → Fuente → Medio receptor → Procesos ambientales → Modelo matemático → IA + simulación → Predicción.
- Fuentes típicas: **industria, agricultura, áreas urbanas**.
- **Lo que debemos conocer:** tipo de contaminante (físico, químico, biológico, radiactivo); características de la fuente (**puntual o no puntual**); medio receptor (aire, agua, suelo, sedimentos); condiciones ambientales (caudal, pH, temperatura); procesos relevantes (transporte y transformación); datos disponibles (mediciones, monitoreos, históricos).
- La IA sirve para: análisis de datos ambientales, identificación de patrones, selección de variables y construcción de escenarios.

### Tipos de contaminantes

| Tipo | Descripción y ejemplos |
|---|---|
| **Físicos** | Alteran la temperatura y la turbidez; también **ruido** y **radiación electromagnética**, que afectan la vida silvestre. |
| **Químicos** | Vienen de la agricultura (fertilizantes, pesticidas), la industria (solventes, residuos tóxicos) y los hogares (productos de limpieza). **Metales pesados (Hg, Pb)**: se **bioacumulan** y son tóxicos a lo largo de la cadena alimentaria. |
| **Biológicos** | **Patógenos** de aguas residuales mal gestionadas (riesgo para la salud pública). **Floraciones de algas nocivas** favorecidas por el exceso de nutrientes (**eutrofización**). |
| **Radiactivos** | Riesgo a **largo plazo** por su persistencia y potencial carcinogénico. Los **accidentes nucleares** son fuentes puntuales; la **minería y el tratamiento de minerales** son fuentes más dispersas. |

### ¿Dónde interviene la IA? (diap. 6) — la IA apoya todo el ciclo

| Etapa | Qué se hace | Aporte de la IA |
|---|---|---|
| 1. Datos | Monitoreos, sensores, imágenes, información histórica | Limpieza de datos, detección de anomalías, integración de fuentes |
| 2. Identificación y selección | Identificar el contaminante y las variables relevantes | Reconocimiento de patrones, selección de variables importantes |
| 3. Modelo conceptual | Representar los procesos de transporte y transformación | Sugerir procesos relevantes y estructuras de modelo |
| 4. Modelo matemático | Formular las ecuaciones y los parámetros | Asistencia en la formulación, estimación de parámetros, revisión de unidades |
| 5. Simulación y análisis | Ejecutar el modelo, análisis de escenarios y sensibilidad | Automatización de código, análisis de sensibilidad, exploración de escenarios |
| 6. Interpretación y decisión | Interpretar los resultados y apoyar decisiones ambientales | Visualización inteligente, resúmenes de resultados, recomendaciones |

**Aporte global de la IA:** ahorra tiempo (procesa grandes volúmenes de datos), mejora la precisión (predicciones y estimación de parámetros), facilita explorar múltiples escenarios alternativos y apoya las decisiones de gestión ambiental.

---

## 2. Procesos de transporte y transformación

- **Transporte:** movimiento de los contaminantes en el ambiente por **procesos físicos**. Responde a la pregunta **¿dónde estará el contaminante?**
- **Transformación:** cambios **químicos, biológicos o radiactivos** que alteran la composición del contaminante. Responde a **¿cuánto contaminante permanecerá?**

### Mecanismos (infografía, diap. 10)

| Transporte | Descripción | Transformación | Descripción |
|---|---|---|---|
| **Advección** | Transporte por el flujo del medio (agua, aire) | **Degradación química** | Transformación por reacciones químicas abióticas |
| **Difusión** | Movimiento de zonas de alta a baja concentración | **Biodegradación** | Degradación por microorganismos |
| **Dispersión** | Esparcimiento por mezcla mecánica del medio | **Fotodegradación** | Degradación inducida por la luz solar |
| **Sedimentación** | Depósito de partículas por gravedad | **Adsorción/desorción** | Unión a superficies y posterior liberación |
| **Volatilización** | Paso del líquido o sólido a la fase gaseosa | **Reacciones químicas** | Cambio de la forma química del contaminante |

Lista de la diap. 8 (transporte): **advección, difusión, dispersión, sedimentación y erosión, volatilización, intercepción y depósito**.

**Transporte + transformación = evolución del contaminante:**

$$\frac{\partial C}{\partial t} = \underbrace{D\frac{\partial^2 C}{\partial x^2}}_{\text{difusión}} - \underbrace{v\frac{\partial C}{\partial x}}_{\text{advección}} - \underbrace{kC}_{\text{degradación (transformación)}}$$

$C$: concentración (mg/L); $t$: tiempo (s); $x$: distancia (m); $D$: coeficiente de difusión o dispersión (m²/s); $v$: velocidad del río (m/s); $k$: coeficiente de degradación (1/s).

**IA aplicada al modelo:** estimar parámetros ($D$, $v$, $k$) a partir de datos ambientales; generar código automáticamente (Python, MATLAB, R); simular escenarios y hacer análisis de sensibilidad; detectar patrones y apoyar la toma de decisiones.

**Clave:** el modelo ambiental combina **transporte (dónde se mueve)** y **transformación (cómo cambia)** para predecir la concentración en el tiempo y en el espacio.

---

## 3. Advección

Es el **transporte de una sustancia por el movimiento del propio fluido**. A diferencia de la difusión, que depende de gradientes de concentración, la advección la impulsa el flujo y **puede llevar sustancias a grandes distancias con rapidez**. Es crítica en ríos, atmósfera y océanos.

### Caso de estudio (diap. 11–13): derrame accidental en un río

Una planta química ubicada aguas arriba de una zona agrícola y de una captación sufre la falla de una línea y vierte un **contaminante orgánico soluble**. Justo aguas abajo se mide **60 mg/L**. El contaminante se mueve por **advección y dispersión** y a la vez se **degrada** química y biológicamente. La zona agrícola está a 5 km (riego) y la captación a 10 km.

| Parámetro | Símbolo | Valor | Unidad |
|---|---|---|---|
| Concentración inicial | $C_0$ | 60 | mg/L |
| Velocidad media del río | $v$ | 1.2 | m/s |
| Coeficiente de dispersión longitudinal | $D$ | 15 | m²/s |
| Coeficiente de degradación | $k$ | 0.00015 | s⁻¹ |
| Zonas de evaluación | $x_1, x_2, x_3, x_4$ | 1, 2, 5 (agrícola), 10 (captación) | km |

**Pregunta:** ¿cuál será la concentración a 1, 2, 5 y 10 km y cómo puede usarse la IA en la simulación?

**Solución del docente (infografía, estado estacionario):**

1. Modelo: $\dfrac{\partial C}{\partial t} = D\dfrac{\partial^2 C}{\partial x^2} - v\dfrac{\partial C}{\partial x} - kC$
2. Estado estacionario ($\partial C/\partial t = 0$): $D\dfrac{d^2C}{dx^2} - v\dfrac{dC}{dx} - kC = 0$
3. Solución general: $C(x) = C_0 e^{rx}$, con $r = \dfrac{v - \sqrt{v^2 + 4Dk}}{2D}$
4. Cálculo de $r$: $(1.2)^2 = 1.44$; $4(15)(0.00015) = 0.009$; $\sqrt{1.449} = 1.20374$
   $r = \dfrac{1.20 - 1.20374}{30} = \dfrac{-0.00374}{30} \approx -0.0001248\ \text{m}^{-1}$
5. Función: $C(x) = 60\,e^{-0.0001248x}$ ($x$ en metros)

| Distancia (km) | Distancia (m) | C (mg/L) | Reducción respecto a $C_0$ |
|---|---|---|---|
| 0 | 0 | 60.00 | 0 % |
| 1 | 1 000 | 52.96 | 11.7 % |
| 2 | 2 000 | 46.75 | 22.1 % |
| 5 | 5 000 | 32.15 | 46.4 % |
| 10 | 10 000 | 17.22 | 71.3 % |

**Interpretación:**
- La concentración baja por la combinación de **transporte (advección + dispersión) y degradación**.
- A 5 km (zona agrícola) la concentración estimada es **32.15 mg/L**; a 10 km (captación), **17.22 mg/L**.
- Hay que **comparar con los estándares de calidad ambiental** para evaluar el riesgo real.

**¿Dónde interviene la IA?** Puede generar el código que resuelve el modelo, graficar, hacer análisis de sensibilidad y explorar escenarios (variando $v$, $D$ y $k$). Pero **el ingeniero define el problema, valida los resultados y toma las decisiones.**

*Prompt sugerido:* "Actúa como asistente de modelación ambiental... genera un código en Python para evaluar la concentración según el modelo de advección–dispersión–degradación con C₀ = 60 mg/L, v = 1.2 m/s, D = 15 m²/s, k = 0.00015 s⁻¹. Calcula C(x) entre 0 y 10 km y grafica."

---

## 4. Difusión y leyes de Fick

La **difusión** es el movimiento de partículas **desde una región de alta concentración hacia una de baja concentración**, en busca del equilibrio. Se describe con las **leyes de Fick**.

### Primera ley de Fick
El flujo de masa por unidad de área es **proporcional al gradiente de concentración**:

$$J = -D\frac{\Delta C}{\Delta x}$$

$J$: flujo de difusión (mol/m²·s); $D$: coeficiente de difusión (m²/s); $\Delta C/\Delta x$: gradiente de concentración (mol/m⁴).

### Segunda ley de Fick
Tal como la escribe la diapositiva:

$$\frac{\partial C}{\partial t} = -D\frac{\partial C}{\partial x}$$

con $\partial C/\partial t$ la tasa de cambio temporal (mol/m³·s), $D$ (m²/s) y la **segunda derivada espacial** de la concentración (mol/m⁵).

> ⚠️ La forma correcta es $\dfrac{\partial C}{\partial t} = D\dfrac{\partial^2 C}{\partial x^2}$ (segunda derivada y signo positivo). La diapositiva la dice en palabras ("segunda derivada"), pero la ecuación sale con primera derivada.

### Caso 1 (diap. 17–19): membrana semipermeable en una PTAR
- $C_1 = 0.30$ mol/m³ (agua residual); $C_2 = 0$ mol/m³ (agua tratada)
- Espesor: $L = 1$ mm $= 0.001$ m; $D = 2\times10^{-10}$ m²/s

$$J = -2\times10^{-10}\,\frac{(0 - 0.30)}{0.001} = 6\times10^{-8}\ \text{mol/m}^2\cdot\text{s}$$

### Caso 2 (diap. 20): fuga de amoniaco (NH₃) en una sala
- $C$ en el punto de fuga: 0.10 mol/m³; en el exterior ≈ 0
- Distancia: 1000 cm = 10 m; $D_{NH_3,\,aire} = 2.5\times10^{-5}$ m²/s
- Se pide el flujo de difusión. Resultado: $J = -2.5\times10^{-5}\cdot(0-0.10)/10 = 2.5\times10^{-7}$ mol/m²·s. *(El docente no dio la solución; está calculada en el notebook.)*

### Caso 3 (diap. 21–26): "segunda ley de Fick" en una placa de acero
- Placa de 1 m, con $C$ inicial de 5 mol/m³ en toda su extensión.
- Luego se mide $C = 3$ mol/m³ a 0.2 m y $C = 2$ mol/m³ a 0.8 m; $D = 8\times10^{-10}$ m²/s.
- Se pide cómo cambia la concentración con el tiempo y la posición.

Solución del docente:
- **Paso 1 (gradiente):** $\dfrac{\partial C}{\partial x} = \dfrac{3 - 2}{0.8 - 0.2} = 1.6$ mol/m⁴
- **Paso 2 (aplicar la ley):** $\dfrac{\partial C}{\partial t} = -D\,\dfrac{\partial C}{\partial x} = -(8\times10^{-10})(1.6)$
- **Resultado:** $\dfrac{\partial C}{\partial t} = 1.28\times10^{-9}$ mol/m²·s

> ⚠️ (a) $1/0.6 = 1.667$, no 1.6. (b) $D\cdot\partial C/\partial x$ tiene unidades de **flujo** (1.ª ley de Fick), no de $\partial C/\partial t$. (c) El signo cambia sin justificación. Con los datos correctos: $|J| = 8\times10^{-10}\times1.667 = 1.33\times10^{-9}$ mol/m²·s. El notebook permite reportar las dos versiones.

---

## 5. Procesos transformativos (infografía, diap. 27)

Los procesos transformativos modifican la **concentración, composición química, movilidad o disponibilidad** de un contaminante por interacciones físicas, químicas y biológicas con el medio:
**contaminante inicial → proceso de transformación → producto, otra fase o menor concentración.**

| Proceso | Descripción | Parámetro |
|---|---|---|
| Degradación química | Reacciones químicas (hidrólisis, oxidación, reducción, etc.) | $k_q$ |
| Degradación biológica | Microorganismos transforman o mineralizan el contaminante | $k_b$ |
| Fotodegradación | La radiación solar provoca o acelera la transformación | $k_f$ |
| Volatilización | El contaminante pasa del agua o el suelo a la atmósfera | $k_v$ |
| Adsorción/desorción | Se retiene en superficies o vuelve a la fase móvil | $K_d$ |

**¿Cómo se representa en un modelo?** Con cinética de primer orden: $\dfrac{dC}{dt} = -kC \;\Rightarrow\; C(t) = C_0e^{-kt}$ ($C_0$: concentración inicial, mg/L; $k$: 1/tiempo; $t$ en s, min, h o días).

**¿Dónde interviene la IA?** Datos experimentales (C vs tiempo) → estimación de $k$ (ajuste) → ajuste del modelo → predicción de $C(t)$ → comparación de escenarios. Sirve para estimar parámetros, ajustar modelos a datos reales, predecir el comportamiento y evaluar escenarios de gestión.

**Pregunta detonadora:** *Un contaminante baja de 50 a 10 mg/L en un río. ¿Podemos afirmar que se degradó?* → **No necesariamente.** La disminución puede deberse a **degradación + volatilización + adsorción + dispersión + dilución**.

---

## 6. Modelación de la degradación química (infografía, diap. 28)

La degradación química es la transformación **abiótica** de un contaminante mediante reacciones químicas que modifican su estructura, concentración, persistencia y movilidad.
**Contaminante $C_0$ → reacción química (abiótica) → productos de transformación ($C < C_0$ o compuestos nuevos).**

| Mecanismo | Qué es | Factores |
|---|---|---|
| **Hidrólisis** | Reacción del contaminante con el agua | pH, temperatura, estructura química |
| **Oxidación** | Pérdida de electrones por agentes oxidantes | O₂, potencial redox, oxidantes |
| **Reducción** | Ganancia de electrones en ciertas condiciones | Eh, donadores de electrones disponibles |
| **Fotólisis** | Transformación inducida directamente por la radiación | Intensidad lumínica, profundidad, turbidez |

**¿Qué controla $k$?** pH, temperatura, radiación, Eh y composición del medio. **Mayor $k$ → menor persistencia.**

**Modelo:** $\dfrac{dC}{dt} = -kC$; integrando, $C(t) = C_0e^{-kt}$. **Vida media** (tiempo para que $C = C_0/2$): $t_{1/2} = \dfrac{\ln 2}{k}$.
Interpretación: mayor $k$ → degradación más rápida; menor $k$ → más lenta. $k$ determina la persistencia.

**Ejemplo rápido:** $C_0 = 10$ mg/L, $k = 0.05$ día⁻¹ → $C(10) = 10e^{-0.05(10)} = 6.07$ mg/L; $t_{1/2} = 0.693/0.05 = 13.86$ días.

**IA:** datos experimentales (t, C) → IA y ajuste numérico (regresión u optimización) → estimación de $k$ → simulación $C(t) = C_0e^{-kt}$ → predicción y comparación de escenarios.
*Pregunta clave:* si tenemos concentraciones medidas durante 10 días pero no conocemos $k$, ¿puede la IA ayudarnos a estimarlo? → Sí, por ajuste o regresión de $\ln C$ vs $t$.

### Caso: pesticida (diap. 29–30)
$k = 0.1$ día⁻¹, $C_0 = 5$ mg/L. ¿Concentración a los 3 días?

$$C(3) = 5\,e^{-0.1\times3} = 3.7\ \text{mg/L}$$

### Caso: contaminante orgánico en un lago (diap. 31)
$C_0 = 10$ mg/L, $k_c = 0.05$ día⁻¹. ¿Concentración a los 10, 15 y 20 días? **Graficar el comportamiento durante 1 año.**
(Resultados: 6.07, 4.72 y 3.68 mg/L; están calculados y graficados en el notebook.)

---

## 7. Degradación biológica

Proceso natural en el que **microorganismos** (bacterias, hongos, algas) descomponen los contaminantes. Puede lograr la **mineralización completa** (CO₂, H₂O e inorgánicos simples) o transformar el contaminante en **metabolitos menos tóxicos o más biodegradables**.

### Infografía (diap. 33)
**Contaminante + microorganismos + condiciones ambientales (O₂ o condiciones redox, nutrientes, pH, temperatura, humedad) → biodegradación → productos + biomasa.** La velocidad depende de la concentración del contaminante, de las condiciones ambientales y de la actividad microbiana.

**Mecanismos:**
1. **Aeróbica (con O₂):** el O₂ es el aceptor final de electrones. Contaminante + O₂ → CO₂ + H₂O + biomasa. Se aplica a hidrocarburos y compuestos orgánicos biodegradables.
2. **Anaeróbica (sin O₂):** usa otros aceptores (NO₃⁻, SO₄²⁻, CO₂). Puede generar CH₄ + CO₂ y otros productos.
3. **Cometabolismo:** el microorganismo usa otro compuesto como fuente principal de energía, pero también transforma el contaminante (sustrato principal → crecimiento microbiano → transformación del contaminante).
4. **Biorremediación:** aplicación tecnológica para limpiar suelos, sedimentos y aguas. **In situ:** en el lugar contaminado. **Ex situ:** se extrae el material y se trata afuera.

**¿Cómo lo modelamos?** Primer orden: $\dfrac{dC}{dt} = -k_bC \Rightarrow C(t) = C_0e^{-k_bt}$; $t_{1/2} = \ln 2/k_b$.
Si el **crecimiento microbiano o la disponibilidad de sustrato** controlan el proceso, se usan modelos más complejos, como **Monod**:

$$\mu = \mu_{max}\frac{S}{K_s + S}$$

($\mu$: tasa específica de crecimiento; $S$: sustrato; $K_s$: constante de semisaturación.)

**¿Qué controla $k_b$?** Temperatura, pH, O₂, nutrientes, biomasa y concentración del contaminante. **Mayor $k_b$ → mayor velocidad.**
**La IA puede:** encontrar relaciones complejas entre las variables ambientales y $k_b$, mejorar la precisión de las predicciones y evaluar escenarios. Flujo: datos (t, C, pH, T, OD, nutrientes) → ML, redes neuronales o regresión → variables relevantes → estimación de $k_b$ → calibración → predicción.
*Pregunta detonadora:* si dos ríos tienen la misma concentración inicial pero distinta temperatura y oxígeno, ¿debemos usar el mismo $k_b$? → **No necesariamente**: las condiciones ambientales cambian la actividad microbiana y, con ella, la velocidad de degradación.

### Modelo (diap. 34)
$$\frac{dC}{dt} = -k_B\,C$$
$k_B$ (1/tiempo) depende de los microorganismos degradadores disponibles, los nutrientes y las condiciones ambientales óptimas (temperatura, pH, oxígeno). Además del primer orden, puede haber cinética de **orden cero** o de **Michaelis–Menten** (saturación enzimática).

### Caso (diap. 35)
Contaminante orgánico, degradación aeróbica: $C_0 = 200$ mg/L, $k_B = 0.1$ d⁻¹. ¿Concentración a los 10 días?
→ $C = 200e^{-1} = 73.58$ mg/L.

---

## 8. Cinética de orden cero

- La **velocidad de reacción es constante** e independiente de la concentración.
- Aparece cuando un **reactivo está en exceso** o la reacción está **limitada por un factor externo** (luz solar, superficie de un catalizador).
- Se aplica a la **degradación a alta concentración** y al **metabolismo de fármacos a dosis altas**, con el sistema de eliminación (enzimas hepáticas) **saturado**.

$$\frac{dC}{dt} = K_0 \quad (\text{diapositiva})$$

$K_0$: constante de orden cero (concentración/tiempo, p. ej. mg/L·s).

> ⚠️ Para una degradación, el signo es negativo: $\dfrac{dC}{dt} = -k_0 \Rightarrow C(t) = C_0 - k_0t$, válida mientras $C \ge 0$; $t_{1/2} = C_0/(2k_0)$.

---

## 9. Cinética de Michaelis–Menten

- Describe cómo la velocidad de una **reacción enzimática** depende de la concentración de **sustrato**.
- Supone que la formación del complejo enzima–sustrato es **rápida y reversible**, y que le sigue un paso **más lento** de formación del producto y regeneración de la enzima.
- La velocidad **aumenta con el sustrato hasta alcanzar una velocidad máxima** (saturación).

$$v = \frac{V_{max}[S]}{K_M + [S]}$$

- $v$: velocidad de reacción
- $V_{max}$: velocidad máxima, con la enzima **saturada** de sustrato
- $[S]$: concentración de sustrato
- $K_M$: constante de Michaelis–Menten, la **concentración de sustrato con la que $v = V_{max}/2$**

**Gráfica (diap. 39):** hipérbola que parte del origen, pasa por $V_{max}/2$ cuando $[S] = K_M$ y tiende asintóticamente a $V_{max}$.
Límites: si $[S] \ll K_M$, $v \approx (V_{max}/K_M)[S]$ (**primer orden**); si $[S] \gg K_M$, $v \approx V_{max}$ (**orden cero**).

### Caso 1 (diap. 41): dos enzimas
Una enzima que cataliza X→Y se aisló de dos bacterias. Ambas tienen la **misma $V_{max}$** pero distinto $K_M$: **A = 2.0 mM** y **B = 0.5 mM** (la diapositiva escribe "MM" y "M"). La gráfica muestra las dos cinéticas con [X] = 1 µM. Se pide identificar el $K_M$ de cada curva.
→ La curva que **sube más rápido y se satura antes (roja)** tiene **menor $K_M$** (mayor afinidad): **enzima B, $K_M = 0.5$ mM**. La curva **más lenta (negra)** es la **enzima A, $K_M = 2.0$ mM**.

### Caso 2 (diap. 42–44): pesticida en un lago con tratamiento enzimático
$C_0 = 50$ mg/L; objetivo 5 mg/L; $V_{max} = 10$ mg/L·día; $K_M = 20$ mg/L. ¿Tiempo estimado?

Solución del docente (velocidad inicial usada como velocidad promedio):
$$v = \frac{10\times50}{20+50} = 7.14\ \text{mg/L·día};\qquad \Delta C = 50 - 5 = 45\ \text{mg/L};\qquad T = \frac{45}{7.14} = 6.43\ \text{días}$$

> ⚠️ **Error aritmético:** $45/7.14 = 6.30$ días, no 6.43. Además, la velocidad baja a medida que baja $[S]$, así que usar $v_0$ **subestima** el tiempo. La solución exacta (Michaelis–Menten integrada) es $t = \dfrac{K_M\ln(S_0/S) + (S_0 - S)}{V_{max}} = \dfrac{20\ln10 + 45}{10} = 9.10$ días.

### Caso 3 (diap. 45): fármaco en aguas residuales
$C_0 = 100$ mg/L → objetivo 10 mg/L; $V_{max} = 25$ mg/L·día; $K_M = 50$ mg/L. ¿Cuánto tiempo toma?
→ Método del docente: $v = 25\cdot100/150 = 16.67$ mg/L·d; $T = 90/16.67 = 5.40$ d. Exacto (integrado): $t = (50\ln10 + 90)/25 = 8.21$ d.

---

## 10. Fotodegradación (diap. 46)

Es la descomposición de sustancias químicas **inducida por la luz solar**. Su tasa varía mucho con la sustancia y la intensidad de la luz; en forma simplificada es de **primer orden**:

$$\frac{dC}{dt} = -K_F\,C \;\Rightarrow\; C(t) = C_0e^{-K_Ft}$$
