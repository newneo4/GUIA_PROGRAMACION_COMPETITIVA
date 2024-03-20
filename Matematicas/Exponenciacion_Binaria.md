## EXPONENCIACION BINARIA

La exponenciación binaria es un algoritmo eficiente para calcular la potencia de un número. En lugar de calcular la potencia multiplicando el número por sí mismo repetidamente, este algoritmo utiliza una estrategia binaria que aprovecha las propiedades de la aritmética modular.

```cpp
int exponenciacion(int x, int n){
    int res = 1;

    while(n  > 0){
        if(n % 2 != 0){
            res = res * x;
        }

        x = x * x;
        n = n/2;
    }

    return res;
}
```
El algoritmo sigue estos pasos:

1. **Inicialización**: Comenzamos con un resultado `res` inicializado a 1.

2. **Bucle while**: Mientras el exponente `n` sea mayor que 0, hacemos lo siguiente:

   - Si el bit menos significativo de `n` es 1, multiplicamos `res` por `x`.
   - Luego, actualizamos `x` multiplicándolo por sí mismo (esencialmente elevándolo al cuadrado) y dividimos `n` por 2.

3. Repetimos el paso 2 hasta que `n` sea 0.

Al final del algoritmo, `res` contendrá el resultado final, es decir, `x` elevado a la potencia `n`.

Este algoritmo tiene una complejidad de tiempo O(log n) debido a la división repetida de `n` por 2 en cada iteración del bucle while. Por lo tanto, es significativamente más rápido que el enfoque ingenuo de complejidad O(n), especialmente para exponentes grandes.

El algoritmo es eficiente porque aprovecha la representación binaria del exponente para reducir el número de multiplicaciones necesarias.

Finalmente, podemos tener un caso donde la potencia sea de numeros grandes que tienden a desbordarse es entonces que podemos usar el siguiente algoritmo, combinando nuestro algoritmo de exponenciacion rapida y aritmetica modular.

```cpp
long long exp_modular(long long base, long long exponente, long long modulo) {
    if (exponente == 0) return 1;

    long long resultado = 1;
    base %= modulo;

    while (exponente > 0) {
        if (exponente & 1)
            resultado = (resultado * base) % modulo;

        exponente >>= 1;
        base = (base * base) % modulo;
    }

    return resultado;
}
```