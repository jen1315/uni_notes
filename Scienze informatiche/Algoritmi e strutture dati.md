“Introduzione agli algoritmi ed alle strutture dati”, Mc. Growhill, 2023

Soluzione di un problema computazionale
$$\boxed{\text{Specifica del problema}}\rightarrow\boxed{\text{Sviluppo una soluzione algoritmica}}\rightarrow\boxed{\text{Codifica del programma}}$$
> Un algoritmo è la descrizione di un procedimento in termine di passi elementari (combinati con meccanismi di controllo) volti a risolvere il problema di interesse.

Passi elementari dipendono dal modello di computazione.

Per un problema, quanti algoritmi ci sono? Infiniti (si possono aggiungere passi inutili) con diversa efficienza.
Obiettivo: classifica degli algoritmi in base all’efficienza e tecniche di progettazione.

Efficienza di risorse si basa da
- Tempo <-
- Spazio <-
- Correttezza (es. algoritmi probabilistici)
- Manutenibilità

## Analisi e progettazione

ORDINAMENTO (problema centrale) $\begin{cases}\text{search}\\\text{DB join}\\\text{scheduling}\end{cases}$
Input: $a_{1},…,a_{2}$ numeri
Output: permutazione $a_{1},…,a_{2}$ tale che $a^{’}_{1}\leq a^{’}_{2}\leq…\leq a^{’}_{n}$

1. INSERTION SORT, incrementale $\sim n^2$
2. MERGE SORT, divide et impera $\sim n\log n$

## Insertion sort
```
[5|2|8|4|7]

[#|5|8|4|7]  [2]
[2|5|#|4|7]  [8]
[2|#|5|8|7]  [4]
[2|4|5|#|8]  [7]

[2|4|5|7|8]
```
Pseudo-codice
```
InsertionSort(A)
n = A.length

for j=2 to n {
    key = A[j]
    i = j-1
    while (i > 0) and (A[i] <= key) {
        A[i+1] = A[i]
        i = i-1
    }
    A[i+1] = key
}
```
**Correttezza?** Definiamo gli invarianti
- `for` esterno `A[1,…,j-1]` ordinata
- `while` interno  $\begin{align*}A[1,…,i]&\text{ ordinata}\\ A[i+2,…,j]&\text{ ordinata }\&>key\\ A[1,…,i]& <= A[i+2,…,j]\end{align*}$

`while b do`
- Invariante vero all’inizio
- Invariante `&b` -> Invariante dopo l’esecuzione di C

**Efficienza?** 
Analisi: Quanto l’esecuzione dell’Insertion Sort?
- <u>modello di calcolo</u> ~> modello dei costi
	Ha operazioni atomiche (elementari) 
	-> costo costante
- <u>dimensione del problema</u>
	ordinamento: numero degli elementi da ordinare
	moltiplicazione: # byte argomenti
	algoritmo sui grafi: # nodi, # archi

$=c_{1}+c_{2}+c_{3}n+(c_4+c_5+c_{9})(n-1)+\sum(t_{j}+1)(c_{6}+c_{7}+c_{8})$
```
InsertionSort(A)                       -> c1
n = A.length                           -> c2

for j=2 to n {                         -> n c3
    key = A[j]                         -> (n-1) c4
    i = j-1                            -> (n-1) c5
    while (i > 0) and (A[i] <= key) {  -> sum(tj) c6
        A[i+1] = A[i]                  -> sum(tj+1) c7
        i = i-1                        -> sum(tj+1) c8
    }
    A[i+1] = key                       -> (n-1) c9
}
```
Problema: 
- complicata e inultimente dettagliata (costanti ignote)
- dipendenza dalla specifica istanza del problema
Allora li risolviamo definendo
<u>Tempo di esecuzione</u>
-> $T_{min}(n)$   caso migliore 
-> $T_{max}(n)$   caso peggiore 
-> $T_{medio}(n)$ caso medio

Caso migliore:
A è già ordinato $\forall j\quad t_{j}=0$
$\begin{align*}T(n)&=c_{1}+c_{2}+c_{3}n+(c_{4}+c_{5}+c_{9})(n-1)\\&=\not{a}n+\not{b}\qquad\sim n\end{align*}$

