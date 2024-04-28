Esame: teoria(1h) ed esercizi(2h, possibile usare un libro)

INDICE
- [Numeri](#Numeri)

## Numeri
$\mathbb{N}=\{0,1,2,…\}$  Numeri naturali
$\mathbb{Z}=\mathbb{N}\cup(-\mathbb{N})=\{…,-2,-1,0,1,2\}$  Numeri interi
$\mathbb{Q}=\{\frac{p}{q}:p\in\mathbb{Z},q\in\mathbb{Z}\setminus\{0\}\}$  Numeri razionali
$\mathbb{N}\subseteq\mathbb{Z}\subseteq\mathbb{Q}$

$\not\exists\frac{p}{q}\in\mathbb{Q}(p\in\mathbb{Z},q\in\mathbb{Z}\setminus\{0\})$ tale che 
$$(\frac{p}{q})^2=2$$
In altre parole $\sqrt{2}\not\in\mathbb{Q}:\sqrt{2}$  é irrazionale

**Densità** di $\mathbb{Q}$ : $\forall a,b\in\mathbb{Q}$ con $a<b$
$\exists$ infiniti elementi $x\in\mathbb{Q}\mid a<x<b$

**Numerosità** di $\mathbb{Q}$ : i numeri razionali sono tanti quanto i numeri naturali

**Completezza** di $\mathbb{R}$ : $\forall A,B\in\mathbb{R}$ tale che
$$a\leq b\quad\forall a\in A,\forall b\in B$$
$\exists\ c\in\mathbb{R}\mid a\leq c\leq b\quad\forall a\in A,\forall b\in B$
Definizione : un intervallo è un sottoinsieme $I$ tale che $\forall\ a,b$ e $I$ se $a<r<b$ allora $r\in I$

Notazione
$a,b\in\mathbb{R},\quad a\leq b$
- $[a,b]=\{x\in\mathbb{R}\mid a\leq x\leq b\}$  intervallo chiuso
In particolare $a,b\in[a,b]$
- $]a,b[=\{x\in\mathbb{R}\mid a<x<b\}$ intervallo aperto
In particolare $a,b\not\in]a,b[$
- $]a,b]=\{x\in\mathbb{R}\mid a<x\leq b\}$
In particolare $a\not\in]a,b],\quad b\in]a,b]$

Retta reale estesa $\bar{R}=\mathbb{R}\cup\{-\infty,+\infty\}$

**Modulo**, detto anche valore assoluto o norma, di un numero $x$ è
$$|x|\begin{cases}x &x\geq 0\\ -x &x< 0\end{cases}$$
Per calcolare la “distanza” di $x$ da $x_2$ sulla retta reale si fa $|x-x_2|(=|x_2-x|)$

Osservazione : Fissato $M\geq 0$ ricordo che
$$|x|\leq M\quad\Longleftrightarrow\quad-M\leq x\leq M$$
Teorema : $\forall\ x,y\in\mathbb{R}$ valgono
$|x+y|\leq|x|+|y|$ (disuguaglianza triangolare)

Osservazione : la disuguaglianza triangolare può essere generalizzata alla somma di $n$ addendi
$$|x_1+x_2+…+x_n|\leq|x_1|+|x_2|+…+|x_n|$$
$$|\sum_{i=1}^n x|\leq\sum_{i=1}^n|x|$$
<u>MASSIMO, MINIMO, ESTREMI INFERIORI E SUPERIORI</u>
Definizione : $A\subseteq\mathbb{R}$ si dice **limitato** se $\exists\alpha,\beta\in\mathbb{R}$ t.c. $A\subseteq[\alpha,\beta]$
$\Longleftrightarrow$ $A$ è limitato superiormente e inferiormente

Proprietà : $A\subseteq\mathbb{R}$ è limitato $\Longleftrightarrow\exists M\geq0$ t.c. $-M\leq a\leq M\quad\forall a\in A$

Si dice **superiormente limitato** se $\exists\ \beta\in\mathbb{R}$ t.c. $a\leq\beta\quad\forall a\in A$
In tal caso, $\beta$ si dice **maggiorante** di $A\quad(A\subseteq]-\infty,\beta])$

