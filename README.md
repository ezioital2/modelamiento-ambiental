# Modelamiento Ambiental

Prácticas y apuntes del curso **Modelamiento Ambiental**.

## Contenido

| Archivo | Descripción |
|---|---|
| [`Practica_2.ipynb`](Practica_2.ipynb) | **Práctica N.° 2 — Modelamiento del transporte y transformación de contaminantes.** Notebook completo: advección, difusión molecular, estimación del coeficiente de dispersión, transformación de primer orden, modelo integrado advección–dispersión–transformación y análisis de sensibilidad. Incluye fundamento teórico, desarrollo matemático, código, tablas y gráficos. |
| [`resultados/`](resultados/) | Tablas de resultados en CSV y [`RESUMEN_RESULTADOS.md`](resultados/RESUMEN_RESULTADOS.md) con todos los valores numéricos consolidados. |
| [`figuras/`](figuras/) | Las 12 figuras generadas por el notebook (PNG, 200 dpi). |
| `introducción1.md`, `clase2.md` | Apuntes de clase: modelamiento conceptual, matemático y numérico. |
| `ejercicio 1.5.ipynb` | Cálculo suelto del ejercicio de advección. |

## Ecuación de referencia

La práctica 2 gira en torno al modelo integrado de transporte y transformación:

```
∂C/∂t + u ∂C/∂x = Dx ∂²C/∂x² − kC
```

- **Advección** (`u`) → desplaza la nube: `x = u·t`
- **Dispersión** (`Dx`) → la ensancha: `σx = √(2·Dx·t)`
- **Transformación** (`k`) → reduce la masa: `e^(−k·t)`

## Ejecución

```bash
pip install numpy pandas matplotlib jupyter
jupyter notebook Practica_2.ipynb   # Kernel → Restart & Run All
```

Al ejecutarse regenera `figuras/`, `resultados/` y el resumen consolidado.

## Integrantes

Gonzales Barrios Diego Benny · González Quiroz Yanira Lucero · Llachi Vargas Claudia Milagros · Palomino Gonzales Bianca Abigail · Rodriguez Chavez Jason Edward
