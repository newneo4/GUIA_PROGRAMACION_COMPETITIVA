## CRIBA DE ERATOSTENES
La criba de Eratóstenes es un algoritmo utilizado para encontrar todos los números primos hasta un cierto límite.

El proceso básico de la criba de Eratóstenes implica los siguientes pasos:

1. Inicializar una lista de números del 2 al límite especificado.
2. Empezando por el primer número (2), marcar todos sus múltiplos como compuestos.
3. Encontrar el siguiente número no marcado en la lista, este será el siguiente número primo.
4. Repetir el paso 2 para este nuevo número primo.
5. Continuar hasta que se hayan marcado todos los múltiplos de los números primos hasta el límite especificado.
6. Los números que no han sido marcados son primos y se devuelven como resultado.

El algoritmo tiene una complejidad de O(n log log n), donde n es el límite superior especificado.

### Implementacion simple
```cpp
void cribaErastotenes(int n){
    // creamos el vector donde guardaremos los valores precalculados
    vector<bool>criba(n+1, true);

    //buscamos los valores primos
    for(int i = 2; i * i <= n; i++){
        if(criba[i]){
            for(int j = i * i; j <= n; j += i){
                criba[i] = false;
            }
        }
    }

    //imprimimos los valores
    for(int i = 2; i <= n; i++){
        if(criba[i]) cout<<i<<' ';
    }
}
```

### Ejemplo

Dado un numero necesitamos imprimir todos los numeros primos menores a este.

Podriamos abordar este problema de tal manera que no necesitamos implementar la criba de Eratostenes, sin embargo, podremos ver que este no es del todo eficiente.


### Algoritmo ingenuo
```cpp
void primosMenores(int n){
    for(int i = 2; i <= n; i++){
        if(esPrimo(i)) cout<<i<<' ';
    }
}
```

Como podemos observar tenemos implementa un bucle que dentro de este implementa la funcion <i>esPrimo</i> que ya vimos anteriormente tenia una complejidad de raiz cuadrada de n. Dando asi como complejidad final un O(n* (n**0.5)).

Entonces, consideramos una solucion mucho mas optima usando la criba de eratostenes de la siguiente forma.

```cpp
void criba(int n){
    vector<bool>criba(n+1, true);

    for(int i = 2; i <= n; i++){
        if(criba[i]){
            cout<<i<<' ';
            for(int j = i * i; j < n; j += i){
                criba[i] = false;
            }
        }
    }
}
```

En apareciencia ambos algoritmos tienen la misma complejidad, pero debemos tomar en cuenta que en el segundo algoritmo no se hace una comprobacion acerca del numero si es primo o no, en su lugar comprobamos si el numero en cuestion tiene un valor booleano positivo (indica que es primo) asociado a este en nuestro array. Siendo así que la complejidad se reduce drasticamente teniendo ahora el algoritmo una complejidad de O(n log log n) que es un valor bastante pequeño casi lineal.
