# GUÍA DE INTERPRETACIÓN — para responder preguntas teóricas y explicar resultados

> Complementa [FORMULARIO.md](FORMULARIO.md). Recoge el **significado físico** de cada resultado, las respuestas modelo a preguntas conceptuales y la estructura recomendada de cada respuesta.

---

## 1. Estructura recomendada para responder un problema

1. **Datos:** tabla con símbolo, valor y unidad. **Convertir unidades** (km→m, días↔s).
2. **Modelo conceptual:** qué procesos actúan (fuente → transporte → transformación → receptor).
3. **Modelo matemático:** escribir la ecuación general y la simplificación usada (estado estacionario, primer orden, etc.).
4. **Sustitución y cálculo**, con pasos intermedios (como en las diapositivas del docente).
5. **Resultados:** tabla y gráfica.
6. **Interpretación:** comparar con un estándar o umbral, decir qué proceso domina y qué significa para la gestión.
7. **Rol de la IA:** qué hace la IA y qué sigue siendo responsabilidad del ingeniero.

---

## 2. Tipos de modelos: diferencias clave (pregunta clásica)

| Criterio | Conceptual | Empírico | Basado en procesos | Integrado |
|---|---|---|---|---|
| Base | Conocimiento cualitativo | Datos observados (estadística) | Leyes físicas, químicas y biológicas | Combinación de los anteriores + otras disciplinas |
| Matemática | Ninguna o mínima | Regresiones y ajustes | Ecuaciones diferenciales | Varios submodelos acoplados |
| Explica el mecanismo | Sí (cualitativamente) | **No** | **Sí** | Sí |
| Predice en condiciones nuevas | No | **Mal** (solo dentro del rango de los datos) | **Sí** | Sí |
| Datos que requiere | Pocos | **Muchos** (históricos) | Parámetros y datos de calibración | Muchos y variados |
| Ventaja | Comunicación, punto de partida | Simple, rápido | Comprensión profunda, escenarios, sensibilidad | Visión holística, decisiones |
| Limitación | No cuantifica | No extrapola; correlación ≠ causa | Complejo, necesita muchos parámetros | Muy complejo, se propagan incertidumbres |

**Frase modelo:** *"El modelo empírico relaciona variables a partir de datos históricos sin describir los mecanismos; el basado en procesos resuelve ecuaciones de los fenómenos físicos, químicos y biológicos, por lo que puede predecir en condiciones no observadas; el conceptual es la representación cualitativa previa a ambos; y el integrado combina los tres con información de varias disciplinas para la toma de decisiones."*

**Secuencia del proceso de modelación:** datos → modelo conceptual → modelo matemático → simulación computacional → análisis de resultados → decisiones (y calibración, validación y actualización continua).

**Buenas prácticas (Wainwright y Mulligan):** desarrollo detallado, calibración y validación con datos reales, participación de los interesados, actualización continua.

---

## 3. Transporte

| Proceso | Qué hace a la "nube" de contaminante | Motor | Parámetro |
|---|---|---|---|
| **Advección** | La **traslada** sin cambiar su forma | Movimiento del fluido (velocidad) | $v$ (m/s) |
| **Difusión molecular** | La **ensancha** muy lentamente | Gradiente de concentración (movimiento molecular) | $D_m \approx 10^{-9}$ m²/s en agua; $\approx 10^{-5}$ m²/s en aire |
| **Dispersión** | La **ensancha** mucho más rápido | Mezcla mecánica o turbulenta y variaciones de velocidad | $D_L$: 1–1000 m²/s en ríos |
| **Sedimentación** | Pasa la fracción particulada al fondo | Gravedad | velocidad de sedimentación $v_s$ |
| **Volatilización** | Pasa del agua o suelo al aire | Presión de vapor, constante de Henry | $k_v$ |

