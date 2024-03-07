# MEDIA Y MEDIANA

## MEDIA

La media, también conocida como promedio, es una medida de tendencia central que representa la suma de todos los valores en un conjunto de datos dividida por el número de valores. Se calcula utilizando la fórmula:

$$
\text{Media} = \frac{\sum_{i=1}^{n} x_i}{n}
$$

Donde:
- \( x_i \): Cada valor individual en el conjunto de datos.
- \( n \): El número total de valores en el conjunto de datos.

## MEDIANA

La mediana es otra medida de tendencia central que representa el valor central de un conjunto de datos cuando se ordena en orden ascendente o descendente. Si el conjunto de datos tiene un número impar de valores, la mediana es el valor central. Si el conjunto de datos tiene un número par de valores, la mediana es el promedio de los dos valores centrales.

### Implementación en C++

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

// Función para calcular la media de un conjunto de datos
double mean(const vector<int>& data) {
    int sum = 0;
    for (int value : data) {
        sum += value;
    }
    return static_cast<double>(sum) / data.size();
}

// Función para calcular la mediana de un conjunto de datos
double median(vector<int> data) {
    size_t size = data.size();
    sort(data.begin(), data.end());
    if (size % 2 == 0) {
        return (data[size / 2 - 1] + data[size / 2]) / 2.0;
    } else {
        return data[size / 2];
    }
}

int main() {
    vector<int> dataset = {4, 7, 2, 9, 5, 1, 8};
    
    // Calcular e imprimir la media
    cout << "Media: " << mean(dataset) << endl;

    // Calcular e imprimir la mediana
    cout << "Mediana: " << median(dataset) << endl;

    return 0;
}
