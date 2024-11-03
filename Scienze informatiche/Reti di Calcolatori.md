“Computer Networks”, Andrew Tanenbaum, 2017

Rete: ogni qual volta che c’è un grafo sottostante

Classificazione di reti
- tipo, il loro uso
- tipo di trasmissione
- mezzo di trasmissione
- taglia
- topologia

**Client-Server Applications**
Molteplici clienti si connettono a un server

**Peer-to-Peer (P2P)**
Dispositivi si connettono tra di loro

Grandezza reti (taglia)
… > WAN (Wide Area Network) > 
MAN (Metropolitan Area Network) > 
LAN (Local Area Network) > 
PAN (Personal Area Network) > …

7 forme della rete
- point-to-point
- star
- ring
- mesh
- tree
- ibrida / gerarchica

Virtualizzazione:
la macchina virtuale non conosce gli altri livelli (non può quindi comunicarvi)

Standard Internet sono formulati da
RFC(Request For Comments), 
IETF(Internet Engineering Task Force)

Un protocollo rete simula quello umano.

Strati di sistemi di rete
Addressing
Error Control
Flow Control
Multiplexing, multitasking ovvero più comunicazioni simultanee
Routing, decidere strada migliore

```
*——————-*                  *——————-*
| Layer | <- protocollo -> | Layer |
*——————-*                  *——————-*
   |                           |
servizio                   servizio
   |                           |
*——————-*                  *——————-*
| Layer | <- protocollo -> | Layer |
*——————-*                  *——————-*
   |                           |
 . . .                       . . .
   |                           |
 *————————————————————————-——————-*
 |          Strato Fisico         |
 *———————————————————————————-————*
```

### OSI
(Open Systems Interconnection)
Prodotto dall’ISO (International Standards Organisation)

1. **Physical**
2. **Data link**, incapsula le unità di informazione da trasmettere. Trova gli errori di trasmissione.
3. **Network**, consegna dei pacchetti, routing
4. **Transport**
5. **Session**
6. **Presentation**, visualizzazione dati
7. **Application**

### TCP / IP
Retroattivamente vedendo cosa c’è già in internet

| OSI          | TCP / IP        | Modello ibrido |
| ------------ | --------------- | -------------- |
| Application  | Application     | Application    |
| Presentation | X               | X              |
| Session      | X               | X              |
| Transport    | Transport       | Transport      |
| Network      | Internet        | Internet       |
| Data link    | Host-to-network | Data link      |
| Physical     |                 | Physical       |
(xkcd)

OSI era troppo complesso (7 livelli) e non ha preso piede. Ora il modello usato è quello ibrido.

## Strato Fisico

Tipo di trasmissione
### Connessione cablata
**coppia annodata**
I cavi sono intrecciati per limitare l’interferenza reciproca da campo magnetico (nell’incrocio le due correnti + e - parzialmente si annullano)
UTP (Unshielded Twisted Pair)

**cavo coassiale**
Il cavo è schermato, insulato e con conduttore a terra. Il filo è più grosso e la banda è più grande dell’UTP.

**fibra ottica**
Invece dell’elettricità passa la luce. C’è vetro inclinato che riflette la luce. Ci sono diversi tipi di luci e non esiste una migliore.

| Proprieties             | LED       | Laser               |
| ----------------------- | --------- | ------------------- |
| Data rate               | Low       | High                |
| Fibre type              | Multimode | Multi or singlemode |
| Distance                | Short     | Long                |
| Lifetime                | Long      | Short               |
| Temperature sensitivity | Minor     | Substantial         |
| Cost                    | Low       | Expensive           |
Contro: 
Ha difficoltà a passare per angoli, ad collegarsi con altri tipi di cavi ed è costosa.
Pro: 
Il filo è più piccolo e la banda è molto più grande degli altri tipi di fili. È da difficile da intercettare (“tap”). Per mantenere la luce si deve usare corrente elettrica. Unire o separare luci diverse è facile.

### Wireless
**Spettro elettromagnetico**

![[1.webp]]

Come vengono assegnate le frequenze?
- “Beauty contest” per chi fa del meglio
- Lotteria/asta per chi fa l’offerta migliore

