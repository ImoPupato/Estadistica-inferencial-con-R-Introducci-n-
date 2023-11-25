# Módulo 4: Ensayos de hipótesis en base a más dos muestras.  
En el módulo anterior comparamos algunos parámetros que describían características de dos poblaciones. Presentamos dos tipos de diseños experimentales en función de la naturaleza de las unidades experimentales. Cuando las unidades eran homogéneas utilizamos un diseño completamente aleatorizado y si se trataban de unidades heterogéneas utilizamos un diseño en bloques completos aleatorizados.  
El estudio que realizamos en el modulo anterior, buscaba determinar el efecto que tenía un nivel del factor. Efecto del método de medición sobre la concentración de HDL, efecto de un medicamento sobre la concentración de glucosa o efecto de la localidad de residencia en la concentración de ácido úrico. En estos casos estabamos comparando sólo dos niveles del factor. Puede resultarnos de interes comparar más niveles del factor o más de un factor, ello se lleva adelante con un Análisis de la Variancia.  
## ANOVA (analisis of variance)  
Consiste en un conjunto de técnicas que _descompone_ la variabilidad total de los datos en _fuentes_ de variación. Estas fuentes provienen del diseño del experimento.  
Supongamos que queremos comparar el efecto de dos fertilizantes en la altura de las plantas. De manera aleatoria, asignaremos el tratamiento (control, fertilizante A y fertilizante B) a 12 plantas (homogéneas). Luego realizaremos mediciones de las alturas de las plantas y las registraremos en un tabla que tendrá las siguientes características:   
- Variable: altura de la planta.
- Parametro de interes: altura promedio ($\mu$).
- Factor: Fertilizante.
- Niveles: Control (sin fertilizante), Fertilizante A y Fertilizante B.  
Solemos recolectar los datos de la siguiente manera:  
  |Número de planta| Tratamiento | Altura (cm) |
  |:-:|:-:|:-:|
  |1| Control| 15.6 |
  |2| Control| 15.5 |
  |3| Control| 14.7 |
  |4| Control| 15.3|
  |5| Fertilizante A| 16.9 |
  |6| Fertilizante A| 17.5 |
  |7| Fertilizante A| 16.9|
  |8| Fertilizante A| 17.3 |
  |9| Fertilizante B| 17.8 |
  |10| Fertilizante B| 16.5|
  |11| Fertilizante B| 16.8 |
  |11| Fertilizante B| 16.2 |

Pero, podríamos rediseñar la tabla anterior para visualizar _mejor_ los niveles del factor:
<table>
    <thead>
        <tr>
            <th> Factor </th>
            <th> Niveles </th>
            <th> Observaviones </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=3 align="center"> Tratamiento </td>
            <td rowspan=1 align="center"> Control </td>
            <td align="center"> 15.6    15.5    14.7    15.3 </td>
        <tr>
            <td rowspan=1 align="center"> Fertilizante A </td>
            <td align="center"> 16.9    17.5    16.9    17.3 </td>
        <tr>
            <td rowspan=1 align="center"> Fertilizante B </td>
            <td align="center"> 17.8    16.5    16.8    16.2 </td>
    </tbody>
</table>  

De esta manera, podemos localizar por ejemplo, a la tercera observación del segundo nivel: $Y_{23}$ = 16.9  
Genericamente, describimos a cada una de las observaciones como $Y_{ij}$ con _i_ indicando el nivel, y _j_ la observación. En nuestro caso I=3 y J=4 es decir, hay 3 niveles del factor y 4 observaciones para cada nivel.  
Si nuestro interés es comparar las alturas promedio de cada nivel, podríamos escibirlo como:  

$\overline{Y_i .}$ = $\frac{1}{J}$ $\displaystyle\sum_{j=1}^{J}$ $Y_{ij}$  

$\overline{Y_{Control} .}$ = $\frac{15.6 + 15.5 + 14.7 + 15.3}{4}$ = 15.275  

También podemos expresar el promedio general:
$\overline{Y..}$ = $\frac{1}{IJ}$ $\displaystyle\sum_{i=1}^{I}$ $\displaystyle\sum_{j=1}^{J}$ $Y_{ij}$ 
$\overline{Y..}$ = $\frac{15.6 + 15.5 + 14.7 + 15.3 +  16.9+17.5+16.9+17.3+17.8 + 16.5 +  16.8 + 16.2}{12}$ = 16.416  

En estos casos, nuestras hipótesis de interés serán: H0) los promedios de cada nivel son iguales (es decir que no hay efecto del nivel) _vs_ H1) al menos un promedio es diferente a los demás (es decir, hay efecto de, al menos, un nivel del factor). 

Cuando descomponemos la variabilidad, de acuerdo a nuestro diseño, vamos a tener una variabilidad en función del nivel del factor
