#Overfitting, Underfitting, Precision y Recall

<span style="font-size: 0.8rem; font-style: italic;">Por Roberto Campos Espejo y Javier</span>

##Overfitting y Underfitting
Como ya sabemos, el machine learning funciona dándole al programa ejemplos para que aprenda de ellos. Por lo tanto es muy importante asegurarse de que los datos aportados al programa son correctos, y es que un mal uso de los datos puede provocar que obtengamos malos resultados, como por ejemplo si hacemos overfitting o underfitting de los datos. Para conseguir un buen funcionamiento es necesario que nuestro programa consiga un equilibrio entre overfitting y underfitting y para esto debemos conseguir que nuestro programa sea capaz de generalizar, por ejemplo, si estamos haciendo un algoritmo que identifique perros, debemos ofrecer suficiente información como para que el programa sea capaz de identificar un perro, incluso aunque sea de una raza que no se le ha aportado en su entrenamiento, y poder discernir qué un gato no es un perro, aunque comparta características similares como las cuatro patas.

Si los datos que le aportamos a nuestro programa son pocos esta no será capaz de generalizar el conocimiento, esto es el underfitting. Y si le otorgamos varios datos, pero todos iguales entre sí, tampoco será capaz de generalizar el conocimiento y esto es el overfitting. A continuación mostraremos un ejemplo gráfico, y procederemos a explicar con más detalle overfitting y underfitting.

<figure markdown="span">
    <img src="../../images/overfitting/overfitting-underfitting-machine-learning.png">
</figure>[5][6]

###Overfitting
El overfitting es un suceso que ocurre cuando se ajusta con exactitud un modelo estadístico. Lejos de beneficiar al análisis de los datos,esto perjudica al entrenamiento del modelo, al no permitirle clasificar con rigor los datos y llegar a aprender información irrelevante que perjudica al resultado. 

El overfitting (sobreajuste, en español) en el aprendizaje automático sucede cuando se entrena en exceso un algoritmo de aprendizaje. El algoritmo se entrena pasándole una serie de datos junto con el resultado esperado y así el algoritmo va aprendiendo y mejorando sus resultados. El problema aparece cuando el algoritmo se entrena en exceso y queda ajustado a una características muy específicas. Esto ocasiona que al usar datos diferentes puede mostrar un resultado erróneo en situaciones más genéricas. Para que un modelo sea correcto no es necesario que se ajuste a la perfección, sólo que tenga un índice de error aceptable para la resolución del algoritmo. 
[1]
[2]

###Underfitting
Underfitting (subajuste, en español) es un término que se utiliza en el aprendizaje automático para definir un modelo incapaz de capturar de forma precisa la complejidad de los datos de entrenamiento, lo que conlleva a tener un modelo demasiado simple e ineficiente, incapaz de hacer predicciones precisas ni aprender patrones importantes en los datos.
Este suceso puede ocurrir debido al uso de una secuencia de datos ineficiente, falta de entrenamiento o un mal proceso del entrenamiento, entre otros. 
Este tipo de problemas se puede solucionar intensificando el nivel de entrenamiento o usando una mayor cantidad de datos, entre otros. 
[3]
[4]

##Precision y Recall
Para evaluar completamente la efectividad de un modelo, debes examinar la precisión y el recall. Normalmente, una mejora de la precisión suele reducir el recall, y viceversa. Para entender estos conceptos, vamos a explicar más detalladamente que son la precisión y el recall.
<figure markdown="span">
    <img src="../../images/overfitting/dos.svg.png">
</figure>[9]


###Precision
El concepto fue propuesto inicialmente por Salton, quién era un especialista en la recuperación de información y el proceso de lenguaje natural. La precisión es el ratio de valores relevantes frente al número de valores recuperados. Así pues, cuanto más se aleje el valor obtenido de nulo mayor será la cantidad de información recuperada que resulte relevante. En caso de que sea 1 toda la información recuperada sería relevante y si fuera 0 ninguno de los datos recuperados nos serviría. 
Su definición es la siguiente:
Precisión = True Positive / Actual Results or True Positive / True Positive + False Positive
<figure markdown="span">
    <img src="../../images/overfitting/3">
