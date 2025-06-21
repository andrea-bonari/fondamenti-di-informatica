>[!note]
>Il modello Von Neumann è un modello di un sistema di elaborazione dove le istruzioni vengono memorizzate per poi essere eseguite. È composto da tre principali elementi essenziali:
>- Memoria di lavoro
>- CPU
>- Mezzo di comunicazione
>  
>Ci sono poi altri elementi che semplificano l'interazione con il sistema di calcolo:
>- Memoria di massa
>- Periferiche I/O

La CPU contiene l'unità di elaborazione e l'unità di controllo, nella memoria di lavoro abbiamo i dati e le istruzioni.

### Bus di sistema
>[!note]
>Il bus di sistema è un canale di comunicazione tra i componenti del modello Von Neumann.
>
>![[Pasted image 20240524102428.png|center]]
>
>Il bus si divide in 3 parti logiche:
>- BUS Indirizzi: ci transitano gli indirizzi di memoria dell'informazione da scambiare, è scrivibile solo dalla CPU e leggibile da tutti gli altri.
>- BUS Dati: bus di informazione, dove transita l'informazione (dati o istruzioni) che viene scambiata.
>- BUS Di controllo: è un insieme di linee ciascuna delle quali ha un significato diverso, che servono a coordinare lo scambio vero e proprio del bus.

Per collegare tutti questi elementi ci sono due scelte:
- comunicazioni punto a punto: collegamento da ogni elemento per ogni elemento, sistema robusto e performante ma difficilmente scalabile
- sistema unico in cui tutti gli elementi coinvolti vengono collegati, sistema non performante come il precedente ma facilmente scalabile

È stato scelto il sistema unico, dove la CPU coordina i dispositivi e quindi la possibilità di avere comunicazioni parallele è irrilevante. Infatti ogni dato passa dalla CPU.
## Memoria di lavoro
>[!note]
> Può essere visto come una tabella dove ogni cella (individuata da un indirizzo) contiene una parola. In base ai dati ricevuti dal bus indirizzi verrà attivata una riga/cella, che verrà messa a disposizione sul bus dati in caso di lettura, in caso di scrittura viene sovrascritto.
>
>Inoltre, in base al numero di bit disponibile nel bus indirizzi si può derivare lo spazio di memoria indirizzabile.

>[!example]
>Se consideriamo il $k$ come il bit di indirizzo e $h$ come dimensione della parola (dimensione del bus dati), allora possiamo definire: $$\begin{align*}
>\text{spazio di indirizzamento}&= 2^{k}\\
>\text{memoria totale indirizzabile}&=  h\cdot 2^{k}
>\end{align*}$$

Questa memoria è detta Random Access Memory (RAM). Ed è detta random perché il tempo di accesso è costante e indipendente dalla posizione in memoria, quindi le prestazioni sono legate al tempo di risposta tipico.

È volatile, quindi quando non alimentata il contenuto viene perso. Inoltre all'accensione il contenuto della memoria è casuale, non esiste il concetto di vuoto, contiene quindi o $0$ o $1$.

La maggior parte del tempo di esecuzione la CPU interagisce con questa memoria.

La RAM può essere statica o dinamica (più usata), per quanto alimentata ha bisogno di essere rinfrescata, quindi per mantenere il contenuto viene sovrascritto con se stesso.

## Unità Centrale di Elaborazione (CPU)
>[!note]
> La CPU è il componente col compito di eseguire le istruzioni, al suo interno contiene l'unità di controllo, l'unità aritmetico-logica e una serie di registri.
> 
>![[Pasted image 20230918113255.png|center]]
Esiste un segnale di Clock nel BUS controllo che scandisce tutte le operazioni, sia del processore che in tutti i dati.

>[!tip] Registri
>Se un istruzione non è perfettamente sincrona sono necessari dei registri per mantenere l'interfaccia stabile con i bus esterni.
>
>Per esempio tra il collegamento tra la CPU e il BUS Indirizzi c'è il Memory Address Register (MAR). Quando ci interfacciamo col BUS Dati esiste il Memory Data Register (MDR). Questo sarà vero per tutti i dispositivi. Per quanto riguarda il BUS Controllo non è necessaria un interfaccia.
>
>All'interno della CPU esiste un BUS interno per scambiare dati, e quindi si ha bisogno di registri per contenere i valori temporanei per l'elaborazione, dato che una volta letti i dati dalla memoria vanno memorizzati temporaneamente dentro il processore. Questi sono detti Register File. Il register file costituisce la memoria più vicina al processore.
>
>Esiste anche un Instruction Register, che contiene una copia dell'istruzione che si sta eseguendo.
>
>Il registro Program Counter (PC), contiene l'indirizzo della prossima istruzione da eseguirsi.
>
>Il registro Processor Status Word (PSW) tiene traccia dello stato del processore.

>[!tip] Unità Aritmetico Logica (ALU)
>Questo componente esegue operazioni logiche e aritmetiche.
>Ha due ingressi, un selettore di operazione e un risultato.
>Ha inoltre un ingresso per il clock, e un ulteriore uscita che è un insieme di bit che ci dice come è andata l'operazione (overflow, riporto, ...).

>[!tip] Unità di Controllo (CU)
>Questa è la parte che è progettata per ricevere il segnale di clock, e sulla base del segnale leggere la prossima istruzione da eseguire, carica l'istruzione nel MDR e poi nell'IR.
>Poi l'istruzione va interpretata ed eseguita, decodificando quindi il contenuto dell'IR.
>Il PC viene incrementato e poi si ricomincia il ciclo.
>Questo ciclo viene detto FETCH-DECODE-EXECUTE.
>
>Quando si termina l'esecuzione si sta eseguendo l'istruzione di `halt`. E quindi quando si progetta la propria CPU, si definisce l'insieme dell'istruzione che può eseguire. Quindi l'insieme di istruzioni è detto architettura.

### Dispositivi periferici
>[!note] Memoria di massa
È una memoria utilizzata per memorizzare in modo permanente e non volatile dei dati che vogliamo persistere. Ha delle capacità superiori di memoria ma tempi di accesso più elevati rispetto alla memoria di lavoro.

Tra queste possono essere:
- HDD
- SSD

In queste memorie solitamente troviamo dati e programmi non in esecuzione (file di paging).
