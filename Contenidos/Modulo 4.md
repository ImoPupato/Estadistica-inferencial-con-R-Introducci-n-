# Módulo 4: Ensayos de hipótesis en base a más dos muestras.  
En el módulo anterior comparamos algunos parámetros que describían características de dos poblaciones. Presentamos dos tipos de diseños experimentales en función de la naturaleza de las unidades experimentales. Cuando las unidades eran homogéneas utilizamos un diseño completamente aleatorizado y si se trataban de unidades heterogéneas utilizamos un diseño en bloques completos aleatorizados.  
El estudio que realizamos en el modulo anterior, buscaba determinar el efecto que tenía un nivel del factor. Efecto del método de medición sobre la concentración de HDL, efecto de un medicamento sobre la concentración de glucosa o efecto de la localidad de residencia en la concentración de ácido úrico. En estos casos estabamos comparando sólo dos niveles del factor. Puede resultarnos de interes comparar más niveles del factor o más de un factor, ello se lleva adelante con un Análisis de la Variancia.  
## ANOVA (analysis of variance)  
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
  |12| Fertilizante B| 16.2 |

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

<cente>$\overline{Y_i .}$ = $\frac{1}{J}$ $\displaystyle\sum_{j=1}^{J}$ $Y_{ij}$</center>  

Por ejemplo, el promedio del primer nivel:  
$\overline{Y_{Control} .}$ = $\frac{15.6 + 15.5 + 14.7 + 15.3}{4}$ = 15.275  
También podemos expresar el promedio general:  
$\overline{Y..}$ = $\frac{1}{IJ}$ $\displaystyle\sum_{i=1}^{I}$ $\displaystyle\sum_{j=1}^{J}$ $Y_{ij}$  
Y para nuestro caso sería:  
$\overline{Y..}$ = $\frac{15.6 + 15.5 + 14.7 + 15.3 +  16.9+17.5+16.9+17.3+17.8 + 16.5 +  16.8 + 16.2}{12}$ = 16.416  

### Hipótesis   
En estos casos, nuestras hipótesis de interés serán: H0) los promedios de cada nivel son iguales (es decir que no hay efecto del nivel) _vs_ H1) al menos un promedio es diferente a los demás (es decir, hay efecto de, al menos, un nivel del factor).  

### Supuestos del modelo
Como vimos en los módulos anteriores, antes de realizar una técnica para contrastar hipótesis debíamos verificar ciertos supuestos como son la normalidad, la homocedasticidad, etc. Para la técnica de ANOVA los supuestos son los siguientes:
- Independencia: los niveles del factor deben ser independientes entre ellos y las observaciones aleatorias. Esto es verificado conociendo el diseño utilizado.  
- Distribución normal: la variable debe distribuirse de forma normal en cada uno de los grupos (niveles del factor). Para este criterio utilizamos el test de Shapiro-Wilk (también puede utilizarse el test de Kolmogorov-Smirnov). En caso de que no se cumpla, se puede recurrir a un testre de Kruskal-Wallis.  
- Variancia constante entre grupos: Tabien denominada _homocedasticidad_, se evalúa con el test de Barlett (tambien puede utilizarse el test de Levene o de Fligner-Killeen). En caso de que no se cumpla este supuesto, se puede utilizar el test de Welch (_oneway.test()_)
#### Estadística base  
Como se mencionó anteriormente, evaluamos y comparamos la variabilidad entre las observaciones. De acuerdo a nuestro diseño, podemos descomponer la variabilidad en aquella correspondiente al nivel (asignable) y en la debida al error (aleatoria). Comparamos la variabilidad utilizando el **cociente de cuadrados medios**. Los cuadrados medios se construyen como la **suma de cuadrados** dividida por los grados de libertad correspondientes. A continuación se describen formalmente:  
$SC_{tratamiento}$ = $J$ $\displaystyle\sum_{i=1}^{I}$ ($\overline{Y_i .}$ - $\overline{Y..}$) $^2$  
$SC_{error}$ = $\displaystyle\sum_{i=1}^{I}$ $\displaystyle\sum_{j=1}^{J}$ $Y_{ij}$ ($\overline{Yij}$ - $\overline{Y_i.}$) $^2$  
$CM_{tratamiento}$ = $\frac{SC_t}{I-1}$  
$CM_{error}$ = $\frac{SC_e}{IJ-I}$  
La estadística base será:
$\frac{CM_t}{CM_e}$ ~ $F_{I-1;IJ-I}$
En el módulo anterior ya presentamos el test F de variancias para dos muestras, en este caso de más de dos muestras utilizaremos la función _aov()_.  

