Sopra la parte di hardware è costruita una serie di strati software che viene identificata come sistema operativo, che ha il compito di utilizzare il componente fisico rendendolo disponibile agli strati software sovrastanti.

- Software di sistema
- Software applicativo

L'obiettivo principale del SO è usare le risorse rendendole disponibili e facilmente utilizzabili a uno strato superiore. Le risorse sono rese disponibili in un formato semplificato ed esteso, diminuendo quindi la complessità, e virtualizzando le risorse quando non disponibili.

Il sistema operativo quindi astrae le primitive.

Per fare questo ogni elemento del SO ha in gestione una delle risorse necessarie per i programmi, e gestirà delle politiche per raggiungere una prestazione nella risorsa.
### Gestore dei processi/Kernel

Strato più vicino alla macchina fisica, la risorsa che gestisce è il processore. Astrae l'interazione con il processore e rende a disposizione ad ogni processo un processore virtuale.

Un processo è un programma attivo, quindi in esecuzione. Ossia l'evoluzione dell'esecuzione. Un programma può dar vita a più processi.

Per rendere disponibile un processore virtuale per ogni programma anche quando il processore fisico non ha tale numero di processori si suddivide/condivide il tempo di elaborazione sul processore fisico, quindi un processo ha a disposizione a turno un po di tempo di elaborazione sul processore fisico.

Un processo appena creato entra subito in uno stato `ready`, quando ad un processo viene assegnata la CPU entra nello stato `running`. Il processo quando finisce entra in stato di `end`. In caso un processo sia in attesa di eventi esterni/risorse entra nello stato di `wait`, una volta il processo riceve questi dati rientra nella coda di esecuzione. Ogni quanto di tempo un processo viene sospeso e riportato nello stato di `ready`, consentendo quindi a tutti un quanto di tempo per cui a rotazione tutti i processi possono evolvere. Questo algoritmo è detto round-robin. Le politiche di assegnamento dell'esecuzione dei processi sono dette scheduling. Un esempio di queste politiche può essere che i processi del SO hanno priorità più alta rispetto ai processi dei software applicativi.

Il cambio di processo fisico ha un costo di tempo non piccolo, perché va salvato lo stato del processo corrente e va caricato lo stato del nuovo processo.

Per gestire il tutto il kernel dispone di una tabella che lista tutti i processi e i loro dettagli. Inoltre il kernel si dovrà preoccupare di gestire la comunicazione tra più processi.
### Gestore della memoria di lavoro

Il gestore fornisce un meccanismo tramite il quale il processo accede alla memoria tramite un indirizzo. Ogni processo ha un area di memoria logicamente accessibile (non sa dove è posizionata ma ci può accedere) e protetta da altri processi. Per quanto riguarda l'estensione mette a disposizione una memoria virtuale.

Il gestore della memoria ha un modulo hardware Memory Manager Unit che mappa una parte della memoria di lavoro a una parte logica (tutti i rif. del programma partono da 0).

Quando il programma viene reso eseguibile, tutti i dati in memoria di lavoro partiranno da 0.

La memoria è divisa in pagine e quando viene creato un processo gli viene assegnato una pagina. Questo purtroppo ci fa sprecare della memoria.

Un altra strategia, detta segmentazione, dove si hanno dei segmenti dimensione diversa, in base a quanto ha bisogno un processo. Purtroppo anche questo costituisce uno spreco di memoria quando un processo viene terminato, e va riempito il buco di memoria lasciato vuoto.

Entrambe le soluzioni causano frammentazione della memoria.
Dato che la memoria è virtualizzata, ogni processo ha tanta memoria quanta gliene serve. Per questo quando la memoria in RAM è esaurita, la memoria di un processo `wait` sarà spostata nella memoria di massa, e sarà assegnata al processo originale quello spazio vuoto. Questo processo si chiama Swapping. Ci sono delle politiche come: swappare processi che hanno avuto da poco un accesso alla memoria perchè meno probabile che la usino o swappare processi che non hanno accessi alla memoria da tanto perchè meno probabile che la usino.

### Gestore delle periferiche

Semplifica la lettura, la scrittura e lo scambio di informazioni delle periferiche, e estende le risorse anche se non sono parte del sistema. Pensare ai driver del SO.

Il driver è il programma che definisce come utilizzare e mette a disposizione le primitive di una periferica fisica.

Lo stesso driver, nel momento in cui la risorsa potrebbe essere condivisa, ha dei meccanismi per cui è possibile condividere un dispositivo, creando ad esempio delle code di accesso.

>[!note] Polling
>Controllo periodico della periferica con una frequenza significativa

>[!note] Interrupt
>Flag per sollevare un interrupt e segnalare una richiesta di interazione interrompendo il flusso dell'evento che è avvenuto

Per gestire le richieste delle periferiche di accesso alla memoria c'è il Direct Memory Access (DMA), che è un coprocessore programmato dalla CPU.