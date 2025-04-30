### Rodrigo Terán Hernández A01704108  
> Última versión: 29/04/2025

> <a href="/proyecto.pdf">Consultar proyecto.pdf para más información</a>

# Contexto

## Objetivo  
El objetivo de este proyecto es clasificar vehículos y predecir marcas específicas de vehículos utilizando dos enfoques de modelos de aprendizaje profundo: un modelo preentrenado **MobileNetV2** y un modelo de **red neuronal convolucional personalizada (CNN)**. El proyecto busca comparar la precisión de ambos modelos en un conjunto de datos de imágenes de vehículos y evaluar su capacidad para predecir las marcas de vehículos, como Audi o Hyundai.

## Set de datos  
El dataset utilizado está compuesto únicamente por imágenes de vehículos, que están organizadas en carpetas por marca. Las imágenes de los vehículos fueron utilizadas para entrenar y evaluar los modelos de clasificación.

Las carpetas del dataset contienen:

- **Marca de vehículo**: Dentro de cada carpeta, las imágenes están organizadas por marca, como `audi`, `hyundai`, etc.

## Preprocesamiento  
Las imágenes fueron procesadas para cumplir con los requisitos de entrada de los modelos:

- **Redimensionamiento**: Las imágenes fueron redimensionadas a 224x224 píxeles para MobileNetV2.
- **Normalización**: Los valores de los píxeles fueron normalizados en un rango de 0 a 1.
- **Aumento de datos**: Se aplicaron transformaciones como rotaciones, volteo horizontal y recortes aleatorios para mejorar la generalización del modelo.

## Separación  
El conjunto de datos fue dividido en dos subconjuntos:

- **Entrenamiento**: 80% de las imágenes.
- **Prueba**: 20% de las imágenes.

## Modelos  
### 1. **MobileNetV2 (Preentrenado)**
Se utilizó **MobileNetV2**, un modelo preentrenado sobre **ImageNet**. Se realizó un ajuste fino para adaptarlo a la tarea específica de clasificación de vehículos y predicción de marcas de vehículos. Utilizamos transferencia de aprendizaje para aprovechar las características previamente aprendidas y ajustarlo al nuevo dominio.

### 2. **CNN Personalizada**
Desarrollamos una **red neuronal convolucional personalizada (CNN)** adaptada específicamente para la clasificación de vehículos. Este modelo fue diseñado para trabajar con las imágenes del dataset y entrenado desde cero con el conjunto de datos.

## Entrenamiento  
Ambos modelos fueron entrenados utilizando **TensorFlow/Keras** con los siguientes parámetros:

- **Epochs**: 50
- **Tamaño del batch**: 32
- **Función de pérdida**: `categorical_crossentropy`
- **Optimizador**: `Adam`

## Visualizaciones  
Se incluyeron varias visualizaciones para evaluar el rendimiento de los modelos:

1. **Curvas de precisión de los epochs**  
   Gráficos que muestran cómo la precisión de ambos modelos mejoró durante el entrenamiento en cada época.

2. **Matriz de confusión**  
   Las matrices de confusión para ambos modelos, mostrando cómo se distribuyen las predicciones correctas e incorrectas entre las clases de vehículos.

3. **Ejemplos de predicciones**  
   Capturas de pantalla con las predicciones realizadas por los modelos. Se comparan las predicciones de tipos y marcas de vehículos con las etiquetas reales.

## Conclusión  
Ambos modelos lograron buenos resultados para la clasificación de vehículos y la predicción de marcas específicas. El modelo **CNN personalizada** demostró ser más efectivo en la clasificación en comparación con **MobileNetV2**, particularmente en el conjunto de prueba. Esto refuerza la idea de que los modelos personalizados ajustados a un conjunto de datos específico pueden superar a los modelos preentrenados en tareas particulares como la clasificación de vehículos y marcas.

## Referencias  
- Valev, Y., Jeatrakul, P., & Wongthanavasu, S. (2018). A Systematic Evaluation of Recent Deep Learning Architectures for Fine-Grained Vehicle Classification. arXiv preprint arXiv:1806.02987. [Link](https://arxiv.org/abs/1806.02987)
- Howard, A. G., et al. (2017). MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications. arXiv:1704.04861. [Link](https://arxiv.org/abs/1704.04861)
- Shorten, C., & Khoshgoftaar, T. M. (2019). A survey on Image Data Augmentation for Deep Learning. Journal of Big Data. [Link](https://link.springer.com/article/10.1186/s40537-019-0197-0)
- Sun, C., Shrivastava, A., Singh, S., & Gupta, A. (2017). Revisiting Unreasonable Effectiveness of Data in Deep Learning Era. ICCV. [Link](https://openaccess.thecvf.com/content_iccv_2017/html/Sun_Revisiting_Unreasonable_Effectiveness_ICCV_2017_paper.html)
- Sokolova, M., & Lapalme, G. (2009). A systematic analysis of performance measures for classification tasks. Information Processing & Management. [Link](https://www.sciencedirect.com/science/article/pii/S0306457308001866)
- Bengio, Y. (2012). Practical recommendations for gradient-based training of deep architectures. In Neural Networks: Tricks of the Trade. [Link](https://link.springer.com/chapter/10.1007/978-3-642-35289-8_2)