Caso peggiore:
A è in ordine decrescente $\forall j\quad t_{j}=j-1$
$\begin{align*}T(n)=&c_{1}+c_{2}+c_{3}n+(c_{4}+c_{5}+c_{9})(n-1)+\sum_{j=2}^{n}(t_{j}+1)+(c_{6}+c_{7}+c_{8})\\=&\not{a^{’}}n^{2}+\not{b^{’}n}+\not{c^{’}}\qquad\sim n^{2}\end{align*}$

Caso medio:
mediamente $t_{j}+\frac{j-1}{2}$

## Merge sort

Divide et impera
- Divide il problema P in $P_{1},…,P_{n}$ sottoproblemi
- Impera, risolve i sottoproblemi $\begin{cases}\text{ricorsivamente}\\\text{soluzione banale di problema piccolo}\end{cases}$
- Combina, “unisce” le soluzioni di $P_{1},…,P_{n}$ per costruire una soluzione $P$

nel Merge sort
-> divide l’ array in due parti (uguali)
-> ordina i sottoproblemi (ricorsivamente)
-> fondo i due sottoarray ordinati

```
[5|2|4|7|1|2|3|6]
[5|2|4|7]         [1|2|3|6]
[5|2]   [4|7]     [1|2]   [3|6]
[5] [2] [4] [7]   [1] [2] [3] [6]
[2|5]   [4|7]     [1|2]   [3|6]
[2|4|5|7]         [1|2|3|6]
[1|2|2|3|4|5|6|7]
```
Pseudo-codice
```
MergeSort(A,p,r)
    if (p < r)
        q = (p+r/2)
	    MergeSort(A,p,q)
	    MergeSort(A,q+1,r)
	    Merge(A,p,q,r)

Merge(A,p,q,r) // A[p-q] e A[q-r] ordinati
	n1 = q-p+1
	n2 = r-q
	// Crea L[1,…,n1+1] e R[1,…,n2+1]
	for i=1 to n1
		L[i] = A[p+i-1]
	for j=1 to n2
		R[i] = A[q+j]
	L[n1] = R[n2] = infty
	i=j=1
	for k=p to r {
		if (L[i]<=R[j]) {
			A[k] = L[i]
			i = i+1
		}else {
			A[k] = R[j]
			j = j+1
		}
	}
```
**Correttezza?** 
Induzione su $\ell=$

**Principio di Induzione**
proprietà parametrica in $n\in\mathbb{N}\qquad P(n)=\{…n…\}$
per dimostrare che $P(n)$ vale per ogni $n\in\mathbb{N}$
$\begin{rcases}P(0)&\text{caso base}\\\text{assumendo }P(n)\text{ dimostro che }P(n+1)&\text{caso induttivo}\end{rcases}\rightarrow$ per ogni $n\in\mathbb{N}$ vale $P(n)$

**Induzione forte**
$\begin{rcases}P(0)\\\text{assumendo }P(n)\text{ vale per ogni }m<n\quad\dim P(n)\end{rcases}\rightarrow P(n)$ vale per ogni $n$

es. Alberi binari
```
    [r]       ^
   /   \      |
  []   [f]    |
 /  \         | n livelli
[f]  []       |
    /  \      |
  [f]  [f]    v
```
$P(n)=$ “per ogni albero binario di altezza $n$, # foglie $\leq 2^n$”

Procediamo per induzione
$(n=0)$ l’albero è `[r]`    # foglie = $1\leq2$
$(P(n)\rightarrow P(n+1))$ assumiamo $P(n)$ e vogliamo dimostrare $P(n+1)=$“se $T$ ha altezza $n+1$, # foglie $\leq2^{n+1}$”
Sia $T$ di altezza $n+1$: 2 possibilità
```
1.                2.
  [r]                 [r]
   |                /     \
  / \             / \     / \
 / T’\           / T’\   / T”\
*—————*         *————-* *————-*
```
Caso 1
$\#\text{foglie}(T)=\#\text{foglie}(T’)\leq2^{n}\leq2^{n+1}$

