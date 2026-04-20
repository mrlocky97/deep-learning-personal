# 01 · Redes densamente conectadas

Redes densas aplicadas a dos problemas clásicos: clasificación de dígitos MNIST y regresión de precios de vivienda (California Housing). Implementados en Keras y PyTorch para comparar filosofías.

## Notebooks

### Clasificación — MNIST

Clasificador de dígitos con una única capa densa + softmax.

```
Input (784 píxeles) ──► Dense(10, softmax) ──► Clase predicha (0-9)
```

- **Parámetros entrenables:** 7.850 (784 × 10 pesos + 10 bias)
- **Función de pérdida:** Sparse Categorical Crossentropy
- **Optimizador:** Adam
- **Accuracy en test:** ~92.4% (Keras) · ~92.5% (PyTorch)

### Regresión — California Housing

Predicción del precio medio de viviendas por distrito (en $100k). 8 features numéricas, 20.640 muestras.

```
Input (8 features) ──► Dense(64, ReLU) ──► Dense(32, ReLU) ──► Dense(1) ──► Precio predicho
```

- **Parámetros entrenables:** 2.689
- **Función de pérdida:** MSE
- **Optimizador:** Adam (50 epochs)
- **Resultados en test:** MAE ~$35k · R² ~0.78 (Keras y PyTorch)

## Clasificación vs Regresión

| | Clasificación (MNIST) | Regresión (precios) |
|---|---|---|
| Salida | 10 neuronas + softmax | 1 neurona, sin activación |
| Loss | CrossEntropy | MSE |
| Métrica | Accuracy (%) | MAE, RMSE, R² |
| ¿Qué predice? | Una clase discreta | Un número continuo |

## Conceptos cubiertos

- Train/Test split y por qué nunca se evalúa con datos de entrenamiento
- Normalización de píxeles al rango [0, 1] y StandardScaler para datos tabulares
- Data leakage: ajustar el scaler solo con train, no con todo el dataset
- Activación Softmax (clasificación multiclase) vs. salida lineal (regresión)
- Capas ocultas con ReLU para aprender representaciones intermedias
- Visualización de pesos aprendidos por cada neurona
- Detección de overfitting con curvas de loss
- Bucle de entrenamiento manual vs. `model.fit()` automático
- `DataLoader` y `Dataset` de PyTorch vs. arrays NumPy directos

## Keras vs PyTorch

| Aspecto | TensorFlow / Keras | PyTorch |
|---|---|---|
| Definir modelo | `Sequential([...])` | Clase que hereda `nn.Module` |
| Bucle de entrenamiento | `model.fit()` automático | Manual — tú lo escribes |
| Gradientes | Invisibles | `loss.backward()` explícito |
| Datos | numpy arrays directos | `DataLoader` + `Dataset` |
| Envío a GPU | Automático | `.to(device)` manual |
| Acceso a pesos | `get_weights()[0]` `(784,10)` | `.weight` `(10,784)` |

## Archivos

| Archivo | Descripción |
|---------|-------------|
| [redes_densamente_conectadas.ipynb](redes_densamente_conectadas.ipynb) | Clasificación MNIST con TensorFlow / Keras |
| [mnist_pytorch.ipynb](mnist_pytorch.ipynb) | Espejo exacto en PyTorch — mismo modelo, mismo dataset |
| [regresion_precios.ipynb](regresion_precios.ipynb) | Regresión California Housing en Keras y PyTorch |
