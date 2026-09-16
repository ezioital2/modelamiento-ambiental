# FORMULARIO — Modelación Ambiental (semanas 1–4)

> Todas las fórmulas del curso con variables, unidades y cuándo usarlas.
> **[D]** = forma que usa el docente en las diapositivas; **[C]** = forma correcta o clásica cuando son distintas.
> Cada fórmula tiene su función en `examen.ipynb` (nombre entre corchetes).

---

## 0. Conversión de unidades (errores más frecuentes)

| De | A | Factor |
|---|---|---|
| km | m | × 1000 |
| cm | m | ÷ 100 |
| mm | m | ÷ 1000 |
| día | s | × 86 400 |
| h | s | × 3600 |
| k (s⁻¹) | k (día⁻¹) | × 86 400 |
| mg/L | g/m³ | = (idénticos) |
| mg/L | kg/m³ | ÷ 1000 |
| mol/m³ | mol/L | ÷ 1000 |
| mM | M | ÷ 1000;  1 µM = 10⁻³ mM = 10⁻⁶ M |
| m³/s | L/s | × 1000 |
| g/s | g/día | × 86 400 |

**Regla:** antes de sustituir, poner **k, t, x, v y D en el mismo sistema** (todo en s y m, o todo en días y m). Revisar que el exponente de $e^{-kt}$ o $e^{rx}$ sea **adimensional**.

---

## 1. Modelo empírico (S1)

**Regresión lineal simple** [`regresion_lineal`]
$$y = a\,x + b,\qquad a = \frac{n\sum xy - \sum x\sum y}{n\sum x^2 - (\sum x)^2},\qquad b = \bar y - a\bar x$$
$$R^2 = 1 - \frac{\sum(y - \hat y)^2}{\sum(y - \bar y)^2}$$
Ejemplo: Caudal = a · precipitación + b (río Chili).

**Métricas de ajuste** [`metricas`]: $RMSE = \sqrt{\frac{1}{n}\sum(y_{obs} - y_{pred})^2}$, $MAE = \frac{1}{n}\sum|y_{obs} - y_{pred}|$, $NSE = 1 - \frac{\sum(y_{obs} - y_{pred})^2}{\sum(y_{obs} - \bar y_{obs})^2}$.

**Estimar k con datos C vs t** (lo que "hace la IA") [`estimar_k`]: $\ln C = \ln C_0 - k\,t$ → regresión lineal de $\ln C$ contra $t$: pendiente $= -k$ e intercepto $= \ln C_0$.

---

## 2. Balance y mezcla (útil en ríos y descargas)

**Mezcla completa en el punto de descarga** [`mezcla`]
$$C_{mezcla} = \frac{Q_r C_r + Q_e C_e}{Q_r + Q_e}$$
Vale para concentraciones de contaminante, OD, DBO ($L_0$) y temperatura.

**Carga másica:** $W = Q\cdot C$ (m³/s × g/m³ = g/s).
**Tiempo de viaje:** $t = x/v$.

---

## 3. Transporte

### 3.1 Advección pura [`adveccion_posicion`]
$$\frac{\partial C}{\partial t} + v\frac{\partial C}{\partial x} = 0 \;\Rightarrow\; x = x_0 + v\,t,\qquad t = x/v$$
La nube se traslada sin cambiar de forma.

### 3.2 Difusión: 1.ª ley de Fick [`fick1`]
$$J = -D\,\frac{\Delta C}{\Delta x} = -D\,\frac{C_2 - C_1}{x_2 - x_1}$$
$J$ en mol/m²·s (o g/m²·s); $D$ en m²/s; $\Delta C$ en mol/m³; $\Delta x$ en m. El **signo negativo** indica que el flujo va de mayor a menor concentración.
Masa transferida: $N = J\cdot A\cdot t$.

### 3.3 Difusión: 2.ª ley de Fick [`fick2_docente`, `fick2_pulso`, `fick2_frontera`]
- **[D]** $\dfrac{\partial C}{\partial t} = -D\dfrac{\partial C}{\partial x}$ (en la placa de acero se calculó $D\cdot$gradiente)
- **[C]** $\dfrac{\partial C}{\partial t} = D\dfrac{\partial^2 C}{\partial x^2}$

