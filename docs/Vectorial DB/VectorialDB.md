# Bases De Datos Vectoriales

Por Nicolás Ildefonso Sirvent Orts

## ¿Qué es una base de datos vectorial?
Una base de datos vectorial es un sistema de almacenamiento diseñado para guardar y buscar información basándose en su significado profundo y no solo en palabras clave exactas. En lugar de tablas tradicionales, organiza los datos (como texto, imágenes o audio) como coordenadas matemáticas en un espacio de miles de dimensiones. Su utilidad principal reside en la búsqueda semántica: permite que las aplicaciones entiendan el contexto, conecten ideas similares y sirvan como una memoria externa ultra rápida para modelos de inteligencia artificial, siendo la pieza clave detrás de los buscadores inteligentes, sistemas de recomendación y asistentes como ChatGPT.

Para entender como es que funcionan estas bases de datos con esteroides primero tenemos que entender el valor con el que trabajan.

# ¿Qué es un embedding?
Un embedding es un vector (lista de numeros) que sirve para representar a un objeto, como una palabra o un texto, de forma que **un modelo** pueda entenderlo. Estos números no se eligen al azar, funcionan como una "firma numérica" o una dirección en un mapa gigante. Lo más importante de un embedding es que, si dos objetos se parecen en el mundo real, sus listas de números también serán numéricamente parecidas.

Bueno ya sabemos que un embedding es un vector númerico, pero, ¿que criterio se usa en su creación para que sean capaces de calificar?

La respuesta corta es, ninguno. 
Un embedding es el resultado de las neuronas de la última capa oculta de una red neuronal ya entrenada. Los modelos que emplean este tipo de bases de datos, se caraterizan por ser capaces de clusterizar (agrupar) datos teniendo en cuenta el contexto en el que se encuentran. No es lo mismo decir que: "estoy sentado en un **banco**" a "voy a robar un **banco**". Aunque cabe la posibilidad de que la segunda se refiera a un banco de un parque, en los entrenamientos no se suele dar este significado, por lo que los embeddings de estos sinonimos serán completamente diferentes.

### Trade-off
Este vector nos ayuda mucho al representar las palabras de forma numérica. No obstante, depende completamente del clustering que haga el modelo, esto implica que este embedding será compatible únicamente con un modelo equivalente entrenado por el mismo dataset. Por lo que un embedding realmente es, una interpretación de información de un agente en concreto impulsada por un entrenamiento posterior.


Sabemos que és un embedding, pero que puedo hacer con una secuencia de números que a simple vista parecen puestos por un randomizer.


# Similitud entre vectores

En una base de datos vectorial, la similitud entre dos objetos se define por la proximidad geométrica de sus embeddings. Debido a que la red neuronal asigna coordenadas basadas en la relación semántica, los conceptos con significados o características análogas generan vectores que se agrupan en regiones cercanas del espacio latente.
Para cuantificar esta semejanza, se emplean diferentes métricas matemáticas que determinan qué tan cerca está un vector de otro:

### Similitud del Coseno ($\cos \theta$)

Esta métrica calcula el coseno del ángulo formado por dos vectores. A diferencia de otras medidas, no considera la longitud (magnitud) de los vectores, sino únicamente su dirección.
- Uso principal: Procesamiento de Lenguaje Natural (NLP) y búsqueda semántica.
- Conveniencia: Es ideal cuando el contenido es lo importante y no su extensión. Por ejemplo, permite que un artículo largo y un resumen corto sobre el mismo tema sean considerados similares.
- Ecuación:$$\text{sim}(\mathbf{A}, \mathbf{B}) = \frac{\mathbf{A} \cdot \mathbf{B}}{\|\mathbf{A}\| \|\mathbf{B}\|}$$

![No se pudo cargar la imagen](data:image/png;base64,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)

### Distancia Euclídea ($L2$)

Mide la distancia física en línea recta entre dos puntos en el espacio multidimensional. Es la métrica más intuitiva, pero es muy sensible a la magnitud de los datos.
- Uso principal: Visión artificial, biometría y detección de duplicados exactos.
- Conveniencia: Es preferible cuando las diferencias exactas en los valores de las dimensiones son críticas, como en el reconocimiento facial, donde pequeños cambios en las coordenadas representan rasgos distintos.
- Ecuación:$$d(\mathbf{A}, \mathbf{B}) = \sqrt{\sum_{i=1}^{n} (a_i - b_i)^2}$$
  

![No se pudo cargar la imagen](data:image/png;base64,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)

### Producto Escalar (Dot Product)

