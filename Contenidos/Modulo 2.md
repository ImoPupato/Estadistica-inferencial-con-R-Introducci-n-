# Modulo 2: Ensayos de hipótesis en base a una muestra.  
Las pruebas o ensayos de hipótesis, junto con la estimación de parámetros trabajada en el módulo anterior, son herramientas muy utilizadas en el contexto de la inferencia estadística.  
Los ensayos de hipótesis nos permiten tomar decisiones acerca del valor de un parámetro a partir de los datos provenientes de una muestra.  
A través de ejemplos iremos presentando las distintas hipótesis para cada parámetro.  
Recordemos que un parámetro es una medida resumen de una característica poblacional. Por ejemplo: *concentración promedio de Vitamina D en personas rosarinas mayores a 18 años*; _proporción de personas que son alérgicas a la penicilina en la ciudad de San Lorenzo_; _variabilidad del pH del agua del río Paraná_.  

## Palabras claves   
- Hipótesis: enunciado positivo o confirmación sobre el valor de uno o varios parámetros. Por ejemplo: *La concentración promedio de Vitamina D en personas rosarinas mayores a 18 años es mayor a 20 ng/mL* ; _La proporción de personas que son alérgicas a la penicilina en la ciudad de San Lorenzo es igual a 10%_; _La variabilidad del pH del agua del río Paraná es menor a 0.5_.  
Podríamos reescribir formalmente las hipótesis anteriores según:  μ>20 ng/ml ; π = 0.01 ; $σ^2$ < 0.5  
- Hipótesis nula (H0): se considera a la afirmación inicial, basara en estudios previos y que corresponde al estado actual del conocimiento. **Generalmente** se plantea en términos de una igualdad.  
- Hipótesis alternativa (H1): se considera a la afirmación que quiero contrastar y contradice a la hiptótesis nula. **Generalmente** se plantea en terminos de desigualdad.  
- p-value (p): a los fines de este curso lo interpretaremos como la probabilidad de rechazar la hipótesis nula, siendo cierta. **Generalmente** se busca que sea un valor pequeño (p<0.05).  
- Potencia: a los fines de este curso la interpretamos como la probabilidad de rechazar la hipótesis nula, siendo falsa. Es decir, tomar la decisión correcta.  
- 𝛼 : nivel de significación del ensayo, podemos interpretar a 𝛼 como el p-value del ensayo de hipótesis.  
- Confianza: es la confianza que nos brinda la estimación, generalmente fijada en 90 o 95% y resulta ser (1-𝛼) x 100%.  

<div align="center">
  
| | Parámetro a estimar | Estimador |
|:---------------------------------:|:---------------------------------:|:---------------------------------:|
|Promedio poblacional| μ | $\overline{x}$ |
|Variancia poblacional| $σ^2$ | $s^2$ |
|Proporción| π | _h_ |

</div>  

## Guía para el ensayo de hipótesis
<div class=text-justify>
  
Resulta muy útil pensar en el ensayo o prueba de hipótesis de manera sistematizada, teniendo así una guía de pasos a seguir para llegar a la conclusión final.  
1. Reconocer las hipótesis y poder plantearlas en término del parámetro de interés: μ, $σ^2$ , π. Puede suceder que queramos contrastar si el parámetro es igual (=) a un valor, contra la propuesta de que sea mayor (>), menor (<) o distinto ($\neq$) de dicho valor.
2. Fijar el nivel de significación 𝛼: generalmente es 0.05.  
3. Especificar la estadística base: estimador o combinación lineal de estimadores.  
  *i*. En caso de que la estadística base sea $\overline{x}$, debemos determinar la distribución muestral de la estadística base: en nuestro caso, nos interesará saber si la distribución es normal o no y lo haremos con un Test de Shapiro Wilk siempre que el tamaño muestral sea menor a 50.  
