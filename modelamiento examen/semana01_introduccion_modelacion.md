# Semana 01 — Introducción a la modelación de contaminantes

> Fuente: *MODELACIÓN AMBIENTAL semana 01.pptx* (22 diapositivas). Docente: Mg. Robert Joaquin Medina Ramos (UCSM).
> Transcripción limpia del contenido de las diapositivas, incluidas las que eran solo imagen.

---

## 1. ¿Qué es la modelación ambiental?

La modelación ambiental es el **uso de técnicas matemáticas y computacionales para simular y entender cómo responden los sistemas naturales** a variaciones en sus condiciones iniciales y a las intervenciones humanas.

- Ayuda a los ingenieros ambientales a **tomar decisiones**, porque permite explorar los efectos potenciales de acciones humanas y fenómenos naturales sobre el ambiente.
- Representa los **procesos físicos, químicos y biológicos** de la **atmósfera, hidrosfera, geosfera y biosfera**.
- Sirve para **predecir cambios ambientales**, **evaluar riesgos** y **formular estrategias de gestión sostenible**.
- Es un campo **interdisciplinario**.

### Diagrama de la modelación ambiental (diap. 3)

```
(1) Entrada de datos → (2) Modelo matemático → (3) Simulación computacional → (4) Análisis de resultados → (5) Decisiones y estrategias
```

---

## 2. Buenas prácticas (Wainwright y Mulligan)

1. **Desarrollo detallado** de los modelos.
2. **Validación y calibración con datos reales.**
3. **Incorporar la perspectiva de los interesados** (stakeholders) en el desarrollo.
4. **Mantener y actualizar** los modelos de forma continua, para reflejar cambios en los datos y en el ambiente.

→ Así se obtienen modelos más **precisos y confiables** para la gestión ambiental.

---

## 3. Tipos de modelos

| Tipo | Idea central | Se basa en | Ejemplo del curso |
|---|---|---|---|
| **Conceptual** | Representación simplificada: componentes clave y relaciones, **sin matemática detallada** | Conocimiento del sistema | Cuenca con minería ilegal (ciclo hidrológico) |
| **Empírico** | Relación **estadística** entre variables observadas | **Datos históricos** | Caudal del río Chili vs precipitación (regresión lineal) |
| **Basado en procesos (mecanicista)** | **Ecuaciones** de los mecanismos físicos, químicos o biológicos | Leyes físicas (balance de masa, Fick, cinética) | Advección–dispersión aguas abajo de una fuente puntual |
| **Integrado** | **Combina** conceptual + empírico + procesos, con datos de varias disciplinas | Varios submodelos | Prácticas agrícolas → nitratos en una cuenca |

### 3.1 Modelos conceptuales

Son representaciones simplificadas de sistemas o procesos reales. Identifican y destacan las **relaciones fundamentales y los componentes clave**, sin detallar la complejidad matemática ni computacional. Su propósito es dar una **comprensión básica** de cómo funciona el sistema y facilitar la **comunicación** entre científicos, gestores e interesados.

**Importancia**
1. **Facilitan la comunicación:** explican las ideas básicas a públicos amplios, incluidos no especialistas.
2. **Son el punto de partida de modelos más complejos:** estructuran el problema al inicio.
3. **Identifican las variables clave y sus relaciones:** enfocan la planificación y la toma de decisiones.
4. **Son versátiles:** sirven desde la gestión de cuencas hasta la conservación de la biodiversidad.

**Caso de estudio (diap. 9–10).** En una cuenca hay contaminación por minería ilegal. ¿Qué aspectos fundamentales debe contener el modelo conceptual?
- **Precipitación:** aporta agua a la cuenca y puede traer contaminantes desde la atmósfera.
- **Escurrimiento superficial:** el agua fluye sobre el terreno y arrastra contaminantes del suelo y de áreas urbanas.
- **Infiltración:** parte del agua entra al suelo, donde puede filtrarse o llevar contaminantes a las aguas subterráneas.
- **Evaporación y transpiración:** el agua regresa a la atmósfera y cierra el ciclo.
- (Diagrama) Además: fuente de contaminación (minera o planta), agua superficial, agua subterránea, viento y transporte de la contaminación, evapotranspiración.

