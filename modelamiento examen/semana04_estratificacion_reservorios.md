# Semana 04 — Métodos para evaluar la estratificación de reservorios

> Fuente: *MODELACIÓN AMBIENTAL semana 04.pptx* (13 diapositivas).

---

## 1. Introducción

La **estratificación** es un fenómeno físico en el que las capas de agua de un **lago, embalse o estanque** tienen **densidades distintas**, normalmente por diferencias de **temperatura** y de **composición**. Tiene implicaciones importantes en la **calidad del agua**, la **vida acuática** y la **gestión de recursos hídricos**.

**Métodos para evaluar la estratificación:**
1. Medición de temperatura y densidad
2. Análisis de oxígeno disuelto (OD)
3. Muestreo de nutrientes y clorofila
4. Modelos matemáticos y de simulación
5. Imágenes satelitales y teledetección
6. Sondas multiparamétricas

**Capas térmicas de un reservorio estratificado:**
- **Epilimnion:** capa superficial, cálida, mezclada y oxigenada.
- **Metalimnion (termoclina):** capa intermedia donde la temperatura cambia rápido con la profundidad.
- **Hipolimnion:** capa profunda, fría y densa. Puede quedarse **sin oxígeno (anoxia)** porque no se mezcla con la superficie.

---

## 2. Medición de temperatura y densidad

- **Perfilado térmico:** termistores o sondas miden la temperatura a distintas profundidades e identifican las capas (**epilimnion, metalimnion, hipolimnion**).
- **Medición de densidad:** con densímetros o perfiles **CTD** (conductividad, temperatura, profundidad) se mide directamente la densidad y se identifican las capas.

## 3. Análisis de oxígeno disuelto

- **Perfiles de OD:** la estratificación afecta la circulación y la mezcla, así que los perfiles de OD la delatan: **OD alto en la superficie y bajo en las capas profundas**.

## 4. Muestreo de nutrientes y clorofila

- **Nutrientes:** nitratos, fosfatos y otros nutrientes medidos a distintas profundidades pueden **acumularse en ciertas capas**, lo que indica **poca mezcla**.
- **Clorofila:** su perfil muestra la **biomasa fitoplanctónica** y su distribución, que dependen de la luz y los nutrientes, ambos influidos por la estratificación.
- **Teledetección:** las imágenes satelitales dan la **temperatura superficial** y la **turbidez**, que indican estratificación y circulación interna en cuerpos de agua grandes.

## 5. Sondas multiparamétricas

- **Monitoreo avanzado:** miden a la vez **temperatura, conductividad (salinidad), pH, OD** y otros parámetros a diferentes profundidades.

---

## 6. Método comparativo

Compara **perfiles fisicoquímicos** (temperatura, OD, conductividad) en **distintos momentos y lugares** del reservorio, para ver cambios y tendencias de la estratificación en el tiempo y bajo distintas condiciones.
1. **Recopilación de datos:** temperatura y OD a varias profundidades y en distintas estaciones del año (variabilidad estacional).
2. **Análisis comparativo:** se comparan los datos para identificar patrones de estratificación.
3. **Evaluación de la dinámica:** la comparación en el tiempo permite evaluar la **mezcla** y la **estabilidad de las capas**, clave para la calidad del agua y los recursos pesqueros.

## 7. Método de Arai (gradiente crítico)

(La diapositiva repite al inicio la definición del método comparativo; lo propio del método de Arai es lo siguiente.)
1. **Medición de gradientes térmicos:** con termistores o sondas CTD se obtienen perfiles de temperatura y se calcula el **gradiente térmico vertical** $\Delta T/\Delta z$.
2. **Cálculo del gradiente crítico:** a partir del gradiente térmico se calcula el **gradiente crítico de temperatura** necesario para que la estratificación resista los procesos de mezcla.
3. **Análisis de estabilidad:** se compara el gradiente observado con el crítico.
   - **Gradiente observado > gradiente crítico → estratificación ESTABLE.**
   - **Gradiente observado < gradiente crítico → susceptible a MEZCLA.**