Soluciones de la forma [C]:
- Pulso instantáneo de masa $M$ (por área) en $x = 0$: $C(x,t) = \dfrac{M}{\sqrt{4\pi Dt}}\exp\left(-\dfrac{x^2}{4Dt}\right)$
- Frontera de concentración constante $C_s$ (medio semi-infinito con $C_i$ inicial): $\dfrac{C - C_i}{C_s - C_i} = \operatorname{erfc}\left(\dfrac{x}{2\sqrt{Dt}}\right)$
- Distancia característica de difusión: $\sigma = \sqrt{2Dt}$; tiempo para recorrer $L$: $t \approx L^2/(2D)$
- Segunda derivada numérica con 3 puntos equiespaciados: $\dfrac{\partial^2C}{\partial x^2} \approx \dfrac{C_{i+1} - 2C_i + C_{i-1}}{\Delta x^2}$

### 3.4 Advección–dispersión (fuente puntual, S1) [`ad_docente`, `ad_pulso`]
- **[D]** $C(x) = \dfrac{Q}{\mu\sqrt{4\pi Dx}}\exp\left(-\dfrac{(x - \mu t)^2}{4Dx} - \gamma t\right)$
  ($Q$: emisión g/s; $\mu$: velocidad m/s; $D$: m²/s; $\gamma$: degradación 1/s). Si se evalúa en $t = x/\mu$ (centro de la nube), el término cuadrático se anula.
- **[C] Pulso instantáneo** de masa $M$ (g) en un río de área $A$ (m²):
  $$C(x,t) = \frac{M}{A\sqrt{4\pi Dt}}\exp\left(-\frac{(x - vt)^2}{4Dt} - kt\right)$$
  Pico en $x = vt$: $C_{max} = \dfrac{M}{A\sqrt{4\pi Dt}}e^{-kt}$; ancho de la nube $\sigma = \sqrt{2Dt}$.
- **[C] Descarga continua** (estado estacionario, mezcla completa): $C_0 = W/Q_{río}$ y luego la ecuación de §3.5.

### 3.5 Advección–dispersión–degradación, estado estacionario (S2) [`add_estacionario`]
$$D\frac{d^2C}{dx^2} - v\frac{dC}{dx} - kC = 0 \;\Rightarrow\; C(x) = C_0\,e^{rx},\qquad r = \frac{v - \sqrt{v^2 + 4Dk}}{2D}\;(<0)$$
- Sin dispersión ($D \to 0$): $r = -k/v$ → $C = C_0e^{-kx/v}$ (flujo pistón: advección + decaimiento)
- Número de Péclet: $Pe = \dfrac{vL}{D}$ (Pe ≫ 1 domina la advección; Pe ≪ 1 domina la dispersión)
- Reducción porcentual: $100\,(1 - C/C_0)$

### 3.6 Ecuación general (transporte + transformación) [`add_numerico`]
$$\frac{\partial C}{\partial t} = D\frac{\partial^2C}{\partial x^2} - v\frac{\partial C}{\partial x} - kC$$
difusión/dispersión − advección − degradación. Se resuelve numéricamente (diferencias finitas) si hay pulsos o condiciones variables.

---

## 4. Transformación

### 4.1 Primer orden (química, biológica, fotodegradación, volatilización) [`primer_orden`, `t_medio`, `tiempo_para`]
$$\frac{dC}{dt} = -kC \;\Rightarrow\; C(t) = C_0e^{-kt}$$
$$t_{1/2} = \frac{\ln 2}{k} = \frac{0.693}{k},\qquad k = \frac{\ln(C_0/C)}{t},\qquad t = \frac{\ln(C_0/C)}{k}$$
- Fracción remanente: $C/C_0 = e^{-kt}$; tras $n$ vidas medias, $C = C_0/2^n$
- Tiempo para remover el 90 %: $t_{90} = \ln 10/k = 2.303/k$; 99 %: $4.605/k$
- Varias vías en paralelo: $k_{total} = k_q + k_b + k_f + k_v + \dots$ (las constantes **se suman**)
- Símbolos del curso: $k_q$ (química), $k_b$ o $K_B$ (biológica), $k_f$ o $K_F$ (fotodegradación), $k_v$ (volatilización), $K_d$ (adsorción, coeficiente de partición)
- Corrección por temperatura (Arrhenius, **no está en las diapositivas**): $k_T = k_{20}\,\theta^{T-20}$ ($\theta \approx 1.047$ para DBO)