Caso 2
$\begin{align*}\#\text{foglie}(T)=\#\text{foglie}(T’)&+\#\text{foglie}(T’’)\\n’,n’’&\leq2^{n}+2^{n+1}\end{align*}$
Ma l’ipotesi induttiva mi assicura solo che vale $P(n)$

Se procedo per induzione completa

**Efficienza?**
Analisi del Merge sort

Se $n$ è la dimensione dell’array
```
Merge(A,p,q,r)
	n1 = q-p+1             -*
	n2 = r-q                |
	for i=1 to n1           |
		L[i] = A[p+i-1]     | costo a’n+b’
	for j=1 to n2           |
		R[i] = A[q+j]       |
	L[n1] = R[n2] = infty  -*
	i=j=1                  -*
	for k=p to r            |
		if (L[i]<=R[j])     |
			A[k] = L[i]     |
			i = i+1         | costo a”n+b”
		else                |
			A[k] = R[j]     |
			j = j+1        -*
Costo complessivo Merge = an+b

MergeSort(A,p,r)
    if (p < r)
        q = (p+r/2)
	    MergeSort(A,p,q)
	    MergeSort(A,q+1,r)
	    Merge(A,p,q,r)
```
$T^{MS}(n)=\begin{cases}c_{0}&\text{se }n\leq1\\T^{MS}(\lceil n\rceil/2)+T^{MS}(n/\lfloor2\rfloor)&\text{se }n>1\end{cases}$

Come stimare $(*)$

<u>Albero di ricorsione</u>
```
                T_ms(n) 
                 an+b                          = an+b
            /            \
  T_ms(n/2)            T_ms(n/2)
   a(n/2)+b             a(n/2)+b               = an+2b
  /         \                 
T_ms(n/4)  T_ms(n/4)  T_ms(n/4)  T_ms(n/4)
 a(n/4)+b   a(n/4)+b   a(n/4)+b   a(n/4)+b     = an+4b
  …     …    …     …              …     …
 / \   / \                       / \   / \
c0 c0 c0 c0 . . .               c0 c0 c0 c0    = nc0
```

quindi
$\begin{align*}T^{MS}(n)&=a’n\log_{2}n+b’n+c’&\sim n\log_{2}n\\T^{IS}(n)&=a^{”}n^{2}+b^{”}n+c^{”}&\sim n^{2}\end{align*}$

$T^{MS}(n)$ è “decisamente” più piccolo di $T^{IS}(n)$
$$\displaystyle\lim_{n\rightarrow\infty}\frac{T^{MS}(n)}{T^{IS}(n)}=\lim_{n\rightarrow\infty}\frac{a’n\log_{2}n+b’n+c’}{a^{”}n^{2}+b^{”}n+c^{”}}=0$$
xcasa
1. Implementare InsertionSort in modo ricorsivo (mai iterazione)
2. Valuta duplicati in un array `(i,j) e i<j t.c. A[i]=A[j]`
	boolean DupCheck(A)
	int DupCount(A)
	 array elemDup(A)
	 array idDup(A)
3. Dato `A[1,…,n]` e key(valore), verificare se esistono i,j tale che `A[i]+A[j]=key`

### Analisi del costo degli algoritmi
Da definire nel tempo peggiore $T_{\text{max}}(n)$, medio $T_{\text{medio}}(n)$ e migliore  $T_{\text{min}}(n)$

$f\cdot g:\mathbb{R}^{’}\rightarrow\mathbb{R}^{”}$
$f(n),g(n)$

