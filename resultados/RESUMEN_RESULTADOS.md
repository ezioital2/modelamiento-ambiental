# RESUMEN DE RESULTADOS — Práctica N.° 2
## Modelamiento del transporte y transformación de contaminantes

Generado automáticamente por `Practica_2.ipynb`. Contiene todas las tablas de resultados,
los valores numéricos clave y el índice de figuras de las Actividades 1 a 10.

---

## 1. Valores numéricos clave

| Clave | Valor | Unidad | Descripción |
|---|---|---|---|
| `A1_x_30min` | 450 | m | Distancia recorrida en 30 min con u=0.25 m/s |
| `A1_x_2h` | 1,800 | m | Distancia recorrida en 2 h con u=0.25 m/s |
| `A1_t_5km_s` | 20,000 | s | Tiempo para recorrer 5 km |
| `A1_t_5km_h` | 5.5556 | h | Tiempo para recorrer 5 km |
| `A1_C_5km` | 10 | mg/L | Concentración tras 5 km (advección pura) |
| `A2_sigma_1h` | 2.6833 | mm | sigma_x a 1 h (D=1e-9) |
| `A2_Cmax_1h` | 1.4868e+05 | mg/m | C_max a 1 h (D=1e-9) |
| `A2_sigma_6h` | 6.5727 | mm | sigma_x a 6 h (D=1e-9) |
| `A2_Cmax_6h` | 60,697 | mg/m | C_max a 6 h (D=1e-9) |
| `A2_sigma_24h` | 13.145 | mm | sigma_x a 24 h (D=1e-9) |
| `A2_Cmax_24h` | 30,349 | mg/m | C_max a 24 h (D=1e-9) |
| `A2_razon_Dx_D` | 5e+10 | - | Razón Dx/D entre dispersión longitudinal y difusión molecular |
| `A3_Dx_1800` | 44.444 | m²/s | Dx estimado a t=1800 s |
| `A3_Dx_3600` | 50 | m²/s | Dx estimado a t=3600 s |
| `A3_Dx_5400` | 59.259 | m²/s | Dx estimado a t=5400 s |
| `A3_Dx_medio` | 51.235 | m²/s | Dx medio de las tres observaciones |
| `A3_Dx_regresion` | 55.556 | m²/s | Dx por regresión de sigma² vs t forzada al origen |
| `A3_CV_Dx` | 14.608 | % | Coeficiente de variación de Dx |
| `A4_C_0h` | 20 | mg/L | Concentración a t=0 h (C0=20, k=0.05 1/h) |
| `A4_C_1h` | 19.025 | mg/L | Concentración a t=1 h (C0=20, k=0.05 1/h) |
| `A4_C_5h` | 15.576 | mg/L | Concentración a t=5 h (C0=20, k=0.05 1/h) |
| `A4_C_10h` | 12.131 | mg/L | Concentración a t=10 h (C0=20, k=0.05 1/h) |
| `A4_C_24h` | 6.0239 | mg/L | Concentración a t=24 h (C0=20, k=0.05 1/h) |
| `A4_t_medio` | 13.863 | h | Vida media del contaminante (k = 0.05 1/h) |
| `A5_k` | 0.069315 | d⁻¹ | Constante de transformación estimada |
| `A5_t_medio` | 10 | d | Vida media estimada |
| `A5_C_20d` | 5 | mg/L | Concentración esperada a 20 días |
| `A5_C_30d` | 2.5 | mg/L | Concentración esperada a 30 días |
| `A6_C_1km` | 9.4596 | mg/L | Concentración a x=1 km (u=0.9 km/h, k=0.05 1/h) |
| `A6_C_5km` | 7.5747 | mg/L | Concentración a x=5 km (u=0.9 km/h, k=0.05 1/h) |
| `A6_C_10km` | 5.7375 | mg/L | Concentración a x=10 km (u=0.9 km/h, k=0.05 1/h) |
| `A6_u_kmh` | 0.9 | km/h | Velocidad convertida a km/h |
| `A6_Lc` | 18 | km | Longitud característica u/k |
| `A7_Cmax_Dx50` | 0.6649 | mg/m | C_max con Dx=50 m²/s a t=1 h |
| `A7_sigma_Dx50` | 600 | m | sigma_x con Dx=50 m²/s a t=1 h |
| `A7_Cmax_Dx100` | 0.47016 | mg/m | C_max con Dx=100 m²/s a t=1 h |
| `A7_sigma_Dx100` | 848.53 | m | sigma_x con Dx=100 m²/s a t=1 h |
| `A7_Cmax_Dx200` | 0.33245 | mg/m | C_max con Dx=200 m²/s a t=1 h |
| `A7_sigma_Dx200` | 1,200 | m | sigma_x con Dx=200 m²/s a t=1 h |
| `A7_x_centro` | 900 | m | Posición del centro de la nube a t=1 h |
| `A8_Cmax_B` | 0.6649 | mg/m | C_max escenario B |
| `A8_Cmax_C` | 0.63248 | mg/m | C_max escenario C |
| `A8_perdida_pct` | 4.8771 | % | Pérdida relativa de C_max por transformación en 1 h |
| `A8_sigma` | 600 | m | sigma_x escenarios B y C |
| `A8_xmax` | 900 | m | Posición del máximo en los tres escenarios |
| `A9_xmax_u010` | 360 | m | x_max con u=0.10 m/s a t=1 h |
| `A9_xmax_u050` | 1,800 | m | x_max con u=0.50 m/s a t=1 h |

