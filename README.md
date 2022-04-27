# BASH BASE TIPS

* `find /path` - Start to "/path" and search the file/dir passed by adding `-d *dirname*`PARTE DAL PERCORSO PASSATO E CERCA IL FILE/DIR DATO IN INPUT; SE MESSO(-D) MOSTRA SOLO LE DIR <br>
        * `find /usr/ -maxdepth 3 -type f -name "*.h" -print   `   <br>
        ---- > 'Stampa tutti i file presenti in tutte le dir di profondità massima 3 a partire da /usr/ e che finiscono per .h'        <br>
        * `find /usr/ -maxdepth 3 -type f -name "*.h" -exec wc -l '{}' \; ` <br>
        ---- > 'Cerca i file come il precedente ma questo giro stampa il numero di righe di ciascuno (ogni file trovato va a sostituire le {})'       
* ` GPG -D ./NOMEFILE | tar xvzf` - --> ESTRAE E DECRIPTA
* ` TOUCH ./filename ` - CREA FILE 
* ` LS `= MOSTRA CONTENUTO DIRECTORY CORRENTE 
* `CAT` - Stampa contenuto di file
* `MV` - SPOSTA FILE E CARTELLE
* `PS` - INFO SUI PROCESSI IN ESECUZIONE
* `SUDO` - ASSUMERE TEMPORANEAMENTE I DIRITTI DI AMMINISTRATORE
* `DU` - QUANTO SPAZIO E' UTILIZZATO            DU -H --> ALBERO DELLE DIRECTORY
* `KILL` - MANDARE UN SEGNALE AD UN PROCESSO
* `BG` -    ||
* `FG` -    ||
* `READ` - LEGGI QUALCOSA DA TASTIERA; 
* `READ` -u {FD} -> legge da fd
* `WC` - FORNISCE RIGHE, IL NUMERO DI PAROLE E DI BYTE DEL FILE PASSATO COME ARGOMENTO
* `ALIAS` - ASSEGNA A "V" UN COMANDO (ES. ALIAS V='LS --COLOR=NEVER')
* `KILLALL` - UCCIDE UNA SERIE DI PROCESSI IN BACKGROUND CON QUEL NOME_PROCESSO (ES. KILLALL NOME_PROCESSO)
* `VI` - APRE EDITOR DI TESTO CHE SI CHIUDE CON :q!
* `NANO` - ALTRO EDITOR DI TESTO
* `START` - APRE APPLICAZIONE O FILE 
* `EXIT` - DETERMINA L'EXIT STATUS DI UNO SCRIPT RESTITUITO ALLA SHELL CHIAMANTE (EXIT = 0 --> SCRIPT ANDATO A BUON FINE)
* `CP` - COPIA IN DESTINAZIONE LA SORGENTE, SE MESSO "-R" COPIA RICORSIVAMENTE (ANCHE TUTTE LE SOTTOCARTELLE)
* `RM` - ELIMINA FILE/DIR (SE MESSO -R RICORSIVAMENTE E SE MESSO -F FORCE OVVERO NON CHIEDE OGNI VOLTA CONFERMA)
* `GREP` "STRINGA" - CERCA LA CORRISPONDENZA DI "STRINGA" DENTRO UN TESTO(DI DEFAULT PRESO IN INPUT)
* `TEE` - CHE LEGGE DATI DALLO STANDARD INPUT E LI VISUALIZZA SULLO STANDARD OUTPUT, MEMORIZZANDOLI NEL CONTEMPO NEI FILE SPECIFICATI
* `HEAD` -N "n" NOMEFILE - RESTITUISCE LE PRIME n RIGHE DEL FILE "NOMEFILE"
* `TAIL` - COME HEAD, MA PARTE DALLA CODA
* `SED` 's/STRINGADASOSTITUIRE/NUOVASTRINGA/g' - EDITOR DI STRINGA (s STA PER SOSTITUISCI E g PER GLOBALMENTE(TUTTE LE OCCORRENZE))
* `CUT` -b 4- NOMEFILE -> MOSTRAMI IL CONTENUTO A PARTIRE DAL 4° CARATTERE IN POI <br>
        CUT -b -4 NOMEFILE -> MOSTRAMI IL CONTENUTO FINO AL 4° CARATTERE