**Limite asintotico superiore**
Dato $g(n)$$$\begin{align*}O(g(n))=\{f(n)\ |\ &\exists\ c>0\ \exists\ n_{0} \forall n\geq n_{0}\\ &0\leq f(n)\leq c\cdot g(n)\}\end{align*}$$
**Limite inferiore asintotico**
Dato $g(n)$$$\begin{align*}\Omega(g(n))=\{f(n)\ |\ &\exists\ c>0\ \exists\ n_{0} \forall n\geq n_{0}\\ &0\leq c\cdot g(n)\leq f(n)\}\end{align*}$$**Limite asintotico stretto**
Dato $g(n)$$$\begin{align*}\Theta(g(n))=\{f(n)\ |\ &\exists\ c_{1}>0, c_{2}>0\ \exists\ n_{0} \forall n\geq n_{0}\\ &0\leq c_{1}\cdot g(n)\leq f(n)\leq c_{2}\cdot g(n)\}\end{align*}$$
<u>Metodo del limite</u>
Dato $f(n),g(n)\quad >0$
1. $\displaystyle\lim_{n\rightarrow\infty}\frac{f(n)}{g(n)}=k>0\qquad\text{allora }f(n)=\Theta(g(n))$
	ovvero $\forall\epsilon>0\ \exists n_{0}\ \forall n\geq n_{0}$
	$\left|\frac{f(n)}{g(n)}=k\right|\leq\epsilon$
	$-\epsilon\leq\frac{f(n)}{g(n)}-k\leq\epsilon$
	$k-\epsilon\leq\frac{f(n)}{g(n)}\leq k+\epsilon$
1. $\displaystyle\lim_{n\rightarrow\infty}\frac{f(n)}{g(n)}=0\qquad\text{allora }f(n)=O(g(n))$
2. $\displaystyle\lim_{n\rightarrow\infty}\frac{f(n)}{g(n)}=\infty\qquad\text{allora }f(n)=\Omega(g(n))$
Vale il contrario? Solo se il limite esiste

**Complessità di un problema**
Dato un problema $P$ la sua complessità è la complessità del più efficiente algoritmo che risolve $P$.

$\rightarrow$ <u>limite superiore</u>
Un algoritmo $A$ che risolve $P$ con complessità $O(f(n))$ allora anche $P$ ha complessità $O(f(n))$.

$\rightarrow$ <u>limite inferiore</u>
Se ogni algoritmo $A$ per il problema $P$ ha complessità $\Omega(g(n))$ allora anche $P$ ha complessità $\Omega(g(n))$.

Es. Ordinamento $\qquad\Omega(n)$ (devo almeno leggere gli elementi di input)
dipendenza sostanziale dal modello di calcolo

$\rightarrow$ <u>limite stretto</u>
Se $P$ ha complessità $O(f(n))$ e $\Omega(f(n))$ allora il problema $P$ ha complessità $\Theta(f(n))$.

**Complessità dell’ordinamento** basato su scambio di elementi contigui
```
       k k+1
A [   | | |   ]      A[k] <-> A[k+1]
```
$\rightarrow$ <u>limite inferiore</u>
```
INVERSIONE  [   |7|    |2|   ]      A[i] > A[j]
.                i   <  j
```
$\#Inv(A)=|\{(i,j)|1\leq i<j\leq n\text{ e }A[i]>A[j]\}|$

Osservazione
1. A è ordinato se e solo se # Inv(A)=0
2. massimo numero di inversioni: A ordinato in senso decrescente (e senza ripetizioni) 
	$\#Inv(A)=\sum_{j=2}^n(j-1)=\frac{n(n-1)}{2}$

Osservazione: valutiamo l’effetto di uno scambio `A[k] <-> A[k+1]` sullo “stato” di inversione di una coppia $(i,j)$ con $i<j$
Vari casi
$\rightarrow i,j\neq k,k+1$

$(i,j)$ è inversione prima dello scambio se e solo se è inversione dopo

$\rightarrow i=k,\ j=k+1$
```
     k k+1            3 possibilità    #inv
[   | | |  ]          A[k] < A[k+1]     +1
     i j              A[k] = A[k+1]      0
.                     A[k] > A[k+1]     -1
```
$\rightarrow i=k,\ j>k+1$

$(k,j)$ è inversione dopo se e solo se $(k+i,j)$ è inversione prima
$(k+i,j)$ è inversione dopo se e solo se $(k,j)$ è inversione prima
$\searrow$ limitatamente a $(k,j),(k+i,j)$ il numero di inversioni è immutato

$\rightarrow i<k\text{ e }j=k$

L’operazione di scambio `A[k] <-> A[k+1]` (unica operazione di modifica dell’array) riduce # Inv(A) al più di 1.

Dato A ordinato in senso decrescente (senza ripetizioni) $\#Inv(A)=\frac{n(n-1)}{2}$ quindi per ordinarlo e ridurre le inversioni a 0 devo fare almeno $\frac{n(n-1)}{2}$ scambi.
$\searrow$ Limite inferiore per il problema $\Omega(\frac{n(n-1)}{2})$