Chi vince? Come facciamo a fare in modo che ci siano risorse per chi ne ha bisogno?
**Banda ISM** (Industrial, Scientific, Medical)
	è libera e distribuita lungo tutto lo spettro.

Esempi: Bluetooth, telecomando, forni a microonde, telefoni senza filo, reti 802.11

*Trasmissioni radio*
Omnidirezionale, non servono allineamenti tra il trasmettitore e il ricevente.
Sono a bassa frequenza e passano tutti gli ostacoli ma si dispergono per la lunga distanza.

Le trasmissioni sonar e pager sono a Hz inferiori di quelle radio.

Le frequenze richiedono il cambio di stato energetico alle cose che incontrano per procedere; quindi quelli da Hz bassi incontrano meno resistenza di quelli alti.

![[images.jpg]]
Tipi di frequenze radio
- AM, passano gli ostacoli, ma si dispergono più in fretta
	segue la superficie terrestre
- FM, non passano bene gli ostacoli, assorbite dalla pioggia
	rimbalzano dall'atmosfera terrestre

*Trasmissioni microonde*
Onde viaggiano quasi a linea retta e possono essere focalizzate per viaggiare distanze più lunghe. Rimbalzano su metalli e acqua, economiche.

Usata dal sistema telefonico e televisivo americano per comunicazioni a lunga distanza (grandi spazi vuoti). MCI (Microwave Communications Inc.)

*Trasmissioni infrarossi e millimetriche*
Direzionali e non passano oggetti solidi. Richiedono poca energia, economiche e sicure (porte infrarossi).

*Trasmissioni luminose*
Uso delle luci visibili. Ritornate in uso con i laser, ma vengono rovinate dalla pioggia e anche dal semplice vapore.

### Satelliti

| Satelliti            | Latenza | N coprire Terra |
| -------------------- | ------- | --------------- |
| GEO                  |         | 3               |
| upper Van Allen Belt | -       | -               |
| MEO                  |         | 10              |
| lower Van Allen Belt | -       | -               |
| LEO                  |         | 40+             |
![[Orbits.gif]]
Van Allen raggruppa l'energia dal sole che raggiunge la Terra.

Più basso è il satellite, più satelliti servono.
I tempi di latenza diminuiscono
La potenza richiesta richiesta diminuisce del quadrato e il loro lancio.

#### MEO
Satelliti in orbita media.
Il primo satellite, lo Sputnik (4 ottobre 1957) è una palla che ruota e ha lunghe antenne. Usa frequenze radio per mandare un audio in loop. Questo audio cambia per effetto Doppler.

- GPS (30 satelliti), tecnologia militare di NAVSTAR
	Non c'erano modi di navigazione tranne la bussola che sballa per cambi elettromagnetici. Per queste variazioni l'aereo civile call 007 dall'USA per la Corea segue una rotta diversa da quella pianificata e viene intercettata dai russi. Pressione pubblica rende il GPS pubblico.

I satelliti MEO si muovono, per usarli si deve capire dove si trovano (tempo di fix) e poi triangolare la posizione. 

A-GPS, viene istituito cosicchè un gestore telefonico tenga la posizione dei satelliti. Viene elimitano il tempo di fix.

#### GEO
Satelliti geostazionari in orbita alta.

![[download.jpg]]
max 180 satelliti, perché?
- interferenze dei coni di trasmissione
- problema di raggiungimento posizione orbita
Idea di Arthur Clarke nel 1945 (scrittore di fantascienza)

- Satelli spia
- Meteo
- Direct broadcast satellitare (televisione analogica e digitale)
	Banda Ku ad alta potenza
	Solo sopra l'equatore, mira il cono di trasmissione

#### LEO
Satelliti in orbita bassa.
IRIDIUM (77 pianificati, 66 effettivi)
- ogni satellite ha 48 celle mobili che coprono la terra
- telefono satellitare, mandano e ricevono dai satelliti
- banda di 2200 a 3800 (4kb)
Non ha successo (durato per 9 mesi), costi troppo alti, mercato troppo ampio, telefono troppo grosso.
Ora usato per Tsunami warning system.

