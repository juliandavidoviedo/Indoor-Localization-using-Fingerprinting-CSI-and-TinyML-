# Guía de Edge Impulse

Este documento detalla el proceso de trabajo en **Edge Impulse** para entrenar y desplegar un modelo de Machine Learning en la placa **XIAO ESP32S3** utilizando **TinyML**. Siga esta guía paso a paso, desde el registro en Edge Impulse hasta el despliegue del modelo entrenado.

---

## Índice
1. [Registro en Edge Impulse](#registro-en-edge-impulse)
2. [Creación de un Proyecto](#creación-de-un-proyecto)
3. [Recolección de Datos](#recolección-de-datos)
4. [Entrenamiento del Modelo](#entrenamiento-del-modelo)
5. [Evaluación del Modelo](#evaluación-del-modelo)
6. [Implementación del Modelo](#implementación-del-modelo)
7. [Despliegue en el Dispositivo](#despliegue-en-el-dispositivo)
8. [Pruebas y Ajustes Finales](#pruebas-y-ajustes-finales)

---

### 1. Registro en Edge Impulse

1. Dirígete a [Edge Impulse](https://www.edgeimpulse.com/) y selecciona **Sign Up**.
2. Ingresa tus datos o regístrate usando cuentas de Google o GitHub.
3. Una vez registrado, accede a tu perfil y configura tu información de usuario.  
![image](https://github.com/user-attachments/assets/997548eb-be9c-49f5-a9ac-f4cc86a06ba4)

   > *Sugerencia*: Puedes incluir una imagen del proceso de registro en esta sección para facilitar la navegación a usuarios nuevos.

### 2. Creación de un Proyecto

1. En el panel principal de Edge Impulse, haz clic en **Create new project**.
2. Asigna un nombre descriptivo a tu proyecto (por ejemplo, “Indoor Localization CSI”) y selecciona el dispositivo de destino.
3. Haz clic en **Create Project** para guardar. Ahora verás un panel con varias opciones para gestionar tu proyecto.

   > *Nota*: Puedes capturar una imagen de la pantalla de creación de proyecto y agregarla aquí como referencia.

### 3. Recolección de Datos

1. En el menú del proyecto, selecciona **Data Acquisition**.
2. Conecta la **XIAO ESP32S3** al ordenador y asegúrate de que esté configurada en modo de comunicación adecuado.
3. **Método de adquisición**:
   - **Directo desde el dispositivo**: Si deseas recolectar datos en tiempo real, selecciona tu dispositivo en **Device** y sigue las instrucciones.
   - **Importación de archivos**: Si ya tienes un dataset, selecciona **Upload files** para cargar datos en formato `.csv`, `.json` u otros soportados.

4. Una vez conectados, sigue los pasos de configuración de Edge Impulse para obtener los datos de **Fingerprinting CSI** (señal de información de canal) para entrenamiento.
   
   > *Consejo*: Es útil incluir una imagen de la pantalla de adquisición de datos y una muestra de la estructura del dataset para dar contexto.

### 4. Entrenamiento del Modelo

1. Ve a **Impulse Design** > **Create Impulse**:
   - **Input Block**: Define el tipo de datos de entrada (e.g., imágenes, señales de audio, etc.)
   - **Processing Block**: Selecciona el bloque de procesamiento más adecuado (e.g., Spectrogram, FFT) para los datos de CSI.
   - **Learning Block**: Selecciona un algoritmo de clasificación adecuado, como **KNN**, **Random Forest**, o una **CNN** si estás utilizando imágenes espectrales.

2. Configura los parámetros del modelo según los datos recolectados. Edge Impulse proporciona configuraciones predeterminadas que puedes ajustar para mejorar el rendimiento.

3. Haz clic en **Start training** y permite que Edge Impulse entrene el modelo utilizando tus datos.

   > *Ejemplo*: Agrega imágenes de la sección de diseño de impulso y entrenamiento para ilustrar el proceso.

### 5. Evaluación del Modelo

1. En **Model Testing**, sube un conjunto de datos de prueba para evaluar la precisión del modelo entrenado.
2. Observa métricas clave como **precisión**, **recall** y **F1-score**.
3. Ajusta los hiperparámetros si los resultados no cumplen con los criterios esperados, y entrena nuevamente el modelo.

   > *Consejo*: Incluye una captura de pantalla de los resultados de evaluación del modelo.

### 6. Implementación del Modelo

1. Ve a **Deployment** y selecciona el formato de salida adecuado para la **XIAO ESP32S3**. Edge Impulse te permite exportar el modelo en varios formatos, como **C++ library**, **WebAssembly** o **TensorFlow Lite**.
2. Selecciona **Arduino library** si estás utilizando el **Arduino IDE** o **PlatformIO** para cargar el modelo en la XIAO ESP32S3.
3. Haz clic en **Build** para generar el archivo descargable que contiene el modelo entrenado.

   > *Nota*: Incluye un enlace al archivo exportado o una captura de pantalla de la configuración de despliegue para mayor claridad.

### 7. Despliegue en el Dispositivo

1. Abre **Arduino IDE** o **PlatformIO** en tu ordenador.
2. Conecta la **XIAO ESP32S3** y asegúrate de que esté configurada en el puerto correcto.
3. En Arduino IDE:
   - Ve a **Sketch** > **Include Library** > **Add .ZIP Library…** y selecciona la biblioteca exportada desde Edge Impulse.
   - Carga el código en la XIAO ESP32S3 utilizando el ejemplo de inferencia de la biblioteca.

4. En PlatformIO, agrega el archivo en la carpeta **lib** y utiliza el ejemplo de inferencia para realizar predicciones con el modelo desplegado.

   > *Consejo*: Añade una captura de pantalla del monitor serial mostrando el despliegue del modelo en la XIAO ESP32S3 para demostrar que funciona correctamente.

### 8. Pruebas y Ajustes Finales

1. **Prueba en Tiempo Real**: Con el monitor serial en Arduino o PlatformIO, verifica que el modelo responde como se espera en diversas condiciones.
2. **Optimización**: Si el modelo no cumple con las expectativas, ajusta el preprocesamiento de los datos o retrena con una mayor cantidad de datos.
3. **Documentación de Resultados**: Guarda y documenta los resultados de las pruebas para futuras referencias o ajustes.

---

## Recursos y Documentación Adicional

- [Documentación de Edge Impulse](https://docs.edgeimpulse.com/)
- [Ejemplos de TinyML](https://github.com/tinyML/examples)
- [Tutorial de Edge Impulse para Arduino](https://docs.edgeimpulse.com/docs/deployment-runners/arduino-deployment)

---

## Conclusión

Esta guía proporciona todos los pasos necesarios para llevar un modelo de Machine Learning desde el entrenamiento hasta el despliegue en la XIAO ESP32S3 usando Edge Impulse.