Soluzione di Ricorrenze
$T(n)=\begin{cases}1&n=1\\ T(n-1)+1&n>1\end{cases}\qquad\stackrel{?}{=}\Theta(n)$

$T(n)=\begin{cases}c&n\leq1\\2T(n/2)&n>1\end{cases}\qquad\stackrel{?}{=}\Theta(n\log_{2}n)$
2 tecniche di soluzione
1. metodo di sostituzione
2. Master Theorem

**1. Metodo di Sostituzione**
2 fasi $\begin{align*}&\rightarrow\text{idea della soluzione (albero delle ricorrenze)}\\&\rightarrow T(n)=\begin{cases}c&n\leq1\\2T(n/2)&n>1\end{cases}\qquad\stackrel{?}{=}\Theta(n\log n)\end{align*}$

-> verificare la correttezza -> dimostrazione induttiva
$T(n)=\begin{cases}4&n\leq1\\2T(n/2)+6n&n>1\end{cases}$

Ipotesi: $T(n)=an\log_{2} n+bn+c$
Per induzione: 
$(n=1)\qquad T(n)=4\quad\stackrel{\text{ipotesi}}{=}\quad$

$\begin{align*}(n>1)\qquad T(n)&=2T(n/2)+6n\\&=an()+bn+2c+6\\&=an\log_{2}n+(-a+b+6)n+2c\\\text{vogliamo che}\\&=an\log_{2}n+bn+c\end{align*}$

<u>Lavorare direttamente a livello contratto?</u>
$T(n)=\begin{cases}\cancel{4}&\cancel{n\leq1}\\2T(n/2)+\underbrace{6n}_{\Theta(n)}&n>1\end{cases}$
$T(n)=2T(n/2)+\Theta(n)\qquad\stackrel{?}{=}\Theta(n\log n)$

Dimostriamo
1. $T(n)=O(n\log n)$
2. $T(n)=\Omega(n\log n)$

(1) $T(n)=O(n\log n)$ 
	$T(n)\leq c\cdot n\log n\qquad c>0$
per induzione, senza caso base
	$\begin{align*}T(n)&=2T(n/2)+\Theta(n)\\\&leq2T(n/2)+dn\\\&leq2\left(c\frac{n}{2}\log\frac{n}{2}\right)+dn\\&=cn(\log n-\log 2)+dn\\&=(c\log_{2}-d)\end{align*}$

(2) $T(n)=\Omega(n\log n)$
	$T(n)\geq c^{’}n\log n$
per induzione

**2. Master Theorem**
$T(n)=\underbrace{a}_{a\geq1}T(\underbrace{\frac{n}{b}}_{b>1})+f(n)$
$a$ numero dei sottoproblemi
$\frac{n}{b}$ dimensione dei sottoproblemi
$f(n)$ costo di "combina"

Quale domina ($f(n)$ vs $n^{log_{b}a}$)

(1) $T(n)=\Theta(n^{log_{b}a})$ se $f(n)=O(n^{log_{b}a-\epsilon})\text{ e }\epsilon>0$
(2) $T(n)=\Theta(n^{log_{b}a}\log n)$ se $f(n)=\Theta(n^{log_{b}a})$
(3) $T(n)=\Theta(n^{log_{b}a})$ se $f(n)=\Omega(n^{log_{b}a+\epsilon})\text{ e }\epsilon>0$ 
	e REGOLARITA $\exists k\quad 0<k<1$ a $f(\frac{n}{b})\leq kf(n))$

```
                  T(n) 
             / ... a ... \
        T(n/b)             T(n/b)
     / ...a... \         / ...a... \
  T(n/b^2)  T(n/b^2)  T(n/b^2)  T(n/b^2)
  /     \    /     \             /     \
  …     …    …     …             …     …
 / \   / \                      / \   / \
c   c c   c . . .              c   c c   c    #foglie= a^(logn)
```

