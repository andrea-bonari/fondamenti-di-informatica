>[!note]
>Le stringhe in C sono array di caratteri che terminano con il carattere nullo (`\0`). La libreria `string.h` fornisce diverse funzioni per manipolare le stringhe. Ecco la struttura base:
>
>```c
>#include <string.h>
>
>char stringa[dimensione];  /* Dimensione deve essere >= lunghezza + 1 per il terminatore \0 */
>```

>[!example]
>```c
>#include <stdio.h>
>#include <string.h>
>
>int main() {
>    char str1[20] = "Ciao\0";
>    char str2[20] = "Mondo\0";
>    
>    /* Copia str2 in str1 */
>    strcpy(str1, str2);
>    printf("Dopo strcpy: %s\n", str1);
>    
>    /* Concatena str2 a str1 */
>    strcat(str1, "!");
>    printf("Dopo strcat: %s\n", str1);
>    
>    /* Confronta le stringhe */
>    int risultato = strcmp(str1, str2);
>    printf("Risultato strcmp: %d\n", risultato);
>    
>    /* Calcola la lunghezza */
>    int lunghezza = strlen(str1);
>    printf("Lunghezza: %d\n", lunghezza);
>    
>    return 0;
>}
>```

Le funzioni principali di `string.h` sono:

```c
/* Copia str2 in str1 */
strcpy(str1, str2);

/* Concatena str2 a str1 */
strcat(str1, str2);

/* Confronta str1 con str2 (0 se sono uguali <0 se str1 < str2 ) e viceversa */
strcmp(str1, str2);

/* Calcola la lunghezza di str1 */
strlen(str1);

/* Copia n caratteri da str2 a str1 */
strncpy(str1, str2, n);

/* Concatena n caratteri da str2 a str1 */
strncat(str1, str2, n);
```
