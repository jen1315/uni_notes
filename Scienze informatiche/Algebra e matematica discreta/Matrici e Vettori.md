(Algebra)
### Matrice e sistema lineare
Siano $m,n\in\mathbb{N}$, una matrice $m\times n$ è una tabella di $m,n$ oggetti(numeri o elementi di uno stesso insieme) disposti ordinatamente in $m$ righe e $n$ colonne. 
Tali oggetti sono detti COEFFICIENTI della matrice.

<u>Notazione</u> Una matrice $m\times n$ sarà indicata con uno dei seguenti modi
$$\begin{pmatrix}a_{11} &a_{12} &… &a_{1n}\\ a_{21} &a_{22} &… &a_{2n}\\ &&…\\ a_{n1} &a_{n2} &… &a_{nn}\end{pmatrix}\qquad (a_{ij})_{\begin{align}1\leq i\leq m\\ 1\leq j\leq n\end{align}}\quad\text{ o }\quad(a_{ij})$$

Osservazione: ogni numero reale può essere visto come una matrice $1\times1$ con coefficiente 

SOMMA
Siano $A=(a_{ij})$ e $B=(b_{ij})$ due matrici $m\times n$ in una matrice $A+B$ definita$$A+B=(a_{ij}+b_{ij})$$
**Proprietà**
Siano $A,B,C$ tre matrici $m\times n$ e siano $\alpha,\beta\in\mathbb{N}$
1. $A+(B+C)=(A+B)+C$  associativa
2. $A+B=B+A$ commutativa
3. $A+0=A\quad(=0+A)$ esistenza identità additiva
4. $A+(-A)=0\quad -A=(-1)A$
5. $\alpha(A+B)=\alpha A+\alpha B$
6. $(\alpha+\beta)A=\alpha A+\beta B$

Una matrice $1\times n$ è detta **vettore riga**.
Una matrice $n\times 1$ è detta **vettore colonna**.
<u>Notazione</u> Se $u=\begin{pmatrix}u_1\\ u_2\\ …\\ u_n\end{pmatrix}$ è scritto $u^T=(u_1\quad u_2\quad …\quad u_n)$. $u^T$ è detto **vettore trasposto** di $u$.


PRODOTTO SCALARE
Siano $n\in\mathbb{N},\ u^T=(u_1\quad u_2\quad …\quad u_n)$ e $w=\begin{pmatrix}w_1\\ w_2\\ …\\ w_n\end{pmatrix}$, 
si definisce prodotto (riga per colonna) il seguente numero complesso$$\begin{align*}u^T\cdot w&=u_1w_1+u_2w_2+…+u_nw_n\\ &=(u_1\quad u_2\quad …\quad u_n)\begin{pmatrix}w_1\\ w_2\\ …\\ w_n\end{pmatrix}\end{align*}$$Proprietà $w^T\cdot u=u^T\cdot w$
Per il prodotto appena definito, NON vale la legge della cancellazione.
$(i\quad0)\Big({0\atop i}\Big)=0\qquad(i)$

Siano $A$ una matrice $m\times n$ e $B$ una matrice $n\times m$. Il prodotto (riga per colonna) di A e B è la matrice $m\times n$, e il suo coefficiente $c_{ij}$ di$$\begin{align*}c_{ij}&=\text{(i-esima di A)(j-esima di B)}\\ &=\sum_{k=1}^ra_{ik}b_{kj}\end{align*}$$
Proprietà (del prodotto matriciale)
Siano $A,B,C$ matrici per cui e $m\times n$ sono definiti e $\alpha\in\mathbb{C}$
1. $A(BC)=(AB)C\quad$(prop. associativa)
2. $0A=A0=0$
3. 	$A\begin{pmatrix}1&&&0\\ &1&&\\ &&…&\\ 0&&&1\end{pmatrix}=\begin{pmatrix}1&&&0\\ &1&&\\ &&…&\\ 0&&&1\end{pmatrix}A=A$
4. $A(B+C)=AB+AC$
5. $(A+B)C=AC+BC$
6. $\alpha(AB)=(\alpha A)B=A(\alpha B)$

**Attenzione:** Il prodotto matriciale NON gode della proprietà commutativa né della legge di cancellazione.

Osservazione: $v^Tu\quad(1\times n)\cdot(n\times1)=1$
$uv^T=\begin{pmatrix}\end{pmatrix}$

