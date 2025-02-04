### Costrutto if
>[!note]
>Il costrutto `if` è il blocco di controllo più semplice in C. Ecco la sua struttura base:
>
>```c
>if (condizione) {
>    /* codice da eseguire se la condizione è vera */
>}
>```
>
>>[!tip]- Flusso di esecuzione
>>```mermaid
>>flowchart TD
>>    A[Inizio] --> B{Condizione}
>>    B -->|Vera| C["Esegui codice
>>   nel blocco if"]
>>    B -->|Falsa| D[Continua
>>    esecuzione]
>>    C --> D
>>    D --> E[Fine]
>>```
>
>Nel diagramma, "Vera" significa qualsiasi valore diverso da zero, mentre "Falsa" significa zero. Questo è il comportamento standard in C per le condizioni.

>[!example]
>```c
>int numero = 5;
>if (numero > 0) {
>    printf("Il numero è positivo\n");
>}
>```

### Condizioni
>[!note]
>Le condizioni in C utilizzano operatori di confronto che ritornano 0 (falso) o 1 (vero).

```c
/* Operatori di confronto */
int x = 5;
int y = 3;

int risultato = (x == y);    /* Uguaglianza (0) */
int diverso = (x != y);     /* Diversità (1) */
int maggiore = (x > y);     /* Maggiore di (1) */
int minore = (x < y);       /* Minore di (0) */
int maggioreuguale = (x >= y);  /* Maggiore o uguale (1) */
int minoreuguale = (x <= y);    /* Minore o uguale (1) */
```

### Operatori Logici
>[!note]
>Gli operatori logici combinano più condizioni.

```c
/* Operatori logici */
int risultato = (x > 0 && y < 10);  /* AND logico (1) */
risultato = (x > 0 || y < 10);       /* OR logico (1) */
risultato = !(x == y);               /* NOT logico (1) */
```

### Costrutto if-else
>[!note]
>Il costrutto if-else permette di eseguire un blocco di codice alternativo quando la condizione è falsa:
>
>```c
>if (condizione) {
>    /* codice da eseguire se la condizione è vera */
>} else {
>    /* codice da eseguire se la condizione è falsa */
>}
>```
>>[!tip]- Flusso di esecuzione
>>```mermaid
>>flowchart TD
>>    A[Inizio] --> B{Condizione}
>>    B -->|Vera| C["Esegui codice
>>    nel blocco if"]
>>    B -->|Falsa| D["Esegui codice
>>    nel blocco else"]
>>    C --> E[Continua]
>>    D --> E
>>    E --> F[Fine]
>>```

>[!example]
>```c
>int numero = 5;
>if (numero > 0) {
>    printf("Il numero è positivo\n");
>} else {
>    printf("Il numero è negativo o zero\n");
>}
>```

### Costrutto if-else if
>[!note]
>Per controllare più condizioni sequenzialmente:
>
>```c
>if (condizione1) {
>    /* codice da eseguire se condizione1 è vera */
>} else if (condizione2) {
>    /* codice da eseguire se condizione1 è falsa e condizione2 è vera */
>} else {
>    /* codice da eseguire se tutte le condizioni sono false */
>}
>```
>>[!tip]- Flusso di esecuzione
>>```mermaid
>>flowchart TD
>>    A[Inizio] --> B{Condizione 1}
>>    B -->|Vera| C["Esegui codice
>>    nel blocco if"]
>>    B -->|Falsa| D{Condizione 2}
>>    D -->|Vera| E["Esegui codice
>>    nel blocco else if"]
>>    D -->|Falsa| F["Esegui codice
>>    nel blocco else"]
>>    C --> G[Continua]
>>    E --> G
>>    F --> G
>>    G --> H[Fine]
>>```

>[!example]
>```c
>int numero = 5;
>if (numero > 0) {
>    printf("Il numero è positivo\n");
>} else if (numero == 0) {
>    printf("Il numero è zero\n");
>} else {
>    printf("Il numero è negativo\n");
>}
>```

### Costrutto Switch
>[!Note]
>Il costrutto switch è una struttura di controllo che permette di eseguire uno dei molti blocchi di codice in base al valore di un'espressione. È particolarmente utile quando si devono gestire molte condizioni diverse su un singolo valore.
>```c
>switch (espressione) {
>    case valore1:
>        /* codice da eseguire per valore1 */
>        break;
>    case valore2:
>        /* codice da eseguire per valore2 */
>        break;
>    default:
>        /* codice da eseguire se nessun caso corrisponde */
>        break;
>}
>```
>>[!tip]- Flusso di esecuzione
>>```mermaid
>>flowchart TD
>>    A[Inizio] --> B[Esegui espressione switch]
>>    B --> C{Confronta con case}
>>    C -->|Corrispondenza trovata| D[Esegui codice case]
>>    C -->|Nessuna corrispondenza| E{Esiste default?}
>>    D --> F{Presente break?}
>>    F -->|Sì| G[Salta al termine]
>>    F -->|No| H[Continua con case successivo]
>>    E -->|Sì| I[Esegui codice default]
>>    E -->|No| J[Salta al termine]
>>    G --> K[Fine]
>>    H --> K
>>    I --> K
>>    J --> K
>>```

>[!example]
>```c
>int giorno = 2;
>
>switch (giorno) {
>    case 1:
>        printf("Lunedì\n");
>        break;
>    case 2:
>        printf("Martedì\n");
>        break;
>    case 3:
>        printf("Mercoledì\n");
>        break;
>    case 4:
>        printf("Giovedì\n");
>        break;
>    case 5:
>        printf("Venerdì\n");
>        break;
>    case 6:
>        printf("Sabato\n");
>        break;
>    case 7:
>        printf("Domenica\n");
>        break;
>    default:
>        printf("Giorno non valido\n");
>        break;
>}
>```
