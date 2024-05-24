### La rappresentazione dell'informazione

Gli elementi della rappresentazione dell'informazione sono 2:
- L'alfabeto: cioè l'insieme di simboli utilizzabili
- Il codice: che ci da le sequenze di simboli ammissibili, ciò che è ammissibile è detto parola di codice

Il codice definisce l'associazione tra gli elementi da rappresentare e una sequenza ammissibile, detta associazione biunivoca.

La dimensione dipende dal numero di simboli e dalla quantità di configurazioni ammissibili.

>[!info]
>Utilizziamo i seguenti simboli per rappresentare i nostri dati
>alfabeto dei simboli: $S=\{...\}$
>cardinalità dell'alfabeto: $|S|$
>numero di elementi da rappresentare: $n$
>dimensione delle configurazioni: k

Valgono le seguenti formule:
$$k=[\log_{|s|}n]$$
$$n=|s|^k$$
### Il sistema binario

Un sistema di calcolo è una realtà costituita da due stati, per esempio
- condensatore carico/scarico
- linea con tensione alta/bassa
- ...

È quindi intuitivo utilizzare un **sistema in base binaria**, utilizzabile per rappresentare qualsiasi tipo di informazione (valori numerici, simboli, immagini, audio, ...)

Esso si avvale di due simboli: $\{0,1\}$, e la cifra della codifica è detta bit (binary digit)

I suoi multipli sono:
- byte (8 bit)
- kilobyte ($2^{10}$ byte) = 1024 bit
- megabyte ($2^{20}$ byte)
- gigabyte ($2^{30}$ byte)
- terabyte ($2^{40}$ byte)

>[!example]
>rappresentiamo i 4 semi delle carte da gioco in binario.
>$S=\{0,1\}$
>$|S|=2$
>
>dimensione delle configurazioni: $[\log_{|S|}n]=[\log_24]=2$
>
>finiamo con 4 combinazioni ammissibili, biunivoche alla rappresentazione dei simboli: $00\quad01\quad10\quad11$

>[!example]
>Rappresentiamo i 7 giorni della settimana in binario.
>
>dimensione della configurazione: $[log_27]\approx3$
>
>combinazioni: $000\quad001\quad010\quad011\quad100\quad101\quad110$, una combinazione è sprecata, ma non è un problema, perchè non si può fare diversamente.

>[!warning]
>non esistono combinazioni di dimensione diversa.

>[!info] Aspetti da considerare
> - è bene considerare di mantenere un legame logico dove possibile (es: elementi adiacenti)
> - Il significato di un informazione non definisce la sua rappresentazione, ciò dipende dalla codifica adottata

### ASCII
>[!note]
nello standard ASCII base si intende rappresentare i seguenti caratteri:
>- alfabeto base: $\{a .. z,A .. Z\}$
>- caratteri numerici: $\{0 .. 9\}$
>- simboli di interpunzione
>- caratteri speciali (new-line, space, ...)

La lunghezza della codifica è: $[\log_2{128}]=7$ bit

lo standard ASCII è stato poi esteso a 8 bit, con la aggiunta di:
- caratteri nazionali: $\{à .. ù\}$
- simboli
- cornici

quindi il numero di combinazioni diventa 256.

>[!info]
>Ogni carattere corrisponde a un byte, e quindi anche a un valore numerico

### UNICODE
>[!note]
>UNICODE è uno standard compatibile con il codice ASCII che utilizza 16 bit per rappresentare i caratteri, rappresentando però $65536$, tuttavia proprio per questo motivo le dimensioni dei file risultano raddoppiate.

### Numeri naturali

Un numero naturale è un valore che può essere rappresentato come una sequenza di simboli. Il quantitativo di simboli indica la base.

>[!example]
>base 2: $\{0, 1\}$
>base 8: $\{0..7\}$
>base 10: $\{0..9\}$
>base 16: $\{0 .. F\}$

Una rappresentazione numerica può essere:
- additiva, dove il peso di un valore è dato dalla combinazione di simboli: numeri romani ($I\quad  IV\quad IX\quad ...$)
- posizionale, dove il peso di un valore è dato dalla sua posizione: numeri arabi ($1 .. 9$)

Per rappresentare un valore numerico naturale in basi diverse dobbiamo saperli convertire

>[!info]
>Formula per la conversione da base $n$ a base $10$.
>
>$n$: numero di cifre
>$c_n$: cifra in posizione $n$
>$b$: valore della base
>
>$$\sum_{i=0}^{n-1}a_i\cdot b^i$$
>
> >[!example]-
> >
> >Convertire $101011_2$ in base $10$
> >
> >$n=1\cdot 2^5+0\cdot2^4+1\cdot2^3+0\cdot2^2+1\cdot2^1+1\cdot2^0=43$

