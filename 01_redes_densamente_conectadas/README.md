# 01 · Redes densamente conectadas

Clasificador de dígitos escritos a mano (MNIST) con la red más simple posible: una única capa densa con softmax. Implementado en dos frameworks para comparar filosofías.

## Arquitectura

```
Input (784 píxeles) ──► Dense(10, softmax) ──► Clase predicha (0-9)
```

- **Parámetros entrenables:** 7.850 (784 × 10 pesos + 10 bias)
- **Función de pérdida:** Sparse Categorical Crossentropy
- **Optimizador:** Adam
- **Accuracy en test:** ~92.4% (Keras) · ~92.5% (PyTorch)

## Conceptos cubiertos

- Train/Test split y por qué nunca se evalúa con datos de entrenamiento
- Normalización de píxeles al rango [0, 1]
- Activación Softmax y clasificación multiclase
- Visualización de pesos aprendidos por cada neurona
- Detección de overfitting con curvas de loss y accuracy
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
| [redes_densamente_conectadas.ipynb](redes_densamente_conectadas.ipynb) | Implementación con TensorFlow / Keras |
| [mnist_pytorch.ipynb](mnist_pytorch.ipynb) | Espejo exacto en PyTorch — mismo modelo, mismo dataset |
