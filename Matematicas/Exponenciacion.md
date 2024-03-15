## EXPONENCIACION
Si bien la exponenciacion puede no ser un tema muy complejo a primera vista, podemos encontrar situaciones donde el problema radique justamente en la implementacion de esta de manera eficiente siendo asi podemos abarcar las siguientes implementaciones.

### ALGORITMO INGENUO
```cpp
int potencia(int x, int n){
    int res = 1;

    for(int i = 0; i < n; i++){
        res = res * x;
    }

    return res;
}
```
Bajo la direccion de este algoritmo tenemos una complejidad de O(n) que puede ser una respuesta aceptable, sin embargo existen situaciones donde la misma puede no ser la mas optima si consideramos que los inputs seran numeros grandes.

Siendo asi podemos tomar la siguiente implementacion

### ALGORITMO EFICIENTE
```cpp
int potenacia(int x, int n){
    if(n == 0){
        return 1;
    }

    int temp =  potencia( x,  n/2);
    temp = temp * temp;

    if(n % 2 == 0){
        return temp;
    }
    else{
        return temp * x;
    }
}
```
Como podemos observar el algoritmo implementado tiene una forma recursiva dado que se llama a si misma dentro de la funcion aunque esto pueda parecer que tiene una mayor complejidad, no es asi dado que si analizamos el algoritmo de manera cuidadosa podremos encontrar que el numero de iteraciones hasta llegar a la condicion principal tomara la mitad de tiempo que iterar desde 0 hasta n, teniendo asi una complejidad de O(log n).