Multiplica las magnitudes de dos vectores por el coseno del ángulo que los separa. A diferencia del coseno, esta métrica sí se ve afectada por la longitud de los vectores.
- Uso principal: Sistemas de recomendación y algoritmos de ranking.
- Conveniencia: Se utiliza cuando tanto la dirección del interés como la "intensidad" o relevancia del objeto son importantes. Por ejemplo, en una tienda online, puede priorizar productos que tienen más interacciones (magnitud alta).
- Ecuación:$$\mathbf{A} \cdot \mathbf{B} = \sum_{i=1}^{n} a_i b_i$$

![No se pudo cargar la imagen](data:image/png;base64,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)

### Enlace de Interés
https://projector.tensorflow.org/

# Indexación: Algoritmo HNSW

Si tenemos 10 millones de vectores de 1536 dimensiones, compararlos uno por uno contra una consulta (búsqueda por fuerza bruta o Flat Search) requeriría un tiempo de procesamiento inasumible para aplicaciones en tiempo real. Necesitamos una estructura que permita encontrar los "vecinos más cercanos" sin tener que evaluarlos todos.

HNSW (Hierarchical Navigable Small Worlds) es un algoritmo basado en grafos jerárquicos. Su estrategia consiste en crear una red de caminos donde cualquier nodo puede alcanzar a otro en muy pocos pasos. Combina dos conceptos clave:

- Small Worlds: Grafos donde la mayoría de los nodos no son vecinos, pero se puede llegar de uno a otro mediante un número pequeño de saltos.

- Jerarquía: Una estructura de capas similar a una Skip List, donde las capas superiores son "vías rápidas" y las inferiores contienen el detalle total.


#### El Proceso de Inserción
Cuando un nuevo vector llega a la base de datos, el algoritmo debe decidir dónde colocarlo y con quién conectarlo:
1. Asignación de Capa: Mediante un cálculo probabilístico, se le asigna al vector una "capa máxima". La mayoría de los vectores se quedan en la Capa 0 (la base), y solo unos pocos llegan a las capas superiores.
2. Búsqueda de Vecinos: Empezando desde la capa más alta, el algoritmo busca el punto más cercano al nuevo vector.
3. Establecimiento de Vínculos ($M$): En cada capa donde el vector debe existir, se conecta con sus $M$ vecinos más cercanos.
4. Heurística de Selección: El algoritmo no siempre elige a los más cercanos "puros", a veces prefiere vecinos que ayuden a "expandir" la red en diferentes direcciones para asegurar que el grafo sea navegable y no queden zonas aisladas.

