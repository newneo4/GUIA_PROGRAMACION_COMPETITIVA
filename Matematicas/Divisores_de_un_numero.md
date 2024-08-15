## Divisores de un Número

Los divisores de un número son todos los números enteros positivos que pueden dividir uniformemente al número dado, es decir, que el residuo de la división es cero. Cada número tiene al menos dos divisores: 1 y él mismo. Los divisores de un número pueden ser utilizados para diversas aplicaciones matemáticas, como la factorización, el cálculo de números perfectos, y para resolver problemas de divisibilidad.

### Ejemplo

Por ejemplo, los divisores de 12 son 1, 2, 3, 4, 6 y 12, ya que todos estos números pueden dividir a 12 sin dejar un residuo.

Una implementacion ingenua para hallar todos los divisores dado un numero n podria ser la siguiente:

### Algoritmo ingenuo
```cpp
void divisores(int n){
    for(int i = 1; i <=n; i++){
        if(n % i == 0){
            cout<<i<<' ';
        }
    }
}
```

Sin embargo, esta solucion necesita recorrer todos los numeros desde 1 hasta n, esto podria mejorarse de la siguiente manera:

### Algoritmo mejorado
```cpp
void divisores(int n){
    for(int i = 1; i * i <= n; i++){
        if(n % i == 0){
            cout<<i<<' ';

            if(i != n/i) cout<<n/i;
        }
    }
}
```
Como podemos observar ahora hemos reducido de manera sustancial las iteraciones que necesitamos para poder hallar todos los divisores dado que unicamente necesitamos iterar hasta la raiz cuadrada de n.

Si somos un poco observados podremos darnos cuenta que aunque el algoritmo halla los divisores de manera eficiente este los imprime en desorden, esto puede no ser una molestia del todo, sin embargo, dados ciertos problemas podriamos querer obtener los numeros de manera ordenada. Una idea que nos puede pasar por la cabeza es crear un array e ir almacenando los elementos en este y finalmente ordenarlos, esto no es una mala idea, pero existe una mucho mejor que no requiere de espacio extra para lograrlo.

### Algoritmo eficiente
```cpp
void divisores(int n){
    int i;

    //primero imprimimos los divisores de i hasta raiz de n
    for(int i = 1; i * i < n; i++){
        if(n % i == 0) cout<<i<<' ';
    }

    //ahora imprimimos los numeros de raiz de n hasta n
    for(; i >= 1; i--){
        if(n % i == 0) cout<<n/i<<' ';
    }
}
```

La naturaleza del algoritmo radica en imprimir primero los divisores menores que vendrian a ser aquellos que son menores de la raiz de n, y posteriormente aquellos que incluyen a la raiz de n hasta el mismo n, esto recurriendo a la idea de que los divisores vienen en pares como podemos observar en el siguiente ejemplo:
$$ 
    20 = 1 * 20 \\
    \\
    20 = 2 * 10 \\
    \\
    20 = 4 * 5
$$

Finalmente no asignamos un nuevo valor para n, dado que el primer for deja de ejecutarse cuando n es igual a la raiz cuadrada de n, quedando unicamente volver a iterar de manera inversa.