### Comparaciones múltiples
Cuando rechacemos la H0 y concluyamos que al menos un nivel del factor tiene efecto, va a ser de nuestro interés determinar cuál o cuales. Para ello procedemos a realizar un test de comparaciones múltiples que que nos permitirá visualizar cuál o cuáles promedios son diferentes.  

A continuación realizaremos los test de ANOVA para diferentes situaciones. Primero recordemos setear el directorio de trabajo:  
```R
setwd("C:/Users/Aylen/Desktop/Curso R (IPS)/Análisis estadístico básico con R/Contenidos/Modulo 4")
```
## Muestras independientes con distribución normal y variancias homogéneas
El enunciado fue planteado anteriormente y del análisis del diseño surge que los datos son independientes.  
### Ensayo de hipótesis
- Ingreso de datos (se encuentran en la tabla anexa):
```R
datos <- read.csv("C:/Users/Aylen/Desktop/Curso R (IPS)/Análisis estadístico básico con R/Contenidos/Modulo 4/datos.txt", sep="")
```
- Test de normalidad:
```R
lapply(split(datos$Altura,datos$Tratamiento),shapiro.test)
```
```R
$Control
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.87149, p-value = 0.3036
$Fertilizante_A
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.8494, p-value = 0.2242
$Fertilizante_B
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.91289, p-value = 0.4978
```
_Consideramos normalidad_
- Test de homocedasticidad:
```R
bartlett.test(list(
  datos$Altura[datos$Tratamiento=="Control"],
  datos$Altura[datos$Tratamiento=="Fertilizante_A"],
  datos$Altura[datos$Tratamiento=="Fertilizante_B"],
))
```
```
	Bartlett test of homogeneity of variances
data:  list(datos$Altura[datos$Tratamiento == "Control"], datos$Altura[datos$Tratamiento == "Fertilizante_A"], datos$Altura[datos$Tratamiento == "Fertilizante_B"])
Bartlett's K-squared = 1.9187, df = 2, p-value = 0.3831
```
_Consideramos homocedasticidad_
- Test ANOVA:
```
summary(aov(Altura~Tratamiento,datos))
```
```
            Df Sum Sq Mean Sq F value   Pr(>F)    
Tratamiento  2  8.032   4.016   16.39 0.000999 ***
Residuals    9  2.205   0.245                     
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```
_Concluimos que, al menos uno de los tratamientos tiene efecto sobre la altura de las plantas._
- Test de comparaciones múltiples:
```
install.packages("agricolae")
library("agricolae")
print(LSD.test(aov(Altura~Tratamiento,datos),"Tratamiento"))
```
```
$statistics
  MSerror Df     Mean       CV  t.value      LSD
    0.245  9 16.41667 3.015075 2.262157 0.791755

$parameters
        test p.ajusted      name.t ntr alpha
  Fisher-LSD      none Tratamiento   3  0.05
$means
               Altura       std r      LCL      UCL  Min  Max    Q25   Q50    Q75
Control        15.275 0.4031129 4 14.71514 15.83486 14.7 15.6 15.150 15.40 15.525
Fertilizante_A 17.150 0.3000000 4 16.59014 17.70986 16.9 17.5 16.900 17.10 17.350
Fertilizante_B 16.825 0.6946222 4 16.26514 17.38486 16.2 17.8 16.425 16.65 17.050
$comparison
NULL
$groups
               Altura groups
Fertilizante_A 17.150      a
Fertilizante_B 16.825      a
Control        15.275      b
attr(,"class")
[1] "group"
```
_Ambos fertilizantes tienen un afecto sobre la altura de las plantas, respecto del control. En ambos casos las alturas promedio son mayores a las del control_.

