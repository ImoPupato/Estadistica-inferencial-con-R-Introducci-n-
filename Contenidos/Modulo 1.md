# Módulo 1: Introducción a la estadística inferencial.  
_La estadística ha sido propuesta como una tecnlogía del método científico, proporcionando instrumentos para la toma de decisiones (Mood & Graybill, 1963)_.  
Podemos dividir a la estadística en dos grandes grupos o ramas;  
- **estadística descriptiva**, abordada en el curso _"Introducción al procesamiento de datos con R"_. Relacionada con el resumen de datos, su descripción y presentación;
- **estadística inferencial**, relacionada con la utilización de datos para la toma de decisiones.  
## Palabras claves   
- Variable: cualquier característica que toma diferentes valores en las unidades elementales.
- Experimento aleatorio: aquel que, a pesar de ser repetido reiteradas veces bajo iguales condiciones controladas, proporciona resultados diferentes no predecibles. Por ejemplo; "registrar el número obtenido al lanzar un dado". Se suele representar con la letro _**E**_.   
- Espacio muestral: aquel conjunto formado por todos los resultados posibles asociados a un experimento aleatorio. Se suele representar con la letra _**S**_.
- Variable aleatoria: es aquella función que asigna a cada elemento del espacio muestral un número real. Se suele representar con la letra _**X**_.  
Podemos formalizar la relación entre _X_ y _S_ de la siguiente manera:
<div align="center">
  𝑋 ∶ 𝑆 → ℝ
</div>  

De acuerdo a los valores posibles que puede tomar una variable aleatoria cuantitativa podemos clasificarla en **continua** (aquella que toma cualquier valor dentro de un intervalo); o **discreta** (valores aislados dentro de un intervalo).   
- Estadísticas descriptivas:  
  - Medidas de localización o posición: permiten localizar al conjunto de datos de destintos puntos de vista.  
     - valor mínimo: menor valor observado entre los datos.  
     - valor máximo: máximo valor observado entre los datos.  
     - percentiles: $p_α$, es el valor de la variable que acumula el α de las observaciones ordenadas.  
     - promedio o media aritmética ($\overline{x}$): es la suma de los valores observados dividida por el número total de datos.
       $$\frac{1}{n} \sum_{i=1}^n x_i\$$
     - primer cuartil (Q1): primer cuartil, es el valor de la variable que acumula el 25% inferior de las observaciones ordenadas de menor a mayor.  
     - mediana (Q2): segundo cuartil, es el valor de la variable que acumula el 50% de las observaciones ordenadas de menor a mayor.  
     - tercer cuartil (Q3): tercer cuartil, es el valor de la variable que acumula el 75% inferior de las observaciones ordenadas de menor a mayor.  
     - modo/moda: es el valor de la variable que se presenta una mayor cantidad de veces.  
  - Medidas de dispersión o variabilidad: ponen de manifiesto las diferencias entre los distintos valores de un conjunto de datos.  
    - rango (R): es la máxima diferencia que observada para la variable $R=x_máx−x_min$.  
    - rango intercuartil (RI): diferencia entre Q1 y Q3, en valor absoluto, representa al 50% central de los datos. $RI=Q1-Q3$. 
    - variancia ($s^2$): medida de la variavilidad, en promedio, de la media.
      $$\frac{1}{n-1} \sum_{i=1}^n(x_i-\overline{x})^2\$$
    - desvío estándar (s): raiz cuadrada positiva de la variancia, su ventaja es que está expresada en las mismas unidades de la variable.  $$\sqrt(s^2)\$$
    - coeficiente de variación (CV): es la desviación estándar dividida por la media aritmética, represanda la desviación estandar medida en unidades de la media aritmética.  $CV=\frac{s}{\mid\ \overline{x}\mid\}$.  

## Funciones de distribución de probabilidad  
La función de densidad de proabilidad de X suele simbolizarse como $f_x$ es una representación o modelo matemático que describe el comportamiento de una variable aleatoria continua en la población. Ésta describe cuáles son los valores posibles para la variable, indicando cuál es la probabilidad asociada a los mismos.
La función de densidad de probabilidad tiene las siguientes condiciones y/o características:
- $f_X (x) ≥ 0, ∀ x$
- $\int_{-∞}^∞ {f_x(x)} \,{\rm d}x=1$  
Llamamos probabilidad a la proporcion poblacional dada por el área bajo la curva sobre un intervalo en el eje
de abscisas. Entonces, la probabilidad (P) de que la variable aleatoria X tome valores en el
intervalo ($x_1, x_2$) está dada por el valor de la integral de la función de densidad de probabilidad en
dicho intervalo. Formalmente la representamos como: $$P(x_1 ≤ X ≤ x_2) = \int_{x_1}^{x_2} {f_x(x)} \,{\rm d}x$$
### Función de distribución acumulada  
Para una variable aleatoria X, tanto discreta como continua, la función de distribución acumulada $F_X$ se define como: $$F_X (x) = P(X ≤ x) ∀ x ∈ R$$  
<div align="center">
  
