Por Cristopher Soto

##¿Qué es una red neuronal convolucional CNN?
Las Redes Neuronales Convolucionales (CNNs) son un tipo de red neuronal de aprendizaje profundo que imita al cortex visual del ojo humano para reconocer objetos en imágenes. Dicho de otro modo, son un tipo de red neuronal muy efectivas para tareas de visión artificial, incluyendo la clasificación y segmentación de imágenes aunque se pueden utilizar en otras áreas.

##¿De qué constan?
Las redes neuronales convucionales constan de múltiples capas interconectadas, incluyendo capas convolucionales y capas completamente conectadas. En las capas convolucionales, se extraen características como líneas, curvas, y formas simples, mientras que en las capas más profundas se reconocen características complejas como rostros o siluetas de animales. Cada neurona artificial, o perceptrón, procesa datos de entrada y produce una salida, contribuyendo al proceso de detección y reconocimiento de objetos en las imágenes. Estas redes pueden tener decenas o cientos de capas, cada una aprendiendo a detectar diferentes características de una imagen mediante la aplicación de filtros con distintas resoluciones. Las características extraídas se combinan en capas completamente conectadas para obtener el resultado deseado, como la clasificación de la imagen en una determinada clase.

##Arquitectura
La arquitectura de una CNN consta de una capa de entrada, una o varias capas ocultas y una capa de salida. Estas capas realizan operaciones como convolución, activación (ReLU) (la cual es una función no lineal que se aplica después de la convolución, manteniendo los valores positivos y estableciendo los valores negativos en cero permitiendo un entrenamiento más rápido y eficaz de la red) y agrupación para procesar los datos de entrada y extraer características relevantes, esto simplifica la salida de las capas convolucionales mediante la reducción no lineal de la tasa de muestreo disminuyendo el número de parámetros que la red debe aprender y ayuda a prevenir el sobreajuste.

##Tipos de capas
En una CNN podemos encontrarnos con 5 tipos de capas:
    - **Capa de entrada (Input Layer)**: Esta capa recibe la imagen original y la pasa a través de la red. Puede incluir operaciones de preprocesamiento, como normalización de píxeles.

    - **Capas convolucionales (Convolutional Layers)**: Estas capas aplican filtros convolucionales a la imagen para extraer características locales. Cada filtro detecta patrones específicos, como bordes o texturas.

    - **Capas de agrupación (Pooling Layers)**: Después de las capas convolucionales, se aplican capas de agrupación para reducir la resolución espacial y extraer características más generales.

    - **Capas completamente conectadas (Fully Connected Layers)**: Estas capas procesan las características extraídas y las utilizan para realizar la clasificación final. La última capa completamente conectada produce las probabilidades de clase.

    - **Capa de salida (Output Layer)**: La capa de salida emite las probabilidades de cada clase (por ejemplo, “gato”, “perro”, “coche”, etc.).

<figure markdown="span">
    <img alt="CNN" src="../../images/CNN/CNN.png">
</figure>

##Extracción de características
En esta fase, las capas convolucionales y de reducción de muestreo se alternan para disminuir la dimensionalidad de los datos y detectar características complejas. Las neuronas convolucionales realizan operaciones sobre los datos de imagen utilizando núcleos de convolución para filtrar la imagen y resaltar ciertas características. Por otro lado, las neuronas de reducción de muestreo reducen la resolución de los datos, lo que permite una mayor tolerancia a perturbaciones en los datos de entrada.

##Clasificación final
Finalmente, las neuronas de clasificación realizan la clasificación final sobre las características extraídas, utilizando pesos y funciones de activación para calcular la salida de cada neurona. Este proceso de aprendizaje automático permite que la CNN aprenda a reconocer patrones y características en las imágenes de forma automatizada, sin necesidad de definir manualmente los filtros. En resumen, las CNNs son poderosas herramientas para tareas de visión por computadora, demostrando cómo el aprendizaje profundo puede automatizar tareas complejas en el procesamiento de imágenes.

##Referencias
https://es.wikipedia.org/wiki/Red_neuronal_convolucional
https://wiki-imcr.vercel.app/Presentaciones/CNN
https://www.ibm.com/es-es/topics/convolutional-neural-networks
https://es.mathworks.com/discovery/convolutional-neural-network.html
Arquitecturas de redes neuronales populares - Promptengineer
Imagen CNN https://www.researchgate.net/figure/Figura-2-Arquitectura-CNN-implementada_fig2_359262472