## Muestras dependientes con distribución normal y variancias homogéneas
Supongamos ahora que utilizamos una mayor cantidad de plantas de tres especies diferentes. En este sentido las muestras resultan dependientes. Para llevar adelante el experimento, eligieron aleatoriamente 12 plantas (homogéneas) de tres especies diferentes y de manera aleatoria les asignamos el tratamiento (control, fertilizante A y fertilizante B). Luego realizaremos mediciones de las alturas de las plantas y las registraremos en una tabla.
- Variable: altura de la planta.
- Parametro de interes: altura promedio ($\mu$).
- Factor: Fertilizante.
- Niveles: Control (sin fertilizante), Fertilizante A y Fertilizante B.
- Bloque: Especie. Muestras dependientes.
### Ensayo de hipótesis
- Ingreso de datos (se encuentran en la tabla anexa):
```
datos2 <- read.csv("C:/Users/Aylen/Desktop/Curso R (IPS)/Análisis estadístico básico con R/Contenidos/Modulo 4/datos2.txt", sep="")
datos2$Especie<-factor(datos2$Especie)
```
- Test de normalidad:
```
lapply(split(datos2$Altura,datos2$Tratamiento),shapiro.test)
```
```
$Control
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.94383, p-value = 0.5492
$Fertilizante_A
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.92111, p-value = 0.2952
$Fertilizante_B
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.95977, p-value = 0.7805
```
_Consideramos normalidad_
- Test de homocedasticidad:
```
	Bartlett test of homogeneity of variances
data:  list(datos2$Altura[datos2$Tratamiento == "Control"], datos2$Altura[datos2$Tratamiento == "Fertilizante_A"], datos2$Altura[datos2$Tratamiento == "Fertilizante_B"])
Bartlett's K-squared = 5.4294, df = 2, p-value = 0.06622
```
_Consideramos hocedasticidad_
- Test ANOVA:
```
summary(aov(Altura~Tratamiento+Especie,datos2)) #con el argumento + Planta, adicionamos el término de la dependencia
```
```
           Df Sum Sq Mean Sq F value   Pr(>F)    
Tratamiento  2  58.77  29.387   62.96 1.21e-11 ***
Especie      2  60.37  30.184   64.67 8.67e-12 ***
Residuals   31  14.47   0.467                     
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```
_Concluimos que, al menos uno de los tratamientos tiene efecto sobre la altura de las plantas y que hay efecto de bloqueo por especie._  
- Test de comparaciones múltiples:
```
print(LSD.test(aov(Altura~Tratamiento+Especie,datos2),"Tratamiento"))
```
```
$statistics
    MSerror Df     Mean       CV  t.value       LSD
  0.4667294 31 17.94722 3.806583 2.039513 0.5688313
$parameters
        test p.ajusted      name.t ntr alpha
  Fisher-LSD      none Tratamiento   3  0.05
$means
                 Altura       std  r      LCL      UCL  Min  Max    Q25   Q50   Q75
Control        16.23333 0.9393744 12 15.83111 16.63556 14.7 17.6 15.575 16.20 16.85
Fertilizante_A 19.30000 1.9711556 12 18.89778 19.70222 16.9 22.5 17.450 19.10 21.00
Fertilizante_B 18.30833 1.4266670 12 17.90611 18.71056 16.2 20.8 17.475 18.05 19.35
$comparison
NULL
$groups
                 Altura groups
Fertilizante_A 19.30000      a
Fertilizante_B 18.30833      b
Control        16.23333      c

attr(,"class")
[1] "group"
```
_Ambos fertilizantes tienen un afecto sobre la altura de las plantas, respecto del control. En ambos casos las alturas promedio son mayores a las del control y diferentes entre sí. El fertilizante A produce plantas de mayor altura_.

## Muestras independientes sin distribución normal y/o sin homocedasticidad
Supongamos ahora que encontraron unos resultados del uso de un tercer fertilizante que habían ensayado para el primer ejemplo. Deciden analizar los datos de nuevo incorporando los que pensaban perdidos.  
### Ensayo de hipótesis
- Ingreso de datos (se encuentran en la tabla anexa):
```R
datos3 <- read.csv("C:/Users/Aylen/Desktop/Curso R (IPS)/Análisis estadístico básico con R/Contenidos/Modulo 4/datos3.txt", sep="")
```
- Test de normalidad:
```R
lapply(split(datos3$Altura,datos3$Tratamiento),shapiro.test)
```
```R
$Control
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.87149, p-value = 0.3036
$Fertilizante_A
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.8494, p-value = 0.2242
$Fertilizante_B
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.90255, p-value = 0.4438
$Fertilizante_C
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.97096, p-value = 0.2886
```
_Consideramos normalidad_
- Test de homocedasticidad:
```R
bartlett.test(list(
  datos3$Altura[datos3$Tratamiento=="Control"],
  datos3$Altura[datos3$Tratamiento=="Fertilizante_A"],
  datos3$Altura[datos3$Tratamiento=="Fertilizante_B"],
  datos3$Altura[datos3$Tratamiento=="Fertilizante_C"]
))
```
```
	Bartlett test of homogeneity of variances
data:  list(datos3$Altura[datos3$Tratamiento == "Control"], datos3$Altura[datos3$Tratamiento == "Fertilizante_A"], datos3$Altura[datos$Tratamiento == "Fertilizante_B"], datos3$Altura[datos3$Tratamiento == "Fertilizante_C"])
Bartlett's K-squared = 29.823, df = 3, p-value = 1.504e-06
```
_No podemos considerar hocedasticidad_
- Test ANOVA:
En vista de que no se cumple el supuesto de homocedasticidad, utilizaremos un test no paramétrico.
```
kruskal.test(Altura~Tratamiento,datos3)
```
```
	Kruskal-Wallis rank sum test
data:  Altura by Tratamiento
Kruskal-Wallis chi-squared = 12.725, df = 3, p-value = 0.005272
```
_Concluimos que, al menos uno de los tratamientos tiene efecto sobre la altura de las plantas._
- Test de comparaciones múltiples:
```
install.packages("pgirmess")
library("pgirmess")
kruskalmc(datos3$Altura,datos3$Tratamiento,paired=FALSE)
```
```
Multiple comparison test after Kruskal-Wallis 
alpha: 0.05 
Comparisons
                              obs.dif critical.dif stat.signif
Control-Fertilizante_A              6     8.881697       FALSE
Control-Fertilizante_B              6     8.881697       FALSE
Control-Fertilizante_C             12     8.881697        TRUE
Fertilizante_A-Fertilizante_B       0     8.881697       FALSE
Fertilizante_A-Fertilizante_C       6     8.881697       FALSE
Fertilizante_B-Fertilizante_C       6     8.881697       FALSE
```
_El ferilizante C tiene un efecto respecto del control_.