Si dice **inferiormente limitato** se $\exists\ \alpha\in\mathbb{R}$ t.c. $\alpha\leq a\quad\forall a\in A$
In tal caso, $\alpha$ si dice **minorante** di $A\quad(A\subseteq[\alpha,+\infty[)$

$\emptyset\not =A\subseteq\mathbb{R}$ 
Un minorante di $A$ appartenente ad $A$ si dice **minimo** e si indica minA
$m=minA\Longleftrightarrow m\in A\ \&\ m\leq a\quad\forall a\in A$
Un maggiorante di $A$ appartenente as $A$ si dice **massimo** e si indica maxA $M=maxA\Longleftrightarrow M\in A\ \&\ M\geq a\quad\forall a\in A$
Se esistono, minA e maxA sono unici

Sia $A\subseteq\mathbb{R},A\not =\emptyset$, superiormente limitato. Si dice **estremo superiore** di $A$ e si indica con supA il minimo dell’insieme dei maggioranti di $A$.
$S=supA\Longleftrightarrow\begin{cases}S\geq a &\forall a\in A\\ \forall\epsilon>0 &\exists a\in A\mid a>S-\epsilon\end{cases}$

Sia $A\subseteq\mathbb{R},A\not =\emptyset$ inferiormente limitato. Si dice **estremo inferiore** di $A$ e si indica con infA il massimo dell’insieme dei minoranti di $A$.
$I=infA\Longleftrightarrow\begin{cases}I\leq a &\forall a\in A\\ \forall\epsilon>0 &\exists a\in A\mid a<I+\epsilon\end{cases}$

Proprietà di Archimede: siano $a,b\in\mathbb{R}$, $a,b>0$. Allora $\exists n\in\mathbb{N}\mid na>b$
Densità di $Q$ in $R$: siano 

<u>RADICI, POTENZE, ESPONENZIALI</u>
In questo corso non mettiamo numeri negativi sotto radice anche cubica.
Osservazione: $|x|=\sqrt{x^2}$
Radice non hanno due risultati. 
$\sqrt[n]{ab}=\sqrt[n]{|a|}\sqrt[n]{|b|}$

Potenze
$a^r=a^{\frac{p}{q}}=(a^p)^{\frac{1}{q}}=\sqrt[q]{a^p}\quad$ dove
$a^p=\underbrace{a+a+…+a}_{p\text{ volte}}\quad\text{se }p\geq 0$
$a^p=\underbrace{\frac{1}{a}+\frac{1}{a}+…+\frac{1}{a}}_{-p\text{ volte}}=\frac{1}{a^{-p}}\quad\text{se }p<0$

<u>Numero di Nepero</u>
$e=2,71828…$

Sarà importante $e^x,\ x\in\mathbb{R}$
- Se $\boxed{a>1}$ $$a^{x_1}<a^{x_2}\Longleftrightarrow x_1<x_2$$
Logaritmi
Tale numero $x$ si dice logaritmo in base $a$ e di $y$ e indicato con $\log_a y$
Osservazione: $a^{\log_a y}=y=\log_a a^y$

Logaritmo naturale $\log_e x=\text{lm}\ x=\log x$

### Funzione
Si dice funzione di un $x$, quando data $x$ corrisponde un solo valore $y$.
Il dominio di una funzione
L’immagine di una funzione

Una funzione si dice iniettiva quando ad ogni $y$ corrisponde un solo $x$.
$$f^{-1}:imf\rightarrow domf$$
Data una funzione $X\rightarrow Y,A\subseteq X$ si dice restrizione di $f$ ad $A$ e si indica $f_{|A}$ la funzione $f_{|A}:A\rightarrow Y$ definita da
$$f_{|A}=f(x)\quad\forall x\in A$$
Le funzioni iniettiva sono invertibili. Il grafico della funzione e la sua inversa sono simmetrici rispetto alla bisettrice del secondo e terzo quadrante.

Funzioni inverse delle restrizione di $\sin x$ e $\cos x$
$f(x)=\sin x,\ x\in\mathbb{Q}$ non è iniettiva
È possibile invertirla nella sua restrizione in $[\frac{1}{2\pi},\frac{1}{2\pi}]$ 
$\arcsin$
$\arccos$


Funzioni iperboliche
$f(x)=\sinh x=\frac{e^x-e^{-x}}{2}\quad$ <u>Seno iperbolico</u> di $x$
$g(x)=\cosh x=\frac{e^x+e^{-x}}{2}\quad$ <u>Coseno iperbolico</u> di $x$

Proprietà
$\sinh(-x)=-\sinh x\quad\Longrightarrow$ dispari
$\cosh(-x)=\cosh x\quad\Longrightarrow$ pari


#### Limiti
$X\subseteq\mathbb{R}\quad f:X\rightarrow\mathbb{R}$
Sia $f(x)=\frac{\sin x}{x}, \dim f=\mathbb{R}\setminus\{0\}$
1. $f$ con $dom f\subseteq\mathbb{R}$
2. $x_0\in\bar{\mathbb{R}}=\mathbb{R}$

Proposizione: siano $r_1,r_2\in\mathbb{R},r_1\neq r_2$
Allora $\exists U_1$, intorno di $r_1\in U_2$ intorno di $r_2$ dia
$$U1\cap U_2=\emptyset$$
dim: Supponiamo $r_1,r_2\in\mathbb{R}$ (altri con ). Prendo $r_1$ e ottengo intorni sferici $U=]r_1-\epsilon_1,r_1+\epsilon_1[, V=]r_2-\epsilon_2,r_2+\epsilon_2[$ tale che $U\cap V=\emptyset$.

Definizione: Sia $A\subseteq\mathbb{R},x_0\in\mathbb{R}$ si dice **punto di accumulazione** per A se $\forall U$ intorno di $x_0,\quad\underbrace{\exists a\in A,a\neq x_0\text{ tale che }a\in U}_{U\cap A\setminus\{x_0\}\neq\emptyset}$

Def: Se $x_0\in A$ non è punto di accumulazione per $A$ allora $x_0$ si dice punto isolato per $A$.

es: $A=\{0\}\cup]2,+\infty[$
0 è punto isolato per A, $]2,+\infty[$ è punto di accumulazione per A

$\mathbb{N}$ è fatto di tutti punti isolati, $+\infty$ è punto di accumulazione per $\mathbb{N}$

$\mathbb{Q}$ tutti gli elementi di $\bar{\mathbb{R}}$ sono punti di accumulazione per $\mathbb{Q}$

Se $A\subseteq\mathbb{R}$
- se $S=\sup A\not\subseteq A$, allora S è punto di accumulazione per A
- se $I=\inf A\not\subseteq A$, allora S è punto di accumulazione per A
- se sono $\subseteq A$ allora non si può dire

Definizione: $f:dom f$
Si dice che f ha una proprietà $(p)$ definitivamente per $x\rightarrow x_0$ se $\exists U$ intorno di $x_0$ in cui $\forall x\in U\cap dom f, x\neq x_0$ si ha che $f(x)$ ha la proprietà $(p)$.

**Definizione  di Limite**:  $f:dom\rightarrow\mathbb{R}, dom f\subseteq\mathbb{R},\ x\in\bar{\mathbb{R}}$ di accumulazione per $dom f, \lim\in\bar{\mathbb{R}}$
Si dice che $f$ ha limite $l$ per $x$ che tende a $x_0$ e si scrive 
$$\lim_{x\rightarrow x_0}f(x)=l$$
(oppure $f(x)\rightarrow l$ per $x\rightarrow x_0$)
Se $\forall V$ intorno di $l,\ \exists U$ intorno di $x_0$ tale che se $x\in U\cap dom f,x\neq x_0$ allora $f(x)\in V$. 

Osservazione: se $l\in\mathbb{R}$, si dice che $f$ ha limite di in $x_0 (l\neq+\infty\text{ e }l\neq-\infty)$
Se $l=+\infty,\ l=-\infty$, allora $f$ si dice divergente.
Se $l=0$, allora si dice che $f$ è infinitesima in $x$.

$\lim_{x\rightarrow 2}f(x)=1$
La def di limite non fa intervenire il valore della funzione nel punto $x_0$.

Osservazione:
$$x_Q:\mathbb{R}\rightarrow\mathbb{R}\begin{cases}1&\text{se }x\in\mathbb{Q}\\0&\text{se }x\end{cases}$$

$V$ intorno di $\mathcal{l}\begin{cases}]\mathcal{l}-\epsilon,l+\epsilon& l\in\mathbb{R}\\]m,+\infty[& l=+\infty\\]-\infty,-m[& l=-\infty[\end{cases}$

$\lim_{x_\epsilon}f(x)=l\quad\Longleftrightarrow\quad\forall V$ intorno di $l,\ \exists U$ intorno di $x_0$ tale che se $x\in U\cap dom f, x\neq x_0$ Allora $f(x)\in V$

**Teorema dell’unicità del limite**: Se $x_0,l_i,l_2\in\bar{\mathbb{R}}$ e $$\lim_{x\rightarrow x_0}f(x)=l\text{ e }\lim_{x\rightarrow x_0}f(x)=l_2$$
allora $l_1=l_2$

Dim: supponiamo per assurdo che $l_1\neq l_2$. 
Per la proprietà di separazione di $\mathbb{R}$
- $\exists V_1$ intorno di $l_1$
- ‘’

Pongo $U=U_1\cap U_2$ intorno di $x\Longrightarrow\exists\bar{x}\in U\setminus\{x\}$
$f(\bar{x})\in V_1\cap V_2=\emptyset$

Sia f funzione che va in condominio R 
Se il limite x che va a limite x0 
Punto di accumulazione destro e sinistro per f(x)
OSS: se limite esiste, esiste anche limite sinistro e destro

Se uno dei due limiti sinistro o destro non esiste, allora il limite non esiste.

**Limiti e valore assoluto**
Proposizione: $$\lim_{x\rightarrow x_0}f(x)=l\quad\Longleftrightarrow\quad \lim_{x\rightarrow x_0}|f(x)-l|=0$$Definizione: segue la definizione di limite.
Conseguenza: $f$ è infinitesima in $x\Longleftrightarrow|f|$ è infinitesimo in $x_0$

Proposizione: Sia $x_0,l\in\bar{\mathbb{R}}$. Se $\lim_{x\rightarrow x_0}f(x)=l$, allora$$\lim_{x\rightarrow x_0}|f(x)|=|l|$$che si intende $|\pm\infty|\geq\pm\infty$
Osservazione: Non vale il viceversa della proposizione.

**Limiti e relazioni d’ordine**
<u>Teorema della permanenza del segno</u>
Sia $f$ una funzione di variabile reale, $x_0\in\bar{\mathbb{R}}$ per $dom f$ e supponiamo$$\lim_{}f(x)=l>0\qquad\Big({l\in]0,+\infty[\atop \tilde{l}=+\infty}\Big)$$Allora $\exists U$ intorno di $x_0$ tale che se $x\in U\cap dom f, x\neq x_0$ allora $f(x)>0$.
Osservazione: vale l’analogo se $l<0$.

Corollario: Sia $f$ una funzione di variabile reale, $x_0\in\bar{\mathbb{R}}$ per $dom f$,
Se $f(x)\geq 0$ def per $x\rightarrow x_0$, allora se $\exists$ il limite over $x\rightarrow x_0$ di $f$ esiste$$\lim_{x\rightarrow x_0} f(x)\geq0$$
<u>Teorema del confronto</u>
Siano $f,g$ funzioni di variabili reali, $x_0\in\bar{\mathbb{R}}$ per $dom f\cap dom g$, tale che$$f(x)\leq g(x)\quad\text{definito per }x\rightarrow x_0$$Se $$l_f=\lim_{x\rightarrow x_0} f(x)\quad l_g=\lim_{x\rightarrow x_0} g(x)$$ allora $$l_f\leq l_g$$
Osservazione: se $f(x)\leq g(x)$ definita per $x\rightarrow x_0$ e $\exists$ i limiti $l_f$ e $l_g$ $\nrightarrow l_g<l_g$

<u>Teorema dei due carabinieri</u>: Sia $x\subseteq\mathbb{R},\ f,g,l:X\rightarrow\mathbb{R},\ x_0\in\bar{\mathbb{R}}$ di accumulazione per $X$. Se $$f(x)\leq h(x)\leq g(x)$$e$$\lim_{x\rightarrow x_0}f(x)=\lim_{x\rightarrow x_0}g(x)=l$$ allora$$\lim_{x\rightarrow x_0} h(x)=l$$
Si dimostra che $\boxed{\lim_{x\rightarrow 0}\frac{\sin x}{x}=1}$

Corollario: Sia $x\subseteq\mathbb{R},\ f,g:X\rightarrow\mathbb{R}, x_0\in\bar{\mathbb{R}}$ di accumulazione per $X$. Se $$f(x)\leq g(x)$$ e $$\lim_{x\rightarrow x_0}f(x)=+\infty$$ allora $$\lim_{x\rightarrow x_0} g(x)=+\infty$$
$\boxed{\lim_{x\rightarrow 0}\frac{1-\cos x}{x^2}=\frac{1}{2}}$
$\boxed{\lim_{x\rightarrow x_0}\sin x=\sin x_0}$

**Limiti di funzioni monotone**
Teorema: Sia $f$ una funzione di variabile reale, $x_0\in\bar{\mathbb{R}}$ punto di accumulazione sinistro per $dom f,\ f$ monotona in $]-x,x_0[\ \cap dom f$ $$\lim f(x)=\sup f(x)\quad\text{se $f$ è crescente}\atop\lim f(x)=\inf f(x)\quad\text{se $f$ è decrescente}$$Sia $f$ una funzione di variabile reale, $x_0\in\bar{\mathbb{R}}$ punto di accumulazione sinistro per $dom f,\ f$ monotona in $]x_0,+x[\ \cap dom f$ $$\lim f(x)=\inf f(x)\quad\text{se $f$ è crescente}\atop\lim f(x)=\sup f(x)\quad\text{se $f$ è decrescente}$$
$\boxed{\lim_{x\rightarrow\pm\infty}(1+\frac{1}{x})^x=e}$

#### Metodo di calcolo di limiti
Sia $x\in\mathbb{R},\ x\neq 0$
$$\lim_{x\rightarrow0}\frac{\sin(\alpha x)}{x}=\lim_{x\rightarrow0}\frac{\sin(\alpha x)}{\alpha x}\cdot\alpha=\lim_{x\rightarrow0}\frac{\sin y}{y}\cdot\alpha=\alpha\cdot1=\alpha$$

<u>Teorema della funzione composta o del cambio di variabile</u>
Siano $f,g$ una funzione di variabile reale tale che $g=f,\ x_0\in\bar{\mathbb{R}}$ punto di accumulazione. Supponiamo

1) $\lim_{y\rightarrow y_0} g(y)=l$
2) $\lim_{x\rightarrow x_0}f(x)=y_0$
3) $f(x)\neq y_0$