---

## 2. Tablas de resultados

### Tabla 1.1 — Resultados del ejercicio de advección (u = 0.25 m/s)
*Archivo:* `resultados/act1_ejercicio.csv`

| Pregunta | Expresión | Resultado | Unidad |
|---|---|---|---|
| 1. Distancia a los 30 min | x = u·t = 0.25 · 1800 | 450 | m |
| 2. Distancia a las 2 h | x = u·t = 0.25 · 7200 | 1,800 | m |
| 3. Tiempo para 5 km | t = x/u = 5000 / 0.25 | 20,000 | s |
| 3b. Tiempo para 5 km | t / 3600 | 5.5556 | h |
| 4. Concentración a 5 km | C = C0 (advección pura) | 10 | mg/L |

### Tabla 1.2 — Distancia recorrida x = u·t para tres velocidades (0–10 h)
*Archivo:* `resultados/act1_x_vs_t.csv`

| t (h) | x (m) | u=0.10 m/s | x (m) | u=0.25 m/s | x (m) | u=0.50 m/s | x (km) | u=0.25 |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 1 | 360 | 900 | 1,800 | 0.9 |
| 2 | 720 | 1,800 | 3,600 | 1.8 |
| 3 | 1,080 | 2,700 | 5,400 | 2.7 |
| 4 | 1,440 | 3,600 | 7,200 | 3.6 |
| 5 | 1,800 | 4,500 | 9,000 | 4.5 |
| 6 | 2,160 | 5,400 | 10,800 | 5.4 |
| 7 | 2,520 | 6,300 | 12,600 | 6.3 |
| 8 | 2,880 | 7,200 | 14,400 | 7.2 |
| 9 | 3,240 | 8,100 | 16,200 | 8.1 |
| 10 | 3,600 | 9,000 | 18,000 | 9 |

### Tabla 2.1 — Difusión molecular: pico y ensanchamiento de la nube
*Archivo:* `resultados/act2_difusion_resumen.csv`

| Tiempo | t (s) | C_max (mg/m) | sigma_x (m) | sigma_x (mm) | Ancho ±2σ (mm) |
|---|---|---|---|---|---|
| 1 h | 3,600 | 148,677.0097 | 0.0027 | 2.6833 | 10.7331 |
| 6 h | 21,600 | 60,697.135 | 0.0066 | 6.5727 | 26.2907 |
| 24 h | 86,400 | 30,348.5675 | 0.0131 | 13.1453 | 52.5814 |

### Tabla 2.2 — Distribución espacial C(x) a 1 h, 6 h y 24 h
*Archivo:* `resultados/act2_perfil_C.csv`

| x (mm) | C (mg/m) | t=1 h | C (mg/m) | t=6 h | C (mg/m) | t=24 h |
|---|---|---|---|
| 0 | 148,677.0097 | 60,697.135 | 30,348.5675 |
| 1 | 138,702.5606 | 59,998.6717 | 30,260.8803 |
| 2 | 112,617.6502 | 57,951.1377 | 29,999.3359 |
| 3 | 79,581.0686 | 54,692.6774 | 29,568.4422 |
| 5 | 26,197.5297 | 45,446.9016 | 28,230.7372 |
| 8 | 1,746.0076 | 28,938.0043 | 25,218.154 |
| 12 | 6.7499 | 11,464.208 | 20,007.0088 |

