Introduzione

$f(x)=x^2$

Per ogni $i=0,…,i=1$ prendo $\xi_i\subseteq[x_i,x_{i+1}]$ e consideri il rettangolo di base $[x_i,x_{i+1}]$ e altezza $f(\xi_i)=\xi_i^2$

$\Longrightarrow$ Approssimo la regione A con l’unione dei rettangolini
$\Longrightarrow A\approx\bigcup_{i=0}^{n=1}[x_i,x_{i+1}]\cdot f(\xi_i)$
$\Longrightarrow$ area (A)$\approx\sum$ area (rettangolo $i-$esimo)
$=\sum(x_{i+1}-x_i)\cdot f(\xi_i)$
$=\sum(\xi_i^2)(x_{i=1}-x_i)$
area = $\int_0^1x^2$

#### L’integrale di Cauchy-Riemann
Definizione: si dice <u>partizione</u> o <u>suddivisione</u> di $[a,b]$ l’insieme finito di punti $\mathcal{P}=\{x_0,x_1,x_2,…,x_{n-1},x_n\}$ tale che
$$a=x_0<x_1<x_2<…<x_{n-1}<x_n=b$$
Definizione: l’<u>ampiezza di una ripartizione</u> $\mathcal{P}$ è
$$\begin{align}|\mathcal{P}|&=\max\{x_i-x_{i-1}:i=1,…,n\}\\&(=\max\{x_j-x_{j-1}:j=0,…,n-1\})\end{align}$$
Definizione: si dice <u>partizione puntata di [a,b]</u> una coppia $(\mathcal{P},\xi)$ dove $\mathcal{P}=\{\}$ e $\xi=\{\xi_1,…,\xi_n\}$

Definizione: data una funzione limitata, $f:[a,b]\rightarrow\mathbb{R}$ la somma alla Cauchy è la somma puntata di $f$ rispetto alla partizione puntata $(\mathcal{P},\xi)$ di $[a,b]$ è il numero$$S(f,\mathcal{P},\xi)=\sum_{k=1}^nf(\xi_k)(x_k-x_{k-1})$$
Definizione (integrale definito): una funzione limitata $f:[a,b]\rightarrow\mathbb{R}$ si dice <u>integrabile alla Cauchy-Riemann in [a,b]</u> “se esiste finito il limite delle somme puntate al tendere dell’ampiezza della partizione a zero” ossia se $\exists I\in\mathbb{R}$ tale che $\forall\epsilon>0\ \ \exists\delta>0$ tale che $\forall(\mathcal{P},\xi)$ partizione puntata di $[a,b]$ con $|\mathcal{P}|<\delta$ si ha$$|S(f,\mathcal{P},\xi)-I|<\epsilon$$Tale valore finito $I$ viene detto <u>integrale definito</u> di $f$ in $[a,b]$ e si indica con$$\int_a^bf(x)dx,\int_{[a,b]}f(x)dx,\int_a^bf,\int_a^bf(t)dt$$
Osservazione:
- $f:[a,b]\rightarrow\mathbb{R}$ integrabile$$\int_a^bf(x)dx=\lim_{n\rightarrow+\infty}S(f,\mathcal{P}_n,\xi)$$
- Se $f$ è non negativa e integrabile, allora il suo integrale $\int_a^bf(x)dx$ è l’area del sotto-grafico$$SG(f)=\{(x,y)\in\mathbb{R}^2:0\leq y\leq f(x),\ x\in[a,b]\}$$
- $f(x)=c\quad\forall x\in[a,b]\quad(f$ costante)
	$\displaystyle\int_a^bf(x)dx=\int_a^bcdx=c(b-a)$
	(le $f$ costanti sono integrabili)

