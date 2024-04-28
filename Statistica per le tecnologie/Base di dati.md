_SQL_ (Structural Query Language), linguaggio dichiarativo (interrogazioni)
_ER_ (Entity Relationship), progettazione scritto-grafica
_XML_ (eXtended Markup Language), composizione di dati semi-strutturato

Informazione, azione di formazione interna
Dato atomico, non suddivisibile
Dato composto, composto da altri dati

I dati possono essere ambigui, sinonimi o polisemi (interpretabili differentemente)
Metadato, dati che danno informazioni sul tipo e azioni degli altri dati
NULL: assenza, ignoranza o inapplicabilità di informazione

Sistema informativo, elaborazione di dati
Sistema informatico, insieme di risorse e processi per gestire dati e informazioni


Proprietà
Attributo, caratteristica di un oggetto
Campo, spazio di memoria per l’attributo
Funzione, programma che descrive oggetto e le sue azioni
Classificazione, costruzione classi

Insieme di oggetti
Identità, individualità dell’oggetto
Estensione, gruppo di oggetti che compongono un insieme
Intensione, definizione di un insieme

Generalizzazione:
-   semplice, insieme superiore da cui si ereditano proprietà
-   multipla, multipli insiemi superiori da cui si ereditano proprietà

Caratteristiche
-   natura auto descrittiva
-   viste multiple, sotto schema
-   condivisione dati
-   gestione conflitti
-   controllo di ridondanza

Sicurezza
-   controllo degli accessi
-   ripristino dai guasti
    -   mirroring
    -   log file

File system
DBMS

Indipendenza logica, cambiamento metadati non intacca dati
Indipendenza fisica, cambiamento dati non intacca metadati

##### Modello ER (Entità Associazione)
> In una biblioteca, un utente prende a prestito un libro ad una certa data e lo restituisce al termine del prestito ad una data non precedente; un libro ha un autore ed un titolo, mentre un utente ha cognome e nome.

![[Biblioteca 2.png]]

**Img 1.1** non tiene conto del vincolo temporale per la quale il prestito avviene prima della restituzione

Decomposizione = sostituzione di una tabella in cui appare una df non di chiave con due tabelle

### Spunti di teoria
Nome | Capacità | Velocità | Persistenza
-----|----------|----------|------------
Random Access Memory (RAM) | Bassa | Elevata | Nulla 
Solid-State Drive (SSD) | Alta |Alta lettura, bassa scrittura | Moderata
Hard Disk Drive (HDD) | Molto Alta | Alta | Lunga

I sistemi operativi Unix descrivono tutto come files. 

Deframmentazione: minimizzare la frammentazione per massimizzare i tempi di accesso

Indici: stringhe che fanno riferimento al posto in memoria dei file.

**Strutture di dati per indici**
Albero binario
