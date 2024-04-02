#Overfitting, Underfitting, Precision y Recall

<span style="font-size: 0.8rem; font-style: italic;">Por Roberto Campos Espejo y Javier</span>

##Introducción
Como ya sabemos, el machine learning funciona dándole al programa ejemplos para que aprenda de ellos. Por lo tanto es muy importante asegurarse de que los datos aportados al programa son correctos, y es que un mal uso de los datos puede provocar que obtengamos malos resultados, como por ejemplo si hacemos overfitting o underfitting de los datos. Para conseguir un buen funcionamiento es necesario que nuestro programa consiga un equilibrio entre overfitting y underfitting y para esto debemos conseguir que nuestro programa sea capaz de generalizar, por ejemplo, si estamos haciendo un algoritmo que identifique perros, debemos ofrecer suficiente información como para que el programa sea capaz de identificar un perro, incluso aunque sea de una raza que no se le ha aportado en su entrenamiento, y poder discernir qué un gato no es un perro, aunque comparta características similares como las cuatro patas.

Si los datos que le aportamos a nuestro programa son pocos esta no será capaz de generalizar el conocimiento, esto es el underfitting. Y si le otorgamos varios datos, pero todos iguales entre sí, tampoco será capaz de generalizar el conocimiento y esto es el overfitting. A continuación mostraremos un ejemplo gráfico, y procederemos a explicar con más detalle overfitting y underfitting.