### Tabla 2.3 — Efecto de duplicar D a t = 24 h
*Archivo:* `resultados/act2_duplicar_D.csv`

| Caso | D (m²/s) | C_max (mg/m) | sigma_x (mm) | Razón C_max | Razón sigma |
|---|---|---|---|---|---|
| D | 1.000e-09 | 30,348.5675 | 13.1453 | 1 | 1 |
| 2D | 2.000e-09 | 21,459.6779 | 18.5903 | 0.7071 | 1.4142 |

### Tabla 2.4 — Tiempo necesario para alcanzar σ = 100 m según el mecanismo
*Archivo:* `resultados/act2_difusion_vs_dispersion.csv`

| Proceso | Coeficiente (m²/s) | t para σ = 100 m (s) | t (años) |
|---|---|---|---|
| Difusión molecular | 1.000e-09 | 5.000e+12 | 158,440.4391 |
| Dispersión longitudinal | 50 | 100 | 3.169e-06 |

### Tabla 3.1 — Estimación puntual del coeficiente de dispersión longitudinal
*Archivo:* `resultados/act3_estimacion_Dx.csv`

| t (s) | t (min) | sigma_x (m) | sigma_x² (m²) | Dx = σ²/(2t) (m²/s) | Desv. respecto a la media (%) |
|---|---|---|---|---|---|
| 1,800 | 30 | 400 | 160,000 | 44.4444 | -13.253 |
| 3,600 | 60 | 600 | 360,000 | 50 | -2.4096 |
| 5,400 | 90 | 800 | 640,000 | 59.2593 | 15.6627 |

### Tabla 3.2 — Comparación de las estimaciones de Dx (m²/s)
*Archivo:* `resultados/act3_resumen_Dx.csv`

| Indicador | Valor |
|---|---|
| Media de las estimaciones puntuales | 51.2346 |
| Mediana de las estimaciones puntuales | 50 |
| Desviación estándar | 7.4842 |
| Coeficiente de variación (%) | 14.6077 |
| Dx por regresión forzada al origen | 55.5556 |
| Dx por regresión libre (pendiente/2) | 66.6667 |
| Ordenada al origen de la regresión libre (m²) | -93,333.3333 |
| R² de la regresión libre | 0.9908 |
| Rango (mín – máx) de Dx | 14.8148 |

### Tabla 4.1 — Concentración bajo transformación de primer orden
*Archivo:* `resultados/act4_decaimiento.csv`

| t (h) | k·t | e^(-k·t) | C (mg/L) | Remanente (%) | Removido (%) |
|---|---|---|---|---|---|
| 0 | 0 | 1 | 20 | 100 | 0 |
| 1 | 0.05 | 0.9512 | 19.0246 | 95.1229 | 4.8771 |
| 5 | 0.25 | 0.7788 | 15.576 | 77.8801 | 22.1199 |
| 10 | 0.5 | 0.6065 | 12.1306 | 60.6531 | 39.3469 |
| 24 | 1.2 | 0.3012 | 6.0239 | 30.1194 | 69.8806 |

### Tabla 4.2 — Vida media y tiempos característicos (4.4)
*Archivo:* `resultados/act4_vida_media.csv`

| Parámetro | Valor | Unidad |
|---|---|---|
| Constante de transformación k | 0.05 | h⁻¹ |
| Vida media t₁/₂ = ln2 / k | 13.8629 | h |
| Vida media en días | 0.5776 | d |
| Tiempo para 90 % de remoción (ln10/k) | 46.0517 | h |
| Tiempo para 99 % de remoción (ln100/k) | 92.1034 | h |
| Tiempo de vida medio 1/k (tiempo característico) | 20 | h |

### Tabla 5.1 — Estimación de k y proyección de la concentración
*Archivo:* `resultados/act5_estimacion_k.csv`

| Magnitud | Expresión | Resultado | Unidad |
|---|---|---|---|
| Constante de transformación | k = −(1/t)·ln(C/C₀) = −(1/10)·ln(0.5) | 0.0693 | d⁻¹ |
| Vida media | t₁/₂ = ln2 / k | 10 | d |
| Concentración a 20 días | C = 20·e^(−0.06931·20) | 5 | mg/L |
| Concentración a 30 días | C = 20·e^(−0.06931·30) | 2.5 | mg/L |

### Tabla 5.2 — Proyección de la concentración hasta 60 días
*Archivo:* `resultados/act5_proyeccion.csv`