</figure>

###Recall
El ratio que representa este concepto es la proporción de documentos recuperados frente a la cantidad de documentos relevantes existentes, siendo independientes a estos últimos.
Si el resultado es 1 quiere decir que se ha encontrado todo documento relevante que estaba en los documentos existentes, en caso de 0 significa que los documentos no tienen ninguna relevancia.

Su definición es la siguiente:
Recall = True Positive / Predicted Results or True Positive / True Positive + False Negative
<figure markdown="span">
    <img src="../../images/overfitting/4">
</figure>
[7][8]

###Ejemplo
Los dos conceptos pueden resultar útiles en los casos en los que haya datos desequilibrados.

Vamos a mostrar un ejemplo para facilitar el entendimiento. 
Imaginemos que, de 10000 casos, solo 100 son positivos, el resto de los 900 son negativos, y queremos predecir cuáles son positivos. Para esto elegimos, por ejemplo, 200 para poder englobar la mayoría de los 100 casos positivos. A esos 200 les aplicamos las fórmulas ya mencionadas y obtenemos los siguientes resultados.
<figure markdown="span">
    <img src="../../images/overfitting/tabla_pred">
</figure>

Como podemos comprobar, los resultados se dividen de la siguiente manera:

-True Negative: predicción y caso negativo.

-True Positive: predicción y caso positivo.

-False Negative: predicción negativa y caso positivo.

-False Positive: predicción positiva y caso negativo.


Tras esto solo nos queda definir los resultados.
La precisión es 60 de 200, un 30%.
El recall es 60 de 100, un 60%. [10]


Por último, vamos a hacer otro ejemplo, uno donde se ilustre mejor la tensión que hay entre la precisión y el recall, pudiendo observar más fácilmente como una disminuye si la otra mejora y viceversa.

La siguiente imagen muestra 30 predicciones realizadas por un modelo de clasificación de correo electrónico. A la derecha del umbral se clasifica el spam, a la izquierda lo que no es spam. 
<figure markdown="span">
    <img src="../../images/overfitting/ejemplo1">
</figure>
Vamos a calcular la precision y el recall como hemos hecho antes.
<figure markdown="span">
    <img src="../../images/overfitting/ejta1">
</figure>
Como ya hemos explicado, la precisión mide el porcentaje de correos electrónicos marcados como spam que se clasificaron correctamente, es decir, el porcentaje de puntos a la derecha del umbral que aparecen en verde en la imágen anterior.

Precisión= (VP)/(VP+FP)=0,8

Y el recall mide el porcentaje de correos reales que se clasificaron correctamente, es decir, el porcentaje de puntos a la izquierda del umbral que aparecen en verde.

Recall=(VP)/(VP+FN)=0.73

Ahora vamos a mostrar el mismo ejemplo aumentando el umbral. 
<figure markdown="span">
    <img src="../../images/overfitting/ejemplo2">
</figure>
En este aso obtenemos una precisión de 0.88 y un recall de 0.64.
Por último, vamos a mostrar qué ocurre si disminuimos el umbral.
<figure markdown="span">
    <img src="../../images/overfitting/ejemplo4">
</figure>
Y en este caso la precisión sería de 0.75 y el recall de 0.82. [11]







##F1-Score
Por último, hablaremos de F1 score. 
F1 score es una métrica de evaluación de machine learning que mide la precisión del modelo, combinando la precisión y el recall del modelo.

