# Positional Encoding y Arquitectura de Transformers

Autor: _Jaime Hernández Delgado_

## 1. Introducción al Positional Encoding

El Positional Encoding (codificación posicional) constituye un elemento fundamental en la arquitectura de los modelos Transformer, una innovación que ha revolucionado el procesamiento del lenguaje natural y múltiples dominios de la inteligencia artificial. A diferencia de arquitecturas previas como las redes neuronales recurrentes (RNN) o convolucionales (CNN), los Transformers procesan todos los elementos de una secuencia en paralelo, lo que aumenta significativamente la eficiencia computacional durante el entrenamiento, pero elimina la noción intrínseca del orden secuencial que es crítica para muchas tareas.

En el procesamiento del lenguaje natural, por ejemplo, el orden de las palabras resulta crucial para determinar el significado de una oración. La frase "el gato persigue al ratón" tiene un significado completamente distinto a "el ratón persigue al gato", aunque contengan exactamente las mismas palabras. Este reto fundamental de preservar la información posicional mientras se mantiene el procesamiento paralelo se resuelve elegantemente mediante el Positional Encoding.

## 2. Fundamentos del Positional Encoding

### 2.1 Propósito y función

El Positional Encoding permite a los modelos Transformer capturar y utilizar información sobre la posición relativa o absoluta de cada elemento dentro de una secuencia. Esto se logra añadiendo información posicional directamente a la representación vectorial (embedding) de cada elemento, permitiendo que el modelo distinga entre diferentes ocurrencias del mismo token en distintas posiciones de la secuencia.

Este proceso inyecta información espacial o temporal sin sacrificar las ventajas del procesamiento paralelo, permitiendo que el modelo:

- Reconozca patrones dependientes del orden
- Capture relaciones secuenciales
- Procese correctamente estructuras gramaticales
- Mantenga coherencia narrativa en generación de texto
- Comprenda la progresión lógica en razonamientos

### 2.2 Implementación matemática

La implementación original presentada en el influyente artículo "Attention is All You Need" (Vaswani et al., 2017) utiliza funciones sinusoidales para generar vectores de posición. La elección de funciones sinusoidales no es arbitraria, sino que responde a propiedades matemáticas específicas que facilitan que el modelo pueda extrapolar a secuencias más largas que las encontradas durante el entrenamiento.

La formulación matemática precisa del Positional Encoding sinusoidal viene dada por:

$$PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d_{model}}}\right)$$

$$PE_{(pos, 2i+1)} = \cos\left(\frac{pos}{10000^{2i/d_{model}}}\right)$$

Donde:

- $pos$ representa la posición en la secuencia (iniciando en 0)
- $i$ denota la dimensión (de 0 a $d_{model}/2 - 1$)
- $d_{model}$ corresponde a la dimensionalidad del modelo o del vector de embedding

### 2.3 Visualización del Positional Encoding

Para comprender intuitivamente cómo funciona el Positional Encoding, podemos visualizarlo como una matriz donde cada fila corresponde a una posición específica en la secuencia, y cada columna representa una dimensión del vector de posición:

~~~
Posición 0: [sin(0), cos(0), sin(0), cos(0), ...]
Posición 1: [sin(ω₁·1), cos(ω₁·1), sin(ω₂·1), cos(ω₂·1), ...]
Posición 2: [sin(ω₁·2), cos(ω₁·2), sin(ω₂·2), cos(ω₂·2), ...]
~~~


Las frecuencias ω₁, ω₂, etc. varían según la dimensión, creando un patrón distintivo para cada posición. Las dimensiones con frecuencias más altas capturan cambios locales detallados, mientras que las de frecuencias más bajas conservan información sobre patrones a mayor escala.

Si visualizamos esta matriz como una imagen, podemos observar patrones claros de ondas sinusoidales que varían a lo largo de las dimensiones, permitiendo que el modelo identifique y diferencie cada posición de manera única.

## 3. Integración con la Arquitectura Transformer

El Positional Encoding no es simplemente un complemento de la arquitectura Transformer, sino un componente esencial sin el cual el modelo perdería capacidades fundamentales. Su implementación se integra orgánicamente con el resto de la arquitectura.

### 3.1 Necesidad del Positional Encoding en Transformers

Los Transformers requieren el Positional Encoding por múltiples razones críticas:

1. *Procesamiento paralelo*: Al procesar todos los tokens simultáneamente, los Transformers pierden la noción secuencial inherente que tienen las RNNs, por lo que necesitan una forma explícita de codificar la posición.
2. *Mecanismo de atención*: El mecanismo de self-attention, pilar fundamental de los Transformers, necesita información posicional para distinguir entre distintas apariciones de una misma palabra en diferentes posiciones. Sin esta información, el modelo tendría una vista "bag-of-words" (bolsa de palabras) de la entrada.
3. *Eliminación de la invariancia posicional*: Sin Positional Encoding, el Transformer sería invariante a la permutación de los elementos de entrada, lo que resulta problemático para tareas donde el orden es crucial, como el procesamiento del lenguaje natural o el análisis de series temporales.
4. *Jerarquía temporal*: Permite capturar dependencias a diferentes escalas temporales o secuenciales, desde relaciones locales hasta patrones globales en la secuencia.

