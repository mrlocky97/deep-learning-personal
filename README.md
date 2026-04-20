# Deep Learning Personal

Exploración práctica de arquitecturas de redes neuronales con TensorFlow/Keras y PyTorch.  
Cada sección incluye implementación comentada, visualizaciones y análisis de resultados.

**Stack:** Python · TensorFlow 2 · Keras · PyTorch · NumPy · Matplotlib

---

## Contenido

| # | Tema | Problemas | Datasets | Métricas |
|---|------|-----------|----------|----------|
| 01 | [Redes densamente conectadas](./01_redes_densamente_conectadas/) | Clasificación · Regresión | MNIST · California Housing | Acc ~92.4% · MAE ~$35k · R² ~0.78 |

> Repositorio en construcción — se irán añadiendo nuevas arquitecturas progresivamente.

---

## 01 · Redes densamente conectadas

Capas densas aplicadas a dos problemas clásicos: clasificación de dígitos y regresión de precios.  
Cada problema se implementa en Keras y PyTorch para comparar su filosofía de diseño.

**Qué explora:**
- Clasificación multiclase (MNIST): `Dense(10, softmax)` — 7.850 parámetros, ~92.4% accuracy
- Regresión (California Housing): `Dense(64) → Dense(32) → Dense(1)` — MAE ~$35k, R² ~0.78
- Preprocesado: normalización de píxeles y `StandardScaler` para datos tabulares
- Data leakage: ajustar el scaler solo con datos de entrenamiento
- Detección de overfitting mediante curvas de loss training vs validación
- Bucle de entrenamiento manual (PyTorch) vs `model.fit()` (Keras)
- `DataLoader` + `Dataset` vs arrays NumPy directos

```
Clasificación:  Input (784) ──► Dense(10, softmax) ──► Clase (0-9)
Regresión:      Input (8)   ──► Dense(64) ──► Dense(32) ──► Dense(1) ──► Precio
```

| Archivo | Problema | Framework |
|---------|----------|-----------|
| `redes_densamente_conectadas.ipynb` | Clasificación MNIST | TensorFlow / Keras |
| `mnist_pytorch.ipynb` | Clasificación MNIST | PyTorch |
| `regresion_precios.ipynb` | Regresión California Housing | Keras y PyTorch |

---

## Ejecución local

```bash
git clone https://github.com/mrlocky97/deep-learning-personal.git
cd deep-learning-personal
pip install tensorflow torch torchvision numpy matplotlib scikit-learn jupyter
jupyter notebook
```

---

*Basado en conceptos del libro "Python Deep Learning" de Jordi Torres (UPC/BSC).*
