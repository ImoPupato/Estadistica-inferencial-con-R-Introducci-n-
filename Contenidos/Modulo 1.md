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
aleatoria<-rnorm(50,5,0.5) # 50 datos, con μ=5 y σ=0.5
no_aleatoria<-rep(c(-1,1),50) # 50 datos cuyos valores alternan entre los valores -1 y 1
runs.test(factor(aleatoria)
runs.test(factor(no_aleatoria)
```
## Estimación de parámetros: puntual y por intervalo de confianza