Teorema (operazione sui limiti): $X\subseteq\mathbb{R},\ f,g:X\rightarrow\mathbb{R},\ x_0$ punto di accumulazione per $X,\ x_0\in\bar{\mathbb{R}}$. Supponiamo
$$\lim_{x\rightarrow x_0}f(x)=l_f\quad,\quad\lim_{x\rightarrow x_0}g(x)=l_g\quad,\quad l_f,l_g\in\mathbb{R}$$
Allora
1) $\in\mathbb{R},\ \lim(cf(x))=c\cdot l_f$
2) $\lim(f(x)+g(x))=l_f+l_g$
3) $\lim(f(x)\cdot g(x))=l_f\cdot l_g$
4) $\lim\frac{f(x)}{g(x)}=\frac{l_f}{l_g}\qquad\text{se }l_g\neq0$
5) $\lim\frac{1}{g(x)}=\frac{1}{l_g}\qquad\text{se }l_g\neq0$

Osservazione: calcoliamo $\lim f(x)^{g(x)}=(l_f)^{l_g}$
$\lim e^{\ln(f(x)^{g(x)})}=\lim e^{g(x)\ln f(x)}$

Proposizione: Sia $X\subseteq\mathbb{R},\ f,g:X\rightarrow\mathbb{R},\ x_0\in\bar{\mathbb{R}}$ di accumulazione per $X,\ f$ infinitesima in $x_0 (\lim_{x\rightarrow x_0}f(x)=0)$ e $g$ limitata. Definisco per $x\rightarrow x_0$ $$\lim_{x\rightarrow x_0} f(x)g(x)=0$$(”prodotto di $f$ infinitesima per $g$ limitata è infinitesimo”)

