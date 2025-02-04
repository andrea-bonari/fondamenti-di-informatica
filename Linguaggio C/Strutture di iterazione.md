### Costrutto while
>[!note]
>Il costrutto `while` è un ciclo che continua l'esecuzione finché una condizione specificata rimane vera. Ecco la sua struttura base:
>
>```c
>while (condizione) {
>    /* codice da eseguire finché la condizione è vera */
>}
>```
>
>>[!tip]- Flusso di esecuzione
>>```mermaid
>>flowchart TD
>>    A[Inizio] --> B[Esegui espressione di inizializzazione]
>>    B --> C{Valuta condizione}
>>    C -->|Vera| D[Esegui corpo del ciclo]
>>    D --> E[Esegui espressione di aggiornamento]
>>    E --> C
>>    C -->|Falsa| F[Continua esecuzione dopo il ciclo]
>>    F --> G[Fine]
>>
>>    style A fill:#90EE90,stroke:#006400,color:#000000
>>    style B fill:#FFB6C1,stroke:#8B0000,color:#000000
>>    style C fill:#87CEEB,stroke:#00008B,color:#000000
>>    style D fill:#DDA0DD,stroke:#800080,color:#000000
>>    style E fill:#FFB6C1,stroke:#8B0000,color:#000000
>>    style F fill:#98FB98,stroke:#006400,color:#000000
>>    style G fill:#FFB6C1,stroke:#8B0000,color:#000000
>>```

L'espressione di inizializzazione viene eseguita una sola volta all'inizio del ciclo
- La condizione viene valutata prima di ogni iterazione
- Se la condizione è vera, il corpo del ciclo viene eseguito
- L'espressione di aggiornamento serve a modificare le variabili per evitare cicli infiniti
- Quando la condizione diventa falsa, il programma continua l'esecuzione dopo il ciclo

>[!example]
>```c
>#include <stdio.h>
>
>int main() {
>    int i = 1;
>    
>    while (i <= 5) {
>        printf("%d\n", i);
>        i++;
>    }
>    
>    return 0;
>}
>```

### Costrutto do while
>[!note]
>Il ciclo `do-while` è simile al `while`, ma esegue il corpo del ciclo almeno una volta prima di valutare la condizione. Ecco la sua struttura:
>
>```c
>do {
>    /* codice da eseguire */
>} while (condizione);
>```
>
>>[!tip]- Flusso di esecuzione
>>```mermaid
>>flowchart TD
>>    A[Inizio] --> B[Esegui corpo del ciclo]
>>    B --> C[Esegui espressione di aggiornamento]
>>    C --> D{Valuta condizione}
>>    D -->|Vera| B
>>    D -->|Falsa| E[Continua esecuzione dopo il ciclo]
>>    E --> F[Fine]
>>
>>    style A fill:#90EE90,stroke:#006400,color:#000000
>>    style B fill:#DDA0DD,stroke:#800080,color:#000000
>>    style C fill:#FFB6C1,stroke:#8B0000,color:#000000
>>    style D fill:#87CEEB,stroke:#00008B,color:#000000
>>    style E fill:#98FB98,stroke:#006400,color:#000000
>>    style F fill:#FFB6C1,stroke:#8B0000,color:#000000
>>```

La differenza principale con il ciclo `while` è che il corpo del `do-while` viene eseguito almeno una volta, indipendentemente dalla condizione.

>[!example]
>```c
>#include <stdio.h>
>
>int main() {
>    int i = 1;
>    
>    do {
>        printf("%d\n", i);
>        i++;
>    } while (i <= 5);
>    
>    return 0;
>}
>```

### Costrutto for
>[!note]
>Il ciclo `for` è una struttura di controllo che permette di eseguire un blocco di codice per un numero specificato di iterazioni. La sua struttura è:
>
>```c
>for (inizializzazione; condizione; incremento) {
>    /* codice da eseguire */
>}
>```
>
>>[!tip]- Flusso di esecuzione
>>```mermaid
>>flowchart TD
>>    A[Inizio] --> B[Esegui inizializzazione]
>>    B --> C{Valuta condizione}
>>    C -->|Vera| D[Esegui corpo del ciclo]
>>    D --> E[Esegui incremento]
>>    E --> C
>>    C -->|Falsa| F[Continua esecuzione dopo il ciclo]
>>    F --> G[Fine]
>>
>>    style A fill:#90EE90,stroke:#006400,color:#000000
>>    style B fill:#FFB6C1,stroke:#8B0000,color:#000000
>>    style C fill:#87CEEB,stroke:#00008B,color:#000000
>>    style D fill:#DDA0DD,stroke:#800080,color:#000000
>>    style E fill:#FFB6C1,stroke:#8B0000,color:#000000
>>    style F fill:#98FB98,stroke:#006400,color:#000000
>>    style G fill:#FFB6C1,stroke:#8B0000,color:#000000
>>```

>[!example]
>```c
>#include <stdio.h>
>
>int main() {
>    for (int i = 1; i <= 5; i++) {
>        printf("%d\n", i);
>    }
>    
>    return 0;
>}
>```

>[!tip] Note sulla scelta del ciclo
>- Usare `while` quando non si conosce in anticipo il numero di iterazioni
>- Usare `do-while` quando il corpo del ciclo deve essere eseguito almeno una volta
>- Usare `for` quando si conosce il numero di iterazioni e si vuole un controllo più strutturato

