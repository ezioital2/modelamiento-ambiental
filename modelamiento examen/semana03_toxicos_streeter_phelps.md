# Semana 03 — Sustancias tóxicas en corrientes de agua: Streeter–Phelps

> Fuente: *MODELACIÓN AMBIENTAL semana 03.pptx* (13 diapositivas). Título: *Modelación del comportamiento de sustancias tóxicas en corrientes de agua.*

---

## 1. Introducción

- Modelar sustancias tóxicas en corrientes de agua es un proceso **complejo**: exige entender y cuantificar múltiples factores y procesos **físicos, químicos y biológicos**.
- **Finalidad:** predecir la **dispersión, concentración y transformación** de los contaminantes a lo largo del **tiempo y el espacio** en sistemas acuáticos.

## 2. Enfoque general para la modelación (7 pasos)

1. Identificar las sustancias tóxicas y las fuentes de contaminación.
2. Caracterizar el sistema acuático.
3. Modelar los procesos de **transporte**.
4. Modelar los procesos de **transformación**.
5. Desarrollar y **calibrar** el modelo.
6. Simular y analizar los resultados.
7. **Validar** y ajustar.

---

## 3. Modelo de Streeter–Phelps (OD y DBO)

Es uno de los modelos más usados para simular la **disminución del oxígeno disuelto (OD)** en un cuerpo de agua, causada por la **descomposición de la materia orgánica** (consumo) y compensada por la **reaireación** desde la atmósfera (aporte).

### Curva de oxígeno o "curva de sag" (diap. 5)
En el punto de descarga de efluentes ($t_0$), el OD cae de $C_r$ (río) a $C_0$ (mezcla). Sigue bajando hasta un **mínimo, el OD crítico $C_c$**, en el **tiempo o distancia crítica $t_c$**, y luego **se recupera** hacia la saturación $C_s$.
- $D_0 = C_s - C_0$: déficit inicial
- $D_c = C_s - C_c$: déficit crítico (máximo)
- Eje x: tiempo (d) o distancia (km), con $x = v\,t$

### Ecuaciones tal como están en las diapositivas

**DBO remanente:**
$$L(t) = L_0\,e^{-k_1 t}$$

**OD (versión del docente):**
$$D(t) = D_s - (D_s - D_0)\,e^{-k_2 t} - L_0\left(1 - e^{-k_1 t}\right)$$

| Símbolo | Significado |
|---|---|
| $L(t)$ | DBO remanente en el tiempo $t$ |
| $L_0$ | DBO inicial |
| $k_1$ | tasa de degradación de la DBO (desoxigenación) |
| $t$ | tiempo |
| $D(t)$ | **concentración** de OD en el tiempo $t$ (en esta versión D no es el déficit) |
| $D_s$ | OD de saturación |
| $D_0$ | OD inicial |
| $k_2$ | tasa de reaireación |

> ⚠️ **Esta forma no es la ecuación clásica de Streeter–Phelps.** Resta toda la DBO ejercida sin descontar la reaireación, así que el OD puede salir negativo. La forma clásica, con el **déficit** $D = OD_s - OD$, es:
> $$D(t) = \frac{k_1L_0}{k_2 - k_1}\left(e^{-k_1t} - e^{-k_2t}\right) + D_0e^{-k_2t},\qquad OD(t) = OD_s - D(t)$$
> $$t_c = \frac{1}{k_2 - k_1}\ln\left[\frac{k_2}{k_1}\left(1 - \frac{D_0(k_2 - k_1)}{k_1L_0}\right)\right]$$
> En el examen conviene plantear la ecuación del docente y, si su resultado no tiene sentido físico, resolver también con la clásica. El notebook calcula ambas.

### Pasos para la simulación (diap. 7–8)
- **Paso 1:** determinar los parámetros iniciales: $L_0$, $D_0$, $D_s$ y las tasas $k_1$ y $k_2$, que dependen de las condiciones ambientales y del cuerpo de agua.
- **Paso 2:** con las ecuaciones de Streeter–Phelps, calcular $L(t)$ y $D(t)$ en varios tiempos para ver cómo cambian la DBO y el OD.
- **Paso 3:** evaluar si el OD cumple los **estándares de calidad** para la vida acuática y cómo lo afecta la descomposición de la materia orgánica en el tiempo.

---

## 4. Caso de estudio 1 (diap. 9–11)

Analizar la recuperación del OD en un tramo afectado por una descarga de aguas residuales y el **tiempo para volver a niveles seguros**.

| Dato | Valor |
|---|---|
| OD inicial en la descarga | 4 mg/L |
| OD de saturación (nivel deseado) | 9 mg/L |
| DBO inicial del efluente $L_0$ | 30 mg/L |
| Tasa de descomposición de la DBO $k_1$ | 0.25 día⁻¹ |
| Tasa de reaireación $k_2$ | 0.4 día⁻¹ |

**Pregunta:** determinar la ecuación y el tiempo que tarda el río en recuperar **OD = 6 mg/L** aguas abajo.

**Solución del docente:**
- DBO: $L(t) = 30\,e^{-0.25t}$
- OD: $6 = 9 - (9 - 4)\,e^{-0.4t} - 30\left(1 - e^{-0.25t}\right)$
- Reordenado en la diapositiva: $5e^{-0.4t} + 30e^{-0.25t} = 33$ → **T = 10**

> ⚠️ **Verificación:** al despejar bien sale $30e^{-0.25t} - 5e^{-0.4t} = 27$, no "= 33". Con $t = 10$ ninguna de las dos igualdades se cumple ($5e^{-4} + 30e^{-2.5} = 2.55$). Con esa ecuación el OD parte de 4 y **baja siempre** ($dOD/dt(0) = 5\cdot0.4 - 30\cdot0.25 < 0$), así que nunca llega a 6.
> Con **Streeter–Phelps clásico** ($D_0 = 5$ mg/L) el OD cae a un mínimo teórico negativo hacia $t \approx 2.4$ d (en la realidad llega a **0 mg/L: anoxia**) y se recupera a **6 mg/L en $t \approx 10.4$ días**. Eso coincide con el **T ≈ 10 días** del docente, así que la respuesta esperada es ≈ 10 días y la forma correcta de justificarla es el modelo clásico.

## 5. Caso de estudio 2 (diap. 12)

Río contaminado por aguas residuales sin tratar, con OD bajo y DBO alta. Determinar el tiempo para que el OD se recupere a un nivel aceptable.

| Dato | Valor |
|---|---|
| OD de saturación $D_s$ | 10 mg/L |
| OD inicial en la descarga $D_0$ | 2 mg/L |
| DBO inicial del efluente $L_0$ | 25 mg/L |
| $k_1$ | 0.3 día⁻¹ |
| $k_2$ | 0.5 día⁻¹ |
| OD aceptable | 6 mg/L |

**Pregunta:** definir la ecuación y el tiempo para alcanzar OD = 6 mg/L aguas abajo.
- Ecuación del docente: $6 = 10 - (10 - 2)e^{-0.5t} - 25(1 - e^{-0.3t})$
- Con la ecuación del docente el OD baja siempre y nunca llega a 6 mg/L (el mismo problema del caso 1).
- **Streeter–Phelps clásico** ($D_0 = 8$ mg/L): OD mínimo ≈ 0 mg/L hacia $t \approx 1.35$ d; **recupera 6 mg/L en $t \approx 6.7$ días**.
- Funciones del notebook: `sp_docente`, `sp_clasico`, `tiempo_OD_objetivo`.