| Función de distribución acumulada |Variable aleatoria continua        |Variable aleatoria discreta        |
|:---------------------------------:|:---------------------------------:|:---------------------------------:|
|$f_X (x)$                          | $\int_{-∞}^X{f_X(s)}ds$           |$$\sum_s^x p_X(s)\$$|

</div>  

## Distribuciones en el muestreo  
### - Binomial
La distribución Binomial es utilizada cuando se busca describir la ocurrencia de un sucesos exitosos o de acierto en un solo ensayo.  
Una **variable aleatoria discreta** X tiene una distribución Binomial con parámetros *n* y *k*, y se simboliza X ∼ Bin(n,*k*), si su función de probabilidad puntual es:  
$p_X (k) = \binom{n}{k}p^k\left(1-p\right)^{n-k}$  
con 0<*k*<1 y n ∈ N. 
Si X ∼ Binom(n; *k*), se demuestra que su media es E(X) = n*k* y su desvío estándar es D(X) = $\sqrt{nk(1-k)}$ .
### - Poisson
La distribución Poisson es util para describir el comportamiento de un conjunto de eventos que suceden aleatoriamente en una unidad de tiempo o espacio.  
Una **variable aleatoria discreta** X tiene una distribución Poisson con parámetro λ, y se simboliza  X ∼ Po(λ), si su función de probabilidad puntual es:  
$p_X (x) = \frac{e^{−λ}λ^{x}}{x!}$ con y = 0, 1, 2, ...donde λ ≥ 0.  
Si Y ∼ Po(λ), se demuestra que su media es E(X) = λ y su desvío estándar es D(X) = $\sqrtλ$.  
### - Normal  
La distribución Normal, o Gaussiana, es muy utilizada puesto que la distribución de muchos de las estadísticas que se usan en los intervalos de confianza y ensayos de hipótesis se aproximan a esta.  
Una **variable aleatoria continua** X tiene una distribución Normal de parámetros μ y σ, X ∼ N(μ;σ), si su función de densidad de probabilidad es:
$$f_X (x) = \frac{1}{\sqrt(2πσ)}e^−\frac{(x−μ)^2}{2σ^2}$$
con x ∈ R donde μ ∈ R y σ ∈ $R^+$.  
Si X ∼ N(μ; σ), se demuestra que su media es E(X) = μ y su desvío estándar es D(X) = σ.
### - Exponencial
Cuando se quiere modelar la duración de un suceso o el tiempo hasta que ocurra un evento, se recurre a la distribución exponencial.  
Una **variable aleatoria continua** X tiene una distribución Exponencial de parámetro λ, y se simboliza X ∼ Exp(λ), si su función de densidad de probabilidad es:  
$f_X (x) = λ e^{-λx}$ si x>0
  y  
