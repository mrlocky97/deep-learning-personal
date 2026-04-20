# Deep Learning Personal

Exploración práctica de arquitecturas de redes neuronales con TensorFlow/Keras y PyTorch.  
Cada sección incluye implementación comentada, visualizaciones y análisis de resultados.

**Stack:** Python · TensorFlow 2 · Keras · PyTorch · NumPy · Matplotlib

---

## Contenido

| # | Tema | Concepto clave | Dataset | Accuracy |
|---|------|---------------|---------|----------|
| 01 | [Redes densamente conectadas](./01_redes_densamente_conectadas/) | Clasificador lineal · Softmax · Detección de overfitting · Keras vs PyTorch | MNIST | ~92.4% |

> Repositorio en construcción — se irán añadiendo nuevas arquitecturas progresivamente.

---

## 01 · Redes densamente conectadas

Red neuronal de una sola capa densa entrenada para clasificar dígitos escritos a mano (0–9).  
Implementada en dos frameworks para comparar su filosofía de diseño.

**Qué explora:**
- Preprocesado de imágenes: aplanado y normalización
- Arquitectura mínima: `Dense(10, softmax)` — 7.850 parámetros
- Ciclo completo: compilación, entrenamiento y evaluación
- Visualización de pesos aprendidos por neurona
- Detección de overfitting mediante curvas training vs validación
- Bucle de entrenamiento manual (PyTorch) vs `model.fit()` (Keras)
- `DataLoader` + `Dataset` vs arrays NumPy directos

```
Input (784) ──► Dense(10, softmax) ──► Predicción (0-9)
```

| Archivo | Framework |
|---------|-----------|
| `redes_densamente_conectadas.ipynb` | TensorFlow / Keras |
| `mnist_pytorch.ipynb` | PyTorch |

---

## Ejecución local

```bash
git clone https://github.com/mrlocky97/deep-learning-personal.git
cd deep-learning-personal
pip install tensorflow torch torchvision numpy matplotlib jupyter
jupyter notebook
```

---

*Basado en conceptos del libro "Python Deep Learning" de Jordi Torres (UPC/BSC).*
