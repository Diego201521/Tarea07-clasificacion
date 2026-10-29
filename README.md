# Convolución y clasificación de imágenes con MNIST

Práctica de visión por computadora para inspeccionar filtros convolucionales de un modelo preentrenado con MNIST, visualizar sus respuestas y clasificar diez imágenes de dígitos descargadas de internet.

## Contenido

- [`notebook.ipynb`](notebook.ipynb): desarrollo de los ejercicios, visualizaciones, predicciones, tratamiento de imágenes y conclusiones.
- [`instrucciones.md`](instrucciones.md): requisitos originales de la actividad.
- [`imagenes/`](imagenes/): diez imágenes `img0.jpg` a `img9.jpg`, cada una con un dígito del 0 al 9.

## Requisitos y ejecución

El archivo [`requirements.txt`](requirements.txt) especifica las dependencias del cuaderno. Se recomienda Python 3.9, como indica el archivo de requisitos. Desde la raíz del repositorio, crea un entorno virtual e instala las dependencias:

```powershell
py -3.9 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Abre `notebook.ipynb` en VS Code con la extensión Jupyter, selecciona el entorno `.venv` como kernel y ejecuta las celdas en orden. Se requiere conexión a internet la primera vez para descargar el modelo Keras preentrenado y los datos de MNIST. El modelo se guarda como `mnist_model.h5`, archivo que no se versiona.

## Tratamiento y alcance de las imágenes

El modelo trabaja con imágenes de dígitos en escala de grises, de 28 × 28 píxeles, con fondo oscuro, trazo claro e intensidades entre 0 y 1. El cuaderno abre cada archivo con Pillow, convierte la imagen a escala de grises, invierte el contraste cuando el borde es claro, recorta el contorno del dígito, lo ajusta proporcionalmente a 20 × 20 y lo centra en un lienzo de 28 × 28. El formato se detecta a partir del contenido, no de la extensión: aunque los archivos tienen extensión `.jpg`, se comprobó que `img6.jpg` contiene datos WebP. Pillow permite leerlo sin que falle la decodificación JPEG. Las clases predichas para `img0` a `img9` se comparan con los dígitos indicados en sus nombres. También se visualizan diez kernels y sus convoluciones sobre una imagen MNIST y sobre `img0.jpg`.

Las imágenes representan los dígitos del 0 al 9, pero son diseños descargados de internet y algunos estilos difieren de los ejemplos manuscritos de MNIST. La exactitud sobre estas diez imágenes describe únicamente este conjunto pequeño; no debe generalizarse al desempeño del modelo.

## Resultados verificados

Se ejecutó el cuaderno con TensorFlow 2.10.1 y los archivos actuales. El modelo obtuvo una exactitud de `0.9935` sobre el conjunto de prueba MNIST. Sobre las diez imágenes descargadas, la exactitud fue `70 %`; las predicciones, en orden de `img0.jpg` a `img9.jpg`, fueron `9, 1, 2, 3, 4, 0, 6, 8, 8, 9`. Los errores en `img0`, `img5` e `img7` muestran que este pequeño grupo de diseños no equivale a datos manuscritos de MNIST.

### Evidencia de adquisición

Según la información proporcionada para la práctica, las diez imágenes fueron descargadas de internet. El repositorio no incluye las direcciones web de origen ni capturas del proceso de descarga. El mosaico del cuaderno documenta qué archivos se procesan, pero no basta para verificar su adquisición. Para completar este punto de las instrucciones, agregue los enlaces de las fuentes y, si está disponible, una captura de las páginas de descarga.

## Uso de herramientas de IA

Se utilizó un asistente de IA para organizar y redactar el cuaderno y este README, y para revisar que las secciones correspondan con las instrucciones. No se usó IA para generar las imágenes. Las imágenes se reportan como descargadas de internet. Los kernels, las convoluciones y las predicciones se obtienen ejecutando el código con los pesos del modelo y las imágenes disponibles.

## Revisión frente a las instrucciones

| Requisito | Estado | Evidencia o pendiente |
|---|---|---|
| 1. Visualizar y mostrar los valores de al menos diez kernels | Implementado | El cuaderno imprime los pesos y los representa en una cuadrícula. |
| 2. Mostrar las salidas de convolución para una imagen | Implementado | Se muestran las salidas de diez filtros sobre una imagen MNIST. |
| 3. Predecir al menos diez imágenes propias y explicar el tratamiento | Implementado con limitación | Se procesan las diez imágenes descargadas, se muestran las predicciones y se comparan con los dígitos indicados por el nombre. Son diseños de internet, no necesariamente dígitos manuscritos de MNIST. |
| 3. Adjuntar evidencia del proceso de adquisición | Parcial | Se declara que se descargaron de internet; faltan los enlaces originales y/o capturas del proceso para verificar las fuentes. |
| 4. Repetir el análisis de convolución con una imagen propia | Implementado | Se muestran las salidas de diez filtros para `img0`, después de preparar el dígito para la entrada del modelo. |
| 5. Adaptar el README a la actividad | Implementado | Este archivo documenta ejecución, alcance y limitaciones. |
| 6. Describir el uso de herramientas de IA | Implementado | Sección «Uso de herramientas de IA». |