## ISTALLAZIONE PACCHETTI
* `APT-GET` -> INSTALLA/DISINSTALLA PACCHETTI
* `SUDO APT-GET UPDATE` -> AGGIORNA LA LISTA DEI PACKS INSTALLABILI
* `SUDO APT-GET INSTALL "NM"` -> INSTALLA PACK DI NOME "NM"
* `SUDO APT-GET PURGE "NM"` -> DISINSTALLA PACK
* `SUDO APT-GET INSTALL` --REINSTALL "NM" -> REINSTALLA SOVRASCRIVENDO LA VECCHIA INSTALLAZIONE
* `APTITUDE` -> PACK INSTALLABILE CHE A SUA VOLTA PERMETTE DI SCARICARE PACKS
* `WGET` -> PACK CHE SALVA NEL FS LOCALE I FILE PASSATO(LINK)(DIR CORRENTE)

## ISTRUZIONI CONTROLLO DI FLUSSO\\

* `FOR DO DONE` -------> for name in a bb ccc ; do echo $name ; echo ciao ciao ; done
* `WHILE DO DONE` 
* `IF THEN ELIF THEN ELSE FILE`
* `((QUALCOSA))` --> "QUALCOSA" DEVE ESSERE VALUTATO ARITMETICAMENTE


## USARE IN UNO SCRIPT GLI ARGOMENTI A RIGA DI COMANDO PASSATOGLI <br>
ESISTONO VARIABILI D'AMBIENTE CHE CONTENGONO GLI ARGOMENTI PASSATI A RIGA DI COMANDO

* `$#` - NUMERO DI ARGOMENTI PASSATI ALLO SCRIPT
* `$0` - NOME DEL PROCESSO IN ESECUZIONE
* `$1` - PRIMO ARGOMENTO, ($2 SECONDO E COSI VIA)
* `"$#`* - TUTTI GLI ARGOMENTI CONCATENATI E SEPARATI DA SPAZI, SE QUOTATO, QUOTA TUTTI GLI ARGOMENTI INSIEME ("$1 $2 ....ECC")
* `$@` - COME $* MA SE QUOTATO GLI ARGOMENTI VENGONO QUOTATI SEPARATAMENTE ("$1" "$2" ... ECC)
* `$?` - CONTIENE L'EXIT STATUS DELLO SCRIPT
* `${!NOMEVARIABILE}` - METTE NELLA VARIABILE IL VALORE CONTENUTO NELL'ARGOMENTO IL CUI NOME E' CONTENUTO IN ESSA
* `$$` - PROCESS ID DELLA SHELL CORRENTE

## REDIZIONAMENTO INPUT/OUTPUT

* `<` - REDIREZIONA L'INPUT VERSO UN FILE ESEMPIO: "GREP CIAO < CIAO.TXT"
* `>` - REDIREZIONA L'OUTPUT VERSO UN FILE CANCELLANDO IL VECCHIO CONTENUTO DEL FILE
* `>>` - COME IL PRECEDENTE ANCHE SE INVECE DI CANCELLARE OGNI VOLTA IL CONTENUTO METTE IN CODA
* `&>` - REDIREZIONA SIA LO STANDARD OUTPUT CHE LO STANDARD ERROR
* `2>` - REDIREZIONA IL SOLO STANDARD ERROR.
* `|` - REDIREZIONA L'OUTPUT DI UN FILE NELL'INPUT DI UN ALTRO FILE
* `< &n OPPURE > &n ` - REDIREZIONA SUL FILE DESCRIPTOR "1"
<br>
TUTTI QUESTI OPERATORI SI POSSONO CONCATENARE 
<br>
## PARAMETER EXPANSION

* %% - CERCA OCCORRENZA DI SUBSTRINGA IN STRINGA E TOGLILA(parte dal fondo) -> "STRINGA%%SUBSTRINGA"
* ## - UGUALE AL PRECEDENTE MA PARTE DALL'INIZIO
