> [!note]  
> L'allocazione dinamica della memoria in C consente di riservare memoria durante l'esecuzione del programma, invece che a tempo di compilazione.  
> Questo è utile quando non si conosce in anticipo la quantità di memoria necessaria.  
> La libreria `<stdlib.h>` fornisce due funzioni principali per gestire la memoria dinamica:
>
> - **`malloc()`** → Alloca un blocco di memoria non inizializzata
> - **`free()`** → Libera la memoria allocata per evitare perdite di memoria (memory leaks)

 - **`malloc(size_t size)`**: Alloca `size` byte di memoria ma non inizializza il contenuto. Siccome restituisce un puntatore `void*` è necessario effettuare un cast
 - **`free(void* ptr)`**: Libera la memoria allocata, dopo averlo eseguito il puntatore diventa invalido

> [!example]
> 
> ```c
> #include <stdio.h>
> #include <stdlib.h>
> 
> int main() {
>    int *p;  
>    p = (int *)malloc(5 * sizeof(int));  /* Allocazione di un array di 5 interi */
>    
>    if (p == NULL) {
>        printf("Allocazione fallita!\n");
>        return 1;
>    }
>    
>    for (int i = 0; i < 5; i++) {
>        p[i] = i * 2;
>        printf("%d ", p[i]);
>    }
> 
>    free(p);  /* Libera la memoria allocata */
>    return 0;
> }
> ```