### 3.2 Modelos empíricos

Se basan en la **observación y el análisis de datos** para establecer relaciones estadísticas entre variables.
- Son útiles cuando **se conoce poco del mecanismo** o cuando se prefiere un enfoque simple de predicción.
- A diferencia de los modelos de procesos, **dependen directamente de datos históricos** para prever el comportamiento futuro.

**Caso de estudio (diap. 12–14): caudal del río Chili a partir de la precipitación**
- Datos: precipitación diaria (mm) y caudal (m³/s) durante **10 años**.
- Objetivo: predecir el caudal de un día conociendo las precipitaciones de los días anteriores.
- Método:
  1. Recopilar los datos de precipitación y caudal diarios.
  2. Establecer una relación empírica; por simplicidad, **lineal**:
     $$\text{Caudal} = a \cdot \text{precipitación} + b$$
  3. Estimar $a$ y $b$ por **regresión lineal** (mínimos cuadrados) con los datos históricos.
  4. Con los parámetros estimados, predecir el caudal para un nuevo valor de precipitación.

### 3.3 Modelos basados en procesos (mecanicistas)

Simulan los **procesos físicos, químicos o biológicos subyacentes**. A diferencia de los empíricos, representan **cómo funciona internamente** el sistema mediante ecuaciones de sus mecanismos fundamentales.

**Importancia**
1. **Comprensión profunda** de los mecanismos internos.
2. **Predicción en condiciones nuevas**, no observadas antes, porque no dependen solo de datos históricos.
3. **Análisis de sensibilidad y de escenarios**, variando los parámetros de forma sistemática.
4. **Diseño de estrategias de mitigación y adaptación.**

**Caso de estudio (diap. 17–18): contaminante aguas abajo de una fuente puntual**
- Velocidad del río: **2 m/s**.
- Emisión puntual: **100 g/s**.
- Coeficiente de dispersión: **0.01 m²/s**. El contaminante **no se degrada** ($\gamma = 0$).
- Se pide estimar la concentración a diferentes distancias aguas abajo.

Modelo de advección–dispersión tal como aparece en la diapositiva:

$$C(x) = \frac{Q}{\mu\sqrt{4\pi D x}}\exp\left(-\frac{(x-\mu t)^2}{4Dx} - \gamma t\right)$$

- $Q$: tasa de emisión del contaminante
- $\mu$: velocidad del río
- $D$: coeficiente de dispersión
- $\gamma$: coeficiente de degradación

> ⚠️ Ver [FORMULARIO.md](FORMULARIO.md) §3.4: esta forma mezcla $x$ y $t$. La solución clásica usa $t$ dentro de la raíz y el área de la sección. En el examen conviene aplicar la fórmula del docente y mencionar la forma estándar.

### 3.4 Modelos integrados

Combinan elementos de **distintos tipos de modelos** e integran **datos de varias disciplinas**, para comprender de forma más completa sistemas complejos con interacciones **bióticas, abióticas y antrópicas**.

**Importancia**
1. **Visión holística:** capturan las interacciones entre componentes.
2. **Interdisciplinariedad:** integran ciencias naturales, sociales y económicas.
3. **Toma de decisiones informada:** gestión ambiental, políticas públicas, planificación territorial.
4. **Evaluación de escenarios:** cambio climático, uso del suelo, políticas de gestión.

**Caso de estudio (diap. 21–22): recurso hídrico en una cuenca**
- Objetivo: evaluar el impacto de distintas prácticas agrícolas en la calidad del agua (**nitratos**).
- Sistema: cuenca con usos agrícola, urbano y forestal.
- Componentes del modelo integrado:
  1. **Modelo de uso del suelo:** predice cambios de uso bajo distintas políticas agrícolas.
  2. **Modelo hidrológico:** simula el ciclo del agua y el transporte de nitratos.
  3. **Modelo de calidad del agua:** estima nitratos en aguas superficiales y subterráneas.
  4. **Modelo económico:** evalúa la rentabilidad y sostenibilidad de las prácticas.
