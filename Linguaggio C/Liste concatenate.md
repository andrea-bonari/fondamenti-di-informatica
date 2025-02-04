> [!note]  
> Le **liste concatenate** sono strutture dati dinamiche composte da nodi collegati tra loro tramite puntatori.  
> Ogni nodo contiene due elementi:
> 
> - **Dati** (informazioni memorizzate)
> - **Puntatore** al nodo successivo nella lista
> 
> Le operazioni fondamentali sulle liste sono:
> 
> - **Inserimento** (all'inizio, alla fine o in una posizione specifica)
> - **Cancellazione** di un nodo
> - **Ricerca** di un valore
> - **Visualizzazione** dell'intera lista

> [!example]
> 
> ```c
> #include <stdio.h>
> #include <stdlib.h>
> 
> /* Definizione della struttura del nodo */
> typedef struct Nodo {
>    int dato;
>    struct Nodo* prossimo;
> } Nodo;
> 
> /* Funzione per creare un nuovo nodo */
> Nodo* creaNodo(int valore) {
>    Nodo* nuovo = (Nodo*)malloc(sizeof(Nodo));
>    if (nuovo == NULL) {
>        printf("Errore di allocazione!\n");
>        return NULL;
>    }
>    nuovo->dato = valore;
>    nuovo->prossimo = NULL;
>    return nuovo;
> }
> ```

### Inserimento di un Nodo
> [!note]  
> Un nuovo nodo può essere inserito in diverse posizioni:
> 
> - **All'inizio** (testa)
> - **Alla fine** (coda)
> - **Dopo un nodo specifico**

> [!example]
> 
> ```c
> /* Inserimento all'inizio */
> void inserisciInTesta(Nodo** testa, int valore) {
>    Nodo* nuovo = creaNodo(valore);
>    if (nuovo == NULL) return;
>    nuovo->prossimo = *testa;
>    *testa = nuovo;
> }
> 
> /* Inserimento alla fine */
> void inserisciInCoda(Nodo** testa, int valore) {
>    Nodo* nuovo = creaNodo(valore);
>    if (nuovo == NULL) return;
> 
>    if (*testa == NULL) {
>        *testa = nuovo;
>        return;
>    }
> 
>    Nodo* temp = *testa;
>    while (temp->prossimo != NULL) {
>        temp = temp->prossimo;
>    }
>    temp->prossimo = nuovo;
> }
> ```

### Eliminazione di un Nodo
> [!note]  
> La rimozione di un nodo può avvenire in tre casi principali:
> 
> - **Rimozione dalla testa**
> - **Rimozione da una posizione specifica**
> - **Rimozione dalla coda**

> [!example]
> 
> ```c
> /* Eliminazione di un nodo con un valore specifico */
> void eliminaNodo(Nodo** testa, int valore) {
>    Nodo* temp = *testa;
>    Nodo* precedente = NULL;
> 
>    /* Se il nodo da eliminare è la testa */
>    if (temp != NULL && temp->dato == valore) {
>        *testa = temp->prossimo;
>        free(temp);
>        return;
>    }
> 
>    /* Cerca il nodo da eliminare */
>    while (temp != NULL && temp->dato != valore) {
>        precedente = temp;
>        temp = temp->prossimo;
>    }
> 
>    /* Se il valore non è nella lista */
>    if (temp == NULL) return;
> 
>    /* Rimuove il nodo */
>    precedente->prossimo = temp->prossimo;
>    free(temp);
> }
> ```

### Stampa della Lista
> [!example]
> 
> ```c
> /* Funzione per stampare la lista */
> void stampaLista(Nodo* testa) {
>    Nodo* temp = testa;
>    while (temp != NULL) {
>        printf("%d -> ", temp->dato);
>        temp = temp->prossimo;
>    }
>    printf("NULL\n");
> }
> ```