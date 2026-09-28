# Modelos relacionados a la DBO y DQO
## El oxigeno disuelto: disponibilidad y saturación
    El OD es la cantidad de oxigeno molecular disponible en el agua para la repsiracion de organismos acuaticos y la degradacion aerobica.
    * Temperatura: mayor temepratura menos solubilidad
    * Presión
    * turbulencia e intercambio
    * Actividad biologica
    Ley de Henry:
    C = Kh * pO2
    C = concentracion de saturación
    p = presión parcial de O2
    kh= constante h dependiente de o2
## OD indicador central de calidad
    Fuentes de O2 reaireacion atmosferica, fotosintesis de algas y amcrofitas y aportes de tributarios oxigenados.
    Sumideros de O2 son DBO carbonacea, nitirficación, demanda del sedimento
### Hipoxia / anoxia (0-2)
### Estrés severo (2-4)
### Estrés (4-5)
### Adecuado ( >= 5)
### Buena calidad ( > 7)
## DBO
    nosotros usamos el oxigeno para degradadr las cosas 
    * DBO remanente: oxigeno que aun falta consumir en el tiempo t = L(t)
    * DBO ejercida: Oxigeno consumido hasta el tiempo t = y(t)
    * DBO última: Demanda total potencial Lo = y(t) + L(t) 
    * DBO a 5 días: Medida de laboratorio (20°C); fracción de L0 = DBO(5)
    y(t) = L0 - L(t) = L0 ( 1 - e ^(-kd*t))
## Degradación de DBO: de la hipotesis a la solución
L(t) = L0 * e ^(-kd*t)
## Constante de desoxigenación
    kd cuantifica con que microorganismos degradan la materia organica osea la rapidez en la que se consume el oxigeno disuelto 
    KT = K20 * (theta^(T-20))
    constante de theta = 1,047 para kd y theta es 1,024 para kr
    k20 = constante a 20 °C
## Constante de reaireación
    kr = 3,93 * u⁽⁰·⁵⁾/ H⁽¹·⁵⁾
    u = velocidad media del rio
    H = profundidad media
    f = kr/kd 
    f = autodepuración 
    f> 1 el rio se recupera
    si e smenor la recuperación es lenta 
## Deficit y el balance de oxígeno
    D(t) = OD sat - OD (t)

    dD/dt = Kd*L - Kr * D
    Si son distintos

    D(t) = (Kd * Lo)/(Kr-Kd) * (e^(-kdt)-e^(-krt))+ D0 * e^(-krt)

    Si son iguales
    D(t) = (kd*L0*t + D0)*e^(-Kd*t)

    OD (t) = OD sat - D(t) se construye el OD a partir de el D(t)

## Punto critico 
    dD/dt = 0
    kd * L(tc) = kr* Dc

    Dc = Kd/Kr * (L0 * (e^(-kd * tc)))

    Od min = OD sat -Dc

    tc = 1/(kr-kd) * ln((kr/kd)*(1-(D0*(kr-kd)/(kd*L0))))
## Tiempo de viaje
    x = v* t
## SUpuestos del modelo
    Estado estacionario
    FLujo piston
    Una sola descarga puntual
    Degradacion de DBO de primer orden con kd constante
    Reaireación proporcional al déficit con Kr constante
    temperatura y velocidad uniformes en el tramo
## Procesos no representados
    fOTOSINTEIS Y REPSIRACION DE ALGAS
    Demanda bentica de oxigeno del sedimento
    Nitrificación
    Sedimentacion y resuspensión de materia organica
    Variaciones de caudal velocidad profundidad y temperatura
    Fuentes difusas y descargas adicionales aguas abajo