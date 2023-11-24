# Módulo 4: Ensayos de hipótesis en base a más dos muestras.  
En el módulo anterior comparamos algunos parámetros que describían características de dos poblaciones. Presentamos dos tipos de diseños experimentales en función de la naturaleza de las unidades experimentales. Cuando las unidades eran homogéneas utilizamos un diseño completamente aleatorizado y si se trataban de unidades heterogéneas utilizamos un diseño en bloques completos aleatorizados.  
El estudio que realizamos en el modulo anterior, buscaba determinar el efecto que tenía un nivel del factor. Efecto del método de medición sobre la concentración de HDL, efecto de un medicamento sobre la concentración de glucosa o efecto de la localidad de residencia en la concentración de ácido úrico. En estos casos estabamos comparando sólo dos niveles del factor. Puede resultarnos de interes comparar más niveles del factor o más de un factor, ello se lleva adelante con un Análisis de la Variancia.  
## ANOVA (analisis of variance)  
Consiste en un conjunto de técnicas que _descompone_ la variabilidad total de los datos en _fuentes_ de variación. Estas fuentes provienen del diseño del experimento.  
Supongamos que queremos comparar el efecto de dos fertilizantes en la altura de las plantas. De manera aleatoria, asignaremos el tratamiento (control, fertilizante A y fertilizante B) a 30 plantas (homogéneas). Luego realizaremos mediciones de las alturas de las plantas y las registraremos en un tabla que tendrá las siguientes características:   
- Variable: altura de la planta
- Parametro de interes: altura promedio ($\mu$)
- Factor: Fertilizante
- Niveles: Control (sin fertilizante), Fertilizante A y Fertilizante B

<div align= "center">
  |Número de planta| Tratamiento | Altura (cm) |
  |:-:|:-:|:-:|
  |1| Control| 15.8 |
  |2| Control| 13.6 |
  |3| Control| 14.7 |
  |...| Control|...|
  |10| Control| 15.9 |
  |1| Fertilizante A| 17.8 |
  |...| Fertilizante A|...|
  |10| Fertilizante A| 12.8 |
  |1| Fertilizante B| 1.8 |
  |...| Fertilizante B| ...|
  |10| Fertilizante B| 16.8 |
</div> 

  

Cuando descomponemos la variabilidad, de acuerdo a nuestro diseño, vamos a tener una variabilidad en función del nivel del factor
