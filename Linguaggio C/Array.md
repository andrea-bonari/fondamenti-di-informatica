>[!note]
>Gli array sono strutture dati che permettono di memorizzare più elementi dello stesso tipo in posizioni di memoria contigue. Ecco la struttura base degli array mono-dimensionali:
>
>```c
>tipo_dato nome_array[dimensione];
>tipo_dato nome_array[dimensione] = {valore1, valore2, ...};
>```
>Dove `dimensione` è un valore costante non ottenuto in runtime.

>[!example]
>```c
>#include <stdio.h>
>#define LEN 5
>
>int main() {
>    /* Dichiarazione e inizializzazione di un array */
>    int numeri[LEN] = {1, 2, 4, 8, 16};
>    
>    /* Accesso e modifica degli elementi */
>    printf("Elemento all'indice 2: %d\n", numeri[2]);
>    numeri[3] = 9721;
>    
>    /* Stampa di tutti gli elementi */
>    for (int i = 0; i < LEN; i++) {
>        printf("%d ", numeri[i]);
>    }
>    printf("\n");
>    
>    return 0;
>}
>```

### Array bidimensionali
>[!note]
>Gli array bi-dimensionali sono strutture che organizzano i dati in una tabella di righe e colonne. Ecco la loro struttura:
>
>```c
>tipo_dato nome_array[num_righe][num_colonne];
>tipo_dato nome_array[num_righe][num_colonne] = {
>    {valore1_riga1, valore2_riga1, ...},
>    {valore1_riga2, valore2_riga2, ...},
>    ...
>};
>```
>
>Come per gli array unidimensionali `num_righe` e `num_colonne` è un valore costante non ottenuto in runtime.

>[!example]
>```c
>#include <stdio.h>
>#define H 2
>#define W 3
>
>
>int main() {
>    /* Dichiarazione e inizializzazione di una matrice 2x3 */
>    int matrice[H][W] = {
>        {1, 2, 3},
>        {4, 5, 6}
>    };
>  
>    /* Accesso e modifica degli elementi */
>    printf("Elemento in riga 0, colonna 1: %d\n", matrice[0][1]);
>    matrice[1][2] = 9721;
>    
>    /* Stampa di tutti gli elementi */
>    for (int i = 0; i < H; i++) {
>        for (int j = 0; j < W; j++) {
>            printf("%d ", matrice[i][j]);
>        }
>        printf("\n");
>    }
>    
>    return 0;
>}
>```

