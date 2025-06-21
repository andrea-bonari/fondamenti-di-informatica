>[!note]
>Un numero naturale è un valore che può essere rappresentato come una sequenza di simboli. Il quantitativo di simboli indica la base.
>
>Una rappresentazione numerica può essere:
>- additiva, dove il peso di un valore è dato dalla combinazione di simboli: numeri romani ($\set{I,\cdots, IV,\cdots, IX,\cdots}$)
>- posizionale, dove il peso di un valore è dato dalla sua posizione: numeri arabi ($\set{1,\cdots,9}$)

Per rappresentare un valore numerico naturale in basi diverse dobbiamo saperli convertire.

>[!tip] Conversione da base $b$ a base $10$
>Si ha che per convertire un numero da base $n$ a base $10$ si deve applicare la formula: $$\sum\limits_{i=0}^{n-1} a_{i}\cdot b^{i}$$
>Dove $n$ è il numero di cifre, $i$ è il numero della cifra partendo dalla parte meno significativa, e $b$ è valore della base.

>[!tip] Conversione da base $10$ a base $b$
>Per convertire un numero da base $10$ a base $b$ bisogna applicare il seguente algoritmo iterativo: Si divide il numero per la base $b$ e segniamo il modulo. Col quoziente ripeteremo lo stesso processo fino a raggiungere quoziente $0$. A questo punto invertiamo l'ordine dei moduli e quello rimanente sarà in base $b$.

>[!tip] Corrispondenza biunivoca con base $2$ e base $16$
>
>Siccome la base $16$ utilizza $4\text{ bit}$ per cifra, si può sostituire il valore della cifra esadecimale con il suo valore binario, creando una corrispondenza biunivoca.
>
>Infatti spesso la base esadecimale è utilizzata per rappresentare dati usando le seguenti notazioni: $$57AB_{16}\qquad 57AB_\text{H}\qquad \mathtt{0x}57AB$$