4. Decidir el test a utilizar:
   - según distribución de $\overline{x}$ = normal: Test T de Student, no normal: Test de Wilcoxon
   - _h_ = Test $\chi^2$ de Pearson
   - $s^2$ = Test $\chi^2$ de la variancia
5. Identificar la decisión de rechazo respecto del p-value.  
6. Llevar adelante el test. 
7. Tomar un decisión y concluir en términos de la situación planteada.  
</div>

Mencionamos cinco tests que serán utilizados en nuestras pruebas de hipótesis, veamos sus características:
- Test de Shapiro Wilk: Es una prueba de normalidad cuya hipótesis nula es que *La variable presenta una distribución normal*. La función a utilizar en R es _shapiro.test(datos)_. En este caso, cuando realicemos el test y obtengamos un p>0.05, aceptaremos H0 y por lo tanto consideraremos que la variable tiene una distribución normal y realizaremos un Test T para contrastar nuestras hipótesis originales. 
- Test T de Student: Aquí contrastaremos la H0 (el parámetro es igual a cierto valor) contra H1 (el parámetro es $\neq$, > o <) para variables que tengan una distribución normal o que provengan de muestras grandes (n>50). A acontinuación vemos cómo sería el código en R.
```R
install.packages("stats") # debemos instalar la librería stats, llamarla y luego correr el test
library("stats")
t.test(datos,
       alternative = c("two.sided", "less", "greater"), #la hipótesis alternativa es bilateral ($\neq$), unilateral a la izquierda (<) o unilateral a la derecha (>)
       mu = 0, paired = FALSE, # mu= valor esperado del parámetro y paired= si las muestras están apareadas, esto proviene del diseño, lo veremos más adelante.
       conf.level = 0.95) # nivel de confianza (1-𝛼)
```
En este caso, cuando realicemos el test y obtengamos un p>0.05, aceptaremos H0 y por lo tanto consideraremos que el parámetro toma el valor planteado.
- Test de Wilcoxon: Aquí contrastaremos la H0 (el parámetro es igual a cierto valor) contra H1 (el parámetro es $\neq$, > o <) para variables que no tengan una distribución normal.
```R
wilcox.test(datos,
       alternative = c("two.sided", "less", "greater"), #la hipótesis alternativa es bilateral ($\neq$), unilateral a la izquierda (<) o unilateral a la derecha (>)
       mu = 0, paired = FALSE, # mu= valor esperado del parámetro y paired= si las muestras están apareadas, esto proviene del diseño, lo veremos más adelante.
       conf.level = 0.95) # nivel de confianza (1-𝛼)
```
- Test $\chi^2$ de Pearson: Aquí contrastaremos la H0 (el parámetro es igual a cierto valor) contra H1 (el parámetro es $\neq$, > o <) para proporciones. Es un test no paramétrico
```R
prop.test(x, n, p, # x= número observaciones exitosas, n= número de observaciones totales, p=valor de referencia
          alternative = c("two.sided", "less", "greater"), #la hipótesis alternativa es bilateral ($\neq$), unilateral a la izquierda (<) o unilateral a la derecha (>)
          conf.level = 0.95, correct = TRUE) # nivel de confianza (1-𝛼)
```
- Test $\chi^2$ de la variancia: Aquí contrastaremos la H0 (el parámetro es igual a cierto valor) contra H1 (el parámetro es $\neq$, > o <) para proporciones. Es un test no paramétrico
```R
install.packages("EnvStats") # debemos instalar la librería stats, llamarla y luego correr el test
library("EnvStats")
varTest(x,
       alternative = c("two.sided", "less", "greater"), #la hipótesis alternativa es bilateral ($\neq$), unilateral a la izquierda (<) o unilateral a la derecha (>)
       sigma.squared, # en caso de conocer la variancia poblacional, sino lo estima con su estimador puntual en la muestra ($\s^2$
       conf.level = 0.95, correct = TRUE) # nivel de confianza (1-𝛼)
```        
En este caso, cuando realicemos el test y obtengamos un p>0.05, aceptaremos H0 y por lo tanto consideraremos que el parámetro toma el valor planteado.  

