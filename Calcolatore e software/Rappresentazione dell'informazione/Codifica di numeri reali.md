>[!note]
>È impossibile rappresentare con precisione un numero reale, possiamo rappresentare soltanto un valore simile utilizzando i numeri razionali.
>
>È possibile valutare la precisione della rappresentazione $V_\text{rappr}$ rispetto al valore reale $V_\text{reale}$ tramite l'utilizzo di errore assoluto e relativo: $$\text{Err}_\text{Ass}= V_{\text{rappr}}- V_\text{reale}\qquad \text{Err}_\text{Rel}= \frac{\text{Err}_\text{Ass}}{V_\text{vero}}$$
>
>Di seguito mostriamo due approcci per la rappresentazione di numeri reali.

### Notazione a virgola fissa
>[!note]
>Nella notazione a virgola fissa è stabilito a priori il numero di cifre destinate alla parte intera e alla parte fissa.
>
>La parte intera è data dal numero di valori interi rappresentabili, mentre la parte frazionaria è data dalla precisione che si vuole ottenere nella rappresentazione.
>
>Se consideriamo una linea dei numeri discreta, la distanza tra valori è data da $\frac{1}{k^2}$, dove $k$ è il numero di bit dati alla parte frazionaria.

In questa notazione l'errore assoluto $\text{Err}_\text{Ass}$ è costante, mentre l'errore relativo $\text{Err}_\text{Rel}$ decresce al crescere che si vuole rappresentare.

>[!tip] Conversione da base $b$ a base $10$ frazionaria
>Per convertire da base $b$ base $10$ si usa la seguente formula:$$\sum\limits_{i=-k}^{n-1}c_{1}\cdot b^i$$
>Dove $k$ è il numero di bit dati alla parte frazionaria, $n$ è il numero di bit totali, $i$ è il numero della cifra partendo dalla parte meno significativa, e $b$ è la base in cui convertire.

> [!tip] Conversione da base $10$ a base $b$ frazionaria  
> Per convertire un numero razionale da base $10$ a base $b$, si procede così:
> 
> 1. Si converte la parte intera con divisioni successive per $b$.
> 2. Si converte la parte frazionaria moltiplicando ripetutamente per $b$ e prendendo la parte intera ad ogni passo.
> 3. Se un resto si ripete, la parte frazionaria è periodica.  

### Notazione a virgola mobile
>[!note]
>La notazione a virgola mobile ci permettere di creare un compromesso tra la dimensione dei valori e la loro precisione permettendo di spostare la virgola. Per ottenere questo effetto si utilizza la notazione scientifica:$$\text{valore}=\text{segno}\cdot\text{mantissa}\cdot\text{base}^\text{esponente}$$
>Abbiamo quindi: $$\underbrace{0}_\text{segno}\underbrace{00000000}_{\text{esponente}-e}\underbrace{00000000000000000000000}_\text{mantissa}$$
>Il bit del segno si comporta come in notazione modulo segno, mentre l'esponente è shiftato di metà del suo valore meno uno ($e=2^{\text{bit esponente}-1}-1$).
>
>In  notazione scientifica un numero è detto normalizzato quando: $1\leq\text{mantissa}<\text{base}$, però in base binaria abbiamo solo una cifra che non è zero, quindi dalla mantissa omettiamo la parte intera.

In questa notazione l'errore relativo $\text{Err}_\text{Rel}$ è costante mentre l'errore assoluto $\text{Err}_\text{Ass}$ cresce al crescere del valore che si vuole rappresentare.

Per stabilire il numero di cifre dedicate a ogni parte utilizziamo lo standard IEEE 754, secondo il quale esiste la rappresentazione a virgola mobile a singola precisione (float) e a doppia precisione (double).

Per rappresentare tali valori in modo coinciso solitamente si usa la base 16.

Quando la parte esponente è impostata tutta a $1$ significa che si vogliono esprimere dei valori speciali:
- $M=0$: Dal bit del segno intendiamo $+\infty$ o $-\infty$.
- $M\neq00$: Non definito ($\text{NaN}$).

Questi valori esistono per rappresentare il risultato di un operazione che ha dato come risultato un valore non rappresentabile, cioè al di fuori dal campo di rappresentabilità o dato da un operazione senza senso ($\frac{0}{0}\quad\infty-\infty\quad0\cdot\infty$).