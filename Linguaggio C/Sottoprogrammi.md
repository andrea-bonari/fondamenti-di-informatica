>[!note]
>I sottoprogrammi in C sono blocchi di codice riutilizzabili che possono ricevere parametri e restituire valori. Ecco la struttura base:
>
>```c
>/* Prototipo della funzione */
>tipo_ritorno nome_funzione(tipo_parametro1 param1, tipo_parametro2 param2);
>
>/* Definizione della funzione */
>tipo_ritorno nome_funzione(tipo_parametro1 param1, tipo_parametro2 param2) {
>    /* corpo della funzione */
>    return valore;
>}
>```

>[!example]
>```c
>#include <stdio.h>
>
>/* Prototipo della funzione */
>int somma(int a, int b);
>
>int main() {
>    int x = 5, y = 7;
>    int risultato = somma(x, y);
>    printf("La somma è: %d\n", risultato);
>    return 0;
>}
>
>/* Definizione della funzione */
>int somma(int a, int b) {
>    return a + b;
>}
>```

È possibile accorpare il prototipo e la definizione della funzione con la seguente sintassi:
```c
/* Definizione della funzione */
tipo_ritorno nome_funzione(tipo_parametro1 param1, tipo_parametro2 param2) {
    /* corpo della funzione */
    return valore;
}
```

### Passaggio parametri
>[!note]
Il passaggio dei parametri può avvenire in due modi principali:
>- Passaggio per valore, dove il sottoprogramma modifica solo una copia locale del parametro
>- Passaggio per riferimento, dove il sottoprogramma modifica il valore originale del parametro
>
>Si ricorda che ogni array è passato per riferimento.

>[!example]
>```c
>/* Passaggio per valore */
>void funzionePerValore(int x) {
>    x = x + 1;  /* Modifica solo la copia locale
>}
>
>/* Passaggio per riferimento (usando puntatori) */
>void funzionePerRiferimento(int *x) {
>    *x = *x + 1;  /* Modifica il valore originale
>}
>```