Es: Sia $P(x)=$polinomio e sia $x$

#### Forme indeterminate
$f,g:X\rightarrow\mathbb{R},\ x_0$ punto di accumulazione per $X$ $$\lim_{x\rightarrow x_0} f(x)g(x)$$ Non posso dire nulla sul limite se so solo che $$\lim f(x)=0\quad\text{e}\quad\lim g(x)=\pm\infty$$$\Longrightarrow\text{Forma Indeterminata}\quad0\cdot\infty$

| Limite                                     | F. indeterminata                             |
| ------------------------------------------ | -------------------------------------------- |
| $\lim_{x\rightarrow x_0} f(x)g(x)$         | $0\cdot\pm\infty$                            |
| $\lim_{x\rightarrow x_0}\frac{f(x)}{g(x)}$ | $\frac{0}{0}$; $\frac{\infty}{\infty}$ |
| $\lim f(x)^{g(x)}=\lim e^{g(x)hf(x)}$      | $0^0$; $+\infty^0$; $1^\infty$             | 
- $f(x)=\frac{1}{x},\ g(x)=x$
- $\lim\frac{f(x)}{g(x)}$

###### Limiti di polinomi
$$P(x)=a_0+a_1x+…+a_nx^n,\quad a\geq1,\quad a_n\neq0$$
degree $P=n$$$\lim_{x\rightarrow+\infty} P(x)=\lim x^n(a_n+\frac{a_{a_n-1}}{x}+…+\frac{a_1}{x^{n-1}}+\frac{a_0}{x^n})$$$=\begin{cases}-\infty&a_n<0\\+\infty&a_n>0\end{cases}$
$=\begin{cases}-\infty&\text{se }a_n<0\text{ e n è pari}&\text{se }a_n>0\text{ e n è dispari}\\+\infty&\text{se }a_n>0\text{ e n è dispari}&\text{se }a_n>0\text{ e n è pari}\end{cases}$