Sia $A=(a_{ij})$ una matrice $m\times n$
$A=\begin{pmatrix}0&1\\1+i&3\\2i&2-2i\end{pmatrix}$
- la trasposta di $A$ è la matrice $n\times m,\ B=(b_{ji})$ definita ponendo $b_{ji}=a_{ij}\quad\begin{align*}\forall1\leq i\leq m\\ \forall1\leq j\leq n\end{align*}$
	Si indica $A^T$.
	$A^T=\begin{pmatrix}0&1+i&2i\\1&3&2-2i\end{pmatrix}$
- la coniugata di $A$ è la matrice $m\times n,\ C=(c_{ij})$ definita ponendo $c_{ij}=\overline{a_{ij}}$
	Si indica $C=\overline{A}$.
	$\overline{A}=\begin{pmatrix}0&1\\1-i&3\\-2i&2+2i\end{pmatrix}$
- la h-trasposta di $A$ è la matrice $n\times m,\ B=(b_{ji})$ tale che $B=\overline{A}^T=\overline{(A^T)}$, ovvero ponendo $b_{ji}=\overline{a_{ij}}$.
	Si indica $A^H$.
	$A^H=\begin{pmatrix}0&1-i&-2i\\1&3&2+2i\end{pmatrix}$

In ciò che segue, date $A,B$ si supponga che $A\neq B$ o $AB$ esistano.

Proprietà (della trasposizione)
Siano $A,B$ delle matrici e $\alpha\in\mathbb{C}$
- $(\alpha A)^T=\alpha A^T$
- $(A+B)^T=A^T+B^T$
- $(A^T)^T=A$
- $(AB)^T=B^TA^T$

Proprietà (della coniugata)
Siano $A,B$ delle matrici e $\alpha\in\mathbb{C}$
- $\overline{(\alpha A)}=\overline{\alpha}\overline{A}$
- $\overline{(A+B)}=\overline{A}+\overline{B}$
- $\overline{\overline{A}}=A$
- $\overline{(AB)}=\overline{A}\overline{B}$

Proprietà (della h-trasposta)
- $(\alpha A)^H=\alpha A^H$
- $(A+B)^H=A^H+B^H$
- $(A^H)^H=A$
- $(AB)^H=B^HA^H$

L’insieme di tutte le matrici $m\times n$ (a coefficienti in $\mathbb{C}$) si indica con $M_{m,n}(\mathbb{C})\text{ o }M_{m\times n}(\mathbb{C})$.
Con $m=n$, si scriverà semplicemente $M_m(\mathbb{C})$.

Solo in $M_m(\mathbb{C})$ sono definite entrambe le operazioni $+$ e $\cdot$ introdotte ieri.

Sia $A=(a_{ij})_{1\leq i,j\leq n}$ e $M_m(\mathbb{C})$ la diagonale principale di $A$ di cui <u>n-upla ordinata</u> 

$A=(a_{ij})\subseteq M_m(\mathbb{C})$ si dice DIAGONALE se $a_{ij}=0$ se $i\neq j$.
$A=(a_{ij})\subseteq M_m(\mathbb{C})$ si dice SCALARE se $a$ 

**Osservazione:** Le matrici scalari si comportano come gli scalari.
$\begin{align*}(d\mathbb{1}_n)A=d(\mathbb{1}_nA)&=dA\quad\forall A\in M_m(\mathbb{C})\\ &=Ad=(Ad)\mathbb{1}_n=A(d\mathbb{1}_n)\end{align*}$
le matrici scalari sono le matrici che 

<u>Notazione</u> 
$M_{n\times1}(\mathbb{C})=\mathbb{C}^n$
$M_{1\times n}(\mathbb{C})=\mathbb{C}_n$

Una matrice $A$ è detta
- **simmetrica** se $A=A^T$
- **anti-simmetrica** se $A=-A^T\quad(\text{cioè se }-A=A^T)$
- **hermitiana** se $A=A^H$
- **anti-hermitiana** se $A=-A^H\quad(\text{cioè se }-A=A^H)$
(da notare che $A$ deve essere quadrata)

