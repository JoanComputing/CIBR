# Proyecto Final: CBIR

Este proyecto implementa un sistema de recuperación de imágenes basado en contenido (Content-Based Image Retrieval, CBIR) utilizando diferentes métodos de extracción de características y técnicas de optimización.

## Tabla de Contenidos

1. [Introducción](#introducción)
2. [Metodología y Resultados](#metodología-y-resultados)
    - [CBIR](#cbir)
    - [Dataset](#dataset)
    - [HOG](#hog)
    - [RESNET](#resnet)
    - [Creación de una base de datos](#creación-de-una-base-de-datos)
    - [Ordenar los resultados por relevancia](#ordenar-los-resultados-por-relevancia)
    - [Cálculo de resultados y visualización](#cálculo-de-resultados-y-visualización)
    - [Optimización de tiempos de búsqueda y memoria](#optimización-de-tiempos-de-búsqueda-y-memoria)
3. [Resultados](#resultados)
    - [HOG & RESNET](#hog--resnet)
    - [PCA](#pca)
    - [Tiempos y calidad de métodos alternativos](#tiempos-y-calidad-de-métodos-alternativos)
4. [Análisis de Resultados](#análisis-de-resultados)
5. [Conclusiones](#conclusiones)

---

## Introducción

El objetivo del proyecto es implementar un sistema CBIR para calcular vectores de características, almacenarlos, ordenarlos por relevancia y probar técnicas de optimización, como PCA, para mejorar el desempeño del sistema en tiempo y memoria.

---

## Metodología y Resultados

### CBIR

El sistema CBIR permite al usuario seleccionar una imagen para extraer sus características, compararlas con una base de datos y generar un ranking de relevancia. Se utilizó Python en Google Colab, aprovechando librerías como `pandas`, `numpy`, `cv2`, `torch`, y `matplotlib`.

### Dataset

Se utilizó el **INRIA Holidays Dataset**, que contiene 1491 imágenes de 500 clases diferentes. Las imágenes de consulta tienen un formato específico (`ID=00`), y las restantes constituyen la base de datos.

### HOG

Se empleó Histogram of Oriented Gradients (HOG) para extraer características, dividiendo las imágenes en celdas y bloques, con interpolación para minimizar la pérdida de información.

### RESNET

Se utilizó un modelo preentrenado de RESNET de PyTorch, eliminando la última capa para extraer vectores de características relevantes.

### Creación de una base de datos

Las características extraídas de las imágenes se almacenan en un archivo CSV para optimizar los procesos y evitar la necesidad de releer las imágenes.

### Ordenar los resultados por relevancia

Se aplicaron métricas como **similitud del coseno**, **distancia euclidiana**, y **Chi-cuadrado** para ordenar las imágenes en un ranking de relevancia.

### Cálculo de resultados y visualización

Se implementó una función para comparar 500 imágenes de consulta, evaluando su ranking y mostrando visualizaciones de las 10 imágenes más similares.

### Optimización de tiempos de búsqueda y memoria

Se utilizó **PCA (Principal Component Analysis)** para reducir dimensionalidad y mejorar tiempos de ejecución y uso de memoria.

---

## Resultados

### HOG & RESNET

El modelo RESNET mostró un mejor desempeño al identificar imágenes relevantes con mayor precisión que HOG.

### PCA

- Mejora el porcentaje de aciertos en HOG y CNN.
- Reduce significativamente el uso de memoria y tiempos de procesamiento.

### Tiempos y calidad de métodos alternativos

| Método | PCA | Sin PCA |
|--------|------|---------|
| HOG (Tiempo) | 0.39s | 0.54s |
| CNN (Tiempo) | 0.28s | 0.36s |
| HOG (% Aciertos) | 17.6% | 13.0% |
| CNN (% Aciertos) | 64.6% | 64.4% |

---

## Análisis de Resultados

Los resultados confirman que PCA mejora la calidad y eficiencia del sistema, especialmente en HOG. RESNET sobresale en la identificación precisa de clases, incluso en condiciones complejas.

---

## Conclusiones

- **RESNET** es el método más efectivo, logrando una identificación precisa en múltiples escenarios.
- **PCA** es crucial para optimizar tiempo y memoria sin comprometer la calidad del ranking.
- Posibles mejoras incluyen explorar configuraciones intermedias en redes convolucionales y utilizar información de color.

---