In entrambi i casi $$\lim_{x\rightarrow+\infty} P(x)=\lim a_nx^n,\quad\lim P(x)=\lim a_nx^n$$Vogliamo calcolare $$\lim\frac{P(x)}{Q(x)}=\frac{\infty}{\infty}$$$\begin{aligned}\text{Con }&P(x)=a_0+a_1x+…+a_gx^g\\&Q(x)=b_0+b_1x+…+b_gx^g\end{aligned}$
$$\lim\frac{x^n(a_n+\frac{a_{n-1}}{x}+…+\frac{a_0}{x^n})}{x^n(b_n+\frac{b_{g-1}}{x}+…+\frac{b_0}{x^g})}$$
Basta ricordarsi i fattori di grado massimo

Osservazione: $f(x)\rightarrow0$ per $x\rightarrow x_0$ e $f(x)>0$ definita per $x\rightarrow0$
$(f(x)\rightarrow0^+$per $x\rightarrow x_0)$
##### O piccolo
(vedi lezione 23/10, 26/10)

##### Confronto di infiniti
Vorrei un modo per poter calcolare $$\lim_{x\rightarrow+\infty}\frac{x^5+e^x+x\sin x}{3e^x+x^{15}\ln x}\qquad\frac{\infty}{\infty}$$capendo chi è più “importante”.
Lo so fare se $P,Q$ sono polinomi
- $\deg P<\deg Q\Longrightarrow P(x)=o(Q(x))\qquad\text{per }x\rightarrow+\infty$
- $\deg P=\deg Q\Longrightarrow$”P,Q sono infiniti dello stesso ordine”

**Confrontiamo esponenziali, logaritmi e potenze**
- $\lim\frac{a^x}{x^n}=+\infty\qquad a>1,\forall\alpha\in\mathbb{R}$
In particolare
$\lim\frac{e^x}{x^n}=+\infty\qquad\forall n\geq1$
- $\lim\frac{x^a}{(\ln x)^\beta}=+\infty$
In particolare

Notazione: $\lim\frac{f(x)}{g(x)}=+\infty$ scrivo 
Quindi$$e^x>>x^n>>\ln x\quad\text{per }x\rightarrow+\infty$$
- $\lim_{x\rightarrow-\infty}|x|^\alpha e^x\qquad\forall a>1,\forall\alpha\in\mathbb{R}$
In particolare $\lim x^ne^x=0\qquad\forall n\in\mathbb{Z}$
- $\lim_{0^+} x^\alpha|\log_a x|^\beta=0\qquad\forall\alpha>0,\beta\in\mathbb{R},a>0,a\neq1$
In particolare $\lim_{0^+} x^n\log x=0\qquad n\geq1$
- $\lim|x|^\alpha a^{1/|e|}=+\infty\qquad\forall a>1$
- $\lim|e|^\alpha a^{-1/|e|}=0\qquad\forall a>1,\forall\alpha\in\mathbb{R}$