es.
$\displaystyle{\begin{pmatrix}1&j\\ j&1\end{pmatrix}\atop\text{simmetrica}}\quad{\begin{pmatrix}0&-i\\ i&0\end{pmatrix}\atop\text{anti-simmetrica}}{\begin{pmatrix}1&1-i\\ 1+i&1\end{pmatrix}\atop\text{hermitiana}}{\begin{pmatrix}1i&1-i\\—1-i&-i\end{pmatrix}\atop\text{anti-hermitiana}}$

#### Sistemi lineari
Un sistema lineare (a coefficienti complessi) è un insieme infinito di equazioni di primo grado nelle stesse incognite.

In generale un sistema lineare di $m$ equazioni a $n$ incognite è$$\begin{cases}a_{11}x_1+a_{12}x_2+…+a_{1n}=b_1\\ a_{21}x_1+a_{22}x_2+…+a_{2n}=b_2\\ …\\ a_{n1}x_1+a_{n2}x_2+…+a_{nn}=b_n\end{cases}\quad(*)$$Dato il sistema lineare $(*)$,
- la matrice $A=(a_{ij})\in M_{m,n}(\mathbb{C})$ è detta **matrice (incompleta) dei coefficienti**
- Il vettore colonna $b=(b_1\ b_2\ …\ b_m)^T\in\mathbb{C}^m$ è detto **vettore dei termini noti**
- il vettore colonna $x=(x_1\ x_2\ …\ x_n)^T$ è detto **vettore delle incognite**.

<u>Osservazione</u>: $\boxed{x\not\in\mathbb{C}^n}$ : $x$ è un vettore di incognite. 
Tuttavia $(*)$ riscrive come $\boxed{Ax=b}$
Infatti, da $(*)$ abbiamo che $$\boxed{b_i=\sum_{j=1}^na_{ij}x_j}\quad\text{ per ogni }1\leq i\leq m$$e in effetti l’i-esimo coefficiente del vettore colonna $Ax$ è$$(Ax)_i=\sum_{j=1}^na_{ij}x_j=b_i$$
##### Algoritmo di Gauss
(lezione 14/03)
Risolvere il sistema lineare $Ax=b$ significa determinare l’insieme$$\{c=(c_1\ …\ c_n)^T\in\mathbb{C}^n|Ac=b\}$$(differenza tra $Ax=b$ e $Ac=b$)

La strategia per risolvere $Ax=b$ è quella di “trasformare” $A$ e $b$ in modo da ottenere matrice
Dobbiamo definire le operazioni nel metodo di eliminazione di Gauss.

Non sono ammesse scale con altezza diversa da 1.

Data una matrice a gradini $u$, il primo coefficiente unitario $(\neq0)$ di ogni riga non nulla è detto PIVOT.
Ogni colonna contenente un pivot è detta colonna DOMINANTE.
Una colonna non dominante è detta LIBERA.

Occorre risolvere i seguenti punti:
1. Bisogna provare che ogni matrice $A\in M_{m,n}(\mathbb{C})$ si può trasformare in una matrice a gradini (forma ridotta)
2. Risolto 1., bisogna dimostrare che detta $u$ una forma di $A$, allora i sistemi lineari associati ad $A$ ed $u$ sono equivalenti

Per risolvere Il punto 1., introduciamo le seguenti operazioni

OPERAZIONI ELEMENTARI SULLE RIGHE
di una matrice $A\in M_{m,n}(\mathbb{C})$
- **scambio di righe**, $\boxed{E_{ij}}$ è l’operazione che scambia la riga i-esima di $A$ con la riga j-esima
- **moltiplicazione di riga per scalare non nullo**, $\boxed{E_i(\alpha)}$ con $\alpha\in\mathbb{C}\setminus\{0\}$
- **somma di riga con multiplo di un’altra riga**, $\boxed{E_{ij}(\alpha)}$ somma di riga i-esima con riga j-esima moltiplicato con $\alpha$

In $\mathbb{C}^n$ i vettori direttori sono $(1\leq i\leq n)$ tali che hanno un 1 in una posizione  $$c_i=(0\ …\ 0\ 1\ 0\ …\ 0)^T$$Definizione
Siano $A=(a_{ij})\in M_{m,n}\text{ e }b=(b_1\ …\ b_n)^T\in\mathbb{C}^m$ in matrice$$(A|b)=\left(\begin{array}{ccc|c}a_{11}&…&a_{1n}&b_1\\ \vdots&\ddots&\vdots&\vdots\\ a_{n1}&…&a_{m,n}&b_n\end{array}\right)\in M_{m,n}$$È detta matrice completa o aumentata del sistema $Ax=b$.