Para todos los contrastes utilizaremos el ejemplo del módulo anterior:  
*"Se registraron los datos provenienientes de una muestra de 33 personas a las cuales se les midió la concentración (cc) de Vitamina D en un laboratorio clínico durante el último mes. Se sabe que en dicha población de personas, la cc **promedio** de Vitamina D es igual a 22 ng/ml con una **variabilidad** de 0.6* $ng^2$ / $ml^2$. *La recomendación es que la cc de Vitamina D sea mayor a 20 ng/ml y se supone que el 20% de las personas cumplen con la recomendación"*.  
Datos: 19.08, 16.38, 20.9, 19.09, 16.72, 22.84, 12.48, 21.57, 23.49, 17.15, 23.05, 14.73, 15.36, 16.3, 22.33, 26.7, 16.09, 11.88, 24.58, 12.37, 28.9, 15.3, 22.83, 19.86, 24.65, 17.94, 22.35, 27.6, 20.96, 12.49, 28.21, 18.5, 13.2  

Procedemos a cargar los datos y consultar un summary para chequear que no hay errores.
```R
cc_vit_D<-c(19.08, 16.38, 20.9, 19.09, 16.72, 22.84, 12.48, 21.57, 23.49, 17.15, 23.05, 14.73, 15.36, 16.3, 22.33, 26.7, 16.09, 11.88, 24.58, 12.37, 28.9, 15.3, 22.83, 19.86, 24.65, 17.94, 22.35, 27.6, 20.96, 12.49, 28.21, 18.5, 13.2)
```
```R
summary(cc_vit_D)
```
```R
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  11.88   16.09   19.09   19.57   22.84   28.90
```
## Ensayo de hipótesis para el promedio poblacional  
Propongamos el análisis siguiendo la guía para el ensayo de hipótesis:
1. En este caso de acuerdo a lo propuesto en el enunciado, podemos difinir la hipótesis nula como H0: μ=22 ng/ml;  
y tenemos las tres posibles hipótesis alternativas;  
- Hipótesis alternativa: μ $\neq$ 22 ng/ml, llamada bilateral  
- Hipótesis alternativa: μ < 22 ng/ml, llamada lateral a la izquierda  
- Hipótesis alternativa: μ > 22 ng/ml, llamada lateral a la derecha  
2. Fijar el nivel de significación: 𝛼 = 0.05.  
3. Especificar la estadística base:  $\overline{x}$ , estimador de μ. 
  *i* Determinar la distribución muestral de la estadística base: como n<50 procedemos a realizar el Test de Shapiro Wilk
```R
shapiro.test(cc_vit_D)
```
```R
	Shapiro-Wilk normality test

data:  cc_vit_D
W = 0.96323, p-value = 0.3182
```
Como el p>0.05, asumimos que la variable cc de Vitamina D tiene una distribución normal y por lo tanto procedemos a elegir el test e identificar la decisión de rechazo del test T.  
4. Decidir el test a utilizar: Test T de Student
5. Identificar la decisión de rechazo: Se rechazará la H0 si el p-value obtenido en el Test T < 0.05.  
Los puntos 6 y 7 los llevaremos adelante según la H1.

### Hipótesis bilateral
6. Llevar adelante el test:
```R
t.test(cc_vit_D,
       alternative = c("two.sided"), #la hipótesis alternativa es bilateral (μ$\neq$22)
       mu = 22, paired = FALSE, # mu= 22
       conf.level = 0.95)
```
```R
	One Sample t-test

data:  cc_vit_D
t = -2.8574, df = 32, p-value = 0.007449
alternative hypothesis: true mean is not equal to 22
95 percent confidence interval:
 17.84135 21.30289
sample estimates:
mean of x 
 19.57212
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0.007, es decir, p-value<𝛼, rechazamos H0 y aceptamos H1. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la concentración promedio de Vitamina D es distinta a 22 ng/mL.*

### Hipótesis unilateral a la derecha
6. Llevar adelante el test:
```R
t.test(cc_vit_D,
       alternative = c("greater"), #la hipótesis alternativa es unilateral a la derecha (μ>22)
       mu = 22, paired = FALSE, # mu= 22
       conf.level = 0.95)
