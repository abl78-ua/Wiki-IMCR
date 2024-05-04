#Overfitting y Underfitting

<span style="font-size: 0.8rem; font-style: italic;">Por Roberto Campos Espejo y Javier Sánchez Felipe</span>

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

##Detección del overfitting y underfitting
Existen varias técnicas para detectar la presencia de overfitting y underfitting.
- **Curva de error de entrenamiento:** Muestra cómo el error del modelo disminuye a medida que se entrena con los datos de entrenamiento. Si la curva sigue disminuyendo incluso después de alcanzar un punto óptimo, es indicio de overfitting.
- **Curvas de aprendizaje planas:** Las curvas de aprendizaje que muestran un error constante o una disminución lenta sugieren que el modelo no está mejorando con el entrenamiento, por lo tanto es una señal de underfitting.
- **Curva de error de validación:** Similar a la curva de error de entrenamiento, pero utilizando datos de validación. Si la curva de error de validación comienza a aumentar después de alcanzar un mínimo, mientras que la curva de error de entrenamiento sigue disminuyendo, es una señal de overfitting.

  <figure markdown="span">
    <img src="../../images/overfitting/img1.webp">
</figure>[5][6]
  









##Referencias

[1] https://www.ibm.com/es-es/topics/overfitting#:~:text=El%20%22overfitting%22%20o%20sobreajuste%20es,a%20sus%20datos%20de%20entrenamiento. 

[2] https://es.wikipedia.org/wiki/Sobreajuste 

[3] https://gamco.es/glosario/underfitting/#:~:text=Underfitting%20es%20un%20t%C3%A9rmino%20utilizado,se%20ajusta%20adecuadamente%20a%20ellos. 

[4]https://protecciondatos-lopd.com/empresas/underfitting/ 

[5]https://www.aprendemachinelearning.com/que-es-overfitting-y-underfitting-y-como-solucionarlo/

[6]https://link.springer.com/article/10.1007/s10270-008-0106-z