Il metodo di eliminazione di Gauss consiste nel portare in forma ridotta la matrice aumentata $(A|b)$. 
Detta $(u|d)$ una tale forma ridotta, allora il sistema lineare $ux=d$ si può risolvere per sostituzione “all’indietro”.

Es. 
$\left(\begin{array}{cccc|c}1&3&-2&1&-1\\0&0&1&2&1\\0&0&0&0&0\end{array}\right)$
Otteniamo 
$\begin{cases}x_1+3x_2-2x_3+x_4=-1\\ x_3+2x_4=1\end{cases}$
Le soluzioni del sistema è
$\left\{\begin{pmatrix}\alpha-8/(-4+i)\\\alpha\\ k/(-k+i)\end{pmatrix}\in\mathbb{C}^3\Big|\alpha\in\mathbb{C}\right\}$

##### Risolubilità di un sistema lineare
Vediamo quando un sistema è risolubile e in caso affermativo, studiamo le sue 
Sia $Ax=b$ un sistema lineare e $(u|d)$ una matrice ridotta di $(A|b)$.
Se $(u|d)$ ha la seguente forma$$\left(\begin{array}{ccc|c}1&&*&d_1\\0&0&1&d_2\\0&0&0&1\end{array}\right)$$cioè se $d$ è colonna dominante, allora $ux=d$ impossibile $Ax=b$ è impossibile: infatti il sistema
Pertanto se $d$ è dominante, allora $Ax=b$ è impossibile.
Supponiamo che $d$ sia libero.

<u>1o caso</u>: $(u|d)$ ha la seguente forma:$$\left(\begin{array}{ccc|c}1&&*&d_1\\0&1&&\vdots\\0&0&1&d_k\\0&0&0&0\end{array}\right)$$quindi con tutte le colonne dominanti (tranne l’ultima).
Il sistema lineare associato diventa$$\begin{cases}x_n=d_n\\ x_{n-1}+*x_n=*\\ x_{n-2}+*x_{n-1}+*x_n=*\\…\\x_1+\sum_{j=2}^nx_j=*\end{cases}$$Conclusione: se $(u|d)$ ha tutte le colonne dominanti (tranne l’ultima) allora $Ax=b$ è risolubile ed ammette una sola soluzione.

<u>2o caso</u>: $(u|d)$ ha almeno una colonna libera
allora $Ax=b$ ammette infinite soluzioni. Più precisamente se $(u|d)$ ha $k<n$ colonne libere, allora $Ax=b$ ha infinite soluzioni dipendenti da $k$ parametri.

19 aprile, 1o compitino
### Matrici invertibili
(Lezione 18/03)
Una matrice $A$ è INVERTIBILE o NON SINGOLARE se esiste una matrice $A$ tale che$$\boxed{AB=BA=I_a}\qquad I_a=\mathbb{1}_n=\begin{pmatrix}1&&&0\\&1&&\\&&\ddots&\\0&&&1\end{pmatrix}$$**NB1:** se $A\in M_n(\mathbb{C})$ è invertibile allora la matrice $B$ della definizione è unica e si indicherà con $B=A^{-1}$.

**NB2:** è possibile dimostrare che
- $(AB=I_a\text{ e }A\in M_n(\mathbb{C}))\Longrightarrow BA=I_a$
- $(BA=I_a\text{ e }A\in M_n(\mathbb{C}))\Longrightarrow AB=I_a$

**NB3:** se $A$ non è quadrata, in generale inversa destra di $A\neq$ inversa sinistra di $A$.

Es. $A=(1\quad0)$. Allora $B=(1\quad1)^T$ è inversa destra $AB=(1\quad0)\begin{pmatrix}1\\1\end{pmatrix}=1$ ma non è inversa sinistra $BA=\begin{pmatrix}1\\1\end{pmatrix}(1\quad0)=\begin{pmatrix}1&0\\1&0\end{pmatrix}\neq I_2=\begin{pmatrix}1&0\\0&1\end{pmatrix}$

Inoltre:esistenza di inversa destra di $A\centernot\Longrightarrow$
       esistenza di inversa sinistra di $A\centernot\Longrightarrow$
	   unicità dell’ inversa sinistra di $A$

