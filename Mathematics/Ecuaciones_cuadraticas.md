## ECUACIONES CUADRÁTICAS

$$
ax^2 + bx + c = 0
$$

Donde podemos considerar las siguientes operaciones:
- Determinante:
$$ 
D = b^2 - 4ac    
$$
- El valor de x:
$$
x = \frac{{-b \pm \sqrt{{b^2 - 4ac}}}}{{2a}}
$$

Donde podemos considerar las siguientes conclusiones dado el valor del determinante:

- Si \( D < 0 \), la ecuación tiene raíces imaginarias.
- Si \( D = 0 \), la ecuación tiene dos raíces iguales.
- Si \( D > 0 \), la ecuación tiene dos raíces distintas.

### Implementación en C++

```cpp
#include <iostream>
#include <cmath>

using namespace std;

int main() {
    double a, b, c;
    cout << "Ingresa los coeficientes (a, b, c): ";
    cin >> a >> b >> c;

    double discriminante = b * b - 4 * a * c;

    if (discriminante < 0) {
        cout << "La ecuación tiene raíces imaginarias." << endl;
    } else if (discriminante == 0) {
        double raiz = -b / (2 * a);
        cout << "La ecuación tiene dos raíces iguales: " << raiz << endl;
    } else {
        double raiz1 = (-b + sqrt(discriminante)) / (2 * a);
        double raiz2 = (-b - sqrt(discriminante)) / (2 * a);
        cout << "La ecuación tiene dos raíces distintas: " << raiz1 << " y " << raiz2 << endl;
    }

    return 0;
}