- Advección vs difusión: la **advección depende del flujo**, la **difusión del gradiente**. La advección lleva el contaminante lejos y rápido; la difusión actúa a escala pequeña.
- **Signo menos en Fick:** el flujo va **en contra del gradiente** (de mayor a menor concentración).
- **$D$ grande** → la pluma se esparce más, el pico baja y la nube se alarga.
- **Péclet** $Pe = vL/D$: $Pe \gg 1$ → domina la advección (flujo pistón); $Pe \ll 1$ → domina la dispersión (mezcla completa).
- En un río, **$D$ casi no afecta el decaimiento estacionario** comparado con $k/v$: en el caso del derrame $r \approx -k/v = -0.000125$ m⁻¹.

---

## 4. Transformación

### 4.1 Interpretación de k y de la vida media
- **Mayor $k$ → degradación más rápida → menor persistencia** (menor $t_{1/2}$).
- $t_{1/2} = 0.693/k$: tiempo en que la concentración baja a la mitad; no depende de $C_0$ (solo en primer orden).
- A 1 $t_{1/2}$ queda 50 %; a 2, 25 %; a 3, 12.5 %; a 3.32, 10 %; a 6.64, 1 %.
- **$k$ depende de:** pH, temperatura, radiación, Eh (redox), composición del medio; en la biodegradación también de O₂, nutrientes, biomasa y concentración del contaminante.

### 4.2 Comparación de cinéticas

| | Orden cero | Primer orden | Michaelis–Menten |
|---|---|---|---|
| Velocidad | Constante ($k_0$) | Proporcional a C ($kC$) | Crece con [S] y se satura en $V_{max}$ |
| Perfil C vs t | **Recta** | **Exponencial** | Recta a C alta y exponencial a C baja |
| $t_{1/2}$ | Depende de $C_0$ ($C_0/2k_0$) | **Constante** ($\ln2/k$) | Variable |
| Cuándo aplica | Reactivo en exceso, sistema **saturado**, limitado por luz o catalizador | Concentraciones bajas o moderadas, la mayoría de procesos ambientales | **Enzimas** o biodegradación con saturación |
| Unidades de k | mg/L·t⁻¹ | t⁻¹ | $V_{max}$: mg/L·t⁻¹; $K_M$: mg/L |

- **Michaelis–Menten reúne los dos:** a $[S] \gg K_M$ es de orden cero y a $[S] \ll K_M$ es de primer orden ($k = V_{max}/K_M$).
- **$K_M$ bajo = alta afinidad:** la enzima trabaja a velocidad casi máxima incluso con poco sustrato.
- **Método del docente vs exacto en MM:** usar $v(S_0)$ como promedio **subestima el tiempo**, porque la velocidad baja al bajar [S]. La integración exacta da un tiempo mayor.

### 4.3 Degradación química vs biológica vs fotodegradación
- **Química:** abiótica (hidrólisis, oxidación, reducción, fotólisis). Factores: pH, T, O₂, Eh, luz.
- **Biológica:** mediada por microorganismos. Puede ser **aeróbica** (O₂ como aceptor → CO₂ + H₂O + biomasa), **anaeróbica** (NO₃⁻, SO₄²⁻, CO₂ como aceptores → CH₄ + CO₂), **cometabolismo** (se transforma sin ser la fuente de energía) o **biorremediación** (in situ o ex situ). Puede llegar a la **mineralización** o a **metabolitos**.
- **Fotodegradación:** inducida por la luz solar. Depende de la intensidad lumínica, la **profundidad** y la **turbidez**. Es de primer orden.

### 4.4 Preguntas detonadoras del docente
- **"Un contaminante baja de 50 a 10 mg/L en un río. ¿Se degradó?"** → **No necesariamente.** La baja puede deberse a **dilución, dispersión, volatilización o adsorción** (procesos que no destruyen el contaminante), además de la degradación. Para atribuirla a degradación hay que cerrar un **balance de masa** (caudales y cargas) o medir productos de transformación.
- **"Dos ríos con igual C₀ pero distinta T y O₂: ¿mismo $k_b$?"** → **No necesariamente**: la temperatura y el oxígeno cambian la actividad microbiana y, por tanto, $k_b$.
- **"Tenemos C medida 10 días pero no conocemos k: ¿puede la IA estimarlo?"** → **Sí**: ajuste o regresión de $\ln C$ vs $t$ (pendiente $= -k$), u optimización no lineal. Con más variables (T, pH, OD), modelos de ML relacionan $k$ con las condiciones.