>[!info]
>Formula per la conversione da base $10$ a base $n$.
>
>Dividiamo il numero per la base e segniamo il resto, col quoziente invece ripeteremo lo stesso processo fino a raggiungere quoziente 0. A questo punto invertiamo l'ordine dei resti e quello sarà il valore in base $n$.
>
> >[!example]-
> >
> >Convertire $28_{10}$ in base $10$
> >
> > | dividendo | resto |
> > | --------- | ----- |
> > | 28        | 0     |
> > | 14        | 0     |
> > | 7         | 1     |
> > | 3         | 1     |
> > | 1         | 1     |
> >| 0         | /     |
> >
> >Quindi il nostro valore binario sarà $n=11100$

>[!info] 
>Formula per la conversione da base $2$ a base $16$ e viceversa.
>
>Semplicemente dato che la base 16 utilizza 4 bit per cifra sostituiamo il valore della cifra in esadecimale con il suo valore il binario. Possiamo fare lo stesso per convertire da base binaria a base esadecimale (in caso le cifre binarie non siano un multiplo di 4 si aggiungono degli 0 di padding a sinistra)
>
> >[!example]-
> >
> >Convertire $10A_{16}$ in base $2$.
> >
> >$n=\underbracket{0001}_{1}\quad\underbracket{0000}_0\quad\underbracket{1010}_A$

La base esadecimale è generalmente più utilizzata per la sua compattezza nella rappresentazione dei dati. Si può utilizzare nelle seguenti notazioni:
$$57AB_{16}\quad57AB_H\quad0\text{x}57AB$$
### Numeri interi
##### Notazione Modulo Segno

Per rappresentare i numeri interi in qualsiasi base utilizziamo la notazione segno modulo.

$$n=\underbracket{-}_\text{segno}\quad\underbracket{10}_\text{modulo}$$
Purtroppo questo ci fa sprecare due spazi per il numero 0:
$$-0_{2MS}=+0_{2MS}$$

Per rappresentare in binario questa notazione aggiungiamo a sinistra un bit che stabilisce il segno, in caso assuma valore $0$ è positivo, altrimenti è negativo.
$$-5_{10}=\underbracket{1}_\text{segno}101_{2MS}$$
>[!warning]
>L'aggiunta del bit del segno ci permette di rappresentare lo stesso numero di configurazioni, ma diminuisce il numero massimo e aumenta il numero minimo
>$$\begin{matrix}-7_{10} & 1111_{2MS} \\ -6_{10} & 1110_{2MS} \\ ... & ... \\ 6_{10} & 0110_{2MS} \\ 7_{10} & 0111_{2MS}\end{matrix}$$

Per quanto riguarda l'aritmetica con queste rappresentazioni in caso di segni discordi il calcolatore controlla prima un controllo sul modulo maggiore, e poi utilizza il segno dell'operando maggiore.

>[!bug]
>In caso il risultato dell'operazione è fuori dall'intervallo dei valori rappresentabili il segno viene cambiato, dato che l'operazione viene eseguita come una somma binaria normale. In questo caso il processore emette nel suo registro dello stato un codice di overflow. Questo fenomeno è detto overflow/underflow.
>Per evitare questo fenomeno si possono aggiungere degli $0$ di padding per aumentare il numero di cifre senza cambiare il valore, questa operazione si dice estensione del segno.
>
##### Notazione in complemento alla base
>[!note]
> si vuole trovare un modo tale per cui sommando due operandi qualsiasi risultato sia quello ci si aspetta.
> Sapendo che $$x+(-x)=0$$

Per farlo nel caso un numero $n$ sia un valore positivo teniamo il numero uguale ma non trattiamo il primo bit come segno.

In caso $n$ sia un numero negativo utilizziamo la precedente equazione, ignorando il riporto in overflow e troviamo $-x$, che è detto codifica ideale.

>Quindi la notazione in complemento alla base afferma che la codifica del valore opposto è la quantità che sommata al valore stesso dà la base elevata a una potenza

>[!example]- Esercizio svolto
>Calcola il valore opposto di $0100_{2C2}$
>
>>[!todo]- Soluzione
>>Il valore è $1100_{2C2}$

1100

>[!tip]
>Quando si svolgono operazioni con segno discorde nella notazione in complemento alla base non si possono verificare overflow/underflow. Essi si verificano solo quando il segno è concorde negli operandi ma è discorde quello del risultato.
### Numeri irrazionali

È impossibile rappresentare con precisione un numero reale, possiamo rappresentare soltanto un valore simile utilizzando i numeri razionali.

Possiamo valutare la precisione della rappresentazione $V_\text{rappr}$ rispetto al valore reale $V_\text{reale}$ tramite l'utilizzo di:
- Errore assoluto ($e_A$): $$V_\text{rappr}-V_\text{reale}$$
- Errore relativo ($e_R$): $$\frac{e_A}{V_\text{vero}}$$
L'errore relativo è ciò che ci da un idea del peso dell'errore.
##### Notazione a virgola fissa

è stabilito a priori il numero di cifre destinate alla parte intera e alla parte fissa.
La parte intera è data dal numero di valori interi rappresentabili, mentre la parte frazionaria è data dalla precisione che si vuole ottenere nella rappresentazione.