Globastar (52 satelliti)
Satelliti ripetitori che mandano a stazione a terra. 
Economici ma poco duraturi. 
Nessuno li toglie: space debris (rottami spaziali)

![[Debris-LEO1280.jpg]]
(11 gennaio 2007) viene lanciato arma anti-satellite, 
satellite distrutto diventa
tanti frammenti (40 milioni) ad alta velocità 
-> la loro energia $E=mv^{2}$, ogniuna è piccola bomba

PROBLEMA: 
- satelliti in orbita sono in pericolo
- diventa difficile andare in spazio
- ci stiamo avvicinando al sindrome di Kessler (reazione a catena)

Cosa possiamo fare? Rottamare “ecologicamente”
- deviare l’orbita e farlo entrare all’atmosfera (si brucia)
	PERICOLOSO
- allontanati nell’**orbita graveyard**

Frammenti già presenti?
Detriti (>=10cm) devono essere tracciati ma, sono tantissimi e difficili da misurare
Ogni satellite viene allarmato di possibili collisioni; sono troppe.
Le si ignorano se si ritengono poco possibili.

Nel passato i satelliti erano una promessa del futuro perché la telecomunicazione terrestre era in mano ai monopoli.
1984, **Revised Telecommunication Act** dagli USA
Fibra+Wireless vince sui satelliti.

Satellite ancora usato per zone senza campo, per la tv e GPS.
Satellite funziona molto bene per il broadcasting, ovvero mono-direzionali.

SpaceX Starlink (2019)
Orbita LEO bassa.
Tantissimi satelliti a basso costo (6426 satelliti, 55 non funzionanti)
46% della popolazione non è collegata ad internet, Starlink aiuta

#### Molniya e Tundra
Orbita ellittica con la Terra in uno dei suoi fuochi.
![[IMG_8400.png]]

### Segnale
La potenzia del segnale è la velocità di oscillazione.
Misura fisica: **bandwidth**, capacità delle frequenze trasmissibili
Misura informatica: **data rate** (bit rate, baud rate, etc)

La potenza per creare frequenze cresce al quadrato.
C’è un limite di banda (limite della potenza) -> bandwidth

Per fare telecomunicazioni si deve simulare la realtà, *FOURIER*
Oscillazioni di energia a cerchio che si sommano
![[centered.jpeg]]
Solo l'onda sinusoidale esiste in natura.
Fourier ha una classifica di frequenze più importanti delle altre.

Problemi: un impulso energetico trasmesso da un mezzo subisce 
- attenuazione di potenza
- dispersione, cambia la forma delle armoniche
#### Attenuazione di potenza
es. attenuazione in decibel: $10\log_{10}(\text{PotenzaTrasmessa/PotenzaRicevuta})$
Il nostro udito attenua logaritmicamente.

L' attenuazione accade indipendentemente tra le diverse frequenza.

**Teorema di Nyquist**
Il data-rate massimo è $$2B\log_2L$$ - B è la grandezza di banda
- L sono i livelli del segnale usato
Nyquist non tiene conto del *rumore* di fondo.

**Teorema di Shannon (-Hartley)**
In cui si tiene conto del rumore.
$B\log_{2}(1+S/N)$

#### Dispersione della potenza
La dispersione cambia la forma delle armoniche.