```
```R
	One Sample t-test

data:  cc_vit_D
t = -2.8574, df = 32, p-value = 0.9963
alternative hypothesis: true mean is greater than 22
95 percent confidence interval:
 18.13283      Inf
sample estimates:
mean of x
19.57212 
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0.996 es decir, p-value>𝛼, aceptamos H0. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la concentración promedio de Vitamina D no es mayor a 22 ng/mL.*

### Hipótesis unilateral a la izquierda
6. Llevar adelante el test:
```R
t.test(cc_vit_D,
       alternative = c("less"), #la hipótesis alternativa es unilateral a la izquierda (μ<22)
       mu = 22, paired = FALSE, # mu= 22
       conf.level = 0.95)
```
```R
	One Sample t-test

data:  cc_vit_D
t = -2.8574, df = 32, p-value = 0.003725
alternative hypothesis: true mean is less than 22
95 percent confidence interval:
     -Inf 21.01141
sample estimates:
mean of x 
 19.57212 
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0.003 es decir, p-value<𝛼, rechazamos H0, aceptando H1. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la concentración promedio de Vitamina D es menor a 22 ng/mL.*  
Como era de esperarse, si el promedio es distinto de 22 y no es mayor; debía ser menor.


## Ensayo de hipótesis para la proporción poblacional  
1. En este caso de acuerdo a lo propuesto en el enunciado, podemos difinir la hipótesis nula como H0: π=0.2;  
y tenemos las tres posibles hipótesis alternativas;  
- Hipótesis alternativa bilateral: π $\neq$ 0.2
- Hipótesis alternativa unilateral a la izquierda: π < 0.2
- Hipótesis alternativa unilateral a la derecha: π > 0.2
2. Fijar el nivel de significación: 𝛼 = 0.05.  
3. Especificar la estadística base:  _h_ , estimador de π. 
4. Decidir el test a utilizar: Test $\chi^2$ de Pearson
### Hipótesis bilateral
6. Llevar adelante el test:
```R
prop.test(sum(cc_vit_D>20), 33, p=0.2,
          alternative = c("two.sided"),
          conf.level = 0.95, correct = TRUE)
```
```R
	1-sample proportions test with continuity correction

data:  sum(cc_vit_D > 20) out of 33, null probability 0.2
X-squared = 11.82, df = 1, p-value = 0.000586
alternative hypothesis: true p is not equal to 0.2
95 percent confidence interval:
 0.2853249 0.6340452
sample estimates:
        p 
0.4545455 
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0.0005, es decir, p-value<𝛼, rechazamos H0. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la proporción de personas con concentración de Vitamina D recomendada es distinta al 20%.*

### Hipótesis unilateral a la derecha
6. Llevar adelante el test:
```R
prop.test(sum(cc_vit_D>20), 33, p=0.2,
          alternative = c("greater"),
          conf.level = 0.95, correct = TRUE)
```
```R
	1-sample proportions test with continuity correction

data:  sum(cc_vit_D > 20) out of 33, null probability 0.2
X-squared = 11.82, df = 1, p-value = 0.000293
alternative hypothesis: true p is greater than 0.2
95 percent confidence interval:
 0.3072888 1.0000000
sample estimates:
        p 
0.4545455 
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0.0002 es decir, p-value<𝛼, rechazamos H0. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la proporción de personas con concentración de Vitamina D recomendada es mayor al 20%.*   
### Hipótesis unilateral a la izquierda
6. Llevar adelante el test:
```R
prop.test(sum(cc_vit_D>20), 33, p=0.2,
          alternative = c("less"),
          conf.level = 0.95, correct = TRUE)