---

## 5. Streeter–Phelps: lectura de la curva

- **Dos procesos opuestos:** **desoxigenación** ($k_1$, las bacterias consumen O₂ al degradar la DBO) y **reaireación** ($k_2$, entra O₂ desde la atmósfera).
- **Curva de sag:** al inicio domina el consumo y el OD baja; en el **punto crítico** ($t_c$, $x_c = vt_c$) consumo = reaireación y el OD es **mínimo**; después domina la reaireación y el OD se **recupera** hacia la saturación.
- **$k_2/k_1$ (autopurificación):** mayor → recuperación más rápida y déficit crítico menor. Los ríos rápidos y poco profundos tienen $k_2$ alto.
- **Si el OD mínimo sale < 0:** físicamente se llega a **0 mg/L (anoxia)**, con mortandad de peces, olores y condiciones anaerobias. El modelo pierde validez en esa zona.
- **Umbrales típicos:** OD ≥ 5–6 mg/L para vida acuática (peces); < 2 mg/L hipoxia; 0 anoxia. ECA Perú (agua categoría 4, conservación del ambiente acuático): OD ≥ 5 mg/L en ríos.
- **Factores:** temperatura (↑T → ↓OD de saturación y ↑$k_1$), **altitud** (↓presión → ↓OD de saturación; en Arequipa ≈ 75 % del valor a nivel del mar), velocidad y profundidad (determinan $k_2$), carga orgánica ($L_0$).
- **Medidas de gestión:** tratar el efluente (↓$L_0$), aireación, diluir con mayor caudal, trasladar o desplazar la descarga.
- **Sobre la versión del docente:** si con su ecuación el OD nunca alcanza el objetivo, explicar que la forma clásica (déficit) sí da la recuperación. El caso 1 del docente (T = 10 d) coincide con la clásica (≈ 10.4 d).

---

## 6. Inteligencia artificial en la modelación ambiental

**Idea central del curso:** *la IA apoya todo el ciclo de modelación, pero la definición del problema y del modelo conceptual, la validación y las decisiones son responsabilidad del ingeniero ambiental.*

| Etapa | Rol de la IA |
|---|---|
| Datos | Limpieza, detección de anomalías, integración de fuentes (sensores, imágenes, históricos) |
| Identificación | Reconocimiento de patrones, selección de variables importantes |
| Modelo conceptual | Sugerir procesos relevantes y estructuras de modelo |
| Modelo matemático | Asistir la formulación, **estimar parámetros ($k$, $D$, $v$)**, revisar unidades |
| Simulación | **Generar código** (Python, MATLAB, R), análisis de sensibilidad, exploración de escenarios |
| Interpretación | Visualización, resúmenes, recomendaciones |

- **Aportes:** ahorra tiempo, mejora la precisión, facilita explorar escenarios y apoya decisiones.
- **Limitaciones y riesgos:** depende de la calidad de los datos; puede extrapolar mal; "caja negra"; puede cometer errores de unidades o de fórmula (como los detectados en las diapositivas). **Siempre hay que validar.**
- **Enfoque híbrido (modelo integrado):** modelo de procesos + ML que corrige el residuo, $C = C_{procesos} + g_{ML}(X)$.

---

## 7. Estratificación: lectura de resultados

