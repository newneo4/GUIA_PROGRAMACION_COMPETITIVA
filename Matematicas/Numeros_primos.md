## NÚMEROS PRIMOS

Los números primos son números naturales mayores que 1 que no tienen divisores positivos distintos de 1 y ellos mismos. Hay varios métodos para identificar números primos, y uno de ellos implica el siguiente patrón:

$$ 
{6n+1} \quad \text{o} \quad {6n-1}  
$$

Excepto por los números 2 y 3, todos los números primos pueden representarse en esta forma.

### Implementación en C++

```cpp
bool esPrimo(int n){
    if(n == 1) return false;

    for(int i = 2; i < n; i++){
        if(n % i == 0) return false;
    }

    return true;
}
```
Como podemos ver si queremos saber si el numero en cuestion es primo o no necesitariamos recorrer desde el 2 hasta el mismo numero en cuestion menos uno.

### Implementacion Optima
```cpp
bool esPrimo(int n){
    if(n== 1) return false;

    for(int i = 2; i * i <= n; i++){
        if(n % i == 0) return false;
    }

    return true;
}
```
En este caso no necesitamos recorrer todos los numeros desde 2 hasta n si no unicamente hasta la raiz del numero en cuestion lo que reduce considerablemente la complejidad del algoritmo.

Finalmente si deseeamos un algoritmo aun mas eficiente para verificar si un numero es primo o no podemos usar el siguiente.
```cpp
bool esPrimo(int n){
    if(n == 1) return false;
    if(n == 2 || n == 3) return true;
    if(n % 2 == 0 || n % 3 == 0) return false;

    for(int i = 5; i * i <= n; i+=6){
        if(n % i == 0 || n % (i + 2) == 0) return false;
    }

    return true;
}
```

## Cómo funciona

1. Comprueba si el número es igual a 1. En tal caso, devuelve `false`, ya que 1 no se considera un número primo.
   
2. Comprueba si el número es igual a 2 o 3. Si es así, devuelve `true`, ya que 2 y 3 son números primos.
   
3. Comprueba si el número es divisible por 2 o 3. Si es así, devuelve `false`, ya que no puede ser primo.
   
4. Utiliza un bucle `for` que comienza en 5 y continúa hasta que el cuadrado de `i` sea menor o igual que el número dado `n`. Esto se hace para verificar si el número es divisible por cualquier otro número primo más grande que 3. El bucle incrementa `i` en 6 en cada iteración, ya que los números primos después de 3 son de la forma 6k ± 1.
   
5. En cada iteración del bucle, comprueba si el número es divisible por `i` o `i + 2` (que son números primos candidatos). Si es divisible por alguno de ellos, devuelve `false`.
   
6. Si no se encontró ningún divisor en el rango especificado, devuelve `true`, lo que indica que el número es primo.