### 3.2 Integración en el flujo de datos

En la arquitectura Transformer, el Positional Encoding se suma directamente a los embeddings de entrada antes de que estos pasen a través de las capas de atención y feed-forward:

1. Los tokens de entrada se convierten primero en vectores densos mediante una capa de embedding.
2. Se generan los vectores de Positional Encoding correspondientes a cada posición.
3. Estos vectores se suman a los embeddings de los tokens: Embedding_final = Token_embedding + Positional_encoding
4. El resultado combinado atraviesa las múltiples capas del Transformer.

Esta integración aditiva, en lugar de concatenativa, mantiene constante la dimensionalidad de los vectores y permite que la información posicional fluya a través de todas las capas del modelo, influenciando cada cálculo de atención y transformación feed-forward.

## 4. Arquitectura Completa de los Transformers
La arquitectura Transformer ha demostrado ser extraordinariamente versátil y potente, sirviendo como base para modelos que han redefinido el estado del arte en múltiples dominios. Su diseño modular y su capacidad para capturar dependencias a larga distancia han catalizado una revolución en la inteligencia artificial.

### 4.1 Componentes principales

#### 4.1.1 Estructura Encoder-Decoder

La arquitectura original del Transformer incluye un encoder (codificador) y un decoder (decodificador), aunque muchos modelos modernos utilizan configuraciones adaptadas:

- *Encoder*: Procesa la secuencia de entrada completa y genera representaciones contextualizadas de alta dimensionalidad. Modelos basados exclusivamente en el encoder, como BERT, son especialmente efectivos para tareas de comprensión.
- *Decoder*: Toma las representaciones generadas por el encoder y produce secuencialmente la salida. Modelos basados únicamente en el decoder, como GPT, destacan en tareas generativas.
- *Modelos encoder-decoder completos*: Utilizados para tareas de traducción, resumen o cualquier transformación secuencia a secuencia, como T5 o BART.

#### 4.1.2 Embedding Layer

La capa de embedding convierte tokens discretos (palabras, subpalabras, caracteres) en vectores densos continuos de alta dimensionalidad. Estos vectores iniciales capturan similitudes semánticas básicas entre tokens, que luego se enriquecen con contexto a través de las capas del modelo.

En modelos modernos, estos embeddings suelen compartirse entre el encoder y el decoder, lo que reduce el número de parámetros y proporciona una base semántica común.

#### 4.1.3 Multi-Head Attention

El mecanismo de atención constituye el núcleo revolucionario de los Transformers, permitiendo modelar dependencias directas entre cualquier par de posiciones en la secuencia, independientemente de su distancia. La atención multi-cabeza amplía esta capacidad permitiendo al modelo atender simultáneamente a diferentes patrones y aspectos de la información:

*Multi-Head Attention*:

En lugar de realizar un único cálculo de atención con vectores de alta dimensionalidad, el modelo divide los vectores en múltiples "cabezas" que operan en paralelo y luego concatena los resultados:

$$\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, \text{head}_2, ..., \text{head}_h)W^O$$

$$\text{donde head}_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)$$

Esta estructura permite que diferentes cabezas se especialicen en distintos tipos de relaciones:

- Algunas cabezas pueden enfocarse en relaciones sintácticas
- Otras pueden captar patrones semánticos
- Otras pueden aprender a seguir referencias anafóricas
- Algunas pueden especializarse en relaciones a corta distancia mientras otras capturan dependencias más globales

#### 4.1.5 Normalización y Conexiones Residuales

Para facilitar el entrenamiento de redes profundas, los Transformers emplean:

- *Layer Normalization*: Normaliza las activaciones para cada posición, estabilizando los gradientes y acelerando el entrenamiento. Se aplica después de cada sublayer.

$$\text{LayerNorm}(x) = \gamma \cdot \frac{x - \mu}{\sqrt{\sigma^2 + \epsilon}} + \beta$$

Donde $\mu$ y $\sigma$ son la media y desviación estándar calculadas sobre las dimensiones del embedding para cada posición.

- *Conexiones Residuales*: Cada sublayer está envuelta en una conexión residual, permitiendo que la información fluya directamente a través de múltiples capas. Esto mitiga el problema del desvanecimiento del gradiente y facilita el entrenamiento de arquitecturas profundas.

$$\text{Output} = \text{LayerNorm}(x + \text{Sublayer}(x))$$

### 4.2 Flujo de información en el Transformer completo

El proceso completo de un Transformer encoder-decoder sigue estos pasos:

1. *Preprocesamiento de entrada*:
    - Tokenización del texto de entrada
    - Conversión a embeddings vectoriales
    - Suma con el Positional Encoding
2. *Procesamiento en el Encoder*:
    - Paso a través de N bloques idénticos
    - Cada bloque contiene:
        - Multi-Head Self-Attention (donde cada token atiende a todos los tokens de entrada)
        - Feed-Forward Network
        - Conexiones residuales y Layer Normalization

3. *Procesamiento en el Decoder*:
    - Desplazamiento de la secuencia objetivo (para entrenamiento autoregresivo)
    - Paso a través de N bloques idénticos
    - Cada bloque contiene:
        - Multi-Head Self-Attention enmascarada (para prevenir atención a posiciones futuras)
        - Multi-Head Cross-Attention (atendiendo a la salida del encoder)
        - Feed-Forward Network
        - Conexiones residuales y Layer Normalization

4. *Generación de salida*:
    - Proyección lineal al tamaño del vocabulario
    - Aplicación de softmax para obtener distribuciones de probabilidad
    - Selección del token más probable o muestreo según la distribución


## 5. Conclusiones

El Positional Encoding ilustra cómo una solución elegante a un problema aparentemente simple (la incorporación de información posicional) puede habilitar capacidades transformadoras. A medida que los modelos continúan evolucionando, es probable que veamos refinamientos adicionales de este mecanismo fundamental, permitiendo a los Transformers abordar tareas cada vez más complejas y variadas.

## Bibliografía

~~~
bibtex
@article{vaswani2017attention,
  author = {Vaswani, Ashish and Shazeer, Noam and Parmar, Niki and Uszkoreit, Jakob and Jones, Llion and Gomez, Aidan N. and Kaiser, Łukasz and Polosukhin, Illia},
  title = {Attention is all you need},
  journal = {Advances in Neural Information Processing Systems},
  volume = {30},
  year = {2017},
  url = {https://arxiv.org/abs/1706.03762}
}

@article{devlin2018bert,
  author = {Devlin, Jacob and Chang, Ming-Wei and Lee, Kenton and Toutanova, Kristina},
  title = {BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding},
  journal = {arXiv preprint arXiv:1810.04805},
  year = {2018},
  url = {https://arxiv.org/abs/1810.04805}
}

@article{shaw2018self,
  author = {Shaw, Peter and Uszkoreit, Jakob and Vaswani, Ashish},
  title = {Self-Attention with Relative Position Representations},
  journal = {Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies},
  year = {2018},
  url = {https://arxiv.org/abs/1803.02155}
}

@article{su2021roformer,
  author = {Su, Jianlin and Lu, Yu and Pan, Shengfeng and Wen, Bo and Liu, Yunfeng},
  title = {RoFormer: Enhanced Transformer with Rotary Position Embedding},
  journal = {arXiv preprint arXiv:2104.09864},
  year = {2021},
  url = {https://arxiv.org/abs/2104.09864}
}

@article{dai2019transformer,
  author = {Dai, Zihang and Yang, Zhilin and Yang, Yiming and Carbonell, Jaime and Le, Quoc V. and Salakhutdinov, Ruslan},
  title = {Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context},
  journal = {Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics},
  year = {2019},
  url = {https://arxiv.org/abs/1901.02860}
}

@article{kazemnejad2019:pencoding,
  title = {Transformer Architecture: The Positional Encoding},
  author = {Kazemnejad, Amirhossein},
  journal = {kazemnejad.com},
  year = {2019},
  url = {https://kazemnejad.com/blog/transformer_architecture_positional_encoding/}
}

@article{dosovitskiy2020image,
  author = {Dosovitskiy, Alexey and Beyer, Lucas and Kolesnikov, Alexander and Weissenborn, Dirk and Zhai, Xiaohua and Unterthiner, Thomas and Dehghani, Mostafa and Minderer, Matthias and Heigold, Georg and Gelly, Sylvain and others},
  title = {An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale},
  journal = {arXiv preprint arXiv:2010.11929},
  year = {2020},
  url = {https://arxiv.org/abs/2010.11929}
}

@article{press2021train,
  author = {Press, Ofir and Smith, Noah A. and Lewis, Mike},
  title = {Train Short, Test Long: Attention with Linear Biases Enables Input Length Extrapolation},
  journal = {arXiv preprint arXiv:2108.12409},
  year = {2021},
  url = {https://arxiv.org/abs/2108.12409}
}

@article{huang2020improve,
  author = {Huang, Cheng-Zhi Anna and Vaswani, Ashish and Uszkoreit, Jakob and Shazeer, Noam and Hawthorne, Curtis and Dai, Andrew M. and Hoffman, Matthew D. and Roberts, Adam and Eck, Douglas},
  title = {Music Transformer: Generating Music with Long-Term Structure},
  journal = {International Conference on Learning Representations},
  year = {2020},
  url = {https://arxiv.org/abs/1809.04281}
}
~~~