<u>Nomenclatura</u>:
$f,g:X\rightarrow\mathbb{R},\ x_0\in\bar{\mathbb{R}}$ punto di accumulazione per $X$
- Se $\lim_{x\rightarrow x_0}|f(x)|=+\infty,\ \lim_{}|g(x)|=+\infty$
$$\lim_{x\rightarrow x_0}\Big|\frac{f(x)}{g(x)}\Big|=\begin{cases}+\infty&\text{si dice che f è un infinito di ordine maggiore}\\ l\in\mathbb{R}\setminus{0}&\text{si dice che f e g sono infiniti dello stesso ordine}\\0&\text{si dice che f è un infinito di ordine inferiore}\\\not\exists&\text{si dice che f e g non sono confrontabili}\end{cases}$$
- Se $\lim|f(x)|=0,\ \lim|g(x)|=0$
$$\lim_{x\rightarrow x_0}\Big|\frac{f(x)}{g(x)}\Big|=\begin{cases}0&\text{si dice che f è un infinito di ordine maggiore}\\ l\in\mathbb{R}\setminus{0}&\text{si dice che f e g sono infiniti dello stesso ordine}\\+\infty&\text{si dice che f è un infinito di ordine inferiore}\\\not\exists&\text{si dice che f e g non sono confrontabili}\end{cases}$$
- $\begin{aligned}\text{Se }&P=a_0+a_1x+…+a_nx^n, \deg P=n\ \\&Q=b_0+b_1x+…+b_gx^g, \deg Q=g,b_g\neq0\end{aligned}$
$$\lim_{x\rightarrow x_0}\Big|\frac{f(x)}{g(x)}\Big|=\begin{cases}+\infty&\deg f>\deg g\\|\frac{f(x)}{g(x)}|\\0&\deg f<\deg g\end{cases}$$

 $x_0\in\mathbb{R},\ \alpha>0$
	1. diciamo che f ha ordine di infinito $\alpha$ per $x\rightarrow x_0$ se $f(x)$ e $\frac{1}{|x-x_0|^\alpha}$ sono infiniti dello stesso ordine
	2. diciamo che f ha ordine di infinitesimo $\alpha$ per $x\rightarrow x_0$ se $f(x)$ e $|x-x_0|^\alpha$ sono infinitesimi dello stesso ordine

 $x_0=\pm\infty,\ \alpha>0$
	1. diciamo che f ha ordine di infinito $\alpha$ per $x\rightarrow\pm\infty$ se $f(x)$ e $|x|^\alpha$ sono infiniti dello stesso ordine
	2. diciamo che f ha ordine di infinitesimo $\alpha$ per $x\rightarrow x_0$ se $f(x)$ e $\frac{1}{|x|^\alpha}$ sono infinitesimi dello stesso ordine

##### Successioni
Una successione è una funzione il cui dominio è $\mathbb{N}$ o un sottoinsieme infinito

Più in generale scriviamo $ $
Una successione è una funzione $\mathbb{N}\rightarrow\mathbb{R}$
Scriveremo anche $\{a_n\}_{n\in\mathbb{N}},\ (a_n)_{n\in\mathbb{N}}$
$$a_1,a_2,…$$
Definizione: si dice che $\lim_{x\rightarrow+\infty} a_n=l$ (oppure $\lim$) $\forall$ V intorno di $l,\ \exists N>0$ tale che $a_n\in V\ \forall n>N$

Definizione: $\{a_n\}_{n\in\mathbb{N}}$ una successione
1. $\{a_n\}$ è convergente se $\lim_{} a_n\in\mathbb{R}$
2. $\{a_n\}$ è divergente se $\lim_{n\rightarrow+\infty} a_n=+\infty$ o $\lim_{n\rightarrow+\infty} a_n=-\infty$
3. $\{a_n\}$ è regolare o determinata se $\exists\lim_{n\rightarrow+\infty}a_n$
4. $\{a_n\}$ è irregolare o indeterminata se $\not\exists\lim_{n\rightarrow+\infty}a_n$

Teorema della permanenza del segno: se $\lim_{n\rightarrow+\infty} a_n=l>0$ allora $a_n>0$ definitivamente per $n\rightarrow+\infty$

Teorema del confronto: $\{a_n\},\{b_n\}$ siano die successioni tali che $a_n\leq b_n$ definiti per $n\rightarrow+\infty$

Teorema dei due carabinieri: …

Limiti notevoli
-  $\lim_{n\rightarrow+\infty}\frac{n^k}{n!}=0$
- $\lim_{n\rightarrow+\infty}\frac{a^n}{n!}=0$
- $\lim_{n\rightarrow+\infty}\frac{n^k}{n^n}=0$

Ordine degli infiniti$$n^n>>n!>>a^n>>n^k>>\log_bn$$Successioni monotone
Definizione: $\{a_n\}_{n\in\mathbb{N}}$ successione reale, si dice
- crescente
- decrescente
- strettamente crescente
- strettamente decrescente

