# PROGRESIÓN ARITMÉTICA Y PROGRESIÓN GEOMÉTRICA

## PROGRESIÓN ARITMÉTICA

Una progresión aritmética es una secuencia de números en la que la diferencia entre dos términos consecutivos es constante. Podemos considerar los siguientes números como ejemplo:

$$
2, 4, 6, 8, 10
$$

Donde:
- \( a \): Número inicial
- \( d \): Diferencia común de esta progresión

Ahora consideremos las siguientes operaciones:
- Suma:
  $$ 
  a + (n + 1) \times d 
  $$
- Promedio:
  $$
  \frac{{\text{{Primer Valor}} + \text{{Último Valor}}}}{2} \times n
  $$
- Promedio:
  $$
  \frac{{\text{{Suma}}}}{{n}} 
  $$
- Suma:
  $$
  \text{{Promedio}} \times n 
  $$
- Suma: 
  $$
  \left( \frac{{\text{{Primer Valor}} + \text{{Último Valor}}}}{2} \right) \times n
  $$
- Suma: 
  $$
  \frac{{n}}{2} \times \left( a + a \times (n - 1) \times d \right) 
  $$

Estas fórmulas nos ayudan a calcular la suma y el promedio de una progresión aritmética. La suma se puede calcular directamente o utilizando el promedio y el número de términos en la progresión.

## PROGRESIÓN GEOMÉTRICA

Una progresión geométrica es una secuencia de números en la que cada término después del primero se encuentra multiplicando el término anterior por un número fijo, distinto de cero, llamado razón común. Por ejemplo:

$$
2, 4, 8, 16, 32
$$

Donde:
- \( a \): Término inicial
- \( r \): Razón común
- \( n \): Número de elementos

Ahora, podemos considerar las siguientes operaciones:

- El \( i \)-ésimo elemento:
$$
a \times r^{i-1}
$$
- El último elemento:
$$
a \times r^{n-1}
$$
- Suma:
$$
\left( \frac{{a \times (1 - r^n)}}{1- r} \right)
$$

### Implementación en C++

```cpp
#include <iostream>
#include <cmath>

using namespace std;

int main() {
    // Progresión Aritmética
    int a = 2; // Número inicial
    int d = 2; // Diferencia común
    int n = 5; // Número de términos

    int suma_aritmetica = n * (2 * a + (n - 1) * d) / 2;
    cout << "Suma de la progresión aritmética: " << suma_aritmetica << endl;

    // Progresión Geométrica
    int a_geo = 2; // Término inicial
    int r = 2; // Razón común

    int ultimo_elemento = a_geo * pow(r, n - 1);
    int suma_geometrica = (a_geo * (1 - pow(r, n))) / (1 - r);
    cout << "Último elemento de la progresión geométrica: " << ultimo_elemento << endl;
    cout << "Suma de la progresión geométrica: " << suma_geometrica << endl;

    return 0;
}
