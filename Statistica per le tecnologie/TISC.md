**Campionamento non probabilistico**
È un campionamento per cui ci sono unità che hanno probabilità nulla di far parte del campione. Accade quando non si ha la lista delle unità da studiare. 
- C. per quote
- C. a valanga

**Campionamento probabilistico**
È un campionamento per cui ogni unità ha una probabilità non nulla di far parte del campione.

### Campionamento casuale semplice
Tutte le unità hanno la stessa probabilità di far parte del campione.
Si usano stimatori semplici.

- Estrazione con reinserimento
$\pi_i=\frac{1}{N}+\frac{1}{N}+...-(\frac{1}{N})^n\sim\frac{n}{N}$
- Estrazione senza reinserimento (in blocco) 
$\pi_i=\frac{1}{N}+\frac{1}{N-1}\cdot(1-\frac{1}{N})+\frac{1}{N-2}\cdot(1-\frac{1}{N})\cdot(1-\frac{1}{N-1})+...=\frac{n}{N}$
Mantengono stessa probabilità

**_Stima della media (CSS senza reinserimento)_**
$$\quad\bar{Y}=\frac{1}{N}\sum_{i=1}^N Y_i$$Stima di $\bar{Y}:\quad E(\bar{y})=\bar{Y}$

**_Varianza di stima_**
$$V(\bar{y})=(1-f)\frac{S^2}{n}=\frac{N-n}{N-1}\frac{\sigma^2}{n}$$
$f=\frac{n}{N}$ frazione di campionamento
$s^2=\frac{1}{n-1}\sum_{i=1}^n(y_i-\bar{y})^2$ stimatore non distorto di $S^2$

**_Stima di proporzioni_**
Y dicotomica
Proporzione campionaria:  $\bar{y}=p\quad\sum\frac{n_1}{n}$
Totale campionaria:  $\hat{Y}=N\cdot p$ 

**Intervallo di confidenza**
$\bar{y}-z_{a/2}se(\bar{y})\leq\bar{Y}\leq\bar{y}+z_{a/2}se(\bar{y})$

Es. $N=807$ professori $\quad n=50$ professori

Publications|0 |1|2|3|4|5|6|7|8|9|10
------------|--|-|-|-|-|-|-|-|-|-|--
Professors  |28|4|3|4|4|2|1|0|2|1|1

a) Trovare media e standard error
$\bar{y}=\frac{\sum_{i=1}^k y_if_i}{n}=\frac{89}{50}=1.78$
$s^2=\frac{1}{n-1}\sum_{i=1}^k(y_i-\bar{y})^2f_i=7.195$
$f=\frac{n}{N}=\frac{50}{807}=0.062\qquad V(\bar{y})=(1-0.062)\frac{7.195}{50}=0.135$
$se=0.367$

b) Trovare la proporzione di docenti con nessuna pubblicazione con intervallo di confidenza 95%
$p_0=\bar{y}\cdot f_0=1.78*28=49.84$


**Determinazione della numerosità ottimale**
$$n=\frac{z^2_{a/2}s^2}{D^2+\frac{z^2_{a/2}s^2}{N}}$$
$D^2=z^2_{a/2}\frac{s^2}{n}\left(1-\frac{n}{N}\right)$  D=errore assoluto

Es. $N=4000\qquad 45\%\leq P_1\leq 65\%\quad\text{e}\quad 5\%\leq P_2\leq 10\%$
$n_0=\frac{z_{a/2}^2S^2}{D^2}$
$S^2=p(1-p)$
$n=\frac{n_0}{1-\frac{n_0}{N}}$
1854

Es. $N=100000$

#### Campionamento sistematico
- con una sequenza delle unità della lista
- determina il "**passo di campionamento**" $k=N/n(=1/\pi_i)$
- identificazione delle n unità

Vantaggi:
- utilizzabile senza avere una lista

Svantaggi:
- pseudo-casuale
- possibile distorsione del campione causato dalla ciclicità
- non ha uno stimatore corretto di varianza di stima

Stratificazione implicita
- sola variabile di stratificazione (quantitativa)
	1. ordinamento decrescente
	2. selezione sistematica delle unità
- variabile di stratificazione quantitativa e una o più variabili qualitativa

Es. $N=15\quad n=3$
passo camp. $k=\frac{15}{3}=5$
$400\quad 600\quad 570\quad 960\quad 780\quad 800\quad 460\quad 650\quad 440\quad 530\quad 470\quad 810\quad 625\quad 510\quad 700$
$r=1\quad C_1=\{400,800,470\}\qquad r=4\quad C_4=\{960,440,510\}$
$r=2\quad C_2=\{600,460,810\}\qquad r=5\quad C_5=\{780,530,700\}$
$r=2\quad C_3=\{570,650,625\}\qquad \bar{y}=\frac{\sum y_i}{n}=620$
$\bar{y}_1=\frac{400+800+470}{3}=556.7\qquad\bar{y}_2=623.3\qquad\bar{y}_3=615\qquad\bar{y}_4=636.7$
$\bar{y}_5=670\qquad f=\frac{3}{15}=0.2$
$V(\bar{y}_1)=(1-0.2)\frac{45633}{3}=12168\qquad V(\bar{y}_2)=8275\qquad V(\bar{y}_3)=446.7$
$V(\bar{y}_4)=21235\qquad V(\bar{y}_5)=4346\qquad\frac{\sum(\bar{y}_i-\bar{y})^2}{n_c}=1365$

