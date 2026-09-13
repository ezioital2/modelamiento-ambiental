# Resumen de resultados — PAP en el río Chili

### Conclusiones automáticas

1. **Ingreso y mezcla.** Con 0.005–0.011 mg/L en el efluente la carga es 648–1,426 g/d y la
   concentración de mezcla 0.00056–0.00122 mg/L. El modelo empírico reproduce el documento
   (C₀ = 0.00086 mg/L, HQ = 0.24, HQ máx. = 0.34).
2. **Hidráulica.** Con Manning el tramo tiene h = 0.61 m, u = 1.10 m/s y TRH = 2.53 h;
   D_L (Fischer) = 56 m²/s.
3. **Destino.** k total ≈ 0.080 1/d; en el tramo se pierde apenas
   0.84 % de la carga y el 99.16 % sale aguas abajo: **la advección domina**.
   La volatilización y la sorción son despreciables; la fugacidad nivel III ubica 99.87 % del PAP en el agua.
4. **Procesos (365 d, horario).** C media en Uchumayo = 0.756 µg/L, máximo horario = 1.074 µg/L;
   el promedio diario subestima el pico en 21.1 %, lo que justifica el paso horario.
   HQ máximo = 0.30 < 1.
5. **Biota.** Entre Control y Perturbado el cambio de biomasa media es
   Fitoplancton -0.0001 %, Daphnia +0.0000 %, Trucha -0.0026 %.
   En la prueba de estrés (100×W): Fitoplancton -0.81 %, Daphnia -1.80 %, Trucha -10.33 %,
   lo que confirma que el acople tóxico–biota responde cuando la exposición se acerca a las CE50.
6. **Modelo integrado.** En validación: procesos NSE = 0.840,
   IA pura NSE = 0.920, integrado NSE = 0.928
   (RMSE 0.0991 → 0.0666 µg/L).
   Orden por NSE: Regresión potencial (0.928) > Integrado (procesos + RF) (0.928) > IA pura (RF) (0.920) > Procesos (nominal) (0.840) > Empírico (dilución) (0.836); techo alcanzable = 0.947.
   El integrado corrige el sesgo del modelo de procesos (sesgo -0.0705 → -0.0014 µg/L)
   y supera tanto a los procesos solos como a la IA pura. La cobertura calibrada del intervalo P5–P95 es 87.2 %.
7. **Riesgo.** Todos los modelos (empírico, procesos, IA e integrado) coinciden en HQ < 1 para las tres especies:
   la dilución del Chili en estiaje basta para el rango de carga planteado. La carga crítica que haría HQ = 1 en
   estiaje es ≈ 4,199 g/d. Esto no implica que el PAP sea inocuo (mayor sensibilidad de estadios embrionarios).

**Limitación principal:** no hay mediciones de PAP en el Chili; las métricas del integrado miden la capacidad de la IA
para corregir procesos no representados en un experimento sintético, no una validación con datos de campo.

## Tablas exportadas

- `t01_constantes.csv` — Tabla 1. Constantes y parámetros del escenario
- `t02_carga_mezcla.csv` — Tabla 2. Carga del efluente y concentración de mezcla (doc.: 648–1426 g/d)
- `t03_hidraulica_base.csv` — Tabla 3. Hidráulica del tramo en caudal base (12 + 1.5 m³/s)
- `t04_constantes_destino.csv` — Tabla 4. Constantes de pérdida de primer orden (15 °C, SS = 25 mg/L)
- `t05_particion_volatilizacion.csv` — Tabla 5. Partición agua–sólidos y volatilización
- `t06_bioconcentracion.csv` — Tabla 6. Cinética de captación (k2 supuestos; BCF en rango 10–46)
- `t07_fugacidad_distribucion.csv` — Tabla 7. Distribución por fugacidad nivel III (doc.: 99.5 % en agua)
- `t08_fugacidad_salidas.csv` — Tabla 8. Destino de la emisión (nivel III)
- `t09_dosis_respuesta.csv` — Tabla 9. Parámetros dosis–respuesta por especie
- `t10_estadios.csv` — Tabla 10. Unidades tóxicas por estadio (ilustrativo)
- `t11_verificacion_empirico.csv` — Tabla 11. Verificación del modelo empírico frente al documento
- `t12_forzantes_resumen.csv` — Tabla 12. Resumen de forzantes horarios (365 d)
- `t13_procesos_toxico.csv` — Tabla 13. Modelo de procesos: PAP en el tramo (365 d, paso horario)
- `t14_balance_masa.csv` — Tabla 14. Balance de masa del PAP en el tramo (estacionario, W = 1000 g/d)
- `t15_biota_escenarios.csv` — Tabla 15. Biota por escenario (365 d)
- `t16_streeter_phelps.csv` — Tabla 16. Streeter–Phelps del efluente (15 °C)
- `t17_monte_carlo_percentiles.csv` — Tabla 17. Incertidumbre Monte Carlo (percentiles 5 y 95)
- `t18_metricas_modelos.csv` — Tabla 18. Desempeño en el conjunto de validación (n = 600)
- `t19_regresion_potencial.csv` — Tabla 19. Regresión potencial C = a·W^b·Q^c (esperado b ≈ 1, c ≈ −1)
- `t20_validacion_cruzada.csv` — Tabla 20. Validación cruzada de 5 pliegues (NSE)
- `t21_importancia_variables.csv` — Tabla 21. Importancia de variables en el residuo
- `t22_incertidumbre_integrado.csv` — Tabla 22. Intervalos de predicción del modelo integrado
- `t23_integrado_anual.csv` — Tabla 23. Procesos vs integrado sobre la serie horaria anual
- `t24_riesgo_por_modelo.csv` — Tabla 24. Riesgo ecológico estimado por cada modelo (validación)
- `t00_valores_clave.csv` — Tabla resumen. Valores clave de la simulación

## Figuras

- `tif_pap/figuras/fig01_hidraulica.png`
- `tif_pap/figuras/fig02_destino_fugacidad.png`
- `tif_pap/figuras/fig03_dosis_respuesta.png`
- `tif_pap/figuras/fig04_modelo_empirico.png`
- `tif_pap/figuras/fig05_forzantes.png`
- `tif_pap/figuras/fig06_C_t_procesos.png`
- `tif_pap/figuras/fig07_C_x_procesos.png`
- `tif_pap/figuras/fig08_biomasas.png`
- `tif_pap/figuras/fig09_streeter_phelps.png`
- `tif_pap/figuras/fig10_monte_carlo.png`
- `tif_pap/figuras/fig11_predicho_vs_simulado.png`
- `tif_pap/figuras/fig12_integrado_serie_horaria.png`
- `tif_pap/figuras/fig13_riesgo_modelos.png`