$f_X (x) = 0$ si x≤0  
Si X ∼ Exp(λ), se demuestra que su media es E(X) = 1/λ y su desvío estándar es D(X) = 1/λ.  
## Simulación de datos 
Muchas veces nos puede resultar interesante generar una muestra de datos que tengan una distribución dada. Para ello contamos con las funciones *rbinom, rpois, rnorm, rexp*.  
### Muestra de datos con distribución de Binomial  
Se tiene el experimento aleatorio *"Lanzar una moneda 5 veces y registrar la salida"*. La moneda tiene *n*=2 salidas posibles de *k*=0.5. Si queremos simular un posible resultado, tendríamos 5 observaciones. En R podríamos hacerlo utilizando rbinom con los argumentos *n* = 5 (número de observaciones) , *size* = 1 (comienza en 0, tenemos dos opciones: cara o cruz -0 o 1-) y *prob* = 0.5 (probabilidad de ocurrencia del éxito) de la siguiente manera:
```r
rbinom(5,1,0.5) # rbinom (n, size, prob)
```
### Muestra de datos con distribución de Poisson  
Sabiendo que un 10% de los utensillos obtenidos en cierto proceso de fabricación resulta defectuoso y que nuestro nuevo E: *"Seleccionar al azar 5 utensillos"*, simulemos una posible muestra proveniente de dicho experimento. *rpois* tiene los argumentos *n* (igual a 5 en nuestro caso) y λ (igual a 10):
```r
rpois(5,10) # rpois(n,λ)
```
### Muestra de datos con distribución de Normal  
Los resultados en los exámenes finales del curso "Introducción al procesamiento de datos con R" fueron valores entre 0 y 10. La puntuación promedio fue 8.9 y su desviación estándar de 1.5. Suponiendo un nuevo E: *"Seleccionar al azar 5 exámenes y registrar su puntuación"*, simulemos una posible muestra proveniente de dicho experimento. *rnorm* tiene los argumentos *n* (igual a 5 en nuestro caso), μ (igual a 8.9 en nuestro caso) y σ (igual a 1.5 en nuestro caso):
```r
rnorm(5,8.9,1.5) # rnorm(n,μ,σ)
```
### Muestra de datos con distribución de Exponencial  
Un centro de atención mantiene un registro del tiempo transcurrido entre dos llamadas, siendo su promedio o valor esperado de 115 segundos. Sea el E: *"Seleccionar al azar 5 registros del tiempo transcurrido entre dos llamadas"*, simulemos una muestra utilizando *rexp* cuyos argumentos son *n* (igual a 5 en nuestro caso) y 1/λ (igual a 1/115):
```r
rexp(5,1/115) # rexp(n,1/λ)
```
## Aleatoriedad de datos  
Como habrán notado, la aleatoridad es un requisito importante. De hecho, en algunos casos resulta indispensable para llegar a conclusiones adecuadas. Por ello resulta de interes determinar si los datos con los que estamos trabajando cumplen este criterio y lo haremos con el "test de rachas". Este test consiste en medir el número de rachas (grupo de valores consecutivos por encima o por debajo de la mediana) que aparecen en la muestra, y compararlo con la
*distribución teórica* de valores para el caso de que la muestra sea aleatoria.  
Aquí nos adentraremos en una primera aproximación al ensayo de hipótesis ya que, en este test, estaremos contrastando la *Hipótesis nula* de que el número de rachas de la muestra es igual a un valor teórico contra la *Hipótesis alternativa* de que sea diferente.  

Si bien hay varias librerías para realizar este contraste (como por ejemplo: snpar y randtests) aquí utilizaremos la librería "tseries" y la función runs.test() cuyo argumento debe estar asignado como factor.  
Utilizaremos una de las funciones previamente utilizadas para generar una muestra aleatoria y construiremos otra que no cumpla este requisito.
```{r, eval = FALSE, warning=FALSE}
install.packages("tseries") # para instalar la librería en caso de que no la tengan
```
```{r, warning=FALSE}
library ("tseries")
```
Generamos dos muestras para trabajar con el test:
```{r, warning=FALSE}
aleatoria<-rnorm(50,5,1.2) # 50 datos, con μ=5 y σ=1.2
no_aleatoria<-rep(c(-1,1),50) # 50 datos cuyos valores alternan entre los valores -1 y 1
```
Exploremos ambos conjuntos de datos con la función summary y observamos las características:
```{r, warning=FALSE}
summary(aleatoria)
```
La salida va a ser levemente diferente ya que cada muestra generada por rnorm será diferente. En mi caso la salida es:
```{r, warning=FALSE}
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  2.435   3.897   4.763   4.835   5.686   8.055 
```
El summary de la muestra guardada en el objeto "no_aleatoria" será igual en todos los casos ya que lo hicimos a través de un vector:
```{r, warning=FALSE}
summary(no_aleatoria)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
     -1      -1       0       0       1       1
```
Además podemos pedir que se genere una tabla:
```{r, warning=FALSE}
table(no_aleatoria)
```
Cuya salida será:
```{r, warning=FALSE}
no_aleatoria
-1  1 
50 50 
```
Podemos ver entonces que efectivamente el test de rachas en el conjunto de datos "no_aleatoria" debería darnos que no es aleatorio, es decir un p<0.05 y por lo tanto Rechazar la Hipótesis nula del test. Corramos entonces los dos test, recordando incluir la funcion factor(), condición requerida por el test:
```{r, warning=FALSE}
runs.test(as.factor(aleatoria > median(aleatoria))) # por el tipo de datos, no dicotómicos, comparamos con la mediana
```
Las salida tiene la siguiente forma, recuerden que puede ser levemente diferente en función de los datos que se hayan generado:
```{r, warning=FALSE}
 runs.test(as.factor(aleatoria > median(aleatoria)))
```
```{r, warning=FALSE}
	Runs Test

data:  as.factor(aleatoria > median(aleatoria))
Standard Normal = 0.85732, p-value = 0.3913 # este es el valor que vamos a utilizar para la toma de decisiones
alternative hypothesis: two.sided
```
Como se puede observar, la prueba utilizada dio por *resultado* un p-value = 0.3913. El p-value puede interpretarse, a los fines de este curso, como la probabilidad de tomar la decisión equivocada rechazando la *Hipótesis nula* planteada por el test. En este caso la probabilidad de equivocarnos al rechazar la Hipótesis de que los datos provienen de un muestreo aleatorio es muy alta (recordemos que la probabilidad varía entre 0 y 1). Como criterio general podemos pensar que una p<0.05 es suficiente para considerar rechazar la Hipótesis nula, es decir aceptar que los datos no provienen de un muestreo aleatorio. En otras palabras, la probabilidad de equivocarnos al pensar que los datos no provienen de un muestreo aleatorio y que así sea es muy baja.  
Ahora bien, corremos el test para la muestra "no_aleatoria":
```{r, warning=FALSE}
runs.test(as.factor(no_aleatoria > median(no_aleatoria)))
```
El resultado que tenemos en este caso es el siguiente:
```{r, warning=FALSE}
	Runs Test
data:  as.factor(no_aleatoria > median(no_aleatoria))
Standard Normal = 9.8499, p-value < 2.2e-16 # este es el valor que vamos a utilizar para la toma de decisiones
alternative hypothesis: two.sided
```
En este caso p-value < 0.05, rechazamos la Hipótesis nula por lo que consideramos que el muestro no fue aleatorio.  

