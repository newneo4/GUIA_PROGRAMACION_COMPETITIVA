# FACTORIALES

Los factoriales son una operación matemática que consiste en multiplicar un número entero positivo por todos los números enteros positivos menores o iguales que él. Se representan con el símbolo "!".

Por ejemplo:
- El factorial de 5 (denotado como 5!) es igual a 5 × 4 × 3 × 2 × 1 = 120.

## ALGORITMO ITERATIVA

```cpp
long long int factorial(int n){
    long long int res = 1;

    for(int i = 2; i <= n; i++){
        res *= i;
    }

    return res;
}

```

## ALGORITMO RECURSIVO
```cpp
long long int factorialRecursivo(int n){
    long long int res = 0;

    if(n == 1) return 1;

    return n * factorialRecursivo(n-1);
}
```

# EJERCICIO
Dado un factorial n contar el numero de ceros que este posee al final y imprimirlos como salida. 

Ejemplo:

### Entrada:

n = 5

### Salida:

1

### Explicacion:

Dado que el factorial de 5 es 120, entonces observamos que 120 tiene exactamente un cero entonces nuestra salida seria 1.

## SOLUCION
### ALGORITMO INGENUO
```cpp
int contarCeros(int n){
    // Calcular el factorial de n
    long long int factorial = 1;
    for (int i = 2; i <= n; ++i) {
        factorial *= i;
    }

    // Contar el número de ceros al final del factorial
    int ceros = 0;
    while (factorial % 10 == 0) {
        ++ceros;
        factorial /= 10;
    }

    return ceros;
}
```

Como podemos observar el algoritmo funcionara de manera correcta para calcular el factorial de numeros pequeños, sin embargo al calcular el factorial de un numero relativamente grande como 100 demorara bastante.

### SOLUCION EFECTIVA
```cpp
int contarCeros(int n){
    int res = 0;

    for(int i = 5; i <= n; i*=5){
        res += n/i;
    }

    return res;
}
```
Esta solución es efectiva para contar la cantidad de ceros al final de `n!` en base al principio de que la cantidad de ceros está determinada por el número de factores de 5 en la factorización de `n!`.

**Explicación paso a paso:**

1. Inicializamos `res` como 0 para llevar la cuenta de los ceros al final de `n!`.
2. Utilizamos un bucle `for` donde iteramos comenzando desde `i = 5`, ya que cada múltiplo de 5 contribuye con al menos un factor de 5 en la factorización de `n!`. Incrementamos `i` multiplicándolo por 5 en cada iteración.
3. En cada iteración, dividimos `n` por `i` y sumamos el cociente a `res`. Esto nos da el número de veces que `i` contribuye como factor de 5 en la factorización de `n!`.
4. Continuamos el bucle hasta que `i` sea mayor que `n`.
5. Finalmente, devolvemos el valor de `res`, que representa la cantidad total de ceros al final de `n!`.

Esta solución es más eficiente que calcular `n!` y contar los ceros, ya que evita el cálculo innecesario del factorial completo y aprovecha la propiedad fundamental de que los ceros en `n!` están determinados por los factores de 5 en `n!`.


## RECOMENDACIONES

- Tipo de dato adecuado: Se recomienda utilizar long long int para almacenar el resultado, ya que los factoriales crecen rápidamente y pueden superar el rango de un int. Esto previene posibles desbordamientos.

- Aritmética modular: En ciertos casos, como al calcular factoriales para fines de aritmética modular, puede ser útil usar aritmética modular para evitar el desbordamiento de enteros y optimizar el cálculo. Esto es especialmente útil cuando se trabaja con números grandes o cuando se necesita calcular factoriales en módulo de un número primo.

- Manejo de errores: Se debe considerar la posibilidad de manejar errores, como el caso cuando se intenta calcular el factorial de un número negativo. Esto puede lograrse verificando la validez del argumento de entrada antes de calcular el factorial.

- Optimización: Para mejorar la eficiencia, se puede aplicar la optimización de memoria y tiempo. Por ejemplo, se podría utilizar una técnica de programación dinámica para almacenar los resultados intermedios y evitar recálculos repetitivos en casos de cálculos frecuentes de factoriales en un rango dado.

Estas recomendaciones ayudan a escribir un código más robusto, eficiente y flexible para calcular factoriales.