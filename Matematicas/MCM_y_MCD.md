# MINIMO COMUN MULTIPLO Y MAXIMO COMUN DIVISOR

## Factores

Los factores son números que dividen exactamente a otro número sin dejar un resto. Por ejemplo, los factores de 12 son 1, 2, 3, 4, 6 y 12.

### Ejemplo

Consideremos encontrar los factores de 12:
- 1 es un factor porque \( 12 \div 1 = 12 \)
- 2 es un factor porque \( 12 \div 2 = 6 \)
- 3 es un factor porque \( 12 \div 3 = 4 \)
- 4 es un factor porque \( 12 \div 4 = 3 \)
- 6 es un factor porque \( 12 \div 6 = 2 \)
- 12 es un factor porque \( 12 \div 12 = 1 \)

## MCM (Mínimo Común Múltiplo)

El mínimo común múltiplo (MCM) de dos o más enteros es el menor entero positivo que es divisible por cada uno de los números. Por ejemplo, el MCM de 4 y 6 es 12.

### ALGORITMOS

- **Método de Factorización Prima**: El MCM se puede calcular encontrando los factores primos de cada número y luego tomando el producto de la mayor potencia de todos los factores primos involucrados.

### IMPLEMENTACION 1 (ALGORITMO INGENUO)
```cpp
vector<int> encontrarFactoresPrimos(int n) {
    vector<int> factoresPrimos;
    for (int i = 2; i * i <= n; ++i) {
        while (n % i == 0) {
            factoresPrimos.push_back(i);
            n /= i;
        }
    }
    if (n > 1) {
        factoresPrimos.push_back(n);
    }
    return factoresPrimos;
}

int calcularMCM(int a, int b) {
    // Encontrar los factores primos de cada número
    vector<int> factoresA = encontrarFactoresPrimos(a);
    vector<int> factoresB = encontrarFactoresPrimos(b);

    // Combinar los factores primos de ambos números
    vector<int> factoresCombinados;
    int i = 0, j = 0;
    while (i < factoresA.size() && j < factoresB.size()) {
        if (factoresA[i] < factoresB[j]) {
            factoresCombinados.push_back(factoresA[i++]);
        } else if (factoresA[i] > factoresB[j]) {
            factoresCombinados.push_back(factoresB[j++]);
        } else {
            factoresCombinados.push_back(factoresA[i++]);
            j++;
        }
    }
    while (i < factoresA.size()) {
        factoresCombinados.push_back(factoresA[i++]);
    }
    while (j < factoresB.size()) {
        factoresCombinados.push_back(factoresB[j++]);
    }

    // Calcular el producto de todos los factores primos
    int mcm = 1;
    for (int factor : factoresCombinados) {
        mcm *= factor;
    }
    return mcm;
}
```

Como podemos ver tenemos un monton de codigo que si bien hace su trabajo aborda el problema de una manera muy ingenua, podemos abordar este problema de la siguiente manera.

### IMPLEMENTACION 2 (OPTIMIZADO)
```cpp
int calcularMCD(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int calcularMCM(int a, int b) {
    return (a * b) / calcularMCD(a, b);
}

```
### Explicación:

**`calcularMCD(int a, int b)`:** Esta función calcula el máximo común divisor (MCD) de dos números utilizando el algoritmo de Euclides. Este algoritmo calcula el MCD de manera eficiente encontrando el residuo de la división de `a` entre `b` repetidamente hasta que `b` se convierte en cero. El último valor no cero de `a` es el MCD.

**`calcularMCM(int a, int b)`:** Esta función calcula el mínimo común múltiplo (MCM) de dos números utilizando la relación entre el MCM y el MCD. La relación establece que el producto de dos números es igual al producto de su MCM y su MCD. Por lo tanto, dividir el producto de los números por su MCD da como resultado el MCM. Esta función simplemente devuelve el producto de `a` y `b` dividido por el resultado de `calcularMCD(a, b)`.

### Ejemplo:

Supongamos que queremos calcular el MCM de 4 y 6.

