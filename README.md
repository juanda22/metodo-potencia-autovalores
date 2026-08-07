# Método de la potencia — Cálculo de autovalores y velocidad de convergencia

**Stack:** Python · NumPy · Matplotlib

## Descripción

Implementación del **método de la potencia** para aproximar el autovalor de mayor módulo de una matriz, con un análisis empírico de en qué casos conviene usar este método según las propiedades de la matriz — en particular, cómo afecta la dominancia de la diagonal a la velocidad de convergencia.

## Qué se implementó

1. **`metodo_potencia(A, k)`:** dada una matriz A y un número de iteraciones k, aplica el método de la potencia partiendo de un vector aleatorio y devuelve la secuencia de aproximaciones al autovalor de mayor módulo (vía cociente de Rayleigh) en cada paso. Validado comparando el resultado final contra `np.linalg.eigvals`.

2. **Comparación entre tipos de matrices:** se generan cuatro matrices de 100×100 con dominancia diagonal creciente —A: aleatoria, B: simétrica, C: B + 100 en la diagonal, D: B + 1000 en la diagonal— y se grafica la convergencia del autovalor estimado en cada caso.

3. **Análisis de velocidad de convergencia:** cálculo del error en cada iteración y comparación contra la recta de convergencia teórica, dada por la relación entre el segundo y el primer autovalor de mayor módulo (λ₂/λ₁).

## Resultados y conclusiones

- El método converge rápido para las matrices A y B, y notablemente más lento para C y D — las de mayor dominancia diagonal.
- Esto se explica por una propiedad algebraica directa: si B tiene autovalores λ, entonces B + x·I tiene autovalores λ + x. Al desplazar los autovalores hacia arriba con una constante grande, la relación λ₂/λ₁ se acerca a 1, ralentizando la convergencia.
- Se verificó empíricamente que a mayor pendiente (en valor absoluto) de la recta de error teórico, más rápido converge el método — y viceversa.

## Cómo correrlo

```bash
pip install numpy matplotlib
jupyter notebook metodo_potencia_autovalores.ipynb
```

## Por qué es relevante

Muestra manejo de álgebra lineal numérica desde los fundamentos: no solo implementar el algoritmo, sino entender y demostrar empíricamente por qué se comporta de determinada manera según las propiedades de la matriz — una base clave para trabajar con modelos que dependen de autovalores/autovectores (PCA, SVD, redes neuronales, sistemas dinámicos, etc.).