Cosa possiamo fare?
limitiamo la grandezza della rete e usiamo ripetitori :(
-> *SOLITONI*
- "Wave of Traslation", 1834
- onda non soggetta di attenuazione e dispersione
- bidirezionale, quando due onde si scontrano, non accade nulla e continuano per la loro strada
- funzionano nelle fibre ottiche
10000km senza dispersione

da fare nella piscina: solitoni di Falaco con i buchi neri di Snells
### La Rete Mondiale

2 CAVI TRANS-ATLANTICI
Data-rate: 8 parole al minuto
Per evitare il caso di "Madman Whitehouse", vengono aggiunti ripetitori.
30 anni dopo, tutto il mondo viene collegato.
1892, Thomas Edison inventa il "duplex telegraph", connessione a due vie contemporanee
54 anni dopo, viene installato il TAT-1, primo cavo telefonico transatlantico
32 anni dopo, viene installato TAT-8, fibra ottica transatlantica con ripetitori ottici SHR (Self Healing Ring)
![[Untitled.png]]
#### La Seconda Grande Rete
Il telefono è inventato da Antonio Meucci (1849)
ottiene caveat perché brevetto costa troppo. American District Telegraph Co. gli ruba il caveat. Bell plagia il brevetto di Gray

Telefono
1. point-to-point, coppie di telefoni collegati
2. switching center, i centralini dove manualmente si devono collegare i fili
3. 
Il *Revised Telecommunication Act* distrugge il monopolio AT&T in 23 diverse compagnie in competizione l'una con l'altra.
Ogni nuova start-up ha diritto di essere inserito, ovvero gli è concesso l'utilizzo di una parte della rete esistente.

Il telefono è attualmente, tutto digitale tranne l'UTP all'ultimo miglio
Il modem serve per collegare il segnale digitale a quello analogico.

Le onde digitali hanno problemi di attenuazione e dispersione.
Possono essere create usando
- **DC** corrente continua, funziona bene a piccole distanze, es. batterie (Edison)
- **AC** corrente alternata, si trasporta bene per le lunghe distanze (Tesla)
AC prevale.

Come codifichiamo il segnale digitale?
- modulando in *ampliezza*
- modulando in *frequenza*
	detta frequency shift keying
- modulando in *fase*
	detta phase shift keying

**QPSK** (Quadrature Phase Shift Keying)
alfabeto di 4 simboli usando 4 sfasamenti tipicamente angoli simmetrici
bitrare è doppio del baudrate

Si potrebbero aumentare il numero di simboli ma così facendo, diventano poco distinguibili.
Allora combiniamo due tipi di modulazione: fase e ampliezza.
Vediamo il loro costellation diagram
![[3-s2.0-B9780323919234000045-f07-05-9780323919234.jpg]]
QAM-16: bitrate quadupro del baud (16)

In teoria i QAM ottimali sono quelli circolari, con massima distanza tra i simboli. Questi non si usano perché sono più difficili da generare e decodificare.
![[The-best-constellation-diagram-for-8-QAM-signal.png]]

>Il limite fisico (di Shannon) della linea telefonica è di 36000bps
>-> il meglio che il modem moderno può ottenere è 35kbps al secondo!!
>
>Questa banda è troppo bassa, come siamo riusciti ad aumentarla?

Filtramo il segnale togliendo i rumori inutili. Con la linea telefonica ci sono alcuni limiti di filtraggio, il limite è

Nel caso di un servizio digitale il limite fisico raddoppia (70kbps)
è possibile usare 64kbps! 
Ma lo standard è di 56kbps perché gli USA usano solo 7bit su 8.

Lo standard è asimmetrico.
V.90 (1998) 56k in download e 33.6k in upload

Il fax è utile per le immagini, ma non molto per il testo. In occidente non è quindi riuscito a prendere piede inizialmente.
In giappone con i loro ideogrammi però, il fax è perfetto per comunicazione testuale e grazie a questo riesce a prendere popolarità nel mondo.

Gruppo 3 impiega 6-15
- Standard: 200x100 dpi
- Fine: 200x200 dpi
- Superfine: 200x400 dpi
- Massima del gruppo 3: 400x400 dpi
V.27 (1998): 4800bps, PSK
V.29 (1988) QAM
V.17 (1991) TCM
V.34 (1994) si ritorna a QAM e linea telefonica e fax si unificano

> Se questi sono i limiti di tramissione come riusciamo ad arrivare ai MB?

La tv via cavo coassiale arrivava già a 10Mbps.
Il satellite poteva servire 50Mbps!
Le compagnie telefoniche devono pensare veloce per non perdere alla competizione.

Il vero problema ricade nell'ultimo miglio, possiamo cambiare il tipo di cavo.
ma il costo è ENORME

Rimuoviamo il filtraggio > nel DSL da 4000Hz si arriva a 1100000Hz!
Il filtro però è necessario per non distruggerci le orecchie:
-> si aggiunge uno *splitter* direttamente dentro il modem di casa.

Ogni splitter genere interferenze sulla linea. Limitiamo a un solo splitter

Però xDSL spesso continua ad essere lenta. Perché?
![[unnamed.gif]]

Frequency Division Multiplexing (FDM) per trasmettere dati a diverse abitazioni.

ADSL (Asymmetric DSL)
Da più spazio a downstream all'upstream.
![[Division-of-ADSL-bandwidth.png]]
Ma in un cavo UTP, due canali sono ingestibili: interferenza in una di questi, fa crollare metà la linea.
Si usano 246 canali, 1 per voce, 5 vuoti, 32 upstream e il resto downstream.
I 5 canali vuoti sono necessari per proteggere la telefonata dai rumori.

![[VDSL2_frequencies.png]]
Usiamo V.34

ADSL2+ usano banda doppia (2.2Mhz invece di 1.1Mhz) ma queste frequenze sono molto fragili, non ci sono molti vantaggi.
Ci sono varianti "all-digital" dove viene tolta la banda telefonica e i vuoti.

< appunti dall'iPad >

Quando una rete si allarga, si aggiungono livelli (come i livelli della linea telefonica). Si usa lo **switching**.
*Circuit switching*, un collegamento fisico tra due dispositivi che si comunicano
delay iniziale

*Message switching*, lanciamo direttamente un messaggio finché non trova lo switch e poi si costruisce il percorso
store and

*Packet switching*, si divide il messaggio in multipli pacchetti di lunghezza massima prefissata. Vengono permesse trasmissioni delle parti in parallelo; pacchetti possono non arrivare in ordine o alcuni possono perdersi.

#### Telefonia mobile
Europa (e Italia) sono alla meglio dell'USA!!

*Standardizzazione*: l'Europa stabilisce standard unico.
Gli USA con eccesso di liberalismo, hanno lasciato che ci fossero standard multipli, creando reti incompatibili.

Principio della *conoscenza tariffaria*
In Europa, i numeri mobili sono diversi da quelli fissi, sono calcolabili prima.
Negli USA non c'è distinzione -> il surplus è pagato dal possessore dal cellulare

In USA la telefonia fissa ha tariffe molto basse quindi la telefonia mobile ha difficoltà ad entrare in mercato. 
In Europa il contrario: monopoli in telefonia fissa con prezzi alti, telefonia mobile tariffe convenienti.

Tutta la telefonia mobile si basa sulla l'infrastruttura fissa del territorio (switching center).
0G, 1G, 2G, 3G, 4G

**0G: Analogica (1950 circa)**
- deriva dalle trasmissioni radio e si sono evolute in sistemi *Push To Talk* (walkie-talkie)
- un solo canale per ricevere e trasmettere, *half-duplex*
il sistema IMTS (1960)
- Improved Mobile Telephone System
- 2 frequenze
- aumenta il livello di privacy: non si sentono le comunicazioni degli altri
- super-trasmettitori ad alta potenza
  "celle" di centinaia di chilometri
- ma massimo di 23 canali nella banda 150-450Mhz, pochi utenti

**1G: Analogica (1982)**
- AMPS (Advanced Mobile Phone System) conosciuto in Italia come TACS (Total Access Communication System)
- le celle sono più piccole, 10-20km
- capacità più grande, più utenti
- diminuisce la potenza richiesta dai telefoni (meno batteria)
- celle creano molte interferenze tra loro
  -> separazione per frequenza -> MA capacità diminuisce! 

Francis Guthrie, coloratore di mappe politiche propone che tutte le mappe si possono colorare con 4 colori (1852).
*Teorema dei quattro colori* (1976), primo teorema dimostrato dal computer.
In 500 pagine dice che ogni mappa al mondo può essere suddivisa in 1936 casi e tutte queste possono essere colorate in 4 colori.

Abbandoniamo 3/4 della banda per risolvere la separazione in frequenza?
No, le città sono molto angolari quindi celle quadrate non funzionano.
Celle esagonali, 3 colori?
-> quando vanno in overload creano microcelle, si arrivano fino a 7 colori


da vedere: Matrix, Inception, Frankestein junior