#### Classe di funzioni integrabili
Proposizione: data $f:[a,b]\rightarrow\mathbb{R}$ allora le seguenti condizioni sono equivalenti
1. $f$ è integrabile secondo Cauchy-Riemann in $[a,b]$
2. Per ogni $\epsilon>0,\ \exists\delta>0$ tale che $\forall$ coppia $(\mathcal{P}’,\xi’)$ e $(\mathcal{P}^”,\xi^”)$ partizione puntata di $[a,b]$ con $|\mathcal{P}’|,|\mathcal{P}^”|<\delta$ si ha$$|S(f,\mathcal{P}’,\xi’)-S(f,\mathcal{P}^”,\xi^”)|<\epsilon$$
Dimostrazione: non la facciamo
Es: formula di Dirichlet
$f(x)=\begin{cases}1&x\in[0,1]\\0&x\in[0,1]\cap\mathbb{Q}\setminus\mathbb{Q}\end{cases}\qquad S(f,\mathcal{P},\epsilon_{\mathbb{Q}})=1\quad S(f,\mathcal{P},\epsilon_{\mathbb{R}\setminus\mathbb{Q}})=1$
$\Longrightarrow f$ non è integrabile alla Cauchy-Riemann in $[0,1]$

**Teorema**: sia $f:[a,b]\rightarrow\mathbb{R}$ monotona (e limitata). Allora $f$ è integrabile.
Dimostrazione: non la facciamo
Esempio: $x\mapsto e^x$ è integrabile in $[a,b],\ \forall a,b\in\mathbb{R},\ a<b$
$\int_a^b$

Definizione: $f:[a,b]\rightarrow\mathbb{R}$ si dice <u>continua a tratti</u> se continua tranne in al più un numero finito di parti in cui la funzione emette limiti destro e sinistro.

**Teorema**: le funzioni continue a tratti sono integrabili.
(“posso sommare dei integrali sui vari tratti”)

Corollario: $\begin{aligned}f\text{ continua in }[a,b]&\Longrightarrow f\text{ continua a tratti in }[a,b]\end{aligned}$ 
Integrabile in $[a,b]$