```
```R
	1-sample proportions test with continuity correction

data:  sum(cc_vit_D > 20) out of 33, null probability 0.2
X-squared = 11.82, df = 1, p-value = 0.9997
alternative hypothesis: true p is less than 0.2
95 percent confidence interval:
 0.0000000 0.6093945
sample estimates:
        p 
0.4545455 
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0.999 es decir, p-value<𝛼, no rechazamos H0, aceptando H1. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la proporción de personas con concentración de Vitamina D recomendada no es menor al 20%.*
Como era de esperarse, la proporción es distinta al 20% y no es mayor; debía ser menor.

## Ensayo de hipótesis para la variancia poblacional  
1. En este caso de acuerdo a lo propuesto en el enunciado, podemos difinir la hipótesis nula como H0:  $σ^2$ = 0.6 $ng^2$ / $ml^2$;  
y tenemos las tres posibles hipótesis alternativas;  
- Hipótesis alternativa bilateral: $σ^2$ $\neq$ 0.6 $ng^2$ / $ml^2$, llamada   
- Hipótesis alternativa unilateral a la izquierda: $σ^2$ < 0.6 $ng^2$ / $ml^2$
- Hipótesis alternativa unilateral a la derecha: $σ^2$ > 0.6 $ng^2$ / $ml^2$
2. Fijar el nivel de significación: 𝛼 = 0.05.  
3. Especificar la estadística base:  $s^2$, estimador de $σ^2$. 
4. Decidir el test a utilizar: Test $\chi^2$ de la variancia
5. Identificar la decisión de rechazo: Se rechazará la H0 si el p-value obtenido en el Test $\chi^2$  < 0.05.  
Los puntos 6 y 7 los llevaremos adelante según la H1.

### Hipótesis bilateral
6. Llevar adelante el test:
```R
varTest(cc_vit_D, 
        alternative = "two.sided", 
        sigma.squared = 0.6,
        conf.level = 0.95)
```
```R
Results of Hypothesis Test
--------------------------

Null Hypothesis:                 variance = 0.6

Alternative Hypothesis:          True variance is not equal to 0.6

Test Name:                       Chi-Squared Test on Variance

Estimated Parameter(s):          variance = 23.82537

Data:                            cc_vit_D

Test Statistic:                  Chi-Squared = 1270.686

Test Statistic Parameter:        df = 32

P-value:                         0

95% Confidence Interval:         LCL = 15.40835
                                 UCL = 41.68288
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0, es decir, p-value<𝛼, rechazamos H0 y aceptamos H1. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la variabilidad en la concentración promedio de Vitamina D es distinta a 0.6* $ng^2$ / $ml^2$.

### Hipótesis unilateral a la derecha
6. Llevar adelante el test:
```R
varTest(cc_vit_D, 
        alternative = "greater", 
        sigma.squared = 0.6,
        conf.level = 0.95)
```
```R
Results of Hypothesis Test
--------------------------

Null Hypothesis:                 variance = 0.6

Alternative Hypothesis:          True variance is greater than 0.6

Test Name:                       Chi-Squared Test on Variance

Estimated Parameter(s):          variance = 23.82537

Data:                            cc_vit_D

Test Statistic:                  Chi-Squared = 1270.686

Test Statistic Parameter:        df = 32

P-value:                         0

95% Confidence Interval:         LCL = 16.50447
                                 UCL =      Inf
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0 es decir, p-value<𝛼, rechazamos H0. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la vaiabilidad en la concentración promedio de Vitamina D es mayor a 0.6* $ng^2$ / $ml^2$.

