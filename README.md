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

### Transfer Learning
Modelo basado en **MobileNetV2 preentrenado en ImageNet**, ajustado para las 6 clases del dataset.  
Se utilizó *fine-tuning* parcial para mejorar la adaptación al dominio del problema.

### Teachable Machine
Modelo generado mediante la herramienta **[Teachable Machine de Google](https://teachablemachine.withgoogle.com/)**, exportado y probado en Google Colab.

## Tecnologías utilizads 
- **Python 3.10+**
- **TensorFlow / Keras**
- **NumPy**, **Matplotlib**, **Pandas**
- **Google Colab**
- **Teachable Machine**
- **Scikit-learn**
