>[!note]
>Per rappresentare l'informazione sono necessari due elementi:
>- Alfabeto: insieme di simboli utilizzati.
>- Codice: sequenze di simboli ammissibili, cioè che è ammissibile è detto parola di codice.
>
>Il codice rappresenta l'associazione biunivoca tra gli elementi da rappresentare e una sequenza ammissibile.
>
>Definendo l'alfabeto dei dati come l'insieme $S$, la sua cardinalità come $|S|$, il numero di elementi da rappresentare come $n$ e la dimensione delle configurazioni come $k$, valgono le seguenti formule: $$k=\lceil \log_{|S|}n\rceil\iff n= |S|^{k}$$

### Codifica binaria
>[!note]
>Un calcolatore è composto da due stati, per esempio condensatore carico/scarico oppure una linea con tensione alta/bassa. È intuitivo quindi usare la base binaria per rappresentare qualsiasi tipo di informazione.
>
>Essa si avvale di due simboli $\set{0,1}$ e la cifra della codifica binaria è detta $\text{bit}$. I suoi multipli sono:
>
>| Nome | Valore |
>| - | - |
>| $\text{B}$ (byte) | $8\text{ bit}$ |
>| $\text{kB}$ | $2^{10}\text{ B}$ |
>| $\text{MB}$ | $2^{20}\text{ B}$ |
>| $\text{GB}$ | $2^{30}\text{ B}$ |
>| $\text{TB}$ | $2^{40}\text{ B}$ |

È bene considerare di mantenere un legame logico dove possibile durante la codifica.

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
