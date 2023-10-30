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
### - Poisson
La distribución Poisson es util para describir el comportamiento de un conjunto de eventos que suceden aleatoriamente en una unidad de tiempo o espacio.  
Una **variable aleatoria discreta** X tiene una distribución Poisson con parámetro λ, y se simboliza Y ∼ Po(λ), si su función de probabilidad puntual es:  
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
Muchas veces nos puede resultar interesante generar una muestra de datos que tengan una distribución dada. Para ello contamos con las funciones *rpois, rnorm, rexp*.  
### Muestra de datos con distribución de Poisson  
El argumento de la distribución de Posisson es λ, utilizaremos un ejemplo para poder construir nuestra muestra aleatoria. *Una persona está interesada en utilizar unos dispositivos para construir circuitos especiales y por seguridad los reemplazar ́ıa ante la ocurrencia de una falla. Este usuario pretende que la mayor ́ıa de
ellos fallen despu ́es de las 150 horas y realiza una consulta en la empresa especializada para ver si
esto es razonable.
Se supone que la distribuci ́on de la variable duraci ́on del dispositivo (o tiempo hasta la falla), Y, es
Exponencial con α = 0, 002 fallas por hora.
```R

```
## Aleatoriedad de datos
## Estimación de parámetros: puntual y por intervalo de confianza
