> [!note]  
> In C, la funzione `main()` può accettare due parametri opzionali:
> 
> ```c
> int main(int argc, char *argv[])
> ```
> 
> - **`argc`** (argument count) è un intero che indica il numero di argomenti passati al programma, incluso il nome dell'eseguibile.
> - **`argv`** (argument vector) è un array di stringhe (`char*`), in cui ogni elemento rappresenta un argomento passato da riga di comando.
> 
> Il primo elemento `argv[0]` è sempre il nome dell'eseguibile, mentre gli argomenti successivi sono quelli forniti dall'utente.

> [!example]
> 
> ```c
> #include <stdio.h>
> 
> int main(int argc, char *argv[]) {
>    printf("Numero di argomenti: %d\n", argc);
> 
>    for (int i = 0; i < argc; i++) {
>        printf("Argomento %d: %s\n", i, argv[i]);
>    }
> 
>    return 0;
> }
> ```
> 
> **Esecuzione da terminale:**
> 
> ```
> ./programma arg1 arg2 arg3
> ```
> 
> **Output:**
> 
> ```
> Numero di argomenti: 4
> Argomento 0: ./programma
> Argomento 1: arg1
> Argomento 2: arg2
> Argomento 3: arg3
> ```

### Conversione di Argomenti Numerici
> [!note]  
> Poiché `argv` è un array di stringhe (`char*`), se gli argomenti devono essere usati come numeri, devono essere convertiti con funzioni come `atoi()` o `strtol()`.

> [!example]
> 
> ```c
> #include <stdio.h>
> #include <stdlib.h>
> 
> int main(int argc, char *argv[]) {
>    if (argc < 3) {
>        printf("Uso: %s numero1 numero2\n", argv[0]);
>        return 1;
>    }
> 
>    int num1 = atoi(argv[1]);  // Converte il primo argomento in intero
>    int num2 = atoi(argv[2]);  // Converte il secondo argomento in intero
> 
>    printf("Somma: %d\n", num1 + num2);
>    return 0;
> }
> ```
> 
> **Esecuzione:**
> 
> ```
> ./programma 5 10
> ```
> 
> **Output:**
> 
> ```
> Somma: 15
> ```
