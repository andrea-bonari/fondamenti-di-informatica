> [!note]  
> La manipolazione dei file in C avviene utilizzando la libreria `<stdio.h>`, che fornisce funzioni per aprire, leggere, scrivere e chiudere i file.  
> Un file in C è gestito attraverso un puntatore di tipo `FILE*`, che viene utilizzato nelle varie operazioni.
>
> Le operazioni principali sui file includono:
> 
> - **Apertura di un file** con `fopen()`, specificando il percorso e la modalità di apertura
> - **Lettura e scrittura** mediante funzioni come `fscanf()`, `fprintf()`, `fgets()`, `fputs()`, `fread()`, `fwrite()`
> - **Chiusura di un file** con `fclose()` per liberare le risorse
> - **Gestione degli errori** tramite il controllo del puntatore `FILE*` e l'uso di `feof()` o `ferror()`.


> [!example]
> 
> ```c
> #include <stdio.h>
> 
> int main() {
>    FILE *file = fopen("testo.txt", "w");  /* Apertura del file in modalità scrittura */
>    if (file == NULL) {
>        printf("Errore nell'apertura del file.\n");
>        return 1;
>    }
> 
>    fprintf(file, "Scrivo questo testo nel file.\n");  /* Scrittura nel file */
>    fclose(file);  /* Chiusura del file
> 
>    return 0;
> }
> ```

### Modalità di Apertura
> [!note]  
> `fopen()` accetta due parametri: il nome del file e la modalità di apertura.  
> Ecco alcune modalità comuni:
> 
> - `"r"` → Apre un file per lettura (deve esistere)
> - `"w"` → Crea un file per scrittura (sovrascrive se esiste)
> - `"a"` → Apre un file in modalità aggiunta (append)
> - `"r+"` → Apre un file per lettura e scrittura
> - `"w+"` → Crea un file per lettura e scrittura (cancella se esiste)
> - `"a+"` → Apre o crea un file per lettura/scrittura, mantenendo il contenuto

> [!example]
> 
> ```c
> #include <stdio.h>
> 
> int main() {
>    FILE *file = fopen("testo.txt", "r");  /* Apertura in modalità lettura */
>    if (file == NULL) {
>        printf("Errore nell'apertura del file.\n");
>        return 1;
>    }
> 
>    char riga[100];
>    while (fgets(riga, sizeof(riga), file) != NULL) {  /* Lettura riga per riga */
>        printf("%s", riga);
>    }
> 
>    fclose(file);
>    return 0;
> }
> ```

### Lettura e Scrittura Binaria
> [!note]  
> Per lavorare con dati binari si usano `fread()` e `fwrite()`, che leggono e scrivono blocchi di dati.

> [!example]
> 
> ```c
> #include <stdio.h>
> 
> typedef struct {
>    char nome[20];
>    int eta;
> } Persona;
> 
> int main() {
>    Persona p = {"Mario", 30};
>    FILE *file = fopen("dati.bin", "wb");  /* Scrittura binaria */
>    fwrite(&p, sizeof(Persona), 1, file);
>    fclose(file);
> 
>    return 0;
> }
> ```
