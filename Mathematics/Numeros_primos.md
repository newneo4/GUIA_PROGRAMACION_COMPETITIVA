## NÚMEROS PRIMOS

Los números primos son números naturales mayores que 1 que no tienen divisores positivos distintos de 1 y ellos mismos. Hay varios métodos para identificar números primos, y uno de ellos implica el siguiente patrón:

$$ 
{6n+1} \quad \text{o} \quad {6n-1}  
$$

Excepto por los números 2 y 3, todos los números primos pueden representarse en esta forma.

### Implementación en C++

```cpp
#include <iostream>
#include <cmath>

using namespace std;

// Función para verificar si un número es primo
bool esPrimo(int n) {
    if (n <= 1) return false; // 0 y 1 no son primos
    if (n <= 3) return true; // 2 y 3 son primos
    if (n % 2 == 0 || n % 3 == 0) return false; // los múltiplos de 2 y 3 no son primos
    
    // Verificar números de la forma 6k ± 1 hasta √n
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false; // si es divisible por i o i + 2, no es primo
    }
    return true; // de lo contrario, es primo
}

int main() {
    int n;
    cout << "Ingresa un número: ";
    cin >> n;

    if (esPrimo(n)) {
        cout << n << " es un número primo." << endl;
    } else {
        cout << n << " no es un número primo." << endl;
    }

    return 0;
}
