# Módulo 3: Ensayos de hipótesis en base a dos muestras.  
En el módulo anterior nos propusimos comparar algunos parámetros que describían características de una población. En este módulo vamos a comparar los parámetros de dos poblaciones. Para ello vamos a extraer una muestra de cada población y realizar la inferencia en función a ellas.  
## Palabras claves   
- Variable respuesta: característa que puedo medir u observar en la unidad experimental y es de interés.  
- Factor: criterio que diferencia a las poblaciones a comparar.  
- Nivel: modalidades de/los factor/es en estudio.  
- Unidad experimental: mínima porción a la que se le determina el valor de la variable. Pueden ser homogéneas o heterogéneas. 
  - Homogéneas: similares respecto de aquellas características influyen en la variable respuesta. Aplicando un diseño apropiado, se obtienen muestras independientes o no apareadas.  
  - Heterogéneas: cuando podrían comportarse de manera diferenciada respecto del nivel. Aplicando un diseño apropiado, se obtienen muestras dependientes o apareadas.
- Población: conjunto de todas los elementos (o eventos) de interés.
  
Utilizaremos dos ejemplos para poder identificar estos aspectos:
_"Una empresa está pensando en cambiar de agencia proveedora de cierto rectivo. Para tomar la decisión, proponen quedarse con aquella agencia que brinde el reactivo de mayor concentración promedio (sospechan que es el proveniente de la agencia 1). Procedieron seleccionando al azar 25 alícuotas (porciones homogéneas) de reactivos de cada agencia y registraron su concentración"_  
 - Variable: Concentración de cierto reactivo.  
 - Factor: Agencia proveedora.  
 - Nivel: Agencia 1, Agencia 2.
 - Unidad experimental: Alícuota del reactivo. Unidades homogénes, diseño completamente aleatorizado, muestras independientes.  
 - Población: Todas las alícuotas de cada agencia.  
 - Parámetro de interés: concentración promedio del reactivo de interés (𝜇).  
 - Hipótesis de interés: H0) 𝜇_1 = 𝜇_2 vs H1) 𝜇_1 > 𝜇_2, o bien H0) 𝜇_1 - 𝜇_2 = 0 vs H1) 𝜇_1 - 𝜇_2 > 0,
 - Estadística base para el análisis: diferencia de promedios muestrales ($\overline{x}$_1 - $\overline{x}$_2).  
 - n_Total=50, n_1=n_2=25  
  
_"Una proveedora de fertilizantes sospecha que el lugar de almacenamiento está afectando el rendimiento de los mismos. Deciden llevar adelante un estudio comparando el rendimiento del fertilizante que fue almacenado en exposición a la luz con aquel que fue almacenado en oscuridad. Como deben aplicar los fertilizantes en parcelas que podrían resultar heterogéneas (humedad, exposición al viento, variedad de soja plantada, etc), deciden aplicar un **diseño en bloques completos aleatorizados**. Para ello, agrupan los lotes de parecelas en pares (similares entre sí) a los que les aplican (aleatoriamente) un tipo de fertilizante. a cada uno empresa está pensando en cambiar de agencia proveedora de cierto rectivo. Finalmente asignaron los dos fertilizantes a 10 pares de lotes y registraron el rendimiento de soja"_  
 - Variable: Diferencia en el rendimiento de soja.  
 - Factor: Lugar de almacenamiento del fertilizante.  
 - Nivel: Oscuridad (A) o luz (B).
 - Unidad experimental: par de lotes. Unidades heterogéneas, diseño en bloques (cada par es un bloque), muestras dependientes.  
 - Población: Todos los pares de lotes.  
 - Parámetro de interés: diferencia promedio de rendimiento de soja (𝜇_D).  
 - Hipótesis de interés: H0) 𝜇_D=0 vs H1) 𝜇_D>0
 - Estadística base para el análisis: promedio muestral de las diferencias ($\overline{x}$_D).  
 - n_Total=10, n_1=n_2=10  

_"Una farmacéutica está proponiendo quitar del mercado una de sus dos vacunas contra la gripe. Para ello decide llevar adelante un estudio multicéntrico para comparar la eficacia de las dos vacunas. Procedieron seleccionando al azar 126 personas de las cuales 53 habían recibido la vacuna X y 73 la vacuna Y. Luego de la consulta, del primer grupo habían enfermado 18 mientras que del segundo grupo 26 lo hicieron"_  
 - Variable: Eficacia de la vacuna.  
 - Factor: Vacuna.  
 - Nivel: Vacuna X, Vacuna Y.
 - Unidad experimental: Personas vacunadas con X o Y. Unidades homogéneas, diseño completamente aleatorizado, muestras independientes.  
 - Población: Tenemos dos poblaciones, la que recibió la vacuna X y la que recibió la vacuna Y.  
 - Parámetro de interés: proporción de personas enfermas en cada población vacunada (π).  
 - Hipótesis de interés: H0) π_X=π_Y vs H1) π_X($\neq$)π_Y.  
 - Estadística base para el análisis: frecuencias relativas de personas enfermas en cada muestra (_h_).  
 - n_Total=126, n_X=53, n_Y=73  
  