| t (d) | C (mg/L) | C/C₀ | Nº de vidas medias | Remoción (%) |
|---|---|---|---|---|
| 0 | 20 | 1 | 0 | 0 |
| 5 | 14.1421 | 0.7071 | 0.5 | 29.2893 |
| 10 | 10 | 0.5 | 1 | 50 |
| 15 | 7.0711 | 0.3536 | 1.5 | 64.6447 |
| 20 | 5 | 0.25 | 2 | 75 |
| 25 | 3.5355 | 0.1768 | 2.5 | 82.3223 |
| 30 | 2.5 | 0.125 | 3 | 87.5 |
| 35 | 1.7678 | 0.0884 | 3.5 | 91.1612 |
| 40 | 1.25 | 0.0625 | 4 | 93.75 |
| 45 | 0.8839 | 0.0442 | 4.5 | 95.5806 |
| 50 | 0.625 | 0.0313 | 5 | 96.875 |
| 55 | 0.4419 | 0.0221 | 5.5 | 97.7903 |
| 60 | 0.3125 | 0.0156 | 6 | 98.4375 |

### Tabla 6.1 — Concentración con advección y transformación (u = 0,90 km/h; k = 0,05 h⁻¹)
*Archivo:* `resultados/act6_adveccion_transformacion.csv`

| x (km) | t de viaje = x/u (h) | k·x/u | e^(−k·x/u) | C (mg/L) | Remanente (%) | Removido (%) |
|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 1 | 10 | 100 | 0 |
| 1 | 1.1111 | 0.0556 | 0.946 | 9.4596 | 94.5959 | 5.4041 |
| 5 | 5.5556 | 0.2778 | 0.7575 | 7.5747 | 75.7465 | 24.2535 |
| 10 | 11.1111 | 0.5556 | 0.5738 | 5.7375 | 57.3753 | 42.6247 |

### Tabla 6.2 — Efecto de la velocidad sobre C(x) (pregunta 22 y 26)
*Archivo:* `resultados/act6_sensibilidad_u.csv`

| x (km) | C (mg/L) | u=0.10 m/s | C (mg/L) | u=0.25 m/s | C (mg/L) | u=0.50 m/s |
|---|---|---|---|
| 1 | 8.7032 | 9.4596 | 9.726 |
| 5 | 4.9935 | 7.5747 | 8.7032 |
| 10 | 2.4935 | 5.7375 | 7.5747 |

### Tabla 6.3 — Efecto de k sobre C(x) (preguntas 23 y 25)
*Archivo:* `resultados/act6_sensibilidad_k.csv`

| x (km) | C (mg/L) | k=0.00 h⁻¹ | C (mg/L) | k=0.02 h⁻¹ | C (mg/L) | k=0.05 h⁻¹ | C (mg/L) | k=0.10 h⁻¹ |
|---|---|---|---|---|
| 1 | 10 | 9.7802 | 9.4596 | 8.9484 |
| 5 | 10 | 8.9484 | 7.5747 | 5.7375 |
| 10 | 10 | 8.0074 | 5.7375 | 3.2919 |

### Tabla 7.1 — Advección + dispersión a t = 1 h (M = 1000 mg, u = 0,25 m/s)
*Archivo:* `resultados/act7_adveccion_dispersion.csv`

| Dx (m²/s) | x_max = u·t (m) | C_max (mg/m) | σₓ² = 2Dx·t (m²) | σₓ (m) | Ancho ±2σ (m) |
|---|---|---|---|---|---|
| 50 | 900 | 0.6649 | 360,000 | 600 | 2,400 |
| 100 | 900 | 0.4702 | 720,000 | 848.5281 | 3,394.1125 |
| 200 | 900 | 0.3325 | 1.440e+06 | 1,200 | 4,800 |

### Tabla 7.2 — Perfil C(x) a t = 1 h para los tres valores de Dx
*Archivo:* `resultados/act7_perfil_C.csv`

| x (m) | C (mg/m) | Dx=50 | C (mg/m) | Dx=100 | C (mg/m) | Dx=200 |
|---|---|---|---|
| 0 | 0.2159 | 0.2679 | 0.2509 |
| 300 | 0.4033 | 0.3662 | 0.2934 |
| 600 | 0.5868 | 0.4417 | 0.3222 |
| 900 | 0.6649 | 0.4702 | 0.3325 |
| 1,200 | 0.5868 | 0.4417 | 0.3222 |
| 1,500 | 0.4033 | 0.3662 | 0.2934 |
| 1,800 | 0.2159 | 0.2679 | 0.2509 |
| 2,100 | 0.09 | 0.173 | 0.2016 |