**NB4:** se di $A\in M_n(\mathbb{C})$ conosco l’invertibilità (in particolare, conosco $A^{-1}$) allora tutti i sistemi lineari $Ax=b$ ammettono una ed una sola soluzione.$$\begin{align*}Ax&=b\\ A^{-1}Ax&=A^{-1}b\\x&=A^{-1}b\in\mathbb{C}^n\qquad I_nX=X\end{align*}$$**NB5:** le matrici invertibili di $M_1(\mathbb{C})$ sono i numeri complessi invertibili, cioè $\mathbb{C}\setminus\{0\}=\mathbb{C}^x$. Ma non è vero che ogni matrice $2\times2$ non nulla è invertibile.

Es. $\begin{pmatrix}1&0\\1&0\end{pmatrix}$ non è invertibile. Altrimenti deve esistere $B=\begin{pmatrix}a&b\\ c&d\end{pmatrix}$ e $M_2(\mathbb{C})$ tale che
$\begin{pmatrix}1&0\\1&0\end{pmatrix}\begin{pmatrix}a&b\\ c&d\end{pmatrix}=\begin{pmatrix}1&0\\0&1\end{pmatrix}\Longleftrightarrow\begin{cases}a=1\\ b=0\\ a=0\\ b=1\end{cases}$

(Lezione 19/03)
Data $A\in M_n(\mathbb{C})$,
$A$ è invertibile $\Longrightarrow Ax=b$ ha un’unica soluzione $\forall b\in\mathbb{C}^n$
						$\uparrow$
ha una forma ridotta di $A$ ha tutte le colonne dominanti

Le implicazioni precedenti si possono invertire.

TEOREMA
Per ogni $A\in M_n(\mathbb{C})$, le seguenti affermazioni sono equivalenti
(a) $A$ è invertibile
(b) $Ax=b$ ha un’unica soluzione, $\forall b\in\mathbb{C}^n$
(c) una (ciascuna) forma ridotta di $A$ ha tutte le colonne dominanti

Ricordiamo che fissato $n\in\mathbb{N}$, i vettori coordinati di $\mathbb{C}^n$ sono i vettori $e_1,e_2,…,e_n$ dove$$e_i=(0\quad…\quad0\quad1\quad0\quad…\quad0)^T$$
Data $A\in M_{m,n}(\mathbb{C})$, una sua ridotta di Gauss-Jordan è una ridotta di $A$ in cui le colonne dominanti sono vettori coordinati di $\mathbb{C}^n$, quindi una matrice della forma$$\begin{pmatrix}…&1&&0&&0&\\&&&1&…&0&\\&&&&&1&…\\&e_1&&e_2&&e_3\end{pmatrix}$$
Analogamente al metodo di eliminazione di Gauss,
<u>PROPOSIZIONE</u>: ogni $A\in M_{m,n}(\mathbb{C})$ ammette una forma ridotta di Gauss-Jordan, ottenibile con le operazioni elementari delle righe di $A$.

Notazione $A\begin{align*}&\xrightarrow{\text{EG\ }}u\\ &\xrightarrow{\text{EGJ}}u’\end{align*}$

 Data $A\in M_{m,n}(\mathbb{C})$, una forma ridotta di Gauss-Jordan $u$
  $n\degree$ di colonne dominanti di $u$
$=n\degree$ di gradini di $u$
$=n\degree$ di righe $\neq0$ di $u$
$=rk(A)$ rango di $A$

<u>COROLLARIO</u>: $A\in M_n(\mathbb{C})$ è invertibile solo se $rk(A)=n$.

xcasa: es 8 foglio 3
#### Calcolo della matrice invertibile
Sia $A\in M_n(\mathbb{C})$, sappiamo quando è invertibile. Ma come calcoliamo $A^{-1}$?
Possiamo sfruttare il metodo di eliminazione di Gauss(-Jordan).
1. Consideriamo la matrice $(A|I_n)\in M_{n,2n}$
2. All’interno di $(A|I_n)$ ottengo una forma ridotta di Gauss-Jordan di $A$, cioè lo porto nella forma $(u’|b)$
3. Portiamo $(u’|b)$ nella forma $(I_n|c)$ (con operazioni elementari nelle righe). A questo punto, $\boxed{c=A^{-1}}$
L’ inversa è unica.

