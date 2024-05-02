#Métricas de evaluación

<span style="font-size: 0.8rem; font-style: italic;">Por Roberto Campos Espejo y Javier Sánchez Felipe</span>

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


##Referencias

[7]https://es.wikipedia.org/wiki/Precisi%C3%B3n_y_exhaustividad 

[8]https://es.wikipedia.org/wiki/Gerard_Salton

[9]https://en.wikipedia.org/wiki/Precision_and_recall 

[10]https://medium.com/@gogasca_/precisi%C3%B3n-y-recuperaci%C3%B3n-precision-recall-dc3c92178d5b

[11]https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall?hl=es-419

[12]https://www.v7labs.com/blog/f1-score-guide#:~:text=The%20F1%20score%20is%20calculated,simple%20arithmetic%20or%20geometric%20means%3F

[13]https://www.cienciasinseso.com/f1_score/ 

[14]https://en.wikipedia.org/wiki/F-score 


