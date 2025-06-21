>[!note]
>Sopra l'hardware si costruisce una serie di strati software che costituiscono il sistema operativo (SO). Questo ha il compito di utilizzare il componente fisico e renderlo disponibile agli strati software superiori, semplificandone l’uso e mascherandone la complessità. I software si suddividono in:
>- Software di sistema: comprende il sistema operativo e altri strumenti di base.
>- Software applicativo: include i programmi utilizzati dagli utenti.

L’obiettivo principale del sistema operativo è rendere le risorse facilmente utilizzabili da uno strato superiore, attraverso semplificazione, astrazione e virtualizzazione.

> [!tip] Virtualizzazione  
>La virtualizzazione è un processo che rende disponibili risorse fisiche come se fossero illimitate e indipendenti, simulandole a livello software.

## Il Kernel e il Gestore dei Processi
>[!note]
>Lo strato più vicino alla macchina fisica è il kernel, che gestisce il processore. Esso astrae l'interazione con il processore, fornendo a ogni processo un processore virtuale.
>
>Definiamo un processo come un programma attivo, cioè in esecuzione. Più processi possono derivare da uno stesso programma.
>
>Per garantire l'esecuzione di più processi su un numero limitato di CPU fisiche, si usa la condivisione temporale (time-sharing): ogni processo riceve un intervallo (quantum) di tempo per usare la CPU.
>
>L'insieme di politiche usato per decidere quale processo eseguire è detto scheduling.

Un processo si può trovare in uno di questi stati
- Ready: pronto per essere eseguito.
- Running: in esecuzione.
- Wait: in attesa di una risorsa/evento.
- End: terminato.

Durante l’esecuzione, i processi passano ciclicamente tra questi stati, utilizzando l’algoritmo round-robin, che assicura una rotazione equa.

Il cambio di contesto (switching) comporta un costo, poiché lo stato del processo corrente va salvato e quello del nuovo processo caricato.

Il kernel gestisce tutto ciò con una tabella dei processi e si occupa anche della comunicazione tra processi (inter-process communication).

## Gestore della Memoria
>[!note]
>Il gestore della memoria consente ai processi di accedere alla memoria tramite indirizzi logici, isolandoli e proteggendoli l’uno dall'altro.
>
>Per farlo si usa la Memory Management Unit (MMU), cioè un modulo hardware che mappa la memoria logica a quella fisica. In questo modo ogni processo ha l’impressione di partire da indirizzo $0$. 
>
>La memoria può essere gestita in due modi:
>- Paginazione: la memoria è suddivisa in pagine di dimensione fissa, e ogni processo riceve una o più pagine. Questo metodo potrebbe però causare frammentazione interna.
>- Segmentazione: la memoria è suddivisa in segmenti di dimensione variabile, dove ogni segmento ha uno scopo. Questo metodo potrebbe però causare frammentazione esterna.

> [!tip] Frammentazione  
>Definiamo il fenomeno di frammentazione come spazio sprecato nella memoria a causa dell’allocazione fissa o non ottimale.

>[!tip] Memoria virtuale s Swapping
>Quando la RAM è piena, i processi in stato `wait` possono essere spostati su disco (memoria di massa), liberando spazio. Questo è detto meccanismo di swapping.
>
>Generalmente le politiche di swapping sono:
>- I processi che hanno avuto accessi recenti hanno minor probabilità di essere swappati.
>- I processi inattivi da tempo sono candidati allo swap.

## Gestore delle Periferiche
>[!note]
>Il gestore delle periferiche è un modulo che semplifica la comunicazione con le periferiche, rendendole accessibili tramite driver, cioè un programma che definisce come interagire con una periferica fisica, offrendo un'interfaccia standard.
>
>I driver possono includere meccanismi di condivisione della risorsa, ad esempio usando delle code di accesso.
>
>Per comunicare con le periferiche si possono utilizzare due metodi:
>- Polling: controllo periodico della periferica da parte della CPU.
>- Interrupt: segnale emesso dalla periferica per richiedere attenzione alla CPU, interrompendone il flusso.

> [!tip] Direct Memory Access (DMA)
> Il Direct Memory Address (DMA) è coprocessore programmabile dalla CPU che gestisce direttamente il trasferimento di dati tra periferiche e memoria, liberando la CPU da questo compito.
