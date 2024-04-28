**Statistica computazionale**: *Valutare procedure inferenziali (stima puntuale, stima intervallare e verifica di ipotesi)*

Indice
1. Generazione numeri (pseudo-)casuali
	1.  Algoritmo Wichmann-Hill
	2. Metodo di inversione
	3. Algoritmo accetta/rifiuto
2. Applicazioni delle simulazioni
	1.  [[Statistica computazionale#Calcolo integrale|Calcolo integrale]]
	2. [[Statistica computazionale#Teorema del Limite Centrale|TLC (Teorema Limite Centrale)]]
	3. [[Statistica computazionale#I test multipli|I test multipli]]
	4. [[Statistica computazionale#Aumentare l’efficienza|Aumentare l’efficienza]]

Principio del campionamento ripetuto
$F_\theta (y_1,...,y_n)$

Stima puntuale $\hat{\theta}$
- Valutazione $E(\hat{\theta})\quad V(\hat{\theta})$
- Distorsione $E(\hat{\theta})-\theta \quad V(\hat{\theta})$

Stima intervallare $(\hat{\theta}_1,\hat{\theta}_2)$
intervallo di confidenza
$P((\hat{\theta}_1,\hat{\theta}_2)\in\theta)=1-\alpha$ grado di fiducia, livello di confidenza

$\begin{array}{cc}&(y_1,...,y_n)_1,&(y_1,...,y_2)_2 \\ &\hat{\theta}_1,&\hat{\theta}_2 \\ &(\hat{\theta}_L,\hat{\theta}_U)_1,&(\hat{\theta}_L,\hat{\theta}_U)_2 \\ &t_1,&t_2\end{array}$

Verifica di ipotesi $H_0:\theta=\theta_0\quad H_1$
$t\rightarrow$ decisione accettare $H_0$

Valutazione probabilità errore I tipo (riferimento $H_0$ è vera)$=\alpha$

Presupponiamo $F_\theta$ nota

Simuliamo (procedura Monte Carlo) M stime puntuali

$\begin{array}{cccc}&(y_1,...,y_n)_1,&(y_1,...,y_2)_2,&…,&(y_1,...,y_2)_M \\ &\theta_1,&\theta_2,&…,&\theta_M\end{array}$
$$ \frac{\sum_{i=1}^M(\hat{\theta_i})}{M}\approx E(\hat{\theta}) \\ V(\hat{\theta}_1,…,\hat{\theta}_n) \approx V(\hat{\theta}) $$
$\begin{array}{ccc}&(\hat{\theta}_L,\hat{\theta}_U)_1,&…,&(\hat{\theta}_L,\hat{\theta}_U)_M \\ &t_1,&…,&t_M\end{array}$  Verifica di ipotesi

## Generazione numeri (pseudo)-casuali uniformi
> 💡 **Obiettivo**: generale una sequenza di number (pseudo)-casuali indipendenti con distribuzione $f(\cdot)$.

I calcolatori non riescono a generare valori totalmente casuali (sono perfettamente prevedibili). Possiamo simulare la casualità.

Simulare numeri casuali uniformemente distribuiti in $[0,1]$:

**Algoritmo congruenziale**
$x_{i+1}=(ax_i+b)\mod m$

`mod = %% (resto)`

$x_0$ seed del generatore

1.  Se $x_i=x_0$ la sequenza si ripete
2.  La sequenza è quindi periodica, il periodo è massimale (m)
3.  L’algoritmo sarà efficace se dobbiamo generare un numero di osservazioni minori del periodo

**Algoritmo di Wichmann-Hill del 1984**

Combina 3 generatori congruenziali.

$\begin{aligned}x_1&=(171\cdot x_{i-1})\mod 30269 \\ y_1&=(172\cdot y_{i-1})\mod 30307 \\ z_i&=(170\cdot z_{i-1})\mod 30323\end{aligned}$

$u_i=(\frac{x_i}{m_x}+\frac{y_i}{m_y}+\frac{z_i}{m_y})\mod 1$

Se c’è uniformità, tra tutti i intervalli equi-probabili, il punti medi si trovano tra loro a distanza $\frac{1-0.5}{n}$.

$0 \frac{1}{n} \frac{2}{n} \frac{n-1}{n} 1$

$\frac{1-0.5}{n}$

u_i,…,u_{i-1} i=2,…,n n-1 coppie

Q_{ij}\quad i,j=1,…,5

$\begin{aligned}P((u_i,u_{i-1})\in Q_{ij})&=P((u_i\in I_i)\cap(u_{i-1}\in I_j))= \\ \text{indip}\rightarrow &=P(u_i\in I_i)\cdot P(u_{i-1}\in I_j)=\text{unif}\ \frac{1}{q}\cdot\frac{1}{q}=\frac{1}{q^2}\end{aligned}$

Pre-allocazione è molto più efficiente.

### Metodo di inversione
Sia $F(\cdot)$ una FdR invertibile

-   $U\sim \text{Unif}(0,1)$
-   $F^{-1}:[0,1]\rightarrow\mathbb{R}$

Allora la v.a. $Y=F^{-1}(U)$ ha FdR $F(\cdot)$

### Distribuzione di Laplace

Funzione di densità: ****$f(y;a,b)=\frac{1}{2b}\exp(-\frac{|y-a|}{b})$

Y ha una distribuzione Laplace a,b qualsiasi.

$Y\sim f(\cdot\ ;a,b)\Longrightarrow\frac{Y-a}{b}\sim f(\cdot\ ;0,1)$

Funzione di ripartizione: ****$F(y;a,b)=\frac{1}{2}\left\{1+\text{sign}(y-a)[1-\exp(-\frac{|y-a|}{b})]\right\}$

Funzione quantile: ****$F^{-1}(p;a,b)=a-b\cdot\text{sign}(p-\frac{1}{2})\log(1-2|p-\frac{1}{2}|)$

**Distribuzione discreta**

$P(X=x_i)=\pi_i,\quad i=1,…,q$

Per generale la distribuzione

Corrisponde al il metodo dell’ inversione $F^{\leftarrow}=\inf_x\{x:F(x)\geq u\}$

Prendiamo la x più piccola per la quale la FdR è maggiore di u.

**Distribuzione Poisson (discreto non finito)**

$X\sim\text{Poisson}(\lambda)$

### Algoritmo accetto/rifiuto
$f(\cdot)$ nota, densità obiettivo

$g(\cdot)$ nota da cui riesco a generale, densità delle proposte

1.  Trovo una $k$ tale che $k\cdot g(x)\geq f(x)\quad\forall\ x$
2.  Genero $x$ da $g$
3.  Genero $u$ da $U(0,k\cdot g(x))$
4.  Se $u\leq f(x)$ accetto $x$ come valore generato da $f$, altrimenti rifiuto e riparto dal punto 2.

$(X,Y)\sim\text{Unif}(A)\qquad f_{X,Y}(x,y)=\begin{cases}1 &(x,y)\in A \\0 &\text{altrimenti}\end{cases}$

$f_X(x)=\int_{-\infty}^{+\infty}f_{X,Y}(x,y)dy=\int_0^{f(x)}1dy=f(x)$

$f_{X,Y}(x,y|(x,y)\in A)=prager \frac{P((x,y)\in A|(X,y))\cdot f_{X,Y}(x,y)}{P((x,y)\in A)}$

$\begin{aligned}P(accettare)=\frac{|A|}{|G|}=\frac{1}{k}\qquad k\cdot g(x)&\geq f(x) \\ k\underbrace{\int g(x)dx}_1&\geq\underbrace{\int f(x)dx}_1 \\ k&\geq 1 \end{aligned}$

Generazione di variabili casuali normali

$Y\sim N(0,1)\Longrightarrow V=\mu+\sigma Y\sim N(\mu,\sigma^2)$

$f(y)=\frac{1}{\sqrt{2\pi}}\exp(-\frac{y^2}{2})$

Consideriamo la Laplace standard come g

$g(z)=\frac{1}{2}\exp(-|z|)$

Troviamo k minimo tale che $\frac{k}{2}e^{-|y|}\geq\frac{1}{\sqrt{2\pi}}e^{-y^2/2}$

$k\geq\sup_y\sqrt{2/\pi}e^{|y|-y^2/2}=\sqrt{2/\pi}e^{\sup_y|y|-y^2/2}=\sqrt{\frac{2e}{\pi}}$

Algoritmo a fette

## Applicazioni delle simulazioni
1.  Calcolo integrale
2. TLC (Teorema Limite Centrale)
3. I test multipli
4. Aumentare l’efficienza

### Calcolo integrale
Metodi Monte Carlo

$E(z(Y))=\begin{cases}\int_Sz(y)p(y)dy &\text{se Y è una variabile continua} \\ \sum_{y\in S}z(y)p(y) &\text{se Y è una variabile discreta}\end{cases}$

Integrazione Monte Carlo

$I(f)=\int_0^1…\int_0^1f(x_1,…,x_n)dx_1,…,dx_n$

$x\in[a,b]\Longrightarrow\frac{x-a}{b-a}[0,1]$

-   Il problema è deterministico non stocastico.
-   Con n piccoli, ci sono altri approcci matematici
-   Con n grandi, MC sono l’unica possibilità.
-   L’errore non dipende da n.

$E(Y)=\int_0^1…\int_0^1f(u_1,…,u_n)p(u_1,…,u_n)du_1,…,du_n=\int_0^1…\int_0^1f(u_1,…,u_n)du_1,…,du_n=I(f)$

$\hat{y}\pm z_{1-\alpha}s(f)/\sqrt{B}$

$s^2(f)=\frac{1}{B-1}\sum_{i=1}^B(y_i-\hat{I}(f))^2$

Ci sono casi in cui non esiste il momento secondo, quindi non si può determinare la precisione con il limite centrale

Funzione beta(a,b)

B=\frac{\Gamma(a)\cdot\Gamma(b)}{\Gamma(a+b)}

Beta(2,2)=\frac{1!\cdot 1!}{3!}=\frac{1}{6}

F(x)=6x(1-x)

K\geq\frac{f(x)}{g(x)}\quad k=\sup_x\frac{f(x)}{g(x)}

### Teorema del Limite Centrale

> 💡 **Obiettivo:** calcoliamo la bontà dell’adattamento della Teoria del Limite Centrale alla funzione.

Siano $y_1,…,y_2$ da $Y\sim f(\cdot)$ e supponendo che $E(Y)=\mu$ e $V(Y);+\infty$

Poniamo
$\bar{Y}=\frac{1}{n}\sum_{i=1}^n Y_i\qquad S^2=\frac{1}{n-1}\sum_{i=1}^n(Y_i-\bar{Y})^2$

per il Teorema del Limite Centrale (TLC)

$T_n=\frac{\sqrt{n}(\bar{Y}-\mu)}{S}\ \xrightarrow[d]{n\rightarrow\infty}\ N(0,1)$
$(\lim_{n\rightarrow\infty}P(T_n\leq z_\alpha)=\alpha\quad(\forall\alpha\in[0,1]))$
dove $z_\alpha\text{ t.c. }P(N(0,1)\leq z_\alpha)=\alpha$

Vera probabilità di rifiutare $\psi$
$\psi_{\text{basso}}(n,\alpha,f)=P(T_n\leq z_\alpha)$
$\psi_{\text{alto}}(n,\alpha,f)=P(T_n\geq z_{1-\alpha})$
$\psi_{\text{bilaterale}} (n,\alpha,f) =1-P(-z_{1-\alpha/2})\leq T_n\leq z_{1-\alpha/2}$

diminuisce all’aumentare di n

Approssimazione probabilità di rifiutare

$\hat{P}\text{ errore standard }\sqrt{\frac{\hat{P}(1-P)}{B}}$

**Campione “contaminato”**

> 💡 **Obiettivo:** stima della media e varianza di v.c. normale con campione contaminato.

Le osservazioni disponibili sono solo

$Y_i\begin{cases}x_i&\text{con prob }1-\pi \\ z_i&\text{con prob }\pi\end{cases}$

FdR
$\begin{aligned}P(Y\leq y)&=P(Y=X)\cdot P(Y\leq y|Y=X)+P(Y=Z)\cdot P(Y\leq y|Y=Z) \\ &=(1-\pi)\cdot P(X\leq y)+\pi\cdot P(Z\leq y)\end{aligned}$

Funzione di densità
$f_Y(y)=(1-\pi)\cdot f_X(y)+\pi\cdot f_Z(y)$

Funzione generatore
$$P(V=v)=\begin{cases}1-\pi&\text{se }v=1\\ pi&\text{se }v=2\end{cases}$$
La media campionaria e varianza non sono stimatori robusti da dati contaminati.

$\mu=\frac{\sum y_i}{n}\Longrightarrow$ Mediana
$S^2=\frac{\sum(y_i-\bar{y})}{n-1}\Longrightarrow$ Median Absolute Deviation

Mediana e MAD sono poco efficienti con valori buoni

Combiniamo i due metodi
1.  $\frac{|y_i-Med|}{\text{MAD}}\leq k \Longrightarrow y_i$ è NON CONTAMINATA
    -   k piccolo, poche (inefficienza) osservazioni veramente buone (correttezza)
    -   k grande, molte osservazioni (efficienza) ma non sono sicuro della bontà (distorsione)
2.  $\bar{y}$ e S solo su osservazioni buone

### I test multipli
usare gli stessi dati per più quesiti

Funzione di densità per $y_{ij}$

$f_i(y)=\begin{cases}0&\text{se }y<0\\ \frac{1}{\mu_i}e^{-y/\mu_i}&\text{altrimenti}\end{cases}$

Funzione di log-verosimiglianza


TRV (Test Rapporto Verosimiglianza)

Sotto H_0: $\mu_1=\mu_2=\mu$

**Teorema di Wilks**
$$ \begin{aligned}W&=2\left(\sup_{\mu_1>0,\mu_2>0}I(\mu_1,\mu_2)-\sup_{\mu>0}(\mu,\mu)\right) \\ &=4n(\log\frac{}{})\end{aligned} $$

$\frac{\partial\ell}{\partial\mu_1}=\frac{n}{\mu_1}+\frac{n\bar{y}_1}{\mu_1^2}=0\Longrightarrow\hat{\mu}_2=\bar{y}_2$

P(\mu,\mu)=n(2\log\mu+\frac{\bar{y}_1+\bar{y}_2}{\mu})

$\frac{\partial\ell(\mu,\mu)}{\partial\mu}=-\frac{2n}{\mu}+n\frac{\bar{y}_1+\bar{y}_2}{\mu^2}=0$

\hat{\mu}=\frac{}{}

P(\hat{\theta}_\sim)=

$=4n(\log\frac{}{}-\log(\bar{y}_1^{1/2}+\bar{y}_2^{1/2}))=4n(\log(\frac{1}{2}\frac{\bar{y}_1+\bar{y}_2}{\bar{y}_1^{1/2}+\bar{y}_2^{1/2}}))$

$r=\frac{\bar{y}_1}{\bar{y}_2}=\frac{\frac{1}{n}\sum y_{1j}}{\frac{1}{n}\sum y_{2j}}\sim\frac{Ga(n,\mu)}{Ga(n,\mu)}$

$W_{ij}=$ statistica test per confrontare il gruppo i con il gruppo j

rifiutiamo $H_0$ se $X_{max}=\max_{i>j}X_{ij}>$ soglia

pwmax, $P(W_{max}\leq x)$ usando B replicazioni di Monte Carlo
qwmax, stima i quantili di $W_{max}$

Test esempio: Tossicità nuovo farmaco
$y_{ij}=\begin{cases}0&i\text{-esimo paziente non presenta problemi di tossicità} \\ 1&i\text{-esimo paziente presenta problemi di tossicità}\end{cases}$

$\theta=$ probabilità che un paziente abbia problemi di tossicità

$s_n=\sum_{i=1}^n y_i=$ # pazienti con tossicità tra i primi $n$
$s_n\sim Bi(n,\theta)$

Sorveglianza secondo la quale

$\theta>\theta_0=0.1=$ livello accettabile di tossicità

Regola: $\begin{cases}\text{se }s_n>g_n\text{ allora blocchiamo lo studio} \\ \text{se }sn\leq g_n\text{ allora continuiamo lo studio}\end{cases}$

$g_n$ è la “barriera” da determinare.

**Secondo Wald**

$E(s_n)=n\cdot\theta_0\qquad \text{sqm}(s_n)=\sqrt{n\cdot\theta_0(1-\theta_0)}$

Segna un aumento di tossicità quando
$$s_n>g_n=n\cdot\theta_0+k\sqrt{n\cdot\theta_0(1-\theta_0)}$$
Statistica test
$$T_n=\frac{(s_n/n)-\theta_0}{\sqrt{\theta_0(1-\theta_0)/n)}}$$
Da rifiutare se $T_n>k$ (soglia prefissata)

**Secondo Wilks**

$H_0: \theta=\theta_0=$ tossicità accettabile (0,1)
$H_1: \theta=\theta_1=$ tossicità inaccettabile

Per $(y_1,…,y_n)$ abbiamo il TRV
$$L=\frac{\theta_1^{S_n}(1-\theta_1)^{n-S_n}}{\theta_0^{S_n}(1-\theta_0)^{n-S_n}}$$

Regione di rifiuto $\{L>\exp(C)\}$

$\begin{aligned}\left(\frac{\theta_1}{\theta_0}\right)^{Sn}\left(\frac{1-\theta_1}{1-\theta_0}\right)^{n-S_n}&>\exp(C) \\ s_n&>\frac{C-n\log\frac{1-\theta_1}{1-\theta_0}}{\log\frac{\theta_1}{\theta_0}-\log\frac{1-\theta_1}{1-\theta_0}}\end{aligned}$

S_n\log\frac{\theta_1}{\theta_0}+(n-S_n)\log

Potenza del test

Confrontare i due test

\gamma(\theta) =P_\theta(\max_{1\leq n\leq N(s_n)})

La velocità

rho()

N di pazienti

E(NP)=\undercbrace{E(NP|\text{no allarme})}_{N}P(no allarme)

P(\theta)=P(E(NP|\text{allarms}))

\rho>N

Se

Se la tossicità è toppo alta

### Aumentare l’efficienza

**Campionamento per importanza**

Valutare $I=\int_0^1 f(x)dx=E(f(U))\approx\frac{1}{B}\sum_{i=1}^Bf(u_i)$

Consideriamo $a>1$
$V\sim Unif

$E_v(f_v(V))=\int_0^af(x)\cdot\frac{1}{a}dx-\mu^2=a\int_0^1f(x)\cdot\frac{1}{a}dx-\mu^2$

V(f_v(V))=\int_0^af_v^2(x)\cdot\frac{1}{a}

Funziona solo per a>1
Inefficiente perché generiamo a inutili

Campioniamo di più dove f è grande

Valore atteso del rapporto tra la densità

\int_0^1f(x)dx=\int<

Generalizziamo

Obiettivo da calcolare $E(f(X))\qquad X\sim\phi(\cdot),\quad x\in S$

Con una v.a $V\sim\psi(\cdot)\quad v\in D$

Abbiamo

$E_V(f_v(V))=\int_D\frac{f(x)\phi(x)}{\psi(x)}\psi(x)dx=\int_Sf(x)\phi(x)dx=E_X(f(X))$

$V_V(f_v(V))=\int_D\left[\frac{f(x)\phi(x)}{\psi(x)}\right]^2\psi(x)dx-\mu^2=\int_D\frac{[f(x)\phi(x)]^2}{\psi(x)}dx-\mu^2$

Denominatore proporzionale col numeratore

V{frac(\ng(\frac{1}{B}\sum}

Sono identicamente distribuita ma non correlate

$\left.\begin{aligned}U\sim U(0,1) \\ 1-U\sim U(0,1)\end{aligned}\right\}\text{id}$

P(1-U\leq u)=P(U\geq 1-u)=u

Cov(U,1-U)=P -V(U)

Corr(U,1-U)=/\frac{V(U)}{\sqrt{V(U)}\sqrt{V(1-U)}}

F^{-1} monotona\Longrightarrow Corr<0

#### Rao-Blackwell
1) $Z\sim U(0,1)$
2) $\begin{aligned}X|Z=z&\sim Bi(n,z)\\ &\Longrightarrow E(X|Z=z)=n\cdot z\end{aligned}$

Procedura diretta
$\left.\begin{aligned}&\text{Genero }z_i\text{ da }U(0,1)\\ &\text{Genero }x_i\text{ da }Bi(n,z)\end{aligned}\right\}\quad\text{Ripetuto }B\text{ volte}$
$$E(X)\approx\frac{1}{B}\sum_{i=1}^B x_i$$

Procedura "Rao-Blackwell"
genero le $z_i$ da $U(0,1)\Longrightarrow z_1,...,z_B$
$$E(X)\approx\frac{1}{B}E_X(X|Z=z_i)$$
Più efficace  
$V_X\left\{\frac{1}{B}\sum_{i=1}^B X_i\right\}=\frac{V_X(X)}{B}\geq V_Z\left\{\frac{1}{B}\sum_{i=1}^B E_X(X|Z_i)\right\}=\frac{V_Z(E_X(X|Z))}{B}$