1. Calculamos el MCD utilizando el algoritmo de Euclides:
   - `calcularMCD(4, 6)`:
     - Primera iteración: `a = 6`, `b = 4`, luego `b = 6 % 4 = 2`.
     - Segunda iteración: `a = 4`, `b = 2`, luego `b = 4 % 2 = 0`.
     - El último valor no cero de `a` es `2`, por lo que el MCD es `2`.

2. Utilizamos el MCD calculado para encontrar el MCM:
   - `calcularMCM(4, 6) = (4 * 6) / 2 = 24 / 2 = 12`.

Por lo tanto, el MCM de 4 y 6 es 12.



Por ultimo tambien podemos optar por la implementacion nativa de c++ para resolver este problema que es la siguiente:
```cpp
#include <numeric>
#include <iostream>

using namespace std;

int main(){
    cout<<lcm(10,6);

    return 0;
}
```
## MCD (Máximo Común Divisor)

El máximo común divisor (MCD), también conocido como el mayor divisor común (MDC), de dos o más enteros es el entero positivo más grande que divide a cada uno de los números sin dejar un resto. Por ejemplo, el MCD de 12 y 18 es 6.

### ALGORITMOS

- **Método de Factorización Prima**: El MCD se puede calcular encontrando los factores primos de cada número y luego tomando el producto de la menor potencia de todos los factores primos involucrados.

### ALGORITMO INGENUO
```cpp
int mcd(int a, int b){
    int res = min(a,b);

    while(res > 0){
        if((a % res == 0) && (b % res == 0)){
            break;
        }

        res--;
    }
}
```
Si bien este algoritmo podria funcionar en muchos casos, existe una manera mas eficiente de hacer dicho calculo.

Para poder calcular este problema podemos lo que llamamos como el algoritmo de Euclides.

### Algoritmo de Euclides

El algoritmo de Euclides es un método eficiente para encontrar el máximo común divisor (MCD) de dos números enteros positivos. Se basa en el principio de que el MCD de dos números no cambia si se resta el número más pequeño del más grande repetidamente hasta que uno de los números sea cero.

**Ejemplo:**

Supongamos que queremos encontrar el MCD de 48 y 18 utilizando el algoritmo de Euclides:

1. Comenzamos dividiendo el número más grande por el más pequeño y obtenemos el residuo:
   - \( 48 \ 18 = 2 \) con un residuo de 12.

2. Luego, tomamos el divisor (18) como el nuevo número más grande y el residuo (12) como el nuevo número más pequeño, y repetimos el proceso:
   - \( 18 \ 12 = 1 \) con un residuo de 6.

3. Nuevamente, tomamos el divisor (12) como el nuevo número más grande y el residuo (6) como el nuevo número más pequeño:
   - \( 12 \ 6 = 2 \) con un residuo de 0.

4. En este punto, el residuo es cero, por lo que detenemos el proceso. El último divisor no cero (6) es el MCD de 48 y 18.

Por lo tanto, el MCD de 48 y 18 es 6. Este proceso es el esquema básico del algoritmo de Euclides y es muy eficiente para calcular el MCD de dos números enteros positivos.


### IMPLEMENTACION 
```cpp
int euclides(int a, int b){
    while(a % b > 0){
        int aux = b;
        b = a % b;
        a = aux;
    }

    return b;
}
```

### IMPLEMENTACION 2
```cpp
int euclides(int a, int b){
    while(a != b){
        if(a > b){
            a = a-b;
        }
        else{
            b = b-a;
        }
    }

    return a;
}
```

### IMPLEMENTACION 3 (OPTIMIZADO)
```cpp
int euclides(int a, int b){
    if(b == 0){
        return a;
    }

    return euclides(b, a%b);
}
```

Tambien podriamos usar una implementacion de esta funcion implementada nativamente dentro de C++, lo unico que necesitamos es llamar a la libreria "algorithm" (esto podria cambiar de acuerdo a la version en la que estemos).
```cpp
#include <algorithm>
#include <iostream>

using namespace std;

int main(){
    int a = 10 , 15;

    cout<<gcd(10,15)>>

    return 0;
}

```