#### Proprietà dell’integrale
Teorema: siano $f,g:[a,b]\rightarrow\mathbb{R}$ integrabili. Allora
1. \[Linearità dell’integrale\]: $\forall\alpha,\beta\in\mathbb{R},\ \alpha f+\beta f$ è integrabile e si ha $$\int_a^b[\alpha f(x)+\beta f(x)]dx=\alpha\int_a^bf(x)dx+\beta\int_a^bf(x)dx$$
2. \[Proprietà di additività rispetto all’insieme di integrazione\]: se $c\in]a,b[$, allora $f$ è integrabile in $[a,b]$ se e solo se è integrabile in $[a,c]$ e $[c,b]$ e si ha $$\int_a^bf(x)dx=\int_a^cf(x)dx+\int_c^bf(x)dx$$
3. \[Monotonia dell’integrale\]: se $f\leq g$ in $[a,b]$ allora $$\int_a^bf(x)dx\leq\int_a^bg(x)dx$$
4. Se $f$ è integrabile in $[a,b]$, allora anche $|f|$ è integrabile in $[a,b]$ e si ha $$|\int_a^bf(x)dx|\leq\int_a^b|f(x)|dx$$ In particolare$$|\int_a^bf(x)dx|\leq(\sup_{x\in[a,b]}|f(x)|)(b-a)$$Dimostrazione: non la facciamo

Teorema (della media integrale): siano $f:[a,b]\rightarrow\mathbb{R}$ integrabile e $m=\inf_{[a,b]}f,\ M=\sup_{[a,b]}f$. Allora $$m\leq\underbrace{\frac{1}{b-a}\int_a^bf(x)dx}_{\text{media integrale di f}}\leq M$$In particolare, se $f$ è continua in $[a,b]$, allora $\exists c\in[a,b]$ tale che $$\frac{1}{b-a}\int_a^bf(x)dx=f(c)$$ossia $$\int_a^bf(x)dx=f(c)$$Dimostrazione: 
$\Longrightarrow\int_a^bmdx\leq\int_a^bf(x)dx\leq\int_a^bMdx$
$\Longrightarrow m(b-a)\leq\int_a^bf(x)dx\leq M(b-a)$
$\Longrightarrow m\leq\frac{1}{b-a}\int_a^bf(x)dx\leq M$
Se $f$ è continua, $f([a,b]\leq[m,M])$. D’altra parte, ho appena dimostrato che $$\frac{1}{b-a}\int_a^bf(x)dx\in[m,M](=f([a,b]))$$$\Longrightarrow\exists c\in[a,b]$ tale che $f(c)=\frac{1}{b-a}\int_a^bf(x)dx$

Osservazione: se $f$ non è continua, potrebbe non esiste $c\in[a,b]$ tale che $f(c)=\frac{1}{b-a}\int_a^bf(x)dx$

**Teorema fondamentale del calcolo**
Definizione (primitiva): sia $A\subseteq\mathbb{R},\ f:A\rightarrow\mathbb{R}$. Una funzione $F:A\rightarrow\mathbb{R}$ si dice <u>primitiva di f</u> o <u>funzione primitiva di f</u> in $A$ se $F$ è deriva bile in $A$ e si ha $$F‘(x)=f(x)\qquad\forall x\in A$$Esempio: - se $f$ $è$ derivabile, allora $f$ è una primitiva di $f’$
- sia $f(x)=x^\alpha\quad\forall\alpha\in\mathbb{R}$. Allora
	- se $\alpha\neq-1,\ F(x)=\frac{1}{\alpha+1}x^{\alpha+1}+c$ è primitiva di $f(x)=x^\alpha$
	- se $\alpha=-1,\ f(x)=x^{-1}=\frac{1}{x}\Longrightarrow F(x)=\lim|x|+c$ è primitiva di $f(x)$ in $\mathbb{R}\setminus\{0\}$

Teorema: siano $F,G$ due primitive di $f$ su $A=I$ intervallo. Allora $\exists c\in\mathbb{R}$ tale che $$G(x)=F(x)+c\qquad\forall x\in I$$Dimostrazione: so $G’(x)=f(x)=F’(x)\quad\forall x\in I$
$\Longrightarrow (F(x)-G(x))’=F’(x)-G’(x)=0\quad\forall x\in I$
$\Longrightarrow F-G$ è costante in $I$
$\Longrightarrow\exists c\in I$

**Teorema (fondamentale del calcolo)**: sia $f:[a,b]\rightarrow\mathbb{R}$ funzione integrabile. Se $F$ è primitiva di $f$ in $[a,b]$ allora $$\int_a^bf(x)dx=F(b)-F(a)$$detta <u>funzione fondamentale del calcolo</u>.
(in altre parole, $\int_a^bf(x)dx$ è uguale all’incremento di una *qualunque* primitiva di $f$ tra a e b)

Dimostrazione: sia $F$ primitiva di $f$ in $[a,b]$. Fissiamo una partizione $\mathcal{P}=\{\underbrace{x_0}_{a},x_1,…,\underbrace{x_n}_{b}\}$ di $[a,b]$Per Teorema di Lagrange, $\forall k=1,…,n\  \exists\xi_k^x\in]x_{k-1},x_k[$ tale che $$\frac{F(x_k)-F(x_{k-1})}{x_k-x_{k-1}}=\underbrace{F’(\xi_k^*)}_{=f(\xi_k^*)}$$$\begin{aligned}\Longrightarrow F(x_k)=F(x_{k-1})&=f(\xi_k^*)(x_k-x_{k-1})\\&=\sum_{k=1}^n(F(x_k)-F_{k-1})\\&=\sum f(\xi_k^x)(x_k-x_{k-1})\end{aligned}$
cioè 
$\displaystyle F(b)-F(a)=\sum_{k=1}^nf(\xi_k^x)(x_k-x_{k-1})$
ossia 
Per la definizione di integrale, fissato $\epsilon>0\ \exists\delta>0$ tale che $\forall(\mathcal{P},\xi)$ con $|\mathcal{P}|<\xi$
Scelta una qualsiasi partizione di $[a,b]$ con $|\mathcal{P}|<\delta$ posso sempre scegliere $\xi_k^n$ con Lagrange come ho fatto prima e rispetto a tale partizione ho $$S(f,\mathcal{P},\xi)=F(b)-F(a)$$$\Longrightarrow|F(b)-F(a)-\int_a^bf(x)dx|<\epsilon$
poichè $|\mathcal{P}|<S$. Ho dimostrato che $\forall\epsilon>0$

Notazione: $F(b)-F(a)=[F(x)]_a^b=F(x)|_a^b$
Corollario: se $f:[a,b]\rightarrow\mathbb{R}$ deriva bile con derivata integrabile, allora $$\int_a^bf’(x)dx=f(b)-f(a)$$
La funzione integrale
Definizione: sia $f:[a,b]\rightarrow\mathbb{R}$ integrabile. Definisco $F:[a,b]\rightarrow\mathbb{R}$ una
$$F(x)=\int_a^bf(x)dx\qquad\forall x\in[a,b]$$
**Teorema fondamentale del calcolo ver.2**: sia $f\in C[a,b]$ si definisce $$F(x)=\int_a^bf(t)dt\qquad\forall x\in[a,b]$$allora $F$ è derivabile in $[a,b]$ e si ha $$F’(x)=f(x)\qquad\forall x\in[a,b]$$Dimostrazione: non la facciamo.
Osservazione: potrei definire 
$G(x)=\int_a^bf(t)dt$

Definizione: sia $f:A\rightarrow\mathbb{R}$, l’<u>integrale indefinito</u> di $f$ in $A$. 

Osservazione: sia$$\int f(x)dx=\{F+c:c\in\mathbb{R}\}$$dove $F$ è una primitiva di $f$ su $A=I$ intervallo.
Si indica 

Osservazione: l’integrale indefinito è lineare$$\int(f(x)+g(x))dx=\int f(x)dx+\int g(x)dx$$
#### Metodi di integrazione
##### Integrazione per parti
Siano $f,g$ funzioni derivabili in $I$, allora $$(f(x)g(x))’=f’(x)g(x)+f(x)g’(x)\qquad\forall x\in I=[a,b]$$$\displaystyle\Longrightarrow\int_a^b(f(x)g(x))’dx=\int_a^bf’(x)g(x)dx+\int_a^bf(x)g’(x)dx$
$\displaystyle\Longrightarrow\Big[f(x)g(x)\Big]_a^b=\int_a^bf’(x)g(x)dx+\int_a^bf(x)g’(x)dx$$$\Longrightarrow\boxed{\int_a^bf’(x)g(x)dx=\Big[f(x)g(x)\Big]_a^b-\int_a^bf(x)g’(x)dx}$$Vale anche per gli integrali indefiniti $$\boxed{\int f’(x)g(x)dx=f(x)g(x)-\int f(x)g’(x)dx}$$
##### Integrazione per sostituzione
$f:[a,b]\rightarrow\mathbb{R}$ continua, sia $\phi:[c,d]\rightarrow[a,b]$ di classe $\phi’$ e tale che $\phi(c)=a,\ \phi(d)=b.\ F$ primitiva di $f$ in $[a,b]$. Allora
$\begin{align}\int_c^d(F\cdot\phi)’(t)dt=\Big[F\cdot\phi(x)\Big]_c^d&=F(\phi(t))F(\phi(t))dt\\&=F(b)-F(a)=\int_a^bf(x)dx\end{align}$$\displaystyle\Longrightarrow\int_c^dF’(\phi(t))\phi’(t)dt=\int_c^df(\phi(t))\phi’(t)dt$$$\Longrightarrow\boxed{\int_a^bf(\phi(x))\phi’(t)dt=\int_a^bf(x)dx}$$La formula si può anche leggere nel senso opposto
Se $\phi$ è invertibile $\displaystyle\int_a^bf(x)dx=\int_{\phi^{-1}(a)}^{\phi^{-1}(b)}f(\phi(t))\phi’(t)dt$

La formula di integrazione per sostituzione funziona anche con integrali indefiniti. $$\boxed{\int f(\phi(x))\phi’(t)dt=\Big(\int f(x)dx\Big)_{x=\phi(t)}}$$Se $\phi$ è invertibile $\displaystyle\int f(x)dx=\Big(\int f(\phi(t))\phi’(t)dt\Big)_{t=\phi^{-1}(x)}$

##### Integrali indefiniti noti
- $\displaystyle\int x^\alpha dx=\frac{1}{\alpha+1}x^{\alpha+1}+c\qquad\alpha\neq-1$
- $\displaystyle\int\frac{1}{x}dx=\ln|x|+c$
- $\displaystyle\int a^xdx=\frac{1}{\ln a}a^x+c\qquad a>0,\ a\neq1$
- $\displaystyle\int\sin x\ dx=-\cos x+c$
- $\displaystyle\int\cos x\ dx=\sin x+c$
- $\displaystyle\int\frac{1}{\cos^2x}dx=\tan x+c$
- $\displaystyle\int\frac{1}{\sin^2x}dx=-\text{cotan} x+c$
- $\displaystyle\int\sinh x\ dx=\cosh x+c$
- $\displaystyle\int\cosh x\ dx=\sinh x+c$
- $\displaystyle\int\frac{1}{1+x^2}dx=\arctan x+c$
- $\displaystyle\int\frac{1}{\sqrt{1-x^2}}dx=\arcsin x+c$

- $\displaystyle\int F’(\phi(x))\phi’(x)dx=F(\phi(x))+c$
- $\displaystyle\int(\phi(x))^\alpha\phi’(x)dx=\frac{1}{\alpha+1}(\phi(x))^{\alpha+1}+c\qquad\alpha\neq1$
- $\displaystyle\int\frac{\phi’(x)}{\phi(x)}dx=(\int\frac{1}{t}dt)=(\ln|t|+c)=\ln|\phi(x)|+c$
Osservazione: non tutte le funzioni hanno primitive che sono esprimibili mediante funzioni elementari.
Esempio: $\int e^{-x^2}dx$ non è esprimibile mediante $f(x)$ elementari

Inversa di cosh si chiama settore cosh

##### Integrazione di funzioni razionali
$\displaystyle\int\frac{P(x)}{Q(x)}dx\qquad$ con $P,\ Q$ polinomi

Idea: scrivere $P(x)/Q(x)$ come somma di funzioni di cui conosco la primitiva.
Sappiamo già integrale
- $\displaystyle\int\frac{1}{ax+b}dx=\frac{1}{a}\ln|ax+b|+c\qquad a\neq0$
- $\displaystyle\int\frac{1}{(ax+b)^2+1}dx=\frac{1}{a}\arctan|ax+b|+c$
- $\displaystyle\int\frac{Q’(x)}{Q(x)}dx=\ln|Q(x)|+c$

Es. $\begin{align}\int\frac{1}{x^2+x+1}&=\int\frac{1}{(x^2+x+\frac{1}{2}^2)+1-\frac{1}{4}}dx=\int\frac{1}{(x+\frac{1}{2})^2+\frac{3}{4}}dx\\&=\int\frac{1}{\frac{3}{4}((\frac{2}{\sqrt{3}}x+\frac{2}{\sqrt{3}}\cdot\frac{1}{2})^2+1)}dx=\frac{4}{3}\int\frac{1}{(\frac{2}{\sqrt{3}}x+\frac{1}{\sqrt{3}})^2+1}dx\\&=\frac{4}{3}\Big(\frac{1}{\frac{2}{\sqrt{3}}}\arctan(\frac{2}{\sqrt{3}}x+\frac{1}{\sqrt{3}})+c\Big)\end{align}$
**Casi importanti di $\int P(x)/Q(x)dx$**$$\int\frac{ax+b}{x^2+cx+d}dx$$con $ax+b$ diverso da D

Caso 1: $\Delta>0$$$x^2+cx+d=(x-x_1)(x-x_2)\qquad x_1,x_2\in\mathbb{R}\quad x_1\neq x_2$$Si cercano $A,B\in\mathbb{R}$ tali che
$\displaystyle\frac{ax+b}{x^2+cx+d}=\frac{A}{x-x_1}+\frac{B}{x-x_2}$
$\begin{align}\Longrightarrow\int\frac{ax+b}{x^2+cx+d}&=A\int\frac{1}{x-x_1}+B\int\frac{1}{x-x_2}\\&=A\ln|x-x_1|+B\ln|x-x_2|+C\qquad C\in\mathbb{R}\end{align}$

Caso 2: $\Delta=0$ $$x^2+cx+1=(x-x_1)^2\qquad x_1\in\mathbb{R}$$Si cercano $A,B\in\mathbb{R}$ tale che
$\displaystyle\frac{ax+b}{x^2+x+1}=\frac{A}{x-x_1}+\frac{B}{(x-x_2)^2}$
$\begin{align}\Longrightarrow\int\frac{ax+b}{x^2+x+1}&=A\int\frac{1}{x-x_1}+B\int\frac{1}{(x-x_2)^2}\\&=A\ln|x-x_1|+B\Big(-\frac{1}{x-x_1}\Big)+C\\&=A\ln|x-x_1|-\frac{B}{x-x_1}+C\end{align}$

Caso 3: $\Delta<0$$$x^2+cx+d\qquad\text{non ha radici reali}$$$\displaystyle\frac{ax+b}{x^2+cx+d}=a\frac{x}{x^2+cx+d}+\frac{b}{x^2+cx+d}$
$\displaystyle=\frac{a}{2}\frac{2x+c}{x^2+cx+d}=\frac{a}{2}\frac{}{}+\frac{b}{}$
$\Longrightarrow\int\frac{ax+b}{x^+cx+d}=\frac{a}{2}\int\frac{2x+}{}$

##### Integrali impropri
Finora abbiamo visto $f:[a,b]\rightarrow\mathbb{R}$ finita e integrabile $$\int_a^bf(x)dx=f\sum_{i=a}^bf(x)(x-x_i)$$Ma ci sono anche
- integrali illimitati $\displaystyle\int_a^{+\infty},\ \int_{-\infty}^b,\ \int_{-\infty}^{+\infty}$
- funzioni illimitate $\displaystyle\int_0^1\frac{1}{x}dx,\ \int_0^1\frac{1}{\sqrt{x}}dx=\lim_{x\rightarrow0^+}\int_0^1\frac{1}{\sqrt{x}}dx=\lim_{x\rightarrow0^+}\Big[\ln|\sqrt{x}|\Big]$
In questi casi, è possibile approssimare l’integrale a un intervallo finito aggiungendo il suo limite
La funzione deve essere integrabile e limitata su tutti i sottointervalli chiusi e limitati.

**Integrale di 1a specie**
Dato un $f$ integrabile in senso classico in ogni intervallo chiuso e limitato, allora $f$ è integrabile in senso improprio su un intervallo $[a,+\infty]$ se e solo se il $\displaystyle\lim_{x\rightarrow+\infty}\int f(x)dx$ esiste.
L’ integrale converge se il limite è finito, diverse se è $\pm$ infinito.

**Integrale di 2a specie**
Definizione: data una $f$ infinita su un intervallo finito $[a,b]$

**Integrale di 3a specie**
Definizione: $f$ infinito ad entrambi i lati, ovvero su un intervallo $[-\infty,+\infty]$ o $f$ infinita su un intervallo $[a,+\infty]$
Deve essere scomposto In somme di integrali di prima e seconda specie.

Definizione: sia $f:I\subseteq\mathbb{R}\rightarrow\mathbb{R}$ limitata e integrale $\forall[a,b]\subseteq I$
- converge se $\exists$ finito
- diverge se $\exists\pm\infty$
- non esiste altrimenti
$f$ è <u>assolutamente integrabile</u> $\Longleftrightarrow\int_I|f(t)|dt<+\infty$

ASSOLUTA INTEGRABILITÀ

Teorema: se $f$ è assolutamente integrabile, allora $f$ è integrabile in senso improprio, esiste e converge $$\Big|\int_If(t)\Big|dt<\int_I|f(t)|dt$$Dimostrazione: non la facciamo.
Osservazione: ci sono casi di $f$ NON assolutamente integrabili ms integrabili in senso improprio.

Criteri del confronto degli integrali
Definizione: siano $f$ e $g$ integrabili nello stesso $I$, se 
$0\leq f(t)\leq g(t)$ e $\int_Ig(t)dt$ converge $\Longrightarrow\int_If(t)dt$ converge

$\int_Ig$ finito $\Longrightarrow\int_If$ finito
$\int_If=+\infty\Longrightarrow\int_Ig=+\infty$

Criterio asintotico del confronto
Definizione: siano $f,g:[a,b]\rightarrow\mathbb{R}$ limitati e integrabili $\lim_{t\rightarrow b}|\frac{f(x)}{g(x)}|=l\in[0,+\infty]$ se 
1. $0<l<+\infty\qquad\int_a^bf(t)dt$ converge$\Longleftrightarrow\int_a^bg(t)dt$ converge
2. $l=+\infty\qquad\int_a^bf(t)dt$ ass. Integrabile$\Longrightarrow\int_a^bg(t)dt$ ass. Integrabile
3. $l=0\qquad\int_a^bg(t)dt$ ass. Integrabile$\Longrightarrow\int_a^bf(t)dt$ ass. Integrabile