### Tabla 8.1 — Resultados comparativos de los escenarios A, B y C
*Archivo:* `resultados/act8_escenarios.csv`

| Escenario | Dx (m²/s) | k (h⁻¹) | x_max (m) | C_max (mg/m) | σₓ (m) | Masa remanente (mg) | Ancho ±2σ (m) |
|---|---|---|---|---|---|---|---|
| A: Advección | 0 | 0 | 900 | n/d | 0 | 1,000 | 0 |
| B: Advección + dispersión | 50 | 0 | 900 | 0.6649 | 600 | 1,000 | 2,400 |
| C: Advección + dispersión + transformación | 50 | 0.05 | 900 | 0.6325 | 600 | 951.2294 | 2,400 |

### Tabla 8.2 — Identificación del máximo, ancho y pérdida (preguntas 35 a 38)
*Archivo:* `resultados/act8_detalle.csv`

| Concepto | Valor | Unidad |
|---|---|---|
| 35. C_max escenario B | 0.6649 | mg/m |
| 35. C_max escenario C | 0.6325 | mg/m |
| 36. Posición del máximo (A, B y C) | 900 | m |
| 37. σₓ escenarios B y C | 600 | m |
| 38. Factor de supervivencia e^(−k·t) | 0.9512 | - |
| 38. Pérdida absoluta de C_max | 0.0324 | mg/m |
| 38. Pérdida relativa de C_max | 4.8771 | % |
| 38. Masa transformada en 1 h | 48.7706 | mg |

### Tabla 8.3 — Perfil de concentración de los escenarios B y C
*Archivo:* `resultados/act8_perfil_BC.csv`

| x (m) | B: C (mg/m) | C: C (mg/m) | Diferencia (mg/m) | Diferencia (%) |
|---|---|---|---|---|
| 0 | 0.2159 | 0.2053 | 0.0105 | 4.8771 |
| 300 | 0.4033 | 0.3836 | 0.0197 | 4.8771 |
| 600 | 0.5868 | 0.5582 | 0.0286 | 4.8771 |
| 900 | 0.6649 | 0.6325 | 0.0324 | 4.8771 |
| 1,200 | 0.5868 | 0.5582 | 0.0286 | 4.8771 |
| 1,500 | 0.4033 | 0.3836 | 0.0197 | 4.8771 |
| 1,800 | 0.2159 | 0.2053 | 0.0105 | 4.8771 |
| 2,100 | 0.09 | 0.0856 | 0.0044 | 4.8771 |
| 2,400 | 0.0292 | 0.0278 | 0.0014 | 4.8771 |

### Tabla 9.1 — Sensibilidad a la velocidad (Dx = 50 m²/s, k = 0,05 h⁻¹, t = 1 h)
*Archivo:* `resultados/act9_sensibilidad_u.csv`

| u (m/s) | x_max = u·t (m) | x_max (km) | C_max (mg/m) | σₓ (m) | Tiempo hasta 5 km (h) |
|---|---|---|---|---|---|
| 0.1 | 360 | 0.36 | 0.6325 | 600 | 13.8889 |
| 0.25 | 900 | 0.9 | 0.6325 | 600 | 5.5556 |
| 0.5 | 1,800 | 1.8 | 0.6325 | 600 | 2.7778 |

### Tabla 9.2 — Sensibilidad a la dispersión (u = 0,25 m/s, k = 0,05 h⁻¹, t = 1 h)
*Archivo:* `resultados/act9_sensibilidad_Dx.csv`

| Dx (m²/s) | σₓ (m) | C_max (mg/m) | Ancho ±2σ (m) | Comportamiento |
|---|---|---|---|---|
| 0 | 0 | n/d | 0 | Sin dispersión (pulso puntual ideal) |
| 50 | 600 | 0.6325 | 2,400 | Dispersión moderada |
| 100 | 848.5281 | 0.4472 | 3,394.1125 | Mayor ensanchamiento |
| 200 | 1,200 | 0.3162 | 4,800 | Mayor ensanchamiento |

### Tabla 9.3 — Sensibilidad a la transformación (u = 0,25 m/s, Dx = 50 m²/s, t = 1 h)
*Archivo:* `resultados/act9_sensibilidad_k.csv`

