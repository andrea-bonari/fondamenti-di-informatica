>[!note]
>In aggiunta ai numeri naturali, per i numeri interi è necessario anche codificare il segno. Di seguito si mostrano i due approcci più utilizzati.

### Notazione modulo segno
>[!note]
>Nella notazione modulo segno si designa il bit più significativo a indicare il segno, se esso è $0$ allora è positivo, viceversa è negativo. Questo approccio ha il divetto di rappresentare diminuire il numero massimo rappresentabile, e ci fa sprecare due spazi per lo $0$.

Per quanto riguarda l'aritmetica con queste rappresentazioni in caso di segni discordi il calcolatore controlla prima un controllo sul modulo maggiore, e poi utilizza il segno dell'operando maggiore.

Nel caso in cui il risultato dell'operazione è fuori dall'intervallo dei valori rappresentabili, il segno viene cambiato. In questo caso il processore emette nel suo registro di stato un codice di overflow, da cui deriva il nome del fenomeno overflow/underflow. 

Per evitare questo fenomeno si possono aggiungere degli $0$ di padding per aumentare il numero di cifre senza cambiare il valore. Questa operazione è detta estensione del segno

### Notazione in complemento a due
>[!note]
>Questa notazione è quella più utilizzata per rappresentare numeri interi. Questo perché a differenza della notazione modulo segno, considerando l'operazione di somma binaria, e  un numero $x$ in base $2$ si ha: $$x_{2} + (-x_{2})=0_{2}$$
>
>Date $n$ cifre binarie sono disponibili $2^{n}$ configurazioni, dove $2^{n-1}$ sono usate per rappresentare valori positivi e lo zero, mentre $2^{n-1}$ sono usate per rappresentare numeri negativi.

Per la conversione si scrive il valore assoluto del numero da rappresentare in notazione posizionale su $n$ cifre:
- Se il numero da rappresentare è maggiore o uguale a $0$, questa è la rappresentazione in complemento a $2$.
- Se il numero da rappresentare è minore di $0$, si complementano tutti i bit e si somma $1$. In alternativa, partendo dal bit meno significativo, si lasciano inalterati i valori dei bit fino al primo $1$, e si complementano i rimanenti bit

In questa notazione il bit più significativo è indicativo del segno come in notazione modulo segno.

>[!tip] Algebra in complemento a due su $n\text{ bit}$
>Consideriamo $2$ numeri $x$ e $y$. Per calcolare $x+y$, si fornisce in ingresso ad un sommatore binario naturale le codifiche binarie, e si ignora il bit di riporto in uscita, il risultato è in complemento a due.
>
>Per calcolare invece $x-y$ si ricava la rappresentazione di $y$ in complemento a due, e si sommano i risultati così ottenuti come nella regola precedente. Il risultato è in complemento a due.
>
>Quando si svolgono operazioni con segno discorde nella notazione in complemento alla base non si possono verificare overflow/underflow. Essi si verificano solo quando il segno è concorde negli operandi ma è discorde quello del risultato.