- **Causa:** diferencias de densidad por **temperatura** (principal), salinidad o sólidos disueltos. El agua es más densa a **4 °C**.
- **Capas:** **epilimnion** (cálido, mezclado, con OD y fotosíntesis), **metalimnion/termoclina** (gradiente térmico fuerte que funciona como barrera), **hipolimnion** (frío y denso; no se reoxigena y **puede volverse anóxico**; acumula nutrientes, Fe, Mn, H₂S).
- **Consecuencias:** anoxia en el fondo, liberación de fósforo, hierro y manganeso desde los sedimentos, mala calidad para agua potable si se capta en profundidad, floraciones de algas en superficie, mortandad de peces si hay volteo súbito.
- **Mezcla o volteo (turnover):** en otoño o invierno la superficie se enfría, las densidades se igualan y la columna se mezcla (puede subir agua anóxica).
- **Richardson:** $Ri > 0.25$ estable (la flotación vence al cizallamiento); $Ri < 0.25$ mezcla (el cizallamiento vence). **Mayor gradiente de densidad o menor cizallamiento → más estable.**
- **Arai:** gradiente observado > crítico → estable; < crítico → susceptible a mezcla.
- **Métodos de evaluación:** perfiles de T y densidad (termistores, CTD), perfiles de OD (alto arriba y bajo abajo = estratificado), nutrientes y clorofila por profundidad, teledetección (temperatura superficial y turbidez), sondas multiparamétricas, **método comparativo** (perfiles en distintas fechas o estaciones) y modelos matemáticos.
- **Gestión:** aireación o desestratificación artificial, oxigenación del hipolimnion, captación selectiva por profundidad, control de nutrientes en la cuenca, monitoreo continuo.

---

## 8. Clasificación de contaminantes (respuesta rápida)

- **Físicos:** temperatura (contaminación térmica), turbidez, ruido, radiación electromagnética.
- **Químicos:** fertilizantes, pesticidas, solventes, residuos industriales, productos de limpieza; **metales pesados (Hg, Pb) bioacumulables**.
- **Biológicos:** patógenos de aguas residuales; floraciones de algas nocivas por **eutrofización**.
- **Radiactivos:** persistentes y carcinogénicos. Fuente puntual: accidentes nucleares; dispersa: minería y procesamiento de minerales.
- **Fuentes:** **puntual** (descarga identificable: tubería, PTAR, derrame) vs **no puntual o difusa** (escorrentía agrícola o urbana, deposición atmosférica).

---

## 9. Errores detectados en las diapositivas (para no arrastrarlos)

| Semana | Diapositiva | Error | Correcto |
|---|---|---|---|
| S1 | 18 | $\sqrt{4\pi Dx}$ y $4Dx$ con $x$; sin área | $\sqrt{4\pi Dt}$, $4Dt$; $M/A$ |
| S2 | 16, 24 | 2.ª ley de Fick con 1.ª derivada y signo − | $\partial C/\partial t = D\,\partial^2C/\partial x^2$ |
| S2 | 23 | $(3-2)/(0.8-0.2) = 1.6$ | $= 1.667$ mol/m⁴ |
| S2 | 25 | Resultado con signo + y unidades de flujo como $\partial C/\partial t$ | Es $J$ (1.ª ley): $1.33\times10^{-9}$ mol/m²·s |
| S2 | 37 | $dC/dt = K_0$ | $dC/dt = -k_0$ para una degradación |
| S2 | 44 | $T = 45/7.14 = 6.43$ d (usa la velocidad inicial) | $45/7.14 = 6.30$ d; integrada: 9.10 d |
| S3 | 6, 10 | OD docente no es Streeter–Phelps clásico | Ecuación del déficit (FORMULARIO §5) |
| S3 | 11 | $5e^{-0.4t} + 30e^{-0.25t} = 33$; T = 10 | $30e^{-0.25t} - 5e^{-0.4t} = 27$ (sin solución); clásico: 10.4 d |
| S4 | 10–11 | $\rho$ extra en el denominador de Ri | $Ri = (g/\rho)(\Delta\rho/\Delta z)/(\Delta u/\Delta z)^2$ |
| S4 | 9 | Método de Arai repite la definición del comparativo | Arai = gradiente observado vs crítico |