## Muestras dependientes sin distribución normal y/o sin homocedasticidad
Supongamos ahora que, en el ejemplo anterior, incorportamos a las especies como bloque.
### Ensayo de hipótesis
- Ingreso de datos (se encuentran en la tabla anexa):
```R
datos4<- read.csv("C:/Users/Aylen/Desktop/Curso R (IPS)/Análisis estadístico básico con R/Contenidos/Modulo 4/datos4.txt", sep="")
datos4$Especie<-factor(datos4$Especie)
```
- Test de normalidad:
```R
lapply(split(datos4$Altura,datos4$Tratamiento),shapiro.test)
```
```R
$Control
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.94383, p-value = 0.5492
$Fertilizante_A
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.92111, p-value = 0.2952
$Fertilizante_B
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.95748, p-value = 0.7474
$Fertilizante_C
	Shapiro-Wilk normality test
data:  X[[i]]
W = 0.95159, p-value = 0.6604
```
_Consideramos normalidad_
- Test de homocedasticidad:
```R
bartlett.test(list(
  datos$Altura[datos$Tratamiento=="Control"],
  datos$Altura[datos$Tratamiento=="Fertilizante_A"],
  datos$Altura[datos$Tratamiento=="Fertilizante_B"],
  datos$Altura[datos$Tratamiento=="Fertilizante_C"]
))
```
```
	Bartlett test of homogeneity of variances
data:  list(datos4$Altura[datos4 $Tratamiento == "Control"], datos4$Altura[datos4$Tratamiento == "Fertilizante_A"], datos4$Altura[datos4$Tratamiento == "Fertilizante_B"], datos4$Altura[datos4$Tratamiento == "Fertilizante_C"])
Bartlett's K-squared = 86.831, df = 3, p-value < 2.2e-16
```
_No podemos considerar homocedasticidad_
- Test ANOVA:
En vista de que no se cumple el supuesto de homocedasticidad, utilizaremos un test no paramétrico para muestras dependientes.
```
kruskal.test(Altura~Tratamiento+Especie,datos4)
```
```
	Kruskal-Wallis rank sum test
data:  Altura by Tratamiento
Kruskal-Wallis chi-squared = 12.725, df = 3, p-value = 0.005272
```
_Concluimos que, al menos uno de los tratamientos tiene efecto sobre la altura de las plantas._
- Test de comparaciones múltiples:
```
pairwise.wilcox.test(x = datos4$Altura,  #variable respuesta
                g = datos4$Tratamiento, #factor
                p.adjust.method = "holm", #método
                paired = TRUE, #muestras aparedadas, dependientes
                alternative = "two.sided") #alterntiva bilateral
```
```
Pairwise comparisons using Wilcoxon signed rank test with continuity correction 

data:  datos4$Altura and datos4$Tratamiento 

               Control Fertilizante_A Fertilizante_B
Fertilizante_A 0.0050  -              -             
Fertilizante_B 0.0029  0.0253         -             
Fertilizante_C 0.0029  0.0029         0.0029        

P value adjustment method: holm 
```
_Los tres fertilizantes tienen un afecto sobre la altura de las plantas, respecto del control, siendo también diferentes entre sí_.
