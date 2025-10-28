# deteccion-amenazas-aereas-deeplearning
Este proyecto implementa y compara diferentes enfoques de **visión por computadora** para detectar **amenazas aéreas** —como misiles, jets, helicópteros, drones, cohetes y aviones— utilizando **redes neuronales convolucionales (CNN)**.

El reto consiste en diseñar, entrenar y evaluar tres modelos distintos, poniendo en práctica los principios de **aprendizaje profundo**, **transfer learning** y **validación de modelos**.

## Objetivos del proyecto
1. **Preparar la base de datos** y generar los conjuntos de entrenamiento y validación.
2. **Diseñar una CNN desde cero**, ajustando los hiperparámetros.
3. **Implementar una CNN con un modelo preentrenado** (transfer learning).
4. **Generar un modelo en Teachable Machine**.
5. **Validar, evaluar y comparar** los tres modelso en términos de precisión.
6. **Exportar los modelos entrenados** para ser utlizados en otros entornos.

## Contexto
En este escenario, la humanidad enfrenta una amenaza sin precedentes: una **plaga zombi** se ha extendido por el mundo.  
Una base científica desarrolla la vacuna que podría detenerla, pero está bajo amenaza de ataques aéreos.

El objetivo consiste en desarrolar un modelo inteligente capaz de **detectar en tiempo real** los objetos voladores, clasificándolos en una de las siguientes seis categorías:
- Misil
- Jet
- Helicóptero
- Dron
- Cohete
- Avión

## Dataset

El dataset contiene **8,530 imágenes** en diferentes formatos (`.jpg`, `.jpeg`, `.png`) distribuidas en **6 clases**.  
Para el entrenamiento se utilizaron **6,575 imágenes** y para validación **1,643 imágenes**.  
Cada imagen fue redimensionada a **224×224 píxeles**.

Durante la etapa de preparación se aplicaron transformaciones como:

- Reescalado de píxeles (`1/255`)
- *Data Augmentation*: volteo horizontal, rotación, zoom y contraste aleatorio
- Separación del conjunto de entrenamiento y validación

## Modelos Implementados
### CNN desde cero
Modelo diseñado con capas convolucionales, normalización por lotes y regularización mediante *Dropout*.  
El entrenamiento se optimizó con *EarlyStopping* y *ReduceLROnPlateau* para mejorar la eficiencia.

### MobileNetv12
MobileNetv2 es una arquitectura de red neuronal profunda optimizada para dispotivos con recursos limitados. 
Se basa en el uso de **convoluciones separables en profundidad** y un bloque llamado ***inverted residual***, que reduce el número de paráemtros sin perder capacidad de representación. 

Ventajas principales:
- Modelo ligero y eficiente, ideal para implementaciones en tiempo real.
- Buena precisión con bajo costo computacional.
- Excelente opción cuando se requiere un equilibrio entre velocidad y rendimiento.

### EfficientNetB0 
**EfficientNetB0** es el modelo base de la familia EfficientNet, desarrollada por Google.
Su diseño se basa en una búsqueda automatizada de arquitectura (NAS) y en un método de escalado compuesto, que equilibra proporcionalmente la profundidad, anchura y resolución de la red.

Ventajas principales: 
-Alta precisión con menos parámetros comparado con otros modelos grandes.
-Excelente eficiencia computacional: logra mejores resultados con menor tamaño y tiempo de entrenamiento.
- Escalable a variantes más potentes (B1–B7) según los recursos disponibles.
### Teachable Machine
Modelo generado mediante la herramienta **[Teachable Machine de Google](https://teachablemachine.withgoogle.com/)**, exportado y probado en Google Colab.

## Comparación de Modelos:

| Modelo | Tipo de entrenamiento | Pérdida (Loss) | Exactitud (Accuracy) |
|:--|:--|:--:|:--:|
| CNN (desde cero) | Entrenamiento desde cero | **1.5589** | **0.3889** |
| MobileNetV2 | Pre-entrenado + Fine-tuning | **0.9856** | **0.6324** |
| EfficientNetB0 | Pre-entrenado + Fine-tuning | **0.8807** | **0.6726** |
| Teachable Machine | Modelo externo (transfer) | **2.9628** | **0.5326** |


## Modelo Seleccionado 🏆
El modelo final elegido fue **EfficientNetB0** con Fine-Tuning, presenta:
- **Mayor exactitud** (0.6726)
- **Menor pérdida** (0.8807)
- Buen balance entre rendimiento y eficiencia computacional
- 
## Tecnologías utilizads 
- **Python 3.10+**
- **TensorFlow / Keras**
- **NumPy**, **Matplotlib**, **Pandas**
- **Google Colab**
- **Teachable Machine**
- **Scikit-learn**

## Conclusiones
- El uso de **modelos preentrenados y fine-tuning** permitió obtener una mejora significativa frente a una CNN entrenada desde cero.
- **EfficientNetB0** logró el mejor rendimiento, mostrando una excelente capacidad de generalización y eficiencia.
- La aplicación de **Data Augmentation y callbacks de regularización** contribuyó a un entrenamiento más estable y a evitar el sobreajuste.  
