# Modulo 2: Ensayos de hipótesis en base a una muestra.  
Las pruebas o ensayos de hipótesis, junto con la estimación de parámetros trabajada en el módulo anterior, son herramientas muy utilizadas en el contexto de la inferencia estadística.  
Los ensayos de hipótesis nos permiten tomar decisiones acerca del valor de un parámetro a partir de los datos provenientes de una muestra.  
A través de ejemplos iremos presentando las distintas hipótesis para cada parámetro.  
Recordemos que un parámetro es una medida resumen de una característica poblacional. Por ejemplo: _concentración promedio de Vitamina D en personas rosarinas mayores a 18 años_; _proporción de personas que son alérgicas a la penicilina en la ciudad de San Lorenzo_; _variabilidad del pH del agua del río Paraná_.  
Retomando lo trabajado en el módulo anterior:  
<div align="center">
| Parámetro a estimar |Estimación puntual|
|:---------------------------------:|:---------------------------------:|
|Promedio poblacional: μ | $\overline{x}$ |

| Parámetro a estimar |Estimación puntual|
|:---------------------------------:|:---------------------------------:|
|Variancia poblacional: $σ^2$ | $s^2$ |

| Parámetro a estimar |Estimación puntual|
|:---------------------------------:|:---------------------------------:|
|Proporción: *π* | _h_ |
</div>  

## Palabras claves   
- Hipótesis: enunciado positivo o confirmación sobre el valor de uno o varios parámetros. Por ejemplo: *La concentración promedio de Vitamina D en personas rosarinas mayores a 18 años es mayor a 20 ng/mL* ; _La proporción de personas que son alérgicas a la penicilina en la ciudad de San Lorenzo es igual a 10%_; _La variabilidad del pH del agua del río Paraná es menor a 0.5_.  
Podríamos reescribir formalmente las hipótesis anteriores según:  
μ>20 ng/ml ; π = 0.01 ; $σ^2$ < 0.5  
</div>  
- Hipótesis nula: se considera a la afirmación inicial, basara en estudios previos y que corresponde al estado actual del conocimiento. **Generalmente** se plantea en términos de una igualdad.  
- Hipótesis alternativa: se considera a la afirmación que quiero contrastar y contradice a la hiptótesis nula. **Generalmente** se plantea en terminos de desigualdad.
- p-value: a los fines de este curso lo interpretaremos como la probabilidad de rechazar la hipótesis nula, siendo cierta. **Generalmente** se busca que sea un valor pequeño (p<0.05).  
- Potencia: a los fines de este curso la interpretamos como la probabilidad de rechazar la hipótesis nula, siendo falsa. Es decir, tomar la decisión correcta.  

## Promedio poblacional  
Puede suceder que queramos contrastar si el promedio poblacional es igual (=) a un valor, contra la propuesta de que sea mayor (>), menor (<) o distinto (!=) de dicho valor. A continuación trabajaremos con un ejemplo para cada caso.
Utilizaremos los datos provenienientes de una muestra de 32 personas a las cuales se les midió la concentración (cc) de Vitamina D en un laboratorio clínico durante el último mes. Se sabe que en dicha población de personas, la cc **promedio** de Vitamina D es igual a 22 ng/ml.  
En este caso;  
- Hipótesis nula: μ=22 ng/ml  
y tenemos las posibles hipótesis alternativas;  
- Hipótesis alternativa A: μ $!=$ 20 ng/ml, llamada bilateral  
- Hipótesis alternativa B: μ < 20 ng/ml, llamada lateral a la izquierda  
- Hipótesis alternativa C: μ > 20 ng/ml, llamada lateral a la derecha
Antes de pasar al contraste, debemos corroborar un supuesto que nos hará decidir qué test utilizar: el supuesto de normalidad.
Para ello utilizaremos el test de Shapiro que, como todo test, tiene una hipótesis nula y es que la variable tiene una distribución normal. En caso de que se cumpla el supuesto de normalidad (p-value>0.05), aplicaremos la función t.test. Si en cambio el supuesto de normalidad **no** se cumple utilizaremos 

```R
cc_vit_D<-c(19.08,16.38,20.9,19.09,16.72,22.84,12.48,21.57,23.49,17.15,23.05,14.73,15.36,22.33,26.7,16.09,11.88,24.58,12.37,28.9,15.3,22.83,19.86,24.65,17.94,22.35,27.6,20.96,12.49,28.21,21.96,21.09)
```



Normalidad (shapiro.test)
Comparación (ttest, wilcox.test)
