# Anti-Spoofing en Reconocimiento Facial

## Introducción

El anti-spoofing es un conjunto de técnicas cuyo objetivo es evitar la suplantación de identidad, especialmente en sistemas de reconocimiento facial. Hoy en día, con el avance de la inteligencia artificial y la facilidad para obtener imágenes o vídeos de una persona en internet, este tipo de fraudes se ha vuelto cada vez más accesible para cualquiera.

Por eso, en los sistemas biométricos modernos es fundamental contar con mecanismos que permitan distinguir entre una cara real y una imagen, vídeo o incluso una máscara hiperrealista. En este post voy a explicar los tipos de ataques que existen, cómo se pueden detectar y qué soluciones se están usando actualmente.

## Cuerpo Teórico

### Tipos de Spoofing en Cámaras

Aquí os dejo los ataques más típicos que se intentan hacer en sistemas de reconocimiento facial, sobre todo en cámaras:

- **Print Attack:** Consiste en mostrar una foto impresa de una persona frente a la cámara para intentar suplantarla.
- **Record Attack:** Es parecido al anterior, pero en vez de una foto se utiliza un vídeo de la persona.
- **Mask Attack:** Este es el más complicado de detectar porque se usan máscaras de silicona muy realistas que imitan a la perfección los rasgos de una cara.

Se pueden entrenar redes neuronales para detectar los ataques Print y Record con bastante éxito, pero para los de tipo Mask se necesitan sensores adicionales como infrarrojos o detección de profundidad, ya que visualmente son muy difíciles de diferenciar.

### Datasets

Para entrenar estos sistemas se usan datasets especializados, que recopilan imágenes o vídeos de caras reales y de ataques. Estos datasets incluyen anotaciones, que son etiquetas o descripciones asociadas a cada imagen o vídeo indicando, por ejemplo, si es una imagen real o falsa, el tipo de ataque que representa (print, vídeo, máscara, etc.) o incluso la calidad de la iluminación, la posición de la cara, etc. Estas anotaciones son clave para que los modelos aprendan a diferenciar correctamente los distintos casos.

Aquí os dejo algunos ejemplos y una tabla donde se comparan por número de sujetos, año de lanzamiento, si son de vídeos (V) o imágenes (I), y el tipo de anotaciones que incluyen:

<img src="../../images/seguridad/infoDatasets" alt="Información Datasets" style="width:400px; vertical-align:middle;">

A día de hoy, uno de los mejores y más recientes es el **CelebA-Spoof**, ya que incluye distintos tipos de ataques y un montón de anotaciones útiles para entrenar modelos más precisos.
## Usos y Aplicación

El anti-spoofing se usa sobre todo en:

- Sistemas de desbloqueo facial en móviles.
- Control de accesos en aeropuertos o edificios.
- Autenticación en apps bancarias.
- Verificación de identidad en procesos online.

En cualquier lugar donde se use una cámara para validar la identidad de una persona, es recomendable tener un sistema anti-spoofing implementado para evitar fraudes.

## Implementación / Ejecución

Para implementar un sistema de detección anti-spoofing se suelen usar redes convolucionales (CNN) y frameworks como PyTorch o TensorFlow. En el proyecto de [hairymax/Face-AntiSpoofing](https://github.com/hairymax/Face-AntiSpoofing) por ejemplo, se utiliza un modelo basado en RGB para detectar intentos de spoofing. Aquí os dejo una muestra de resultados de detección:


<img src="../../images/seguridad/anotaciones" alt="anotaciones" style="width:400px; vertical-align:middle;">

También se pueden ver ejemplos y notebooks prácticos en esta [demo interactiva](https://nbviewer.org/gist/hairymax/021a8cd550a3c0fa14c8e6ae815265c9).

## Referencias

- [CelebA-Spoof Dataset](https://github.com/ZhangYuanhan-AI/CelebA-Spoof/tree/master?tab=readme-ov-file)
- [Papers With Code: Face Anti-Spoofing](https://paperswithcode.com/task/face-anti-spoofing)
- [Proyecto hairymax/Face-AntiSpoofing](https://github.com/hairymax/Face-AntiSpoofing?tab=readme-ov-file)
- [Demo interactiva de detección](https://nbviewer.org/gist/hairymax/021a8cd550a3c0fa14c8e6ae815265c9)
- [Artículo: Anti-Spoofing en Reconocimiento Facial](https://medium.com/@fractal.ai/face-anti-spoofing-fas-101-using-rgb-images-e73a48e1dd9)
- [Blog de IDNow sobre detección de fraude](https://www.idnow.io/blog/fraud-detection-anti-spoofing-facial-recognition/)
- [Vídeo explicativo en YouTube](https://www.youtube.com/watch?v=UiK1aIjOBlQ)