_"Un laborario está probando dos métodos para cuantificar la concentración de Cinc. Sospechan que el método A es más preciso que el método B. Para comparar ambos métodos, deciden tomar una muestra aleatoria de 28 comprimidos y registrar la concentración de Cinc medida por cada método"_  
 - Variable: Concentración de Cinc en suplementos vitamínicos.  
 - Factor: Método de cuantificación de Cinc.  
 - Nivel: Método A y Método B.  
 - Unidad experimental: Comprimido. Unidades homogéneas, diseño completamente aleatorizado, muestras independientes.  
 - Población: Todos los comprimidos.
 - Parámetro de interés: variancia poblacional.
 - Hipótesis de interés: H0) $σ^2_A$ = $σ^2_B$ H1) $σ^2_B$>$σ^2_A$.  
 - Estadística base para el análisis: cociente de variancias muestrales.  
 - n_Total=28, n_A=n_B=28  
  
## Guía para el ensayo de hipótesis en base a dos muestras   
1. Reconocer las hipótesis y poder plantearlas en término del parámetro de interés: μ, $σ^2$ , π. Puede suceder que queramos contrastar si los parámetros son iguales, contra la propuesta de que uno sea mayor (>), menor (<), o que sean distintos ($\neq$) entre sí.
2. Fijar el nivel de significación 𝛼: generalmente es 0.05.  
3. Especificar la estadística base: combinación lineal de estimadores.  
  *i*. Análisis de la distribución muestral (Shapiro Wilk).
  *ii*. Análisis de la homogeneidad de variancias (Barlett).
  *iii*. Análisis del tipo de datos (apareados o no apareados) (respecto del diseño). 
5. Decidir el test a utilizar:
   Comparación de promedios:
   - Distribución normal, variancias homogéneas: Test T de Student (paired T o F dependiendo del diseño)
   - Distribución no normal o variancias no homogeneas: Test de Wilcoxon (paired T o F dependiendo del diseño)
   Comparación de proporciones:
   - _h_ = Test $\chi^2$ de Pearson
   - $s^2$ = Test $\chi^2$ de la variancia
7. Identificar la decisión de rechazo respecto del p-value.  
8. Llevar adelante el test. 
9. Tomar un decisión y concluir en términos de la situación planteada.  

## Base de datos
Utilizaremos la base de datos disponible para este módulo.
- Seteo del directorio de trabajo
```R
setwd("C:/Users/Aylen/Desktop/Curso R (IPS)/Análisis estadístico básico con R")
```
- Carga de datos
```R
library(readr)
datos <- read.csv("C:/Users/Aylen/Desktop/Curso R (IPS)/Análisis estadístico básico con R/datos.txt", sep="")
```
- Exploración de datos
```R
summary(datos)
```
## Comparación de promedios
Supongamos que queremos comparar la Glucosa promedio en personas que pertenecen a dos grupos diferentes (A y B):  
 - Variable: Glucosa en sangre.  
 - Factor: Grupo.  
 - Nivel: Grupo, Grupo B.
 - Parámetro de interés: índice de masa corporal promedio (𝜇).  
 - Hipótesis de interés:
   - H0) 𝜇_A = 𝜇_B vs H1) 𝜇_A > 𝜇_B
   - H0) 𝜇_A = 𝜇_B vs H1) 𝜇_A < 𝜇_B
   - H0) 𝜇_A = 𝜇_B vs H1) 𝜇_A ($\neq$) 𝜇_B
 - Estadística base para el análisis: diferencia de promedios muestrales ($\overline{x}$_1 - $\overline{x}$_0).  
### Análisis
1. H0) 𝜇_A = 𝜇_B vs H1) 𝜇_A > 𝜇_B  
2. 𝛼:0.05.  
3. Especificar la estadística base: combinación lineal de estimadores.  
  *i*. Análisis de la distribución muestral (Shapiro Wilk).
```R
 shapiro.test(datos$Glucosa[datos$Grupo=="A"])
```
```R
	Shapiro-Wilk normality test

data:  datos$Glucosa[datos$Grupo == "A"]
W = 0.99165, p-value = 0.6607
```
```R
 shapiro.test(datos$Glucosa[datos$Grupo=="B"])
```
```R
	Shapiro-Wilk normality test

data:  datos$Glucosa[datos$Grupo == "B"]
W = 0.99439, p-value = 0.9041
```
Como el p>0.05, para ambos niveles, consideramos normalidad.  
4, 5 y 6. Test T de Student




Kruskall-Wallis rank sum test:
```R
kruskal.test(BMI~HighBP,data=datos)
```
```R
	Kruskal-Wallis rank sum test

data:  BMI by HighBP
Kruskal-Wallis chi-squared = 31.823, df = 1, p-value = 1.689e-08
```
7. Como el p<0.05, el BMI difiere entre los tratamientos.  

shapiro.test(tablaR341$calcemia[tablaR341$tratamiento=="control"])
Shapiro-Wilk normality test
data: tablaR341$calcemia[tablaR341$tratamiento == "control"]
