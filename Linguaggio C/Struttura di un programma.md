>[!note]
>La struttura base di un programma C89 è composta da tre elementi fondamentali:
>```c
>#include <stdio.h>
>
>int main(void) {
>    /* Il tuo codice qui */
>    return 0;
>}
>```
>
>- `#include <stdio.h>`: direttiva del preprocessore che include la libreria standard per l'input/output
>- `int main(void)`: funzione principale che ritorna un valore intero, dove `void` indica che non accetta parametri
>- `return 0`: indica il corretto termine del programma

### Tipi di Dati
>[!note]
>I tipi di dati principali sono:
>
>| Tipo | Dimensione | Valore Minimo | Valore Massimo |
>| --- | --- | --- | --- |
>| `char` | 1 byte | -128 | 127 |
>| `short int` | 2 bytes | -32768 | 32767 |
>| `int` | 2 bytes | -32768 | 32767 |
>| `long int` | 4 bytes | -2147483648 | 2147483647 |
>| `float` | 4 bytes | ~1.2E-38 | ~3.4E38 |
>| `double` | 8 bytes | ~2.3E-308 | ~1.8E308 |

### Operatori
>[!note]
>Gli operatori permettono di manipolare i dati di una o più variabili.
##### Operatori Aritmetici
```c
int x = 5;
int y = 3;

/* Operazioni aritmetiche di base */
int somma = x + y;      /* Somma */
int differenza = x - y; /* Differenza */
int prodotto = x * y;   /* Prodotto */
int quoziente = x / y;  /* Divisione intera */
int resto = x % y;      /* Modulo */
```

##### Operatori Logici
```c
/* Operatori logici */
int risultato = (x > 0 && y < 10);  /* AND logico */
risultato = (x > 0 || y < 10);       /* OR logico */
risultato = !(x == y);               /* NOT logico */
```

##### Operatori Relazionali
```c
/* Operatori relazionali */
int uguale = (x == y);          /* Uguaglianza */
int diverso = (x != y);         /* Diversità */
int maggiore = (x > y);         /* Maggiore di */
int minore = (x < y);           /* Minore di */
int maggioreuguale = (x >= y);  /* Maggiore o uguale */
int minoreuguale = (x <= y);    /* Minore o uguale */
```

### Cast (Conversioni di Tipo)
>[!note]
>Il sistema di cast permette al compilatore di convertire un dato in un altro tipo, si distingue in cast implicito e esplicito:
>- Il cast implicito avviene automaticamente quando il compilatore lo ritiene sicuro
>- Il cast esplicito si utilizza quando si vuole forzare una conversione che il compilatore non effettuerebbe automaticamente
>
>È necessario prestare attenzione alle perdite di precisione durante le conversioni.

>[!example] Esempio cast implicito
>
>```c
>double x = 5.5;     /* Conversione implicita da intero a double */
>int y = x;          /* Conversione implicita da double a int */
>```

>[!example] Esempio cast esplicito
>```c
>double x = 5.5;
>int y = (int)x;     /* Cast esplicito da double a int */
>
>char c = 'A';
>int z = (int)c;     /* Cast esplicito da char a int */
>```

### Istruzione \#define
>[!note]
>Il direttiva `#define` è un comando del preprocessore che permette di definire costanti simboliche e macro. Ecco la sua struttura base:
>
>```c
>#define NOME_VALORE valore
>#define NOME_MACRO(parametri) codice_sostituzione
>```

>[!example]
>```c
>#include <stdio.h>
>
>#define MAX_SIZE 100
>#define PI 3.14159
>
>#define STAMPA_MESSAGGIO(messaggio) printf("%s\n", messaggio)
>
>int main() {
>    int array[MAX_SIZE];
>    STAMPA_MESSAGGIO("Hello World");
>    return 0;
>}
>```

### Commenti
>[!note]
>I commentiin C sono utilizzati per documentare il codice su più righe. Ecco la loro struttura:
>
>```c
>/* Questo è un commento
>   che può estendersi su più righe
>   fino alla chiusura */
>```
