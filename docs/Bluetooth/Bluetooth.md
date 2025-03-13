# Bluetooth

## 1. Introducción a Bluetooth
**Bluetooth** es una tecnología inalámbrica de corto alcance que permite la comunicación entre diversos dispositivos electrónicos, como teléfonos, computadoras y auriculares, sin necesidad de cables.

El origen se remonta en 1994, cuando la empresa sueca **Ericsson** comenzó a desarrollar una solución para conectar dispositivos móviles sin cables. El nombre "Bluetooth" proviene del rey vikingo **Harald "Blåtand" (Bluetooth) Gormsson**, quien unificó tribus en el siglo X, simbolizando la idea de unir tecnologías. En 1998, Ericsson se unió a IBM, Intel, Nokia y Toshiba para formar el Bluetooth Special Interest Group (SIG), una organización que desde entonces ha liderado su desarrollo y estandarización.

- **Bluetooth 1.0 (1999):** Esta primera versión oficial fue básica, con velocidades de hasta 721 kbps con un alcance de unos 10m. No era muy estable.
- **Bluetooth 2.0 + EDR (2004):** Se introdujo *Enhanced Data Rate (EDR)*, trplicando la velocidad hasta 3 Mbps.
- **Bluetooth 3.0 + HS (2009):** Con *High Speed (HS)*, se alcanzaron velocidades de hasta 24 Mbps al usar Wi-Fi como complemento.
- **Bluetooth 4.0 (2010):** Marcó un hito con *Bluetooth Low Energy (BLE)*, optimizado para dispositivos de bajo consumo, abriendo puertas al *Internet de las Cosas (IOT)*.
- **Bluetooth 5.0 (2016):** Duplicó la velocidad (hasta 2 Mbps en modo BLE), cuadruplicó el alcance (hasta 240 metros en condiciones ideales) y mejoró la capacidad de transmisión.

Bluetooth se ha convertido en una herramienta esencial gracias a su versatilidad y facilidad de uso. Algunos ejemplos destacados son:

- **Audio inalámbrico:** Es ampliamente usado para conectar auriculares, audífonos y altavoces portátiles a teléfonos o computadoras. Por ejemplo, escuchar música o hacer llamadas sin cables es una de sus aplicaciones más comunes.
- **Transferencia de datos:** Aunque menos frecuente hoy debido a la nube, sigue siendo útil para compartir fotos, contactos o documentos entre dispositivos cercanos.
- **Conectividad en automóviles:** Permite sincronizar teléfonos con sistemas de manos libres en autos para realizar llamadas, reproducir música o usar GPS sin distracciones.
- **Dispositivos inteligentes:** IoT en el hogar, conecta termostatos, bombillas, cerraduras y cámaras a teléfonos o asistentes como Alexa...etc.
- **Wearables:** Relojes inteligentes, pulseras de actividad...etc.

## 2. Fundamentos Técnicos
Bluetooth opera en dos modos principales: **Bluetooth Classic** y **Bluetooth Low Energy (BLE)**. Ambos comparten la misma banda de frecuencia (2.4 GHz), pero difieren en diseño, propósito y funcionamiento técnico.

### 2.1. Bluetooth Classic
- **Propósito:** Diseñado para conexiones continuas y transmisión de datos de mayor ancho de banda.
- **Características técnicas:** 
    - Velocidad: Hasta 3 Mbps.
    - Alcance: Aproximadamente 10 metros.
    - Consumo: Alto.
- **Ejemplos de uso:** Auriculares estéreo, altavoces inalámbricos, transferencia de archivos entre teléfonos...
- **Limitaciones:** No es eficiente para dispositivos con batería limitada debido a su alto consumo continuo.

![Transferencia Bluetooth](https://mike.miracomosehace.com/uploads/images/content/image_1585333369.jpg)
### 2.2. Bluetooth Low Energy (BLE)
- **Propósito:** Optimizado para comunicaciones esporádicas ideales para el Internet de las Cosas (IoT) y wearables.
- **Características técnicas:** 
    - Velocidad: Hasta 2 Mbps.
    - Alcance: Aproximadamente 240 metros (En condiciones ideales).
    - Consumo: Muy bajo, gracias a su modo de "reposo" entre transmisiones.
- **Ejemplos de uso:** Sensores (temperatura, ritmo cardíaco), rastreadores (AirTags), dispositivos médicos...
- **Limitaciones:** No es eficiente para dispositivos con batería limitada debido a su alto consumo continuo.

![AirTag](https://th.bing.com/th/id/R.63dc77da91ed3130a5cec04c5c22a63c?rik=lyICk1%2fVLsc2fg&pid=ImgRaw&r=0)
### 2.3. Cómo funciona: Protocolos y capas
#### Protocolos de nivel superior:
- **RFCOMM: (Radio Frequency Communication)** Proporciona una interfaz de comunicación serial virtual.
- **SDP (Service Discovery Protocol):** Permite a los dispositivos descubrir servicios disponibles (ej., audio, impresión).
- **ATT (Attribute Protocol):** Usado en BLE para definir atributos (datos) en un formato ligero.
- **GATT (Generic Attribute Profile):** Construido sobre ATT, organiza datos en servicios y características (ej., medir batería o temperatura).
- **SPP (Serial Port Profile):** Es un perfil de Bluetooth Classic que emula mediante RFCOMM un puerto serial. Simula que los dispositivos estan conectados por un cable serial.
- **SMP (Security Manager Protocol):** Protocolo usado para gestionar la seguridad y el emparejamiento entre dispositivos. Usa el cifrado AES-CCM.
- **GAP (Generic Access Profile):** Perfil fundamental, ya que define las reglas básicas de cómo los dispositivos se descubren.

#### Capa L2CAP:
La capa L2CAP (Logical Link Control and Adaptation Protocol) multiplexa datos entre protocolos superiores, segmenta paquetes y asegura la calidad de servicio.

#### Capa de enlace (Link Layer):
- Gestiona la conexión entre dispositivos (emparejamiento, autenticación).
- En Bluetooth clásico actua como *maestro-esclavo*, un dispositivo maestro controla múltiples esclavos. 
- En BLE actua como cliente-servidor.

![Modos Bluetooth](https://www.wikiversus.com/informatica/bluetooth-classic-vs-bluetooth-low-energy/img/_hu9e9108e4b68a91855005075bdc2e6d1c_120927_5777e0ecf8aa925d120ff716d04d0715.jpg)
### 2.4. Perfiles y estándares (GATT, GAP, etc.)

## 3. Bluetooth en el Desarrollo de Aplicaciones
- ### 3.1. ¿Por qué usar Bluetooth en apps?
- ### 3.2. Casos de uso comunes
- ### 3.3. Requisitos y permisos en móviles (Android/iOS)
- ### 3.4. Herramientas y bibliotecas populares

## 4. Ejemplos de Proyectos
- Control de dispositivos IoT.
- Transferencia de datos entre dispositivos.
- Aplicaciones de salud (monitoreo con wearables).

## 5. Limitaciones y Desafíos
- Compatibilidad entre dispositivos.
- Seguridad y privacidad.
- Debugging y testing.

## 6. Referencias