### 4.2 Orden cero [`orden_cero`]
- **[D]** $\dfrac{dC}{dt} = K_0$
- **[C]** $\dfrac{dC}{dt} = -k_0 \Rightarrow C(t) = C_0 - k_0t$ (mientras $C \ge 0$)
- $t_{1/2} = \dfrac{C_0}{2k_0}$; tiempo para llegar a $C$: $t = \dfrac{C_0 - C}{k_0}$; $k_0$ en mg/L·tiempo⁻¹

### 4.3 Michaelis–Menten [`mm_velocidad`, `mm_tiempo_docente`, `mm_tiempo_exacto`]
$$v = \frac{V_{max}[S]}{K_M + [S]}$$
- $[S] = K_M \Rightarrow v = V_{max}/2$ (definición de $K_M$). **Menor $K_M$ → mayor afinidad** (se satura antes).
- $[S] \ll K_M$: $v \approx (V_{max}/K_M)[S]$ (primer orden, $k = V_{max}/K_M$); $[S] \gg K_M$: $v \approx V_{max}$ (orden cero)
- Fracción de saturación: $v/V_{max} = [S]/(K_M + [S])$
- **Tiempo [D]** (velocidad inicial usada como promedio): $T = \dfrac{S_0 - S}{v(S_0)}$
- **Tiempo [C]** (integrada): $t = \dfrac{K_M\ln(S_0/S) + (S_0 - S)}{V_{max}}$
- Linealización de Lineweaver–Burk (para estimar parámetros): $\dfrac{1}{v} = \dfrac{K_M}{V_{max}}\dfrac{1}{[S]} + \dfrac{1}{V_{max}}$

### 4.4 Monod (crecimiento microbiano) [`monod`]
$$\mu = \mu_{max}\frac{S}{K_s + S}$$

---

## 5. Oxígeno disuelto: Streeter–Phelps (S3) [`sp_docente`, `sp_clasico`, `tiempo_OD_objetivo`, `od_saturacion`]

**DBO remanente:** $L(t) = L_0e^{-k_1t}$; DBO ejercida: $y(t) = L_0(1 - e^{-k_1t})$

**[D] OD del docente**
$$OD(t) = D_s - (D_s - D_0)e^{-k_2t} - L_0(1 - e^{-k_1t})$$
($D_s$ = OD de saturación, $D_0$ = OD inicial; aquí "D" es concentración, no déficit)

**[C] Streeter–Phelps clásico** (déficit $D = OD_s - OD$, $D_0 = OD_s - OD_0$):
$$D(t) = \frac{k_1L_0}{k_2 - k_1}\left(e^{-k_1t} - e^{-k_2t}\right) + D_0e^{-k_2t},\qquad OD(t) = OD_s - D(t)$$
$$t_c = \frac{1}{k_2 - k_1}\ln\left[\frac{k_2}{k_1}\left(1 - \frac{D_0(k_2 - k_1)}{k_1L_0}\right)\right],\qquad D_c = \frac{k_1}{k_2}L_0e^{-k_1t_c}$$
- Si $k_1 = k_2 = k$: $D(t) = (k\,L_0\,t + D_0)e^{-kt}$
- Distancia crítica: $x_c = v\,t_c$
- Factor de autopurificación: $f = k_2/k_1$ (mayor $f$ → mejor recuperación)
- Si el argumento del logaritmo es ≤ 1, $t_c = 0$: el mínimo está en la descarga
- Mezcla inicial: $L_0 = \dfrac{Q_rL_r + Q_eL_e}{Q_r + Q_e}$, $OD_0 = \dfrac{Q_rOD_r + Q_eOD_e}{Q_r + Q_e}$
- **Reaireación k₂** (no en las diapositivas): O'Connor–Dobbins $k_2 = 3.93\,v^{0.5}/H^{1.5}$ (día⁻¹, v en m/s, H en m); Churchill $k_2 = 5.026\,v/H^{1.67}$
- **OD de saturación** (no en las diapositivas): $OD_s = 14.652 - 0.41022T + 0.007991T^2 - 0.000077774T^3$, corregida por altitud con $\times(1 - 2.25577\times10^{-5}z)^{5.25588}$

