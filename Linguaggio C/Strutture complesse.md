>[!note]
>Le strutture (`struct`) sono tipi di dati composti che permettono di raggruppare variabili di tipo diverso in un'unica unità. Il `typedef` può essere utilizzato per creare alias più semplici per le strutture. Ecco la struttura base:
>
>```c
>struct nome_struttura {
>    tipo_dato membro1;
>    tipo_dato membro2;
>    /* altri membri... */
>};
>
>/* Definizione con typedef */
>typedef struct nome_struttura NomeStruttura;
>```

>[!example]
>```c
>#include <stdio.h>
>
>/* Definizione della struttura */
>struct Studente {
>    char nome[50];
>    int eta;
>    float media;
>};
>
>/* Creazione di un alias con typedef */
>typedef struct Studente Studente;
>
>int main() {
>    /* Dichiarazione di una variabile usando il typedef */
>    Studente studente1;
>    
>    /* Inizializzazione dei membri */
>    snprintf(studente1.nome, sizeof(studente1.nome), "Mario");
>    studente1.eta = 20;
>    studente1.media = 8.5;
>    
>    /* Accesso ai membri */
>    printf("Nome: %s\n", studente1.nome);
>    printf("Età: %d\n", studente1.eta);
>    printf("Media: %.2f\n", studente1.media);
>    
>    return 0;
>}
>```

Esistono due modi principali per definire una struttura con `typedef`:

```c
/* Metodo 1: Definizione separata */
struct Studente {
    char nome[50];
    int eta;
    float media;
};
typedef struct Studente Studente;

/* Metodo 2: Definizione combinata */
typedef struct Studente {
    char nome[50];
    int eta;
    float media;
} Studente;
```