$\displaystyle T(n)=f(n)+af(\frac{n}{b})+a^{2}f(\frac{n}{b^{2}})+...+a^{log_{b}n}f(\frac{n}{b^{log_{a}n}})+ca^{log_{b}n}$
$\displaystyle T(n)=f(n)+af(\frac{n}{b})+a^{2}f(\frac{n}{b^{2}})+...+(f(1)+c)n^{log_{b}a}$

(1) se "domina" $n^{\log_{b}a}\qquad\rightsquigarrow\qquad T(n)=\Theta(n^{\log_{b}a})$
(2) se sono "pari" $\qquad\rightsquigarrow\qquad T(n)=\Theta(n^{log_{b}a}\log n)$

$\begin{align*}\text{(3) se "domina" }f(n)\qquad\rightsquigarrow\qquad &T(n)=\Theta(f(n))\\ &\text{regolarità }af\left(\frac{n}{b}\right)\leq kf(n)\end{align*}$
$T(n)=f(n)+af\left(\frac{n}{b}\right)+a^{2}f\left(\frac{n}{b^{2}}\right)+...+$
tende a una costante

<u>Uso del Master Theorem</u>
$T(n)=aT(\frac{n}{b})+f(n)$
confrontare $f(n)\qquad n^{\log_{b}a}$

metodo del limite (se possibile)
(a) $\displaystyle\lim_{n\rightarrow\infty}\frac{f(n)}{n^{log_{b}a}}=k >0$
(b) \[caso 1\] 
$\displaystyle\lim_{n\rightarrow\infty}\frac{f(n)}{n^{log_{b}a}}=0\qquad\rightsquigarrow\qquad f(n)=O(n^{(log_{b}a)-\epsilon}),\ T(n)=\Theta(n^{log_{b}a})$
(c) $\displaystyle\lim_{n\rightarrow\infty}\frac{f(n)}{n^{log_{b}a}}=k >0$

esempio. 
$T(n)=5T(\frac{n}{2})+n^{3}$
$\begin{align*}f(n)=n^{3}\qquad=\qquad\Omega(n^{log_{b}a}+\epsilon)=&\Omega(n^{log_{2}5+\epsilon})\\ &\epsilon<3-\log_{2}5\end{align*}$
unica cosa possibile è il caso 3.
Devo verificare la regolarità
$af(\frac{n}{b})\leq kf(n)\qquad k>1$ asintoticamente
$5\frac{n^{3}}{2^{3}}=5f(\frac{n}{2})\leq kf(n)=kn^3$
$\rightarrow T(n)=\Theta(f(n))=\Theta(n^{3})$

xcasa
1. Implementare InsertionSort in modo ricorsivo (mai iterazione)
2. Valuta duplicati in un array `(i,j) e i<j t.c. A[i]=A[j]`
	boolean DupCheck(A)
	int DupCount(A)
	 array elemDup(A)
	 array idDup(A)
3. Dato `A[1,…,n]` e key(valore), verificare se esistono i,j tale che `A[i]+A[j]=key`

```
Insert(A, i) {
	if(i > 1) and (A[i] <= A[i-1])
			tmp = A[i]
			A[i] = A[i-1]
			A[i-1] = tmp
			Insert(A, i-1)
}

RecInsertionSort(A, j)
	if(j > 1)
		RecInserionSort(A, j-1)
		Insert(A, j)
```
Complessità?
$T_{insert}(j)=c+T_{insert}(j-1)\qquad\rightsquigarrow\quad T_{insert}(j)=\Theta(j)$
$\begin{align*}T_{RIS}(n)=&T_{RIS}(n-1)+\overbrace{\underbrace{T_{insert}(n)}_{\Theta(n)}+c}^{\Theta(n)}\\=&T_{RIS}(n-1)+\Theta(n)=\Theta(n^2)\end{align*}$