| k (h⁻¹) | e^(−k·t) | Pérdida (%) | C_max (mg/m) | Masa remanente (mg) | Vida media (h) |
|---|---|---|---|---|---|
| 0 | 1 | 0 | 0.6649 | 1,000 | ∞ |
| 0.02 | 0.9802 | 1.9801 | 0.6517 | 980.1987 | 34.6574 |
| 0.05 | 0.9512 | 4.8771 | 0.6325 | 951.2294 | 13.8629 |
| 0.1 | 0.9048 | 9.5163 | 0.6016 | 904.8374 | 6.9315 |

### Tabla 9.4 — Índices de sensibilidad adimensionales (perturbación ±10 %)
*Archivo:* `resultados/act9_indices_sensibilidad.csv`

| Parámetro | Variable de salida | Valor base | −10 % | +10 % | Índice S (elasticidad) | |S| |
|---|---|---|---|---|---|---|
| u | x_max (m) | 900 | 810 | 990 | 1 | 1 |
| u | C_max (mg/m) | 0.6325 | 0.6325 | 0.6325 | 0 | 0 |
| u | Masa remanente (mg) | 951.2294 | 951.2294 | 951.2294 | 0 | 0 |
| Dx | x_max (m) | 900 | 900 | 900 | 0 | 0 |
| Dx | C_max (mg/m) | 0.6325 | 0.6667 | 0.603 | -0.5031 | 0.5031 |
| Dx | Masa remanente (mg) | 951.2294 | 951.2294 | 951.2294 | 0 | 0 |
| k | x_max (m) | 900 | 900 | 900 | 0 | 0 |
| k | C_max (mg/m) | 0.6325 | 0.6356 | 0.6293 | -0.05 | 0.05 |
| k | Masa remanente (mg) | 951.2294 | 955.9975 | 946.4851 | -0.05 | 0.05 |

### Tabla 9.5 — Matriz de elasticidades S(parámetro, salida)
*Archivo:* `resultados/act9_matriz_sensibilidad.csv`

| Parámetro | C_max (mg/m) | Masa remanente (mg) | x_max (m) |
|---|---|---|---|
| Dx | -0.5031 | 0 | 0 |
| k | -0.05 | -0.05 | 0 |
| u | 0 | 0 | 1 |

### Tabla 10.1 — Parámetros del modelo y su obtención en un sistema real
*Archivo:* `resultados/act10_parametros.csv`

| Parámetro | Significado físico | Método de obtención | 45. ¿Medible en campo? | 46. ¿Estimable? | 47. ¿Requiere calibración? | 48. ¿De literatura? | Valor usado en la práctica |
|---|---|---|---|---|---|---|---|
| u | Velocidad media de desplazamiento del agua y del contaminante | Aforo (caudal / área de la sección) o medición directa con correntómetro o ADCP | Sí | Sí | Rara vez | Poco recomendable | 0,25 m/s (valor de la práctica) |
| D | Coeficiente de difusión molecular; transporte por agitación térmica de las moléculas | Literatura, ensayos de laboratorio o correlaciones según el contaminante y la temperatura | No | Sí | No | Sí | 1×10⁻⁹ m²/s |
| Dx | Coeficiente de dispersión longitudinal; ensanchamiento por advección diferencial y turbulencia | Ensayos con trazadores (método de momentos), fórmulas empíricas y calibración del modelo | Indirectamente | Sí | Sí | Con precaución | ≈51 m²/s (Actividad 3); 50 m²/s adoptado |
| k | Constante de transformación de primer orden (degradación biótica/abiótica) | Ensayos de degradación, series temporales de concentración o calibración | Indirectamente | Sí | Sí | Como valor inicial | 0,05 h⁻¹ / 0,06931 d⁻¹ |
| C₀ | Concentración inicial del contaminante en la fuente | Muestreo y análisis fisicoquímico en el punto de vertido | Sí | No | No | No | 10 y 20 mg/L |
| M | Masa total de contaminante liberada al sistema | Volumen o caudal de la descarga × concentración del efluente | Sí | Sí | A veces | No | 1000 mg |

### Tabla 10.2 — Clasificación de los parámetros según su obtención
*Archivo:* `resultados/act10_clasificacion.csv`