### Hipótesis unilateral a la izquierda
6. Llevar adelante el test:
```R
varTest(cc_vit_D, 
        alternative = "less", 
        sigma.squared = 0.6,
        conf.level = 0.95)
```
```R
Results of Hypothesis Test
--------------------------

Null Hypothesis:                 variance = 0.6

Alternative Hypothesis:          True variance is less than 0.6

Test Name:                       Chi-Squared Test on Variance

Estimated Parameter(s):          variance = 23.82537

Data:                            cc_vit_D

Test Statistic:                  Chi-Squared = 1270.686

Test Statistic Parameter:        df = 32

P-value:                         1

95% Confidence Interval:         LCL =  0.00000
                                 UCL = 37.98401
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 1 es decir, p-value>𝛼, aceptamos H0, rechazamos H1. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la vaiabilidad en la concentración promedio de Vitamina D no es menor a 0.6* $ng^2$ / $ml^2$.
Como era de esperarse, la variabilidad es distinta a 0.6 $ng^2$ / $ml^2$ y es mayor; por lo que no debía ser menor.

## Ensayo de hipótesis para el promedio poblacional cuando la estadística base que no cumple el criterio de normalidad   
Proponemos el siguiente set de datos que fueron simulados para que no tengan una distribución normal:
cc_vit_D2<-c(1.720675, 41.568301, 38.353545, 2.297701, 1.073103, 58.066633, 42.576757, 48.275281, 37.200148, 51.675629 111.510998, 54.515121, 6.432142, 88.462465, 3.249789 123.373373, 21.118178, 36.746506, 53.832461, 21.503287, 25.919496, 14.621059, 17.052441, 2.696813, 73.082098, 16.036116, 17.414659, 36.649046, 37.622159, 3.760085, 1.901215, 14.040065, 16.439864)  

1. En este caso de acuerdo a lo propuesto en el enunciado, podemos difinir la hipótesis nula como H0: μ=22 ng/ml;  
y la hipótesis alternativa será planteada en función de la *localización de los datos*. Con la intención de simplificar el análisis, vamos a decidir si el valor del parámetro (propuesto en H0) se encuentra dentro del rango de los datos observados en la muestra:
```R
range(cc_vit_D2)
```
Vemos que el rango es (1.073103; 123.373373) contiene al valor de 22 ng/ml, por lo que nos interesaría saber si el valor de la media muestral difiere o no de 22 ng/ml. Es decir, querriamos llevar adelante un test bilateral.  
2. Fijar el nivel de significación: 𝛼 = 0.05.  
3. Especificar la estadística base:  $\overline{x}$ , estimador de μ. 
  *i* Determinar la distribución muestral de la estadística base: como n<50 procedemos a realizar el Test de Shapiro Wilk
```R
shapiro.test(cc_vit_D2)
```
```R
	Shapiro-Wilk normality test

data:  cc_vit_D2
W = 0.87147, p-value = 0.00105
```
Como el p<0.05, concluimos que la variable cc de Vitamina D no tiene una distribución normal y por lo tanto procedemos a elegir el test e identificar la decisión de rechazo.  
4. Decidir el test a utilizar: Test T de Wilcoxon
5. Identificar la decisión de rechazo: Se rechazará la H0 si el p-value obtenido en el Test de Wilcoxon < 0.05. 
6. Llevar adelante el test:
```R
wilcox.test(cc_vit_D2,
       alternative = c("two.sided"), 
       mu = 22, paired = FALSE,
       conf.level = 0.95)
```
```R
	Wilcoxon signed rank exact test

data:  cc_vit_D2
V = 368, p-value = 0.1211
alternative hypothesis: true location is not equal to 22
```
7. Tomar un decisión y concluir en términos de la situación planteada: Como p = 0.1211, es decir, p-value>𝛼, no rechazamos H0. Por lo que podemos concluir:  
*Bajo la evidencia muestral y con un nivel de significación del 5%, la concentración promedio de Vitamina D no es distinta a 22 ng/mL.*  