```
# per trovare i duplicati a “cavallo” faccio in modo che la ricerca dei duplicati come “effetto collaterale” ordini l’array
CrossCheck(A, p, q, r) {
	n1 = q-p+1
	n2 = r-q
	L[1,…,n1] <- A[p,…,q]
	R[1,…,n2] <- A[q+1,…,r]
	L[n1+1] = R[n2+1] = infty
	i = j = 1
	k = p
	while(k <= r) and (L[i] != R[j])
		if L[i] < R[i]
			A[k] = L[i]
			i++
		else
			A[k] = R[j]
			j++
		k++
	return (k <= r)
}

DupCheck(A, p, r) {  # verifica la presenza di duplicati
	if(p < r)
		q = p+r/2
		return DupCheck(A, q, p) or
			   DupCheck(A, p+1, r) or
			   CrossCheck(A, p, q, r)
	else
		return false
}
```
Complessità?
$T(n)=2T(\frac{n}{2})+\Theta(n)\qquad\rightsquigarrow\quad T(n)=\Theta(n\log n)$
$\text{senza ordinare}\qquad\rightsquigarrow\quad T(n)=\Theta(n^2)$

```
Cross(A, p, q, r) {
	n1 = q-p+1
	n2 = r-q
	L[1,…,n1] <- A[p,…,q]
	R[1,…,n2] <- A[q+1,…,r]
	L[n1+1] = R[n2+1] = infty
	i = j = 1
	k = p
	while(k <= r) and (L[i] != R[j])
		if L[i] < R[i]
			A[k] = L[i]
			i++
		else
			A[k] = R[j]
			j++
		k++
	return (k <= r)
}

DupCount(A, p, r) {
	if(p < r)
		q = p+r/2
		return DupCount(A, q, p) +
			   DupCount(A, p+1, r) +
			   CrossCount(A, p, q, r)
	else
		return 0
}
```

```
Sum(A, key) {
	for i to len(A)
		j = i+1
		for j to len(A)
			if(A[i]+A[j] = key)
				return 
			j++
}
```
idea2: ordino `A[1,…,n]`
costo -> n interazioni di costo $\Theta(1)$
	  -> costo totale $\Theta(n)$
	  (+ ordinamento $\Theta(n log n)$)
COMPLESSO $\Theta(n)+\Theta(n\log n)=\Theta(n\log n)$

Se volessi gli indici $i$ e $j$ nell’array di partenza? Usa array di indici.

<u>array di occorrenze</u>

Se $\begin{align*}A[1,…,n]\\ A[i]>=0\end{align*}$ è array di interi, k intero

Se $A[i]+A[j]=k\quad\rightsquigarrow\quad A[i]+a[j]\leq k$
$\searrow$ unici elementi di interesse sono $A[i]$ tali che $0\leq A[i]\leq k$

uso un array $V[0,…,k]$ booleano
`V[v] = true` se e solo se esiste $1\leq i\leq n\quad A[i]=v$
- inizializza `V[0,…,k] = false`
- scorre l’array A
	se $A[i]\leq k$ allora
	- `V[A[i]] = true`$\rightsquigarrow\exists\ j\leq i$

Ordinamento
- altri algoritmi
- limite inferiore $\Omega(n\log n)$
- ordinamento in tempo lineare

<u>InsertionSort</u>
- incrementale
- complessità 
	tempo $\Theta(n^2)$
	spazio: in loco (+ un paio di variabili) $\Theta(1)$

<u>MergeSort</u>
- divide-et-impera
- complessità 
	tempo $\Theta(n\log n)$
	spazio:
	- merge $\Theta(n)$ copia dell’input
	- mergesort $S^{MS}(n)=\max\{S^{MS}\left(\frac{n}{\lfloor2\rfloor}\right),S^{MS}\left(\frac{\lceil n\rceil}{2}\right),\Theta(n)\}=\Theta(n)$

-> miglioramento: allocare `B[1,…,n]` esplicitamente (risparmio tempo di allocazione)
```
MergeSort(A, n)
	allora B[1,…,n]
	MergeSortRec(A, B, 1, n)
```
xcasa
1. Evita la copia dell’ input nel Merge e usa A e B alternativamente come sorgente/destinazione.
2. Versione iterativo divide fino a un k ordinato in InsertionSort (Timsort)
3. In loco

<u>HeapSort</u>
- complessità
	tempo: $\Theta(n\log n)$
	spazio: $O(1)$
- min-heap / max

Usa gli alberi binari ordinati (figlio sx, dx).
```
    [r]       ^
   /   \      |
  []   [f]    |
 /  \         | h cammino max radice-foglia
[f]  []       |
    /         |
  [f]         v
```