#### Selezione con probabilità variabili
Stimatore di Horvitz-Thompson $$\bar{Y}=\sum_{i\in C}\frac{Y_i}{\pi_i}=\sum\frac{Y_i}{\pi_i}I_i$$ dove $1/\pi_i=$coefficienti di riporto all'universo

### Campionamento complesso
- Non sempre è possibile usare il campionamento casuale semplice (non si è disposti di una lista completa)
- Si vuole campionare più efficientemente 

DEFF: effetto del disegno di campionamento
$$DEFF=\frac{Var(\hat{\vartheta}')}{Var(\hat{\vartheta})}$$
$\hat{\vartheta}'$ campione complesso $\quad\hat{\vartheta}$ campione casuale semplice

#### Campionamento stratificato
La variabile ausiliaria deve essere conosciuta a priori.
Selezionare i campioni secondo la variabile ausiliaria.

1) Variabili di stratificazione
2) Numero di strati
3) Determinazione della numerosità campionaria
4) Eventuali unità autorappresentative
5) Selezione
	- ottimale
	- proporzionale

**Stime**
Allocazione proporzionale
$$n_h=n\cdot W_h$$
Efficienza tra stratificato proporzionale e CCS
$V_{ccs}(\bar{y})-V_{pr}(\bar{y}str)\tilde{=}\frac{1-f}{nN}\sum N_h(\bar{Y}hU-\bar{Y}_U)^2$

Allocazione di Neyman $$n_h=n\frac{W_hS_h/\sqrt{C_h}}{\sum W_hS_h/\sqrt{C_h}}$$
Efficienza dell'allocazione di Neyman rispetto prop
$V_{Prop}-V_{}=$

Es. $N=90000\quad N_1=35000\quad N_2=45000\quad N_3=10000$
$i=$(case singole, appartamenti proprietà, appart. affitto)
$\mu_1=2\mu_2\quad \mu_2=\mu_3\quad \sigma_1=k\mu_1=2k\sigma_2\quad \sigma_2=\sigma_3$
a. Campione stratificato $n=900$
	$W_1=\frac{N_i}{N}=0.39\quad W_2=0.5\quad W_3=0.11$
	Allocazione proporzionale
	$n_1=900\cdot 0.38=351\quad n_2=450\quad n_3=99$
	Allocazione di Neyman
	$\sum W_hS_h=2\cdot0.39+0.5+0.11=1.39$
	$n_1=900\cdot\frac{0.39\cdot 2}{1.39}=505\quad n_2=324\quad n_3=71$
b. 45% proprietari di casa, 25% dei proprietari di appartamento e 3% affittuari praticano il risparmio energetico
	$Y=\begin{cases}1&\text{SI}\\ 0&\text{NO}\end{cases}\qquad y_1=0.45\quad y_2=0.25\quad y_3=0.03$

Stratificazione ad hoc dipendentemente dalle liste o dagli strati

### Campionamento per quote
È un campionamento **NON probabilistico**.


## Campionamento a stadi
Si usa quando
- non si dispone di un'unica lista
- la popolazione è organizzata in cluster
- la popolazione è distribuita in un territorio vasto

Stratificato è più efficiente.

1) Numero di stadi, minimo indispensabile
2) Campionamento al primo stadio (grappoli)
	UPS = unità primo stadio
3) Campionamento al secondo stadio
	USS = unità secondo stadio

Campionamento a grappoli di dimensione costante
ANOVA (Analisi della varianza)
Fonte | GdL | Numeratore | Varianza
--- | --- | --- | --- 
Fra UPS | N-1 | $\displaystyle SSB=\sum_{i=1}^N\sum_{j=1}^M(\bar{Y}_i-\bar{Y})^2$ | MSB
Entro UPS | N(M-1) | $\displaystyle SSW=\sum_{i=1}^N\sum_{j=1}^M(\bar{Y}_{ij}-\bar{Y}_i)^2$ | MSW
Totale | NM-1 | $\displaystyle \sum_{i=1}^N\sum_{j=1}^M(\bar{Y}_{ij}-\bar{Y})^2$ | $S^2$
SS- (Sum of Squares)
MS- (Mean of Squares)

Formulazione ANOVA $\displaystyle\quad\rho=\frac{M}{M-1}\frac{SSW}{SSTO};-\frac{1}{M-1}\leq\rho\leq 1$
$\rho=$ coefficiente di correlazione interclasse

- Cluster omogenei $\quad SSW=0\rightarrow\rho=1$
- Cluster eterogenei $\quad SSW=SSTO\rightarrow\rho=-1/(M-1)$
- UPS distribuite casualmente $\rho=0$

$$DEFF(\text{stadi})=\frac{MSB}{S^2}=\frac{NM-1}{M(N-1)}[1+(M-1)\rho]$$
**Campionamento sistematico come caso speciale del campionamento a stadi**
Considerando 




![[Indagini consumi energetici delle famiglie]]


