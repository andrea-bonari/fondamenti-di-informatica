>[!note]
>I puntatori sono variabili speciali che memorizzano indirizzi di memoria. Ecco la loro struttura base:
>
>```c
>/* Dichiarazione di un puntatore */
>tipo_dato *nome_puntatore;
>
>/* Inizializzazione di un puntatore */
>tipo_dato variabile;
>tipo_dato *puntatore = &variabile;
>```

I puntatori in C sono variabili speciali che memorizzano indirizzi di memoria. Ecco un esempio pratico che mostra come utilizzarli senza passaggio parametri:

>[!example]
>```c
>#include <stdio.h>
>
>int main() {
>    /* Dichiarazione di variabili e puntatori */
>    int numero = 10;
>    int *puntatore = &numero;  /* puntatore che punta a numero */
>    
>    /* Stampa dei valori */
>    printf("Valore di numero: %d\n", numero);
>    printf("Indirizzo di numero: %p\n", (void*)&numero);
>    printf("Valore puntato da puntatore: %d\n", *puntatore);
>    
>    /* Modifica del valore attraverso il puntatore */
>    *puntatore = 20;
>    printf("Valore di numero dopo modifica: %d\n", numero);
>    
>    /* Utilizzo dell'operatore -> */
>    struct Persona {
>        char nome[50];
>        int eta;
>    };
>    
>    struct Persona persona;
>    struct Persona *ptr_persona = &persona;
>    
>    /* Accesso ai membri della struttura */
>    strcpy(ptr_persona->nome, "Mario");
>    ptr_persona->eta = 25;
>    
>    printf("Nome: %s\n", ptr_persona->nome);
>    printf("Età: %d\n", ptr_persona->eta);
>    
>    return 0;
>}
>```

