
# Indoor-Localization-using-Fingerprinting-CSI-and-TinyML

Localización en espacios cerrados utilizando fingerprinting y TinyML. Aquí encontrarás una estructura detallada del proyecto dirigida a los usuarios que quieran implementar **Edge Impulse** con la **XIAO ESP32S3** y **TinyML** para una aplicación de localización en interiores basada en el modelo de fingerprinting.

---

# Edge Impulse con XIAO ESP32S3 y TinyML

Este repositorio contiene una guía para implementar un modelo **TinyML** entrenado en **Edge Impulse** y ejecutarlo en la placa **Seeed XIAO ESP32S3**, lo que permite realizar inferencias de ML en tiempo real en el borde. 

## Tabla de Contenidos
1. [Descripción](#descripción)
2. [Requisitos](#requisitos)
3. [Instalación](#instalación)
4. [Estructura del Repositorio](#estructura-del-repositorio)
5. [Configuración del Hardware](#configuración-del-hardware)
6. [Uso del Proyecto](#uso-del-proyecto)
7. [Conjuntos de Datos](#conjuntos-de-datos)
8. [Contribuir](#contribuir)
9. [Licencia](#licencia)

---

## Descripción

Este proyecto permite entrenar un modelo de Machine Learning en **Edge Impulse** y desplegarlo en la placa **XIAO ESP32S3** utilizando **TinyML**. Este repositorio está dirigido a aplicaciones de localización en interiores utilizando señales de fingerprinting basadas en la información de canal (CSI). Ideal para implementaciones que necesiten eficiencia energética y procesamiento local en tiempo real, el proyecto puede aplicarse a monitoreo ambiental, detección de movimiento, y más.

El repositorio incluye:
- Código para cargar el modelo y ejecutar inferencias en la XIAO ESP32S3.
- Instrucciones de hardware y configuración de sensores.
- Documentación de entrenamiento y despliegue del modelo usando Edge Impulse.

---

## Requisitos

### Hardware
- [Seeed XIAO ESP32S3](https://www.seeedstudio.com/XIAO-ESP32S3-p-5320.html)
- Sensores o antenas compatibles para la captura de CSI
- Cables y protoboard para conexiones

### Software
- [Edge Impulse](https://www.edgeimpulse.com/) para entrenamiento de modelos
- [Arduino IDE](https://www.arduino.cc/en/software) o [PlatformIO](https://platformio.org/) para carga de código en la XIAO ESP32S3
- Controladores y librerías `Edge Impulse SDK` para Arduino o ESP-IDF

---

## Instalación

### Paso 1: Clonar el repositorio
   ```bash
   git clone https://github.com/tu_usuario/edge-impulse-xiao-esp32s3-tinyml.git
   cd edge-impulse-xiao-esp32s3-tinyml
   ```

### Paso 2: Configurar el entorno
   - **Arduino IDE**: Instala la biblioteca de **Edge Impulse** desde el gestor de bibliotecas.
   - **PlatformIO**: En `platformio.ini`, agrega:
     ```ini
     lib_deps = 
        edgeimpulse/ei-edge-impulse-sdk@^1.0.0
     ```

### Paso 3: Entrenamiento en Edge Impulse
   - Ve a [Edge Impulse](https://studio.edgeimpulse.com/), crea un proyecto y sigue las instrucciones para recolectar datos de señales (por ejemplo, CSI), entrenar y exportar el modelo.

### Paso 4: Cargar el modelo en XIAO ESP32S3
   - Copia el código exportado en el directorio `src/`.
   - Conecta la XIAO ESP32S3 a tu PC y carga el código desde Arduino IDE o PlatformIO.

---

## Estructura del Repositorio

Este repositorio incluye la siguiente estructura:

```plaintext
.
├── docs/                       # Documentación técnica y explicaciones detalladas
├── edge_impulse/               # Guía de implementación de clasificación de sonido
│   ├── training_data/          # Conjunto de datos de entrenamiento
│   ├── pre-processing/         # Scripts y guías de preprocesamiento
├── src/                        # Código fuente para ejecución en XIAO ESP32S3
├── tests/                      # Resultados y pruebas del modelo de clasificación
│   ├── metrics/                # Métricas de rendimiento (precisión, recall)
└── README.md
```

Cada carpeta contiene información y pasos para facilitar la reproducción del proyecto:

- **/docs**: Información técnica del hardware y configuración de CSI.
- **/edge_impulse**: Guía de entrenamiento en Edge Impulse y preprocesamiento.
- **/tests**: Resultados documentados de las pruebas de modelo.

---

## Configuración del Hardware

1. **Conexiones del Sensor**:  
   Conecta los sensores a los pines correctos de la **XIAO ESP32S3**. Consulta el esquema en [docs/connections.png](./docs/connections.png) para ver el diagrama.

2. **Alimentación**:  
   La XIAO ESP32S3 puede alimentarse desde el puerto USB; asegúrate de que los sensores tengan la potencia correcta.

---

## Uso del Proyecto

1. **Inferencias en Tiempo Real**:
   Abre el monitor serial en Arduino IDE o PlatformIO para ver las predicciones del modelo.

2. **Actualización de Modelos**:
   Para entrenar un nuevo modelo, sube datos a **Edge Impulse**, entrena el modelo, y exporta el nuevo archivo para la XIAO ESP32S3.

---

## Conjuntos de Datos

1. **Dataset de Localización en Interiores (CSI/Fingerprinting)**:
   - [Indoor User Movement Prediction from CSI](https://archive.ics.uci.edu/ml/datasets/Wireless+Indoor+Localization)  
     (UCI Machine Learning Repository): contiene datos de localización basados en fingerprinting que podrían adaptarse para clasificar ubicaciones en interiores.
   
2. **Edge Impulse Public Dataset Library**:
   - Explora la biblioteca de datasets públicos de Edge Impulse para ver si alguno se ajusta a tu proyecto. Puedes encontrar datos preprocesados y listos para utilizar en proyectos TinyML.

---

## Contribuir

Para contribuir:
1. Haz un **fork** del repositorio.
2. Crea una rama:
   ```bash
   git checkout -b nombre-rama
   ```
3. Realiza los cambios y abre un **pull request**.

---

## Licencia

Este proyecto está bajo la Licencia MIT.