## 8. Cálculo del gradiente crítico: número de Richardson

El gradiente crítico se obtiene con el **número de Richardson**, que compara la **flotación** (estabilidad) con el **cizallamiento** (mezcla). En cuerpos de agua con estratificación térmica se escribe en términos de gradientes:

$$Ri = \frac{g}{\rho}\cdot\frac{\Delta\rho/\Delta z}{\rho\,(\Delta u/\Delta z)^2} \quad (\text{forma de la diapositiva})$$

- $Ri$: número de Richardson (flotación / cizallamiento)
- $g$: gravedad ≈ 9.81 m/s²
- $\rho$: densidad media del agua
- $\Delta\rho/\Delta z$: gradiente de densidad con la profundidad; se relaciona con el gradiente de temperatura mediante ecuaciones de estado (agua dulce o salada)
- $\Delta u/\Delta z$: gradiente de velocidad con la profundidad; en una primera aproximación **suele asumirse pequeño o se ignora**

> ⚠️ La forma dimensionalmente correcta, y la habitual, es $Ri = \dfrac{(g/\rho)\,(\Delta\rho/\Delta z)}{(\Delta u/\Delta z)^2} = \dfrac{N^2}{(\Delta u/\Delta z)^2}$. La $\rho$ extra del denominador de la diapositiva sobra. $N^2$ es la frecuencia de flotación (Brunt–Väisälä).
> **Criterio usual (no aparece en la diapositiva):** $Ri > 0.25$ → flujo estable, la estratificación resiste la mezcla; $Ri < 0.25$ → posible mezcla turbulenta. Si $\Delta u/\Delta z \to 0$, $Ri \to \infty$ (muy estable).

---

## 9. Caso de estudio: Embalse Alfa (diap. 12–13)

El **Embalse Alfa** es una fuente importante de agua potable y recreación en clima templado. En verano presenta una **marcada estratificación térmica**, con posibles impactos en la calidad del agua, como **anoxia en el hipolimnion**. La gestión necesita evaluar con precisión la **estabilidad de la estratificación** para prevenir eventos adversos y planificar la mitigación.

**Objetivo:** usar el **gradiente crítico** para evaluar la estabilidad de la estratificación en verano y ver si hay **riesgo de mezcla** que deteriore la calidad del agua.

**Datos iniciales:**
- Perfiles de julio: **ΔT = 10 °C** entre la **superficie (25 °C)** y el **fondo (15 °C)**, a **20 m** de profundidad.
- Caudal de entrada y salida estable, con mínima variación estacional.
- Las actividades recreativas son superficiales y no afectan la estratificación.

**Resolución (en el notebook):**
1. Gradiente térmico: $\Delta T/\Delta z = 10/20 = 0.5$ °C/m.
2. Densidades (ecuación de estado del agua dulce): $\rho(25\,°C) \approx 997.0$ kg/m³; $\rho(15\,°C) \approx 999.1$ kg/m³ → $\Delta\rho/\Delta z \approx 0.10$ kg/m⁴.
3. $N^2 = (g/\rho)(\Delta\rho/\Delta z) \approx 1.0\times10^{-3}$ s⁻².
4. Cizallamiento crítico para $Ri = 0.25$: $(\Delta u/\Delta z)_c = \sqrt{N^2/0.25} \approx 0.063$ s⁻¹ → una diferencia de velocidad de ≈ 1.3 m/s en los 20 m.
5. **Interpretación:** en un embalse con caudal estable las velocidades son muy bajas, así que $Ri \gg 0.25$: la estratificación es **estable**. La mezcla no es probable (salvo viento fuerte o enfriamiento en otoño), y **persiste el riesgo de anoxia en el hipolimnion**. Medidas posibles: aireación o desestratificación, monitorear el OD en el fondo y elegir la profundidad de captación.