Esta se calcula como la media armónica de los puntajes de precisión y recuperación, como se muestra a continuación. Varía de 0 a 100% donde a más alto el puntaje más alto de F1 denota un clasificador de mejor calidad. Se usa la media armónica en lugar de la aritmética ya que esta penaliza más fuertemente los valores extremadamente bajos. Por lo tanto, un puntaje más alto de F1 indica que el clasificador tiene un mejor equilibrio entre precisión y recuperación, lo que generalmente se interpreta como una mejor calidad en la capacidad del clasificador para identificar correctamente las clases de interés.
<figure markdown="span">
    <img src="../../images/overfitting/f1">
</figure>
[12]

F1-score da una idea general del desempeño de la prueba en función de su sensibilidad y su valor predictivo positivo. Según el resultado, tal y como hemos explicado anteriormente, cuanto más alto sea el resultado mejor capacidad tendrá.
F1-score normalmente presenta un balance equilibrado entre los parámetros, pero en ocasiones, puede interesarnos priorizar uno sobre otro. En ese caso, utilizamos Fβ, que usa a beta de forma que el recall se considera beta veces tan importante como la precisión, quedando la siguiente fórmula:
<figure markdown="span">
    <img src="../../images/overfitting/f2">
</figure>
En casos de falso positivo o falso negativo la fórmula quedaría así:
<figure markdown="span">
    <img src="../../images/overfitting/f3">
</figure>
Valores comunes para beta son:
- 2: Pesa el reacall más que la precisión
- 0,5: Pesa menos el recall que la precisión.
Esta medida se basa en la medida de eficacia de Van Rijsbergen:
<figure markdown="span">
    <img src="../../images/overfitting/f4">
</figure>
Su relación es Fβ = 1 - E dónde:
<figure markdown="span">
    <img src="../../images/overfitting/f5">
</figure>
[13]
[14]


##Relación
La alta precisión en un conjunto combinada con una baja precisión en el conjunto de prueba, es un indicio de overfitting.
De manera similar, el recall puede verse afectado por el overfitting . Si el modelo tiene un sobreajuste puede perderse al clasificar algunas instancias positivas, creando falsos negativos, disminuyendo así el recall del conjunto de prueba.
En el caso de underfitting, al tratarse de un modelo demasiado simple puede perderse de clasificar correctamente tanto instancias positivas como negativas, resultando en una baja precisión y recall.  Al no capturar los patrones subyacentes en los datos, el modelo con underfitting puede crear resultados inconsistentes y erróneos, afectando negativamente tanto a la precisión como al recall.











##Referencias

[1] https://www.ibm.com/es-es/topics/overfitting#:~:text=El%20%22overfitting%22%20o%20sobreajuste%20es,a%20sus%20datos%20de%20entrenamiento. 

[2] https://es.wikipedia.org/wiki/Sobreajuste 

[3] https://gamco.es/glosario/underfitting/#:~:text=Underfitting%20es%20un%20t%C3%A9rmino%20utilizado,se%20ajusta%20adecuadamente%20a%20ellos. 

[4]https://protecciondatos-lopd.com/empresas/underfitting/ 

[5]https://www.aprendemachinelearning.com/que-es-overfitting-y-underfitting-y-como-solucionarlo/

[6]https://link.springer.com/article/10.1007/s10270-008-0106-z

[7]https://es.wikipedia.org/wiki/Precisi%C3%B3n_y_exhaustividad 

[8]https://es.wikipedia.org/wiki/Gerard_Salton

[9]https://en.wikipedia.org/wiki/Precision_and_recall 

[10]https://medium.com/@gogasca_/precisi%C3%B3n-y-recuperaci%C3%B3n-precision-recall-dc3c92178d5b

[11]https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall?hl=es-419

[12]https://www.v7labs.com/blog/f1-score-guide#:~:text=The%20F1%20score%20is%20calculated,simple%20arithmetic%20or%20geometric%20means%3F

[13]https://www.cienciasinseso.com/f1_score/ 

[14]https://en.wikipedia.org/wiki/F-score 