---

## 6. Estratificación de reservorios (S4) [`densidad_agua`, `richardson`, `gradiente_termico`, `evaluar_estratificacion`]

**Gradiente térmico:** $\dfrac{\Delta T}{\Delta z} = \dfrac{T_{sup} - T_{fondo}}{z}$ (°C/m)

**Densidad del agua dulce** (ecuación de estado, $T$ en °C, **no está en las diapositivas**):
$$\rho(T) = 1000\left[1 - \frac{(T + 288.9414)(T - 3.9863)^2}{508929.2\,(T + 68.12963)}\right]\ \text{kg/m}^3$$
(máxima densidad a 4 °C ≈ 1000 kg/m³; 15 °C ≈ 999.1; 25 °C ≈ 997.0)

**Número de Richardson**
- **[D]** $Ri = \dfrac{g}{\rho}\cdot\dfrac{\Delta\rho/\Delta z}{\rho(\Delta u/\Delta z)^2}$
- **[C]** $Ri = \dfrac{(g/\rho)(\Delta\rho/\Delta z)}{(\Delta u/\Delta z)^2} = \dfrac{N^2}{(\Delta u/\Delta z)^2}$, con $N^2 = \dfrac{g}{\rho}\dfrac{\Delta\rho}{\Delta z}$ (s⁻²)
- **Criterio:** $Ri > 0.25$ → estable (resiste la mezcla); $Ri < 0.25$ → mezcla turbulenta posible
- **Cizallamiento crítico** ($Ri = 0.25$): $(\Delta u/\Delta z)_c = \sqrt{N^2/0.25} = 2N$
- **Gradiente crítico de densidad** para un cizallamiento dado: $(\Delta\rho/\Delta z)_c = Ri_c\,\dfrac{\rho}{g}(\Delta u/\Delta z)^2$, que se convierte a gradiente térmico con $d\rho/dT$
- **Método de Arai:** gradiente observado > crítico → **estable**; < crítico → **susceptible a mezcla**
- Criterio práctico de termoclina (bibliografía general): $\Delta T/\Delta z \ge 1$ °C/m
- **Número de Schmidt de estabilidad** (opcional): $S = \dfrac{g}{A_s}\int (z - z_v)(\rho_z - \rho_{mix})A_z\,dz$

---

## 7. Resumen: ¿qué fórmula uso?

| Si la pregunta menciona... | Usa |
|---|---|
| "relación entre variables", "datos históricos", "predecir a partir de registros" | Regresión (§1) |
| "flujo a través de membrana, pared o capa", "gradiente", "tasa de difusión" | Fick 1 (§3.2) |
| "cómo cambia con el tiempo y la posición por difusión" | Fick 2 (§3.3) |
| "derrame", "aguas abajo", "velocidad del río", "coeficiente de dispersión", "a X km" | ADD estacionario (§3.5) o pulso (§3.4) |
| "cinética de primer orden", "k en día⁻¹", "vida media" | Primer orden (§4.1) |
| "velocidad constante", "saturado", "k₀ en mg/L·t" | Orden cero (§4.2) |
| "enzima", "Vmax", "KM", "sustrato" | Michaelis–Menten (§4.3) |
| "crecimiento microbiano", "μmax", "Ks" | Monod (§4.4) |
| "OD", "DBO", "reaireación", "recuperación del río", "punto crítico" | Streeter–Phelps (§5) |
| "embalse", "termoclina", "estratificación", "gradiente crítico", "Richardson" | Estratificación (§6) |
| "¿dónde interviene la IA?" | Ver GUIA_INTERPRETACION.md §6 |