Albero (binario) completo
1. Ogni nodo non foglia ha esattamente 2 figli
2. Ogni cammino nodo-foglia ha la stessa lunghezza
```
        [r]       
      /     \     
    []       []   
   / \       / \   
 []   []   []   []   
 /\   /\   /\   /\  
[][] [][] [][] [][]   Completo
```

Allora binario completo di altezza $h$ ha $2^{h-1}$

L’albero quasi completo: tutti i livelli completi tranne l’ultimo, dove le foglie “a sx”.

Heap: albero ordinato binario quasi completo
Implementato come array
![[Pasted image 20241017152519.png]]
```
Radice A[i]
Nodo A[i] figlio sx A[2*i]
     ''   figlio dx A[2*i+1]
Nodo A[i] parente A[i/2]
A.length  A.size = # nodi albero
```

Max-Heap: Heap + proprietà d’ordine
-> ogni nodo è $\geq$ discendenti
$\begin{align*}\forall\ i\qquad A[i]\geq&A[Left(i)]\\ \geq&A[Right(i)]\end{align*}$
-> ogni nodo è $\leq$ antenati
$\forall\ i\qquad A[i]\leq A[Parent(i)]$

Come ottengo un max-heap?
2 osservazioni
- un albero con un solo nodo è max-heap
- dato un nodo i in heap con sottoalbero max-heap, è facile sistemarla con
```
MaxHeapify(A, i)
	l = Left(i)
	r = Right(i)
	if (l <= A.size) and (A[l] > A[i])
		max = l
	if (r <= A.size) and (A[r] > A[i])
		max = r
	if max != i
		A[i] <-> A[max]
		MaxHeapify(A, max)
```
Correttezza?
- caso base 
	i foglia: non faccio niente, foglia è max-heap
	i non foglia: $A[i]\geq A[l],A[r]$
Complessità?
$O(\log n)$

Build Max-Heap
dato un array $A$, parto dal primo nodo parente a destra dove uso MaxHeapify e così ai nodi precedenti.

Come individuare nodi non foglia
se $i\geq\frac{n}{2}+1\Rightarrow$ `A[i]` foglia, ovvero non ha figlio sinistro `Left(i)`
se $i\leq\frac{n}{2}+1\Rightarrow$ `A[i]` non foglia, ovvero `Left(i)<=n`
```
BuildMaxHeap(A)
A.length
for i = A.length/2 down to 1
	MaxHeapify(A,i)
```
<u>inizio</u>: $i=\lfloor\frac{A.length}{2}\rfloor\Rightarrow\forall\ j>\frac{A.length}{2}$
<u>iterazione</u>:
Complessità?

$n_{h}\leq2^{h_{T}-h}=\frac{2^{h_{T}}}{2^{T}}\leq\frac{2^{\log_{2}n}}{2^{h}}=\frac{n}{2^{h}}$
$\begin{align*}T(n)=&\sum\limits_{n=1}^{\log_{2}n}n_{h}O(h)\leq\sum\limits_{n=1}^{\log_{2}n}\frac{n}{2^{h}}O(h)=O(\sum\limits_{n=1}^{\log_{2}n}n\frac{h}{2^{h}})\\=&O(n\sum\limits_{n=1}^{\log_{2}n}\frac{n}{2^{h}})=O(n)\end{align*}$

```
HeapSort(A)
	BuildMaxHeap(A)
	for i = A.length down to 2
		A[1] <-> A[i]
		A.size = A.size-1
		MaxHeapify(A, 1)
```
Complessità?
$\begin{cases}n-1\text{ iterazioni}\\ \text{ogni iterazione: costo MaxHeapify }O(\log n)\end{cases}$
-> complessivamente $O(n+n\log n)=O(n\log n)$

Code con priorità
$\begin{align*}\text{collezioni dinamiche di elementi }x\qquad& x.key\\\text{operazioni}\qquad&\text{ExtractMax(a)}\\\qquad&\text{Insert}\\\qquad&\text{Delete}\end{align*}$
ExtractMax, basta che ritorni la radice dopo BuildMaxHeap
Insert, devo tenere conto dell'i che sto inserendo che sballa il max-heap esistente