Teorema: se $\{a_n\}_{n\in\mathbb{N}}$ è monotona crescente, allora$$\lim_{n\rightarrow+\infty} a_n=\sup_{n\in\mathbb{N}}a_n\in\bar{\mathbb{R}}$$
             : se $\{a_n\}_{n\in\mathbb{N}}$ è monotona decrescente, allora$$\lim_{n\rightarrow+\infty} a_n=\inf_{n\in\mathbb{N}}a_n\in\bar{\mathbb{R}}$$
Progressione geometrica di ragione $\begin{aligned}q\in\mathbb{R}:\ &\{q^n\}_{n\geq1}\\&a_n=q^n,\ \forall n\geq1\end{aligned}$
- Se $q=1$, allora $q^n=1^n=1,\ \forall n\geq1$ quindi
- Se $0\leq q<1$, allofa $q^n$ è decrescente
	$\lim_{n\rightarrow+\infty} q^n=0$
- Se $-1<q<0$, allora non è monotona
	$q^n=\begin{cases}|q|^n&\text{n è pari}\\(-1)^n|q|^n&\text{n è dispari}\end{cases}\qquad\lim q^n=0$
- Se $q\leq-1,\ q^n$ è indeterminata
	$\not\exists\lim_{n\rightarrow+\infty}q^n$

Corollario: se $\{a_n\}$ è limitata e monotona, allora è convergente ($\exists l\in\mathbb{R}$ tale che $\lim_{n\rightarrow+\infty}a_n=l$)

###### Successione di Cauchy
Voglio trovare un criterio “intrinseco” per la convergenza.

Definizione: una successione reale $\{a_n\}$ si dice di Cauchy (o successione fondamentale) se $\forall\epsilon>0,\ \exists N>0$ tale che $$n,p>N\Longrightarrow|a_n-a_p|<\epsilon$$Successione che si “concentra”

Teorema: una successione reale $\{a_n\}_{n\in\mathbb{N}}$ è convergente se e solo se è di Cauchy. $\Longleftrightarrow$ “completezza di $\mathbb{R}$”

<u>Sottosuccessioni</u>
Voglio estrarre da $\{a_n\}$ un’altra successione prendendo solamente valori specifici di $n$

Definizione: data una successione $\{a_n\}_{n\in\mathbb{N}}$ si dice sottosuccessione di $\{a_n\}$ una successione $\{a_{n_k}\}_{k\in\mathbb{N}}$ con $\{n_k\}_{k\in\mathbb{N}}$ una successione strettamente crescente di numeri naturali, cioè $n_{k+1}>n_k\quad\forall k\in\mathbb{N}$

Proposizione: Sia $\{a_n\}_{n\in\mathbb{N}}$ una successione reale. Allora$$\lim a_n=l\quad\Longleftrightarrow\quad{\forall\text{ sottosuccessione }\{a_{n_k}\}_{k\in\mathbb{N}}\text{ di }\atop\{a_n\}_{n\in\mathbb{N}}\text{ si ha }\lim a_{n_k}=l}$$
Conseguenza: Per mostrare che una successione non ha limite, basta dimostrare, per esempio, che due sottosuccessioni hanno limiti diversi o che una sottosuccessione non ha limite.

**Teorema di Bolzano-Weiesstrass**: Sia $\{a_n\}$ una successione limitata allora $\exists$ una sottosuccessione di $\{a_n\}$ convergente.

Limiti di successioni e limiti di funzioni 
Teorema: Sia $f$ funzione reale di variabile, $x_0\in\bar{\mathbb{R}}$ di accumulazione per $dom f$, allora$$\lim_{x\rightarrow x_0} f(x)=l\quad\Longleftrightarrow\begin{cases}\forall\text{ succ. }\{a_n\}\text{ a valori è }dom f\setminus\{x_0\}\\\text{convergente a }x_0\text{ si ha}\\\lim_{n\rightarrow+a}f(a_n)=l\end{cases}$$Osservazione: può essere usata per dimostrare che $f$ non ha limite.
#### Funzioni continue
Abbiamo visto che $$\begin{aligned}&\lim_{z\rightarrow x_0}\sin x=\sin x_0\qquad\forall x_0\in\mathbb{R}\\ &\not\exists\lim_{x\rightarrow0}sgnx\end{aligned}$$Definizione: $f$ funzione reale di variabile reale, $x_0\in domf$. $f$ si dice <u>continua in x0</u> se è verificata una delle seguenti:
1. $x_0$ è punto isolato del dominio
2. se $x_0$ non è punto isolato del $domf$ (ossia $x_0$ è punto di accumulazione per $domf$), allora $$\lim_{x\rightarrow x_0} f(x)=f(x_0)$$
Osservazione: si parla di continuità solo nei punti del $domf$.

Definizione: se $x_0\in domf$ è punto di accumulazione per $domf$, ho che $f$ è continua in $x_0\Longleftrightarrow\forall\epsilon>0\exists\delta>0$ tale che se $|x-x_0|<\delta$ e $x\in domf$, allora $|f(x)-f(x_0)|<\epsilon$
Osservazione: se $x_0$ è punto isolato, posso prendere la definizione con $\epsilon$ e $\delta$ “perché per $\delta$ abbastanza piccolo c’è solo $x_0$”

Notazione: dato $X\subseteq\mathbb{R}$ 

