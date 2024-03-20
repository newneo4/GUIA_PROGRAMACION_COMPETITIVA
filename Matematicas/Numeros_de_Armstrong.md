## Números de Armstrong

Los números de Armstrong, también conocidos como números narcisistas o números plenos, son aquellos números que son iguales a la suma de sus dígitos elevados a la potencia del número total de dígitos. Por ejemplo, 153 es un número de Armstrong porque:

$$
    (1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153)
$$

```cpp
#include <iostream>
#include <cmath>

bool esNumeroArmstrong(int numero) {
    int original = numero;
    int suma = 0;
    int numDigitos = floor(log10(numero)) + 1;

    while (numero > 0) {
        int digito = numero % 10;
        suma += pow(digito, numDigitos);
        numero /= 10;
    }

    return suma == original;
}

int main() {
    int numero = 153;

    if (esNumeroArmstrong(numero)) {
        std::cout << numero << " es un número de Armstrong." << std::endl;
    } else {
        std::cout << numero << " no es un número de Armstrong." << std::endl;
    }

    return 0;
}
```


Este código en C++ implementa una función llamada `esNumeroArmstrong` que determina si un número dado es un número de Armstrong. Luego, en la función `main`, se prueba esta función con el número 153. El resultado se imprime en la consola, indicando si el número es o no un número de Armstrong.

El enfoque utilizado sigue una estrategia similar a la exponenciación binaria, donde se calcula el número de dígitos y se suman los dígitos elevados a la potencia del número total de dígitos para verificar si el número es un número de Armstrong.
