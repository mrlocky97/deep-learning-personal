# 01 · Redes densamente conectadas

Implementación de un clasificador de dígitos escritos a mano usando la red neuronal más simple posible: una única capa densa con activación softmax.

## Arquitectura

```
Input (784 píxeles) ──► Dense(10, softmax) ──► Clase predicha (0-9)
```

- **Parámetros entrenables:** 7.850 (784 × 10 pesos + 10 bias)
- **Función de pérdida:** Sparse Categorical Crossentropy
- **Optimizador:** Adam
- **Accuracy en test:** ~92.4%

## Conceptos cubiertos

- Train/Test split y por qué nunca se evalúa con datos de entrenamiento
- Normalización de píxeles al rango [0, 1]
- Activación Softmax y clasificación multiclase
- Visualización de pesos aprendidos por cada neurona
- Detección de overfitting con curvas de loss y accuracy

## Archivo

| Archivo | Descripción |
|---------|-------------|
| `redes_densamente_conectadas.ipynb` | Notebook completo con implementación y análisis |
