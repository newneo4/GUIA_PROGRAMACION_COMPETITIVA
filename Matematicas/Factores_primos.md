## FACTORES PRIMOS
## Factores Primos

Los factores primos son los números primos que, multiplicados entre sí, dan como resultado un número dado. Un número primo es un número natural mayor que 1 que solo tiene dos divisores positivos: él mismo y 1.

Los factores primos son fundamentales en matemáticas y tienen varias aplicaciones, como la criptografía, la factorización de números grandes y la resolución de problemas de divisibilidad.

### Ejemplo

Por ejemplo, si queremos encontrar los factores primos de 24, primero descompondríamos 24 en sus factores primos:

- 24 = 2 × 2 × 2 × 3

En este caso, los factores primos de 24 son 2 y 3.

Una implementacion ingenua para poder hallar los factores primos dado un numero n podria ser la siguiente:

### Algoritmo ingenuo
```cpp
bool esPrimo(int n){
    if(n == 1) return false;
    if(n == 2 || n == 3) return true;
    if(n % 2 == 0 || n % 3 == 0) return false;

    for(int i = 5; i * i <= n; i+= 6){
        if(n % i == 0 || n % (i+1) == 0) return false;
    }

    return true;
}

void factoresPrimos(int n){
    for(int i = 2; i <= n; i++){
        if(esPrimo(i)){
            int x = i;
            while(n % x == 0){
                cout<<i<<' ';
                x = x * i;
            }
        }
    }
}
```
Como podemos observar si bien tenemos un algoritmo que logra buscar de manera efectiva los factores primos de un numeros n, este es poco eficiente ya que recorre completamente todos los numeros desde 2 hasta n, ademas de que esta anidado dos veces, la primera al llamar a la funcion <strong>esPrimo</strong> y la segunda con el ciclo while dentro de este.

Una forma mas efectiva de hacer esto es mediante el siguiente algoritmo.
### Algoritmo mejorado
```cpp
void factoresPrimos(int n){
    if(n <= 1) return;

    for(int i = 2; i * i <= n; i++){
        while(n % i == 0){
            cout<<i;
            n /= i;
        }
    }

    if(n > 1) cout<<n;
}
```
Como podemos ver en este punto hemos reducido sustancialmente las iteraciones, dado que ya no tenemos un for anidado tres veces, ni tenemos la intencion de iterar sobre todos los numeros desde 2 hasta n. Sin embargo, podemos seguir optimizando aun mas este codigo, siguiente la idea expuesta en el archivo de numeros primos, que sugiere eliminar primero los multiplos de 2 y 3, para asi poder seguir con los demas primos que tienen la forma de:

$$ 
{6n+1} \quad \text{o} \quad {6n-1}  
$$

## Algoritmo eficiente
```cpp
void factoresPrimos(int n){
    if(n <= 1) return;

    while(n % 2 == 0){
        cout<<2<<' ';
        n /= 2;
    }

     while(n % 3 == 0){
        cout<<3<<' ';
        n /= 3;
    }

    for(int i = 5; i * i <= n; i+=6){
        while(n % i == 0){
            cout<<i<<' ';
            n /= i;
        }

        while(n % (i+2) == 0){
            cout<<i+2<<' ';
            n /= (i+2);
        }
    }

    if(n > 3) cout<<n;
}
```