Le matrici invertibili $A\in M_2(\mathbb{C})$ sono caratterizzate dalla condizione è $ad-bc\neq0$, e in tal caso$$A^{-1}=\frac{1}{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$$
PROPRIETÀ 
Siano $A,B\in M_n(\mathbb{C})$ matrici invertibili. Allora
1. $AB$ e $BA$ sono invertibili e 
	$(AB)^{-1}=B^{-1}A^{-1}$ e $(BA)^{-1}=A^{-1}B^{-1}$
2. $A^T$ è invertibile, e $(A^T)^{-1}=(A^{-1})^T$
3. $A^{-1}$ è invertibile, e $(A^{-1})^{-1}=A$

# Spazi vettoriali complessi e reali

Sia $k\in\{\mathbb{R,C}\}$,
> Uno spazio vettoriale su $k$
> - se $k=\mathbb{C}$ si dice spazio vettoriale (complesso)
> - se $k=\mathbb{R}$ si dice uno spazio vettoriale reale
> è un insieme NON VUOTO $V$ su cui vengono definite 2 operazioni $$\begin{align*}+:V\times V&\longrightarrow V\qquad\text{e}\qquad &\cdot:k\times V&\longrightarrow kV\\(\underline{v},\underline{w})&\longmapsto\underline{v}+\underline{w}&(\alpha,\underline{v})&\longmapsto\alpha\underline{v}\end{align*}$$che soddisfano le seguenti condizioni
> $\forall\underline{u},\underline{v},\underline{w}\in V$ (detti vettori e usano il simbolo di vettore colonna)
> $\forall\alpha,\beta\in K$ (detti scalari)
> si ha
> 1. $\underline{u}+(\underline{v}+\underline{w})=(\underline{u}+\underline{v})+\underline{w}$  ASSOCIATIVA
> 2. $\underline{u}+\underline{v}=\underline{v}+\underline{u}$  COMMUTATIVA
> 3. $\alpha(\beta\underline{v})=(\alpha\beta)\underline{v}$
> 4. $1\cdot\underline{v}=\underline{v}$ 
> 5. $(\alpha+\beta)\underline{v}=\alpha\underline{v}+\beta\underline{v}$  DISTRIBUTIVA
> 6. $\alpha(\underline{u}+\underline{v})=\alpha\underline{u}+\alpha\underline{v}$  DISTRIBUTIVA
> 7. $\forall\underline{v}\in V\ \exists\underline{w}\ |\ \underline{v}+\underline{w}=0$
	$\underline{w}$ si indica con $-\underline{v}$ e si chiama opposto di $\underline{v}$

1. Vettori
2. Funzioni
	$A,b\in\mathbb{R}\qquad[a,b]=\{x\in\mathbb{R}|a\leq x\leq b\}$
	$F([a,b])$ è insieme di tutte le funzioni $f:(a,b)\rightarrow\mathbb{R}$
	$\begin{align*}f,g\in F([a,b])\qquad f+g&:(a,b)\rightarrow\mathbb{R}\\(f\cdot)&\end{align*}$
3. Polinomi $f(x)=a_0+a_1x+…+a_xx^x$
	**NB1.** $\deg(f(x)+g(x))\leq\min(\deg f(x)+\deg g(x))$
	**NB2.** Siano $x\in$
	NB3. $\deg(\alpha f(x))\leq f(x)\quad\forall\alpha\in\mathbb{R}$

4. $\begin{align*}\mathbb{R}_n[x]=&\text{ insieme di polinomi a coefficienti reali di grado }\leq n\\&\{f(x)\leq\mathbb{C}[x]|\deg f(x)\leq n\}\end{align*}$

5. $V=\{0\}\qquad\underline{0}+\underline{0}=\underline{0}$
	$\forall\alpha\in V\qquad\alpha\underline{0}=\underline{0}$
	si chiama spazio nullo

### Sottospazi di spazi vettoriali

Sia $V$ uno spazio vettoriale e $k\in\{\mathbb{R,C}\}$,
> Un sottoinsieme $U$ di $V$ si dice un SOTTOSPAZIO VETTORIALE (o semplicemente sottospazio) se sono soddisfatte le seguenti condizioni
> 1. $\underline{0}\in U$
> 2. $\underline{u}_1+\underline{u}_2\in U\qquad\forall\underline{u}_1,\underline{u}_2\in U$
>    (si dice che $U$ è chiuso rispetto alla somma)
> 3. $\alpha\underline{u}\in U\qquad\forall\underline{u}\in U\quad\forall\alpha\in k$
>    (si dice che $U$ è chiuso rispetto al prodotto scalare)

Un sistema lineare del tipo $A\underline{x}=\underline{0}$ (cioé col vettore dei termini noti uguale a 0) si chiama SISTEMA LINEARE OMOGENEO.
**NB.** $A\underline{x}=\underline{0}$ ha sempre soluzioni!
     $A\underline{v}=\underline{0}\qquad\underline{v}=\underline{0}$
     Il vettore $\underline\ n\times2$ è una soluzione di $A\underline{x}=\underline{0}$
Sia $A\in M_{m\times n}(\mathbb{C})$, l’insieme delle soluzioni del sistema lineare omogeneo $A\underline{x}=\underline{0}$ viene indicato con il simbolo $N(A)$.$$N(A)=\{\underline{v}\in\mathbb{C}^n|A\underline{v}=\underline{0}\}\in\mathbb{C}^n$$VERIFICHIAMO CHE $N(A)$ È UN SOTTOSPAZIO DI $\mathbb{C}^n$
Dobbiamo fare 3 verifiche
1. $\underline{0}\in N(A)$
2. $\forall\underline{u},\underline{v}\in N(A)\Longrightarrow\underline{u}+\underline{v}\in N(A)$
	$\begin{rcases}\underline{u}\in N(A)\Longrightarrow A\underline{u}=\underline{0}\\\underline{v}\in N(A)\Longrightarrow A\underline{v}=\underline{0}\end{rcases}\qquad\underline{0}=A(\underline{u}+\underline{v})=A\underline{u}+A\underline{v}=\underline{0}+\underline{0}=\underline{0}$
3. $\forall\underline{u}\in N(A)\quad\forall\alpha\in\mathbb{C}\Longrightarrow\alpha\underline{v}\in N(A)$
	$\underline{0}=A(\alpha\underline{u})=\alpha (A\underline{u})=\alpha\cdot\underline{0}=\underline{0}$

**NB1.** Se $W$ è un sottospazio di $V$, allora $U$ è uno spazio vettoriale (con il )
**NB2.** $\displaystyle\Big({U\text{ soddisfa}\atop[1]+[2]+[3]}\Big)\Longleftrightarrow\Big({U\text{ soddisfa: }[1]_{BIS}: U\neq\emptyset\atop+[2]+[3]}\Big)$ 

PROPOSIZIONE
Siano $V$ uno spazio vettoriale su $k\in\{\mathbb{R,C}\}$
Si prende:
1. $U\leq W\leq V\Longrightarrow U\leq V$
2. $\{\underline{0}\}\leq V$
NB1. $\alpha\in k,\ \underline{v}\text{ e }\alpha\underline{v}=\underline{0}$
Vale la legge della cancellazione dei prodotti
NB2. $\forall\alpha\in k,\ \forall\underline{}\in V$
NB3. $\forall\alpha\in k,\ \alpha\cdot\underline{0}=\underline{0}$
#### Insieme di multipli di un vettore
Siano $V$ uno spazio vettoriale su $k\in\{\mathbb{R,C}\}$ e $\underline{v}\in V$$$\{\alpha\underline{v}|\alpha\in\mathbb{C}\}=\text{insieme dei multipli di }V$$
1. $<\underline{v}>$ è un sottospazio di $V$

Di conseguenza
segue che anche $U$ ha infiniti elementi.

Sia $V$ uno spazio vettoriale su $k\in\{\mathbb{R,C}\}$
> Una COMBINAZIONE LINEARE degli $n$ vettori $v_1,v_2,…,v_n$(lista di vettori, possibili ripetizioni) con coefficienti $\alpha_1,\alpha_2,…,\alpha_n\in k$ è il vettore $\alpha_1\underline{v}_1+\alpha_2\underline{v}_2+…+\alpha_n\underline{v}_n$

Dati $v_1,v_2,…,v_n\in V$,
l’insieme di tutte le loro combinazioni lineari è $\{\alpha_1\underline{v}_1+\alpha_2\underline{v}_2+…+\alpha_n\underline{v}_n|\alpha_1,\alpha_2,…,\alpha_n\in k\}$ e si indica con $<\underline{v}_1,\underline{v}_2,…,\underline{v}_n>$ e si chiama il SOTTOSPAZIO GENERATORE