Proposizione: se $f$ è continua su $x_0$ allora $|f|$ è continua su $x_0$.
Sia $f$ reale di variabile reale, continua su $x_0$ tale che $f(x_0)>0$. Allora $\exists U$ di $x_0$ tale che
$$f(x)>0\qquad\forall x\in U\cap domf$$
Continuità di funzioni composte
Teorema: Siano $f$ e $g$ funzioni reali di variabile reale 
$$g\cdot f:x\mapsto g(f(x))$$
Proposizione: comporre funzione continua con funzione non continua

Proposizione (): siano $f$ e $g$ funzioni reali di variabile reale, tale che $g(f)$ sia definita
a.
b.

###### Analisi dei punti di discontinuità
I. $$\lim_{x\rightarrow0+} f(x)\neq\lim_{x\rightarrow0-} f(x)$$discontinuità di salto.

II. Sia $f$ funzione reale di variabile reale, $x_0\in domf$ tale che 
1. almeno
2. almeno uno dei due limiti sinistro o destro di $x_0$ non esista
Allora si dice che $x_0$ è punto di discontinuità.

III. Sia $I\subset\mathbb{R}$ intervallo, $f:I\rightarrow\mathbb{R},x_0\in I,l\in\mathbb{R}$ tale che $$\lim_{x\rightarrow x_0} f(x)=l\neq f(x_0)$$ è chiamata discontinuità eliminabile.

Prolungamento per continuità

Supponiamo $I\in\mathbb{R}$. Per definizione di $\inf$$$I=\inf f(x)\Longleftrightarrow\begin{cases}I\leq f(x)&\forall x\in[a,b]\\\forall\epsilon>0\exists x\in[a,b]\end{cases}$$Se $\epsilon=\frac{1}{n},\ n\in\mathbb{N}\setminus\{0\},\ \exists x_n\in[a,b]$ tale che $$$$
Per il teorema di Bolzano-Weiesstrass, poiché $\{x_n\}_{n\geq1}$ è successione limitata (è contenuta in $[a,b]$) è possibile estrarre una s.s.

Per continuità di $f$$$\lim_{x\rightarrow+\infty} f(x_{n_k})=f(x_0)$$D’altra parte $\{f(x_{n_k})\}$ è s.s. di $\{f(x_0)\}$ e $f(x_n)$ convergente a $I$, ossia $\lim f(x_n)=I$. Quindi anche $$\lim_{x\rightarrow+\infty}f(x_{n_k})=I$$Di conseguenza$$f(x_0)=I$$$I$ è minimo perché assente in $x_0$
$\Longrightarrow I\in\mathbb{R},\ x_0$ è punto di minimo.

**Teorema dei zeri (Bolzano)**: sia $f:[a,b]\mapsto\mathbb{R}$ continua in $[a,b]$ chiuso e limitato. Se $f(a)\cdot f(b)<0$ (cioè $f$ assume valori di segno opposto agli estremi $[a,b]$), allora $\exists\xi\in]a,b[$ tale che $f(\xi)=0$.

Dimostrazione: suppongo che $f(a)<0$ e $f(a)>0$
O trovo $\xi$ in un numero finito di passaggi tale che $\xi\in]a,b[$ e $f(\xi)=0$
O costruisco due successioni $\{a_n\}_{n\geq1}$ e $\{b_n\}_{n\geq1}$
1. $a_n\leq b_n\quad\forall n\geq1$
2. $a_n$ è crescente e $b_n$ è decrescente
3. $b_n-a_n=\frac{b-a}{2^n}\quad\forall n\geq1$
4. $f(a_n)\leq0$ e $f(b_n)\geq0\quad\forall n\geq1$
Se trovo due successioni che soddisfano 1. - 4. Ho dimostrato il teorema, perché: …

Teorema dei valori intermedi: siano $I\subseteq\mathbb{R}$ intervallo, $f:I\mapsto\mathbb{R}$ continua. Allora $f(I)$ è un intervallo, cioè $\forall x_1,x_2\in I$ e $y\in\mathbb{R}$ tale che $$f(x_1)<y<f(x_2)$$allora $\exists\xi\in I$ tale che $f(\xi)=y$.
Dimostrazione: Sia $x_1,x_2\in I,\ f(x_1)<f(x_2)$ e $x_1<x_2$ (per semplicità). Sia $y\in\mathbb{R}$ tale che$$f(x_1)<y<f(x_2)$$Voglio mostrare che $\exists\xi\in I$ tale che $f(\xi)=y$. Uso il teorema di Bolzano dove pongo $y$ al posto di 0.

Osservazione: è importante che $I$ sia intervallo.
Corollario: sia $f:[a,b]\rightarrow\mathbb{R}$ continua in $[a,b]$. Sia $$m=\min_{x\in[a,b]} f(x), M=\max_{x\in[a,b]} f(x)$$Allora $f([a,b])=[m,M]$

Continuità della funzione inversa
Teorema: siano $I\subseteq\mathbb{R}$ intervallo, $f:I\rightarrow\mathbb{R}$ continua e invertibile. Allora
1. $f$ è strettamente monotona
2. $f$ inversa $f^{-1}:f(I)\rightarrow I$ è continua
Osservazione: è importante per 1. che $I$ sia intervallo.