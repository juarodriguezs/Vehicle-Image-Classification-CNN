# 🚗 Vehicle Image Classification (CNN y Transfer Learning con ResNet50)

Este proyecto aplica técnicas de **aprendizaje profundo supervisado** para la **clasificación multiclase de vehículos** a partir de imágenes.  
El objetivo principal es comparar el rendimiento de un modelo base de **Red Neuronal Convolucional (CNN)** entrenado desde cero con una red preentrenada **ResNet50**, aplicando **Transfer Learning** para mejorar la precisión del modelo y reducir el tiempo de entrenamiento.

---

## 📘 Descripción general

El análisis se basa en el dataset **["5 Vehicles for Multi-category Classification"](https://www.kaggle.com/datasets/mrtontrnok/5-vehichles-for-multicategory-classification)**, disponible en *Kaggle*.  
El conjunto de datos contiene imágenes de **cinco tipos de vehículos**: buses (bus), carros (car), motocicletas (motorcycle), trenes (train) y camiones (truck).  

El proceso de desarrollo se centra en la **comparación de desempeño entre dos enfoques**:
- Una **CNN básica** entrenada desde cero.  
- Un modelo **ResNet50 preentrenado** en ImageNet, aprovechando *Transfer Learning* para mejorar la generalización y precisión en el reconocimiento de vehículos.

---

## 📂 Estructura del proyecto

```plaintext
Vehicle-Classification/
│
├── vehicle_image_classification.ipynb
└── README.md
```

---

## 📈 Resultados destacados

Los resultados se evaluaron sobre el **conjunto de prueba**, utilizando las métricas estándar de clasificación:  
**Accuracy**, **Precision**, **Recall** y **F1-score (macro)**.  
A continuación se presentan los valores promedio obtenidos por cada modelo y su respectivo análisis comparativo.

| Modelo | Accuracy (Test) | Precision (Macro) | Recall (Macro) | F1-score (Macro) |
|:--------|:---------------:|:-----------------:|:---------------:|:----------------:|
| 🧩 CNN Base (entrenamiento desde cero) | 0.76 | 0.75 | 0.73 | 0.73 |
| 🔁 CNN con Transfer Learning (ResNet50) | **0.80** | **0.80** | **0.78** | **0.78** |

---

### 🧩 CNN Base (entrenamiento desde cero)

El modelo **CNN entrenado desde cero** alcanzó una **Accuracy del 76%**, mostrando un rendimiento razonable en la clasificación de los cinco tipos de vehículos. Sin embargo, presentó variaciones notables entre clases, con algunas mostrando buen desempeño y otras dificultades debido a similitudes visuales entre vehículos.

#### 🔹 Clase mejor clasificada: *motorcycle*
- **F1-score:** 0.89 (el más alto).  
- **Precisión:** 0.88 → Cuando el modelo predice *motorcycle*, acierta el 88% de las veces.  
- **Recall:** 0.89 → El 89% de las motocicletas reales fueron correctamente identificadas.  
- **Confusiones:** Principalmente con *car* (6) y ocasionalmente con *bus* y *truck*  (1 vez cada una).  
- **Conclusión:** El modelo logra distinguir con gran precisión las motocicletas, con un bajo número de errores.

#### 🔻 Clase peor clasificada: *car*
- **F1-score:** 0.56 (el más bajo).  
- **Precisión:** 0.77 → Cuando el modelo predice *car*, acierta el 77% de las veces.  
- **Recall:** 0.44 → Solo el 44% de los autos reales fueron correctamente identificados.  
- **Confusiones:** Se confunde con *bus* (15), *motorcycle* (8), *train* (10) y especialmente con *truck* (27).  
- **Conclusión:** La clase “car” representó el mayor desafío, debido a su similitud visual con camiones y autobuses, lo que afectó su tasa de aciertos.

En general, la **CNN base** sirvió como punto de partida sólido, aunque evidenció **limitaciones de generalización** y una tendencia al **sobreajuste** en etapas avanzadas del entrenamiento.

---

### 🔁 CNN con Transfer Learning (ResNet50)

El modelo basado en **ResNet50 preentrenado en ImageNet** logró un **Accuracy del 80%**, representando una mejora del **4%** respecto a la CNN base.  
El uso de **Transfer Learning** permitió aprovechar características previamente aprendidas por una red profunda, mejorando la discriminación entre clases similares y reduciendo el tiempo de entrenamiento.

#### 🔹 Clase mejor clasificada: *motorcycle*
- **F1-score:** 0.91 (el más alto).  
- **Precisión:** 0.87 → Cuando el modelo predice *motorcycle*, acierta el 87% de las veces.  
- **Recall:** 0.95 → El 95% de las motocicletas reales fueron correctamente identificadas.  
- **Confusiones:** Muy pocas; principalmente con *car* (4) y solo 1 caso con *bus* y *train*.  
- **Conclusión:** El modelo mantiene una excelente capacidad para identificar motocicletas, con muy baja tasa de error.

#### 🔻 Clase peor clasificada: *truck*
- **F1-score:** 0.61 (el más bajo).  
- **Precisión:** 0.79 → Cuando el modelo predice *truck*, acierta el 79% de las veces.  
- **Recall:** 0.50 → Solo el 50% de los camiones reales fueron correctamente identificados.  
- **Confusiones:** Se confunde con *bus* (17), *car* (14) y *train* (19).  
- **Conclusión:** A pesar de las mejoras globales, el modelo aún enfrenta dificultades al diferenciar vehículos grandes y similares visualmente.

El modelo preentrenado con ResNet50 logró una mejor capacidad de generalización, redujo el sobreajuste, aceleró la convergencia y mejoró la precisión global, mostrando un aprendizaje más estable y eficiente.

---

### ⚖️ Conclusión general

El uso de **Transfer Learning con ResNet50** permitió una mejora tangible del **Accuracy (+4%)** en comparación con la CNN entrenada desde cero.  
Aunque la ganancia numérica puede parecer moderada, el modelo preentrenado presentó un entrenamiento más rápido, una mejor generalización y mayor estabilidad frente a variaciones del conjunto de datos.  
En contextos con recursos limitados o datasets pequeños, esta estrategia representa una mejora significativa tanto en desempeño como en eficiencia.

## 🛠️ Tecnologías y librerías utilizadas

- **Python 3.9 o superior**
- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `scikit-learn`
- `TensorFlow` (Keras, ResNet50)

---

## 👥 Autores

Proyecto desarrollado colaborativamente como Microproyecto 4 del curso de **Introducción a la Inteligencia Artificial** de la Universidad Nacional de Colombia - Sede Medellín.

**Equipo 9:**

- Jacobo Ochoa Ramírez
- Juan Manuel Rodríguez Sánchez
- Luis Alejandro Varela Ojeda