[![No se pudo cargar el video](https://www.pinecone.io/_next/image/?url=https%3A%2F%2Fcdn.sanity.io%2Fimages%2Fvr8gru94%2Fproduction%2Fd6e3a660654d9cb55f7ac137a736539e227296b6-1920x1080.png&w=3840&q=75)](https://www.youtube.com/watch?v=QvKMwLjdK-s)

# Cuantización de Producto (PQ)

Un embedding estándar (por ejemplo, de 1536 dimensiones en formato float32) ocupa unos 6 KB. Aunque parece poco, una base de datos con 100 millones de vectores requeriría más de 600 GB de memoria RAM solo para almacenar los vectores, sin contar la estructura del grafo HNSW. La Cuantización de Producto (PQ) reduce este consumo drásticamente transformando vectores pesados en códigos compactos.

### Proceso de Compresión

La técnica PQ descompone el problema de la compresión en tres pasos fundamentales:
1. Segmentación (Splitting): El vector original se divide en $M$ trozos o sub-vectores iguales. Por ejemplo, un vector de 1024 dimensiones se puede dividir en 8 trozos de 128 dimensiones cada uno.
2. Cuantización por Sub-espacio: Para cada uno de los 8 trozos, el sistema ya ha entrenado previamente un "catálogo" (llamado Codebook) con 256 variantes típicas (centroides).
3. Asignación de IDs: Cada trozo del vector original se compara con los 256 candidatos de su catálogo correspondiente. En lugar de guardar los 128 números decimales del trozo, solo guardamos el ID (un solo byte, de 0 a 255) del candidato que más se le parece.

Resultado: El vector original de 1024 números decimales se convierte en una combinación de los identificadores.

### Cálculo de Distancia

Una de las mayores ventajas de PQ es que permite calcular distancias sin necesidad de descomprimir los vectores a su estado original. Este proceso se conoce como ADC (Asymmetric Distance Computation):

1. Pre-cálculo: Cuando el usuario realiza una consulta, el sistema compara el vector de búsqueda (que está completo, sin comprimir) contra los 256 candidatos de cada uno de los 8 catálogos.
2. Tabla de Distancias: Se genera una pequeña tabla con estos resultados.
3. Suma de IDs: Para saber la distancia entre la consulta y cualquier vector de la base de datos, el sistema solo tiene que mirar los 8 IDs del vector guardado, buscar sus valores en la tabla de pre-cálculo y sumarlos.

Este método es extremadamente rápido, ya que sustituye cálculos matemáticos complejos por simples consultas a una tabla y sumas de enteros.

[![No se pudo cargar el video](https://www.pinecone.io/_next/image/?url=https%3A%2F%2Fcdn.sanity.io%2Fimages%2Fvr8gru94%2Fproduction%2F0425edbee092b14b4a6a32cfb50e99a1971399ba-1920x1080.gif&w=3840&q=75)](https://www.youtube.com/watch?v=BMYBwbkbVec&t=11s)

# Filtrado por metadatos: Búsqueda Híbrida

La búsqueda híbrida combina la similitud semántica (vectores) con filtros de atributos tradicionales (metadatos). 
El reto técnico es integrar estos filtros sin degradar la eficiencia del algoritmo HNSW.
Estrategias de Filtrado:
- Post-filtering: Se realiza la búsqueda vectorial y luego se descartan los resultados que no cumplen los metadatos.
  - Riesgo: Puede devolver menos resultados de los solicitados ($K$) si los vecinos más cercanos no cumplen el filtro.
- Pre-filtering: Se filtran los datos primero y luego se busca entre los supervivientes.
  - Riesgo: Si el filtro es muy estricto, el grafo HNSW se fragmenta, obligando al sistema a realizar una búsqueda lineal lenta.
- In-search Filtering: El filtro se aplica en tiempo real mientras el HNSW navega por el grafo.
  - Ventaja: Es la opción más eficiente; garantiza encontrar los $K$ resultados exactos manteniendo la velocidad logarítmica del grafo.


Una vez entendidas las bases de datos vectoriales vemos la función más extendida de estas.

# RAG: Retrieval-Augmented Generation
El RAG es una arquitectura que permite a un Modelo de Lenguaje (LLM), como GPT-4 o Claude, consultar una base de datos externa en tiempo real antes de responder. En lugar de confiar solo en lo que aprendió durante su entrenamiento, la IA consulta sus embeddings almacenados para la generación de promps con memoria.

### Workflow

1. Recuperación (Retrieval): Cuando el usuario hace una pregunta, esta se convierte en un embedding. El sistema usa el HNSW (para navegar rápido) y el PQ (para ahorrar memoria) para encontrar los fragmentos de texto más parecidos en la base de datos.

2. Aumentación (Augmentation): Los fragmentos encontrados (párrafos de manuales, PDFs, chats) se extraen del disco y se pegan junto a la pregunta original del usuario.

3. Generación (Generation): El LLM recibe un "super-prompt" que dice: "Basándote exclusivamente en este contexto que te paso, responde a la pregunta", generando así prompts mejorados a la vez que consigue un mayor contexto en su base de datos.

## Recomenendaciones bases de datos vectoriales
- Pinecone (Recomendada)
  >*pip install pinecone-client*
- ChromaDB (Recomendada)
  >*pip install chromadb*
- Weaviate
  >*docker run -p 8080:8080 -p 50051:50051 cr.weaviate.io/semitechnologies/weaviate:1.36.6*
- PostgreSQL (con extension pgvector) 
  >*sudo apt-get install postgresql-server-dev-all*
  *git clone https://github.com/pgvector/pgvector.git*
  *cd pgvector*
  *make*
  *sudo make install*

# Referencias
[Pinecone vector-similarity](https://www.pinecone.io/learn/vector-similarity/)
[Proyector de embeddings](https://projector.tensorflow.org/)
[Info embeddings](https://cohere.com/blog/embeddings)
[Video HNSW](https://www.youtube.com/watch?v=QvKMwLjdK-s)
[info HNSW](https://www.pinecone.io/learn/series/faiss/hnsw/)
[info busqueda híbrida](https://weaviate.io/blog/hybrid-search-explained)
[info RAG](https://blogs.nvidia.com/blog/what-is-retrieval-augmented-generation/)
[infp PQ](https://www.pinecone.io/learn/series/faiss/product-quantization/)
[video PQ](https://www.youtube.com/watch?v=BMYBwbkbVec&t=11s)