## Estimación de parámetros: puntual y por intervalo de confianza
Los parámetros describen características poblacionales como el promedio poblacional, la variancia poblacional, el desvío poblacional y la probabilidad de que ocurra un evento o suceso en una población. Al referirse a la población, los parámetros suelen ser desconocidos y por ello es necesario estimar su valor. Para ello se recurre al muestreo, por ejemplo, y al cálculo de estadísticos que permiten estimar su valor ya sea de forma puntual o por intervalo de confianza.  
La principal ventaja de una estimación por intervalo de confianza es que, justamente, se tiene una nivel de confianza de la estimación y un error asociado a la determinación.  
<div align="center">
  
| Parámetro a estimar |Estimación puntual|Estimación por intervalo de confianza con σ conocido|Estimación por intervalo de confianza con σ desconocido|
|:---------------------------------:|:---------------------------------:|:---------------------------------:|:---------------------------------:|
|Promedio poblacional: μ | $\overline{x}$ | ($\overline{x}$ - $Z_{1-\frac{α}{2}}$ $\frac{σ}{\sqrt(n)}$ ; $\overline{x}$ + $Z_{1-\frac{α}{2}}\frac{σ}{\sqrt(n)}$) | ($\overline{x}$ - $t_{1-\frac{α}{2}}\frac{s}{\sqrt(n)}$ ; $(\overline{x}$ + $t_{n,1-\frac{α}{2}}\frac{s}{\sqrt(n)}$)|

| Parámetro a estimar |Estimación puntual|Estimación por intervalo de confianza|
|:---------------------------------:|:---------------------------------:|:---------------------------------:|
|Variancia poblacional: $σ^2$ | $s^2$ | ($\frac{(n-1)s^2}{\chi^2_{n-1,1-\frac{α}{2}}}$ ; $\frac{(n-1)s^2}{\chi^2_{n-1,\frac{α}{2}}}$) |  

| Parámetro a estimar |Estimación puntual|Estimación por intervalo de confianza|
|:---------------------------------:|:---------------------------------:|:---------------------------------:|
|Proporción: *p* | _h_ | (_h_ - $Z_{1-\frac{α}{2}}$ $\sqrt(\frac{h(1-h)}{n})$ ; _h_ + $Z_{1-\frac{α}{2}}$ $\sqrt(\frac{h(1-h)}{n})$ ) |
</div>  
Afortunadamente, contamos con funciones en R que nos permiten obtener los intervalos sin necesidad de utilizar las fórmulas descriptas anteriormente.  
  
Trabajaremos con el siguiente ejemplo para las determinaciones: _"Se determinó la concentración de Vitamina D (nga/ml) en 30 muestras de sangre, cuyos resultados se enuncian a continuación:"_   
19.08, 16.38, 20.9, 19.09, 16.72, 22.84, 12.48, 21.57, 23.49, 17.15, 23.05, 14.73, 15.36, 16.3, 22.33, 26.7, 16.09, 11.88, 24.58, 12.37, 28.9, 15.3, 22.83, 19.86, 24.65, 17.94, 22.35, 27.6, 20.96, 12.49, 28.21, 18.5, 13.2  

### Promedio
Para estimar de manera puntual el promedio poblacional de concentración de Vitamina D en R, lo haremos a través de la media muestral. Primero creamos el objeto datos, con los valores de Vitamina D muestreados.
```{r, warning=FALSE}
mean(datos)
[1] 19.57212 
```
Para poder realizar la estimación por intervalo de confianza, necesitamos recurrir a la función t.test (desconocemos la variancia poblacional) y definir el nivel de confianza (90%, en este caso).
```{r, warning=FALSE}
t.test(x=datos, conf.level=0.90)
```
La salida en R será la siguiente:	
```{r, warning=FALSE}
	One Sample t-test
data:  datos
t = 23.034, df = 32, p-value < 2.2e-16
alternative hypothesis: true mean is not equal to 0
90 percent confidence interval:
 18.13283 21.01141
sample estimates:
mean of x 
 19.57212  
```
Podemos expresar nuestra conclusión como: _"Con un nivel de confianza del 90% el intervalo (18.13; 21.01) mg/ml cubre al valor promedio de Vitamina D"_.  
### Variancia
Para estimar de manera puntual el la variancia poblacional de concentración de Vitamina D en R, lo haremos a través de la variancia muestral. Ya hemos creado el objeto datos, por lo que procederemos a la estimación.
```{r, warning=FALSE}
var(datos)
[1] 23.82537
```
Para poder realizar la estimación por intervalo de confianza, necesitamos recurrir a la función varTest() del paquete "EnvStats" y definir el nivel de confianza (90%, en este caso).
```{r, warning=FALSE}
install.packages("EnvStats")
library("EnvStats")
varTest(x=datos, conf.level=0.90)
```
La salida en R será la siguiente, y se encuentra la estimación puntual y los valores de los extremos del intervalo (LCL y UCL):	
```{r, warning=FALSE}
Results of Hypothesis Test
--------------------------

Null Hypothesis:                 variance = 1

Alternative Hypothesis:          True variance is not equal to 1

Test Name:                       Chi-Squared Test on Variance

Estimated Parameter(s):          variance = 23.82537

Data:                            datos2

Test Statistic:                  Chi-Squared = 762.4118

Test Statistic Parameter:        df = 32

P-value:                         0

90% Confidence Interval:         LCL = 16.50447
                                 UCL = 37.98401
```
Podemos expresar nuestra conclusión como: _"Con un nivel de confianza del 90% el intervalo (16.50; 37.98) m$g^2$ / \ml^2 cubre el valor de la variancia poblacional de la concentración de de Vitamina D, siendo su estimación puntual de 23.83 $\ng^2$/$\ml^2$"_.  

### Proporción
Supongan que ahora queremos determinar la proporción de personas con concentración de Vitamina D menor a la recomendada (mayor a 20 ng/ml).  
Para poder realizar la estimación, con la frecuencia relativa primero debemos determinar cuántas muestras cumplen con el requisito. Para ello podemos utilizar la siguiente linea:
```{r, warning=FALSE}
sum(datos2<=20)
[1] 18
```
Entonces para estimar de manera puntual la proporción tendriamos:
```{r, warning=FALSE}
18/33
[1] 0.5454545
```
Para poder realizar la estimación por intervalo de confianza, necesitamos recurrir a la función prop.test() y definir el nivel de confianza (90%, en este caso).
La salida en R será la siguiente, y se encuentra la estimación puntual y los valores de los extremos del intervalo:
```{r, warning=FALSE}
prop.test(18,33,conf.level = 0.9)

	1-sample proportions test with continuity correction

data:  18 out of 33, null probability 0.5
X-squared = 0.12121, df = 1, p-value = 0.7277
alternative hypothesis: true p is not equal to 0.5
90 percent confidence interval:
 0.3906055 0.6927112
sample estimates:
        p 
0.5454545 
```
Podemos expresar nuestra conclusión como: _"Con un nivel de confianza del 90% el intervalo (0.39; 0.69) cubre la proporción de personas que cumplen con la recomendación de Vitamina D, siendo su estimación puntual de 0.54"_. 
