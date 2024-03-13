# CONTANDO EL NÚMERO DE DÍGITOS

Para contar los dígitos de un número n, podemos considerar el siguiente algoritmo.

## ALGORITMO ITERATIVO

```cpp
int contarDigitos(int n){
    int contador = 0;

    while(n != 0){
        n /= 10;
        ++contador;
    }

    return contador;
}
```
La complejidad de este algoritmo es O(n).

## ALGORITMO RECURSIVO

```cpp
int contarDigitos(long n){
    
    if(n == 0) return 0;

    return 1 + contarDigitos(n / 10);
}
```

## SOLUCIÓN LOGARÍTMICA

```cpp
int contarDigitos(int n){
    return floor(log10(n) + 1);
}
```
