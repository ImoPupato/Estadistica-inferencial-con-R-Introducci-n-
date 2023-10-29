# Módulo 1: Introducción a la estadística inferencial.  
_La estadística ha sido propuesta como una tecnlogía del método científico, proporcionando instrumentos para la toma de decisiones (Mood & Graybill, 1963)_.  
Podemos dividir a la estadística en dos grandes grupos o ramas;  
- **estadística descriptiva**, abordada en el curso _"Introducción al procesamiento de datos con R"_. Relacionada con el resumen de datos, su descripción y presentación;
- **estadística inferencial**, relacionada con la utilización de datos para la toma de decisiones.  
## Palabras claves   
- Variable: cualquier característica que toma diferentes valores en las unidades elementales.
- Experimento aleatorio: aquel que, a pesar de ser repetido reiteradas veces bajo iguales condiciones controladas, proporciona resultados diferentes no predecibles. Por ejemplo; "registrar el número obtenido al lanzar un dado".   
- Espacio muestral: aquel conjunto formado por todos los resultados posibles asociados a un experimento aleatorio. Se suele representar con la letra _**S**_.
- Variable aleatoria: es aquella función que asigna a cada elemento del espacio muestral un número real. Se suele representar con la letra _**X**_.  
Podemos formalizar la relación entre _X_ y _S_ de la siguiente manera:
<div align="center">
  𝑋 ∶ 𝑆 → ℝ
</div>  

De acuerdo a los valores posibles que puede tomar una variable aleatoria cuantitativa podemos clasificarla en:  
   Continua: aquella que toma cualquier valor dentro de un intervalo.  
   Discreta: valores aislados dentro de un intervalo.   
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
dicho intervalo. Formalmente la representamos como: $P(x_1 ≤ X ≤ x_2) = \int_{x_1}^{x_2} {f_x(x)} \,{\rm d}x$
### Función de distribución acumulada  
Para una variable aleatoria X, tanto discreta como continua, la función de distribución acumulada $F_X$ se define como: $F_X (x) = P(X ≤ x) ∀ x ∈ R$.  

## Distribuciones en el muestreo  
### - Binomial
### - Poisson
### - Normal
### - Exponencial
## Simulación de datos 
## Aleatoriedad de datos
## Estimación de parámetros: puntual y por intervalo de confianza