| Categoría | Parámetros |
|---|---|
| 45. Medibles directamente en campo | u, C₀, M |
| 46. Estimables (ensayos o correlaciones) | D, Dx, k |
| 47. Requieren calibración | Dx principalmente; k con frecuencia |
| 48. Obtenibles de literatura | D (fiable); k y Dx solo como valores iniciales |

### Tabla 11.1 — Números adimensionales y escalas de tiempo por longitud de tramo
*Archivo:* `resultados/disc_numeros_adimensionales.csv`

| L (m) | L (km) | t_advección (h) | t_dispersión (h) | t_reacción (h) | Péclet Pe = uL/Dx | Damköhler Da = kL/u | C/C₀ al final del tramo (%) | Proceso dominante |
|---|---|---|---|---|---|---|---|---|
| 100 | 0.1 | 0.1111 | 0.0278 | 20 | 0.5 | 0.0056 | 99.446 | Dispersión |
| 1,000 | 1 | 1.1111 | 2.7778 | 20 | 5 | 0.0556 | 94.5959 | Advección |
| 5,000 | 5 | 5.5556 | 69.4444 | 20 | 25 | 0.2778 | 75.7465 | Advección |
| 10,000 | 10 | 11.1111 | 277.7778 | 20 | 50 | 0.5556 | 57.3753 | Advección |

### Tabla 11.2 — Magnitud comparada de la difusión molecular y la dispersión longitudinal
*Archivo:* `resultados/disc_difusion_vs_dispersion.csv`

| Mecanismo | Coeficiente (m²/s) | σ tras 1 h (m) | σ tras 24 h (m) | Razón σ frente a D | Razón frente a D |
|---|---|---|---|---|---|
| Difusión molecular D | 1.000e-09 | 0.0027 | 0.0131 | 1 | 1 |
| Dispersión longitudinal Dx | 50 | 600 | 2,939.3877 | 223,606.7977 | 5.000e+10 |

---

## 3. Índice de figuras

| Figura | Archivo |
|---|---|
| Figura 1. Advección pura: distancia recorrida frente al tiempo | `figuras/fig01_adveccion_x_vs_t.png` |
| Figura 2. Difusión molecular de un pulso instantáneo | `figuras/fig02_difusion_molecular.png` |
| Figura 3. Estimación del coeficiente de dispersión longitudinal | `figuras/fig03_estimacion_Dx.png` |
| Figura 4. Transformación de primer orden | `figuras/fig04_primer_orden.png` |
| Figura 5. Estimación de k y proyección del decaimiento | `figuras/fig05_estimacion_k.png` |
| Figura 6. Advección + transformación C(x)=C0·e^(−kx/u) | `figuras/fig06_adveccion_transformacion.png` |
| Figura 7. Advección + dispersión: efecto de Dx | `figuras/fig07_adveccion_dispersion.png` |
| Figura 8. Modelo integrado: concentración frente a distancia | `figuras/fig08_modelo_integrado.png` |
| Figura 9. Análisis de sensibilidad: efecto individual de u, Dx y k | `figuras/fig09_sensibilidad_paneles.png` |
| Figura 10. Sensibilidad relativa de cada salida a cada parámetro | `figuras/fig10_tornado_sensibilidad.png` |
| Figura 11. Síntesis conceptual del transporte y la transformación | `figuras/fig11_sintesis_conceptual.png` |
| Figura 12. Secuencia de las prácticas dentro del curso | `figuras/fig12_secuencia_curso.png` |

---

## 4. Ecuaciones utilizadas

| Proceso | Ecuación de gobierno | Solución empleada |
|---|---|---|
| Advección | ∂C/∂t + u ∂C/∂x = 0 | x = u·t ; C = C₀ |
| Difusión | ∂C/∂t = D ∂²C/∂x² | C = M/√(4πDt)·exp(−x²/4Dt) |
| Dispersión (estimación) | σₓ² = 2Dₓt | Dₓ = σₓ²/(2t) |
| Transformación | dC/dt = −kC | C = C₀e^(−kt) ; t½ = ln2/k |
| Advección + transformación | ∂C/∂t + u ∂C/∂x = −kC | C(x) = C₀e^(−kx/u) |
| Advección + dispersión | ∂C/∂t + u ∂C/∂x = Dₓ ∂²C/∂x² | C = M/√(4πDₓt)·exp(−(x−ut)²/4Dₓt) |
| Modelo integrado | ∂C/∂t + u ∂C/∂x = Dₓ ∂²C/∂x² − kC | el anterior × e^(−kt) |