>[!example]
>Se la parte frazionaria è costituita da una sola cifra $k=1$ allora possiamo rappresentare un univo valore razionale tra due numeri interi.
>![[rM drawing 2023-09-21-16.17.06.png]]

La distanza tra valori è data da $\frac{1}{k^2}$, dove $k$ è il numero di bit dati alla parte frazionaria.

>[!info]
>In questa notazione l'errore assoluto $e_A$ è costante, mentre l'errore relativo $e_R$ decresce al crescere che si vuole rappresentare.

Per convertire in base $n$ si usa la seguente formula:$$\sum\limits_{i=-k}^{n-1}c_{1}\cdot b^i$$ dove:
$k$ è il numero di bit dati alla parte frazionaria
$n$ è il numero di bit totali
$c_i$ è il valore in posizione $i$
$b$ è la base in cui convertire

>[!example]- Esercizio svolto
>Convertire $1101.101000_2$ in base 10:
>
>>[!todo]- Soluzione
>>$1101.101000_2=\sum\limits_{i=-k}^{n-1}c_{1}\cdot b^i=2^3+2^2+2^0+2^{-1}+2^{-3}=13.625$

Per convertire in base 2 un numero in base $n$, convertiamo la parte intera in binaria come di norma, e per quanto riguarda la parte decimale moltiplico la parte decimale per $n$, se raggiungo l'unità segno $1$, altrimenti $0$, e a questo punto moltiplico di nuovo la parte decimale per $n$ per il numero di cifre che vogliamo avere in parte decimale. La sequenza di $0$ e $1$ trovata sarà la parte decimale.

>[!tip]
>Se trovo il numero zero nelle moltiplicazioni ripetute posso assumere che tutte le moltiplicazioni successive saranno $0$

>[!example]- Esercizio svolto
>Convertire $156.45_{10}$ in base 2 utilizzando 12 cifre per la parte frazionaria:
>
>>[!todo]- Soluzione
>>Calcoliamo la parte intera
>>$156=\underbracket{10011100}_\text{parte intera}$
>>
>>Calcoliamo la parte frazionaria
>>$\begin{matrix}0.45&2&\\0.9&&0\\1.8&&1\\1.6&&1\\1.2&&1\\0.4&&0\\0.8&&0\\1.6&&1\\1.2&&1\\0.4&&0\\0.8&&0\\1.6&&0\\1.2&&1\end{matrix}$
>>
>>$.45_{10}=011100110011$
>>
>>quindi $56.45_{10}=10011100.011100110011$
##### Notazione a virgola mobile

La notazione a virgola mobile ci permettere di creare un compromesso tra la dimensione dei valori e la loro precisione permettendo di spostare la virgola. Per ottenere questo effetto si utilizza la notazione scientifica:$$\text{valore}=\text{segno}\cdot\text{mantissa}\cdot\text{base}^\text{esponente}$$
Abbiamo quindi:$$\underbracket{0}_\text{segno}\underbracket{00000000}_{\text{esponente}-e}\underbracket{00000000000000000000000}_\text{mantissa}$$
Il bit del segno si comporta come in [[#Notazione Modulo Segno|notazione modulo segno]], mentre l'esponente è shiftato di metà del suo valore meno uno ($e=2^{\text{bit esponente}-1}-1$).

In  notazione scientifica un numero è detto normalizzato quando: $1\leq\text{mantissa}<\text{base}$, però in base binaria abbiamo solo una cifra che non è zero, quindi dalla mantissa omettiamo la parte intera.

>[!info]
>In questa notazione l'errore relativo $e_R$ è costante mentre l'errore assoluto $e_A$ cresce al crescere del valore che si vuole rappresentare.

Per stabilire il numero di cifre dedicate a ogni parte utilizziamo lo standard IEEE 754, secondo il quale esiste la rappresentazione a virgola mobile a singola precisione (float) e a doppia precisione (double).

>[!info]
>Lo standard float ha a disposizione:
>$s$: 1 bit
>$esp + e$: 8 bit ($e = 127$ => $esp+e\in[-127,+128]$)
>$M$: 23 bit
>
>Mentre lo standard double ha a disposizione:
>$s$: 1 bit
>$esp + e$: 8 bit ($e=1023$ => $esp+e\in[-1023,+1024]$)
>$M$: 52 bit

Per rappresentare tali valori in modo coinciso solitamente si usa la base 16:

>[!example]
>$00111101100100000000000000000000_{2IEEE754}=3D900000_{16IEEE745}=0\text{x}3D900000_{IEEE745}$

Quando $\text{esponente}+e$ è impostata tutta a $1$ significa che si vogliono esprimere dei valori speciali:
- $M=00..00$: Dal bit del segno intendiamo $+\infty$ o $-\infty$
- $M\neq00..00$: Non definito ($NaN$)

Questi valori esistono per rappresentare il risultato di un operazione che ha dato come risultato un valore non rappresentabile, cioè al di fuori dal campo di rappresentabilità o dato da un operazione senza senso ($\frac{0}{0}\quad\infty-\infty\quad0\cdot\infty$).