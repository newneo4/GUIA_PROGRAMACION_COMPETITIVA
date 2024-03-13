# NUMEROS PALINDROMOS

Cuando hablamos de palíndromos, nos referimos a cuando podemos escribir una expresión de manera inversa y esta seguirá siendo exactamente la misma que al inicio.

Por ejemplo:
- 323 es palíndromo porque al invertirlo, sigue siendo 323.
- 423 no es palíndromo porque al invertirlo, se convierte en 324.

```cpp
bool esPalindromo(int n){
    int aux = 0;
    int temp = n;

    // Reversión del número
    while(temp != 0){
        int digito = temp % 10;
        aux = aux * 10 + digito;
        temp /= 10; 
    }

    // Verificar si el número original es igual a su reverso
    return (aux == n);
}
