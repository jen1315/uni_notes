# Modelli statistici

$Y_1,…,Y_n\sim f(\cdot\ ;\theta)\qquad\theta\in\Theta\subset\mathbb{R}^d\quad d\geq 1$

#### Modello normale
Comportamento di variabili indipendenti e identicamente distribuite

$Y_i\sim N(\mu;\sigma^2)\qquad\theta=(\mu,\sigma^2)\in\Theta=]0,+\infty]$

Densità di $Y_i$ è
$$f(y;\theta)=\frac{1}{\sqrt{2\pi\sigma^2}}\exp\left(-\frac{(y-\mu)^2}{2\sigma^2}\right)$$
Stimatori
$$\hat{\mu}=\bar{Y}=\frac{\sum_{i=1}^n Y_i}{n}\qquad S^2=\frac{\sum_{i=1}^n(Y_i-\bar{Y})^2}{n-1}$$
Correttezza
$E(\bar{y})=E(\frac{\sum_{i=1}^n y_i}{n})=\frac{1}{n}E(\sum_{i=1}^n y_i)=\frac{1}{n}\sum_{i=1}^n E(y_i)=\frac{1}{n}(\mu_1,…,\mu_n)$

$\begin{aligned}E(S^2)&=E(\frac{1}{n-1}\sum_{i=1}^n(y_i-\bar{y})^2)=E(\frac{1}{n-1}\sum(y_i-\mu+\mu-\bar{y})^2) \\ &=\frac{1}{n-1}[E(\sum(y_i-\mu)^2)+2E((\mu-\bar{y})\sum(y_i-\mu))+E(\sum(\mu-\bar{y})^2)]\end{aligned}$

\sum(y_i-\mu)=\sum y_i-\sum\mu=n\bar{y}-n\mu=n(\bar{y}-\mu)

E(y_i-\mu)^2=V(y_i)=\sigma^2

E(y_i-\bar{y})^2=E(\bar{y}-\mu)^2=V(\bar{y}) E(\bar{y})=\mu

V(\bar{y})=

=\frac{1}{n-1}[\sum \underbrace{E(y_i-\mu)^2}_{\sigma^2}+2n E((\mu-\bar{y})(\bar{y}-\mu))+\sum E(\bar{y}-\mu)^2] =\frac{}{}[n\sigma^2-2n\frac{\sigma^2}{n}+n\frac{\sigma^2}{n}]

-E((\bar{y}-\mu^2))=-V(\bar{y})=-\frac{\sigma^2}{n}=\frac{1}{n-1}(n-1)\sigma^2=\sigma^2\rightarrow E(S^2)

V(S^2)\qquad V(\chi^2_r)=2\cdot r sotto normalità

\frac{(n-1)S^2}{\sigma^2}\sim\chi^2_{n-1}

V(\frac{(n-1)S^2}{})

\bar{y}, S^2 sono consistenti

Infatti: E(\hat{y})=\mu E(S^2)=\sigma^2 ok correttezza

V(\bar{y})=\frac{\sigma^2}{n}\rightarrow 0\quad V(S^2)=\frac{2\sigma^4}{n-1}\rightarrow 0 per n\rightarrow\infty

Sotto assunz di normalità

\frac{\bar{y}-\mu}{\frac{S}{\sqrt{n}}}\sim t_{n-1}

\frac{\bar{y}-\mu}{\frac{\sigma^2}{\sqrt{n}}}\sim N(0,1)

\frac{(n-1)}{}

\bar{y}\sm t_{n-1,1-\frac{\alpha}{2}}\cdot \frac{S}{\sqrt{n}} IC per \mu con grado di fiducia 1-\alpha

H_0:\mu=\mu_0 H_1:\mu\neq\mu_0 t=\frac{\bar{y}-\mu_0}{\frac{S}{\sqrt{n}}}\sim t_{n-1}

Rifiuto H_0 se

Relazione tra variabili

$(Y_{i1},Y_{i2},…,Y_{in})\sim F(\cdot\ ;E)\\ \theta\in\Theta\in\mathbb{R}^d\quad d\geq 1\quad i=1,…,n$

Caso bidimensionale

$\left[\begin{matrix}y_{i1} \\ y_{i2}\end{matrix}\right]\sim N_2(\underbrace{\left[\begin{matrix}\mu_{i1} \\ \mu_{i2}\end{matrix}\right]}_{\mu}, \underbrace{\left[\begin{matrix}\sigma^2_{1} &\sigma_{12}\\ \sigma_{12} &\sigma^2_2\end{matrix}\right]}_{\sum})$

$E(y_{i1}|y_{i2}=y_{i2})=(\mu_1-\mu_2)=\beta_1+\beta_2 y_{i2}$

$$ Y\sim F(\cdot\ ;x_1,…,x_\rho;\theta) $$

$Y$ (casuale): variabile dipendente, risposta, spiegata

$x_1,…,x_\rho$ (deterministiche): variabili esplicativa, prenditori, esogene, indipendenti (non in senso stocastico), covariate

Hanno correlazione ma ciò non implica casualità.

Obiettivi:

-   Previsivo
-   Descrittivo

$Y=\underbrace{g(x_1,…,x_\rho;\theta_\sim)}_{\text{deterministica}}+\underbrace{\varepsilon}_{\text{casuale}}\qquad\varepsilon_i\sim F(\cdot\ ;\theta)$

$Y_1,…,Y_n\quad\text{i.i.d} \quad N(\mu,\sigma^2)$

\bar{Y}\quad S^2 Corretti Consistenti

Y\sim F(\cdot\ ;x_{i1},…,x_{i\rho};\theta) i,…,n Non identicamente distribuite

\begin{tabular}{ccccc}unità stat & variabili osservate \\ 1 & $y_1$ & $x_{11}$ & … & $x_{1p}$\end{tabular}

Modello lineare

$h(Y_i)=\beta_1g_1(x_{i1})+…+\beta_pg_p(x_{ip})+\varepsilon_i$

\varepsilon_i\sim f_\varepsilon(\cdot\ ;\theta) N(0;\sigma^2)

Modello non lineare: $Y_i=e^{\beta_1+\beta_2x_{i2}}+\varepsilon_i$

Modello non lineare ma linearizzabile: $Y_i=e^{\beta_1+\beta_2x_{i2}}\cdot\varepsilon_i$

$\log(Y_i)=\beta_1+\beta_2x_{i2}+\log(\varepsilon_i)$

Es 1.4 Analisi delle varianze (quantitativa x qualitativa)

$\text{calorie}=g(\text{carne};\theta)+(\text{errore})\qquad\theta=(\mu_1,\mu_2,\mu_3)$

$g(\text{carne};\theta)=\begin{cases}\mu_1 &\text{se carne=Bovina} \\ \mu_2 &\text{se carne=Pollame} \\ \mu_3 &\text{se carne=Mista}\end{cases}$

Es 1.5 Analisi della covarianza

Es 1.8 Modello non normale

## Ch.2 Regressione lineare semplice

Coefficiente di correlazione, confronto delle variabili per ciascuna media

$(x_i-\bar{x})(y_i-\bar{y})>0$

$$ 1<\frac{(\sum_{i=1}^n (x_i-\bar{x})(y_i-\bar{y}))/n}{\sqrt{\sum(x_i-\bar{x}))/n}\sqrt{(\sum(y_i-\bar{y})})/n}<1 $$

$r_{xy}$, forza della relazione lineare

$Y_i=\underbrace{\beta_1+\beta_2x_i}_{\text{deterministico}}+\underbrace{\varepsilon_i}_{\text{casuale}}$

**Assunzioni**

1.  $E(Y_i|X_i=x_i)=\beta_i+\beta_2x_i$ Linearità
2.  $V(Y_i|X_i=x_i)=\sigma^2>0$ Omoschedasticità (varianza costante)

$\sigma^2=0\quad\text{caso banale} \quad\Longrightarrow\quad Y_i=\beta_1+\beta_2x_i$

$Y_i=\underbrace{\beta_1+\beta_2x_i}_{\mu_i}+\varepsilon_i=\mu_i+\varepsilon_i$

$\boxed{E(Y_i)=\mu_i+E(\varepsilon_i)}$

$E(Y_i)=\mu_i\Longleftrightarrow E(\varepsilon_i)=0$

$V(Y_i)=V(\mu_i+\varepsilon_i)$

$\theta_\sim=(\beta_1,\beta_2,\sigma^2)\in\Theta=\R^2\cdot\R^2$

$(Y_1,…y_n)\in\mathcal{F}=\R^n$

Stimare $\beta_1,\beta_2\leftarrow(x_i,y_i)\quad i=1,…,n$

Stimiamo usando la distanza verticale quadratica:

-   Verticale perché siamo interessati alla y
-   Quadratica perché non hanno punti non derivabili, coincidono con gli stimatori di massima verosimiglianza

Obiettivo da minimizzare

$$ S(\beta_1,\beta_2)=\sum_{i=1}^n(y_i-(\beta_1+\beta_2x_i))^2 $$

Stima dei minimi quadrati

$$ ⁍ $$

Quando $\sum(x_i-\bar{x})^2\neq 0$ ossia $x_i$ ﻿non sono tutte uguali, si ottiene

$$ \beta_2=\frac{n\sum y_ix_i-\sum x_i\sum y_i}{n\sum x_i^2-(\sum x_i)^2}=\frac{\sum(y_i-\bar{y})(x_i-\bar{x})}{\sum(x_i-\bar{x})^2}=\boxed{\frac{s_{xy}}{s_x^2}} $$

\sum x_iy_i-n

\sum(x_i-\bar{x})^2=\sumx_i^2-2n\bar{x}^2+n\bar{x}^2=\sumx_i^2-n\bar{x}^2

$\boxed{\hat{\beta_1}=\bar{y}-\hat{\beta_2}\bar{x}}$

$$ ⁍ $$

\hat{y}, valore previsto

x qualsiasi

$E(Y)=\beta_1+\beta_2x\qquad E(Y|X=0)=\beta_1$

E(Y|X=x)=\beta_1+\beta_2x

$\beta_2=E(Y|X=x+1)-E(Y|X=x)$

\hat{y}_{|x=0}=\hat{\beta_1}+\hat{\beta_2}0=\hat{\beta_1}

\hat{y}_{|x=0}=\hat{\beta_1}+\hat{\beta_2}0=\hat{\beta_1}

\sum(y_i-(\hat{\beta}_1+\hat{\beta}_2x_i))=0

Metodo matriciale

$\underbrace{\left[\begin{matrix}n &\sum x_i \\ \sum x_i &\sum x_i^2\end{matrix}\right]}_{M}\left[\begin{matrix}\beta_1 \\ \beta_2\end{matrix}\right]=\left[\begin{matrix}\sum y_i \\ \sum x_iy_i\end{matrix}\right]$

$M=\left[\begin{matrix}a&b\\c&d\end{matrix}\right]\Longrightarrow M^{-1}=\frac{1}{ad-bc}\left[\begin{matrix}d&-b\\-c&a\end{matrix}\right]$

$\left[\begin{matrix}\hat{\beta_1}\\ \hat{\beta_2}\end{matrix}\right] =\frac{1}{n\sum x_i^2-(\sum x_i)^2} \left[\begin{matrix}\sum x_i^2&-\sum x_i\\-\sum x_i&n\end{matrix}\right] \left[\begin{matrix}\sum y_i\\ \sum x_iy_i\end{matrix}\right]$

S(\beta_1,\beta_2)=2(y_i-\beta_1-\beta_2x_i)^2

y_i^*=y_i-\beta_2x_i

S(\beta_1,\beta_2)=2(y_i^*-\beta_i)^2

\beta_1=\frac{\sum y_i^*}{n}=\frac{1}{n}\sum(y_i-\beta_2x_i)=\bar{y}-\beta_2\bar{x}

$\sum(y_i-\bar{y}-\beta_2x_i+\beta_2\bar{x})^2=\sum((y_i-\bar{y})-\beta_2(x_i-\bar{x}))^2=\sum(y_i-\bar{y})+\beta_2^2\sum(x_i-\bar{x})-2\beta_2\sum(y_i-\bar{y})(x_i-\bar{x})=n\beta_2^2s_x^2-2n\beta_2s_{XY}+ns^2_Y$

E se tutte le $y_i$ sono uguali?

$y_i=c\quad i=1,…,n$

$\bar{y}=\frac{c+…+c}{n}=c\quad\Longrightarrow\quad\hat{\beta}_2=\frac{\sum(x_i-\bar{x})(c-c)}{\sum(x_i-\bar{x})^2}=0\rightarrow\hat{\beta}_1=\bar{y}$

E se tutte le $x_i$ sono uguali?

$X_i=c\quad i=1,…,n\qquad\bar{x}=c$

$\hat{\beta}_2=\frac{\sum(c-c)(y_i-\bar{y})}{\sum(c-c)^2}=\frac{0}{0}$ Indeterminato

Assunzioni momento misto

$Corr(y_i,y_j)=0=Corr(\varepsilon_i,\varepsilon_j)$

Cov(y_i,y_j)=E((y_i-E(x_i))\cdot (y_j-E(y_j)))=E((y_i-\beta1)())=E()

Stimare $\beta_2$

$\begin{aligned}\hat{\beta}_2&=\frac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})^2}=\sum_{i=1}^n\frac{(x_i-\bar{x})}{\sum_{i=j}^n(x_j-\bar{x})^2}(y_i-\bar{y}) \\ &=\sum_{i=1}^n w_i(y_i-\bar{y})\end{aligned}$

$\sum_{i=1}^n w_i=\frac{\sum_{i=1}(x_i-\bar{x})}{\sum(x_j-\bar{x})^2}=0$

$\sum_{i=1}^n x_iw_i=\frac{\sum_{i=1}(x_i^2-x_i\bar{x})}{\sum(x_j-\bar{x})^2}=\frac{\sum x_i^2-n\bar{x}^2}{\sum x_j^2-n\bar{x}^2}=1$

$\hat{\beta}_2=\sum w_i(y_i-\bar{y})=\sum w_iy_i-\bar{y}\underbrace{\sum w_i}_{=0}=\sum w_iy_i$

$$ \begin{aligned}E(\hat{\beta}_2)&=\sum w_iE(y_i)=\sum w_i(\beta_1+\beta_2x_i) \\ &=\beta_1\sum w_i+\beta_2\sum w_ix_i=\boxed{\beta_2}\\ \\ V(\hat{\beta}_2)&=\sum w_i^2V(y_i)=\sum w_i^2\sigma^2=\sigma^2\frac{\sum_{i=1}^n(x_i-\bar{x})^2}{(\sum_{j=1}^n(x_j-\bar{x})^2)^2} \\ &=\boxed{\frac{\sigma^2}{\sum_{j=1}^n(x_j-\bar{x})^2}}\end{aligned} $$

Preferibile che x abbia varianza grande e y varianza piccola

Stimare $\beta_1$

$\begin{aligned}\hat{\beta}_1=\bar{y}&=\hat{\beta}_2\bar{x}\underbrace{=}_{\hat{\beta}_2\sum w_iy_i}\frac{\sum y_i}{n}-\sum w_i\bar{x}y_i \\ &=\sum(\frac{1}{n}-\bar{x}w_i)y_i=\sum w_i^*y_i\end{aligned}$

\sum w_i^*=\sum(\frac{1}{n}-\bar{x}w_i)=1-\bar{x}\sum w_i=1

\sum x_iw_i^*=\sum(\frac{x_i}{n}-\bar{x}x_iw_i)=\bar{x}-\bar{x}\underbrace{\sum x_iw_i}_{=1}=0

E(\hat{\beta}_1)\underset{\text{lin}} {=}\sum w_i^_(\beta_1+\beta_2x_i)=\beta_1\sum w_i^_+\beta_2\sum w_i^*x_i=\beta_1

$\begin{aligned}V(\hat{\beta}_1)&\underset{\text{incorr}} {=}\sum(w_i^_)^2V(y_i)\underset{\text{omosch}} {=}\sum(w_i^_)^2\sigma^2=\sigma(\frac{1}{n}+\bar{x}^2\sum w_i^2-\frac{2\bar{x}}{n}\sum w_i) \\ &=\sigma^2(\frac{1}{n}+\frac{\bar{x}^2}{\sum(x_i-\bar{x})^2})\end{aligned}$

$\bar{x}^2$ quanto sono lontane da 0 le x

$\begin{aligned}Cov(\hat{\beta}_1,\hat{\beta}2)&=Cov(\bar{y}-\hat{\beta}_2\bar{x},\hat{\beta}_2) \\ &=Cov(\bar{y},\hat{\beta}_2)-\bar{x}\underbrace{Cov(\hat{\beta}_2,\hat{\beta}_2)}_{V(\hat{\beta}_2)}\end{aligned}$

Cov(\bar{y},\hat{\beta}_2)=Cov(\frac{1}{n}\sum y_i,\sum w_jy_j)=\frac{1}{n}\sum Cov(y_i,\sum w_jy_j)=\frac{1}{n}\sum\sum w_j Cov(y_i,y_j)=\

\hat{y}=\hat{\beta}_1+\hat{\beta}_2\bar{x}=\bar{y}

Stimare $\sigma^2$

$\varepsilon_i=y_i-\beta_1-\beta_2x_i$ ERRORI

$e_i=y_i-\hat{\beta}_1-\hat{\beta}_2x_i$ RESIDUI

I residui sono rappresentanti campionari degli errori.

$\hat{\sigma}^2=\frac{\sum(e_i-\bar{e})^2}{n}=\frac{\sum e_i^2}{n}$ stimatore distorto

$\sum e_i=\sum(y_i-\hat{\beta}_1-\hat{\beta}_2x_i)=0$ (sulla base della prima eq min quadrati che riguarda l’Inter certa $\beta_1$)

$\begin{aligned}n\sigma^2=\sum e^2_i&=\sum(y_i-\hat{\beta}_1-\hat{\beta}_2x_i)^2 \\ &=\sum((y_i-\bar{y})-\hat{\beta}_2(x_i-\bar{x}))^2 \\ &=\sum(y_i-\bar{y})^2+\hat{\beta}_2^2\sum(x_i-\bar{x})-2\hat{\beta}_2\sum(y_i-\bar{y})(x_i-\bar{x}) \\ &=\sum(y_i-\bar{y})^2-\hat{\beta}_2^2\sum(x_i-\bar{x})^2\end{aligned}$\hat{\beta}_2=\frac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})}

E(Z^2)=V(Z)+E(Z)^2

E(n\sigma^2)=\sum E(\hat{\beta}_2^2)\sum(x_i-\bar{x})^2

E(n\hat{\sigma}^2

$$ ⁍ $$

$Y_i=\beta_1+\varepsilon$

v.a. e identicamente distribuiti

\hat{Y}\rightarrow

V(\hat{\beta}_2)=\frac{\sigma^2}{\sum(X(x_))}

Coefficiente di determinazione R^2

\frac{1}{n}\sum y_i =\hat{\beta}_1\bat{\beta{io}}

\sum(y_i-\ha\{y})=\sum(\hat{y}_i-\bar{y})+\sum e_i^2

Scomposizione della devianza (SQ_{TOT})

Devianza spiegata + Devianza residua

SQ_{RES}=0\quad\sum e_i^2=0 \varepsilon_i=0 \forall i

SQ_{REG}=SQ_{TOT}

SQ_{REG}=0\quad\sum e_i^2=0 \varepsilon_i=0 \forall i

Y_i=\beta_i+\varepsilon_i\ \rightarrow\ \hat{\beta}_1=\argmin_{\beta_1}()

No inclinazione, no x

$0\leq R^2=\frac{SQ_{reg}}{SQ_{tot}}=1-\frac{SQ_{res}}{SQ_{tot}}\leq 1$

R^2 =\fra{SQ_{TOT}-SQ_{RES}}{SQ_{TOT}}=

R^2=\hat{beta}_1^2\frac{\sum(x_i-\bar{x})^2}{\sum(y_i-\bar{y})}=\frac{[\sum(x_i-\bar{x})(y_i-\bar{y})]}{\sum()}=r_{XY}^2

$$ \varepsilon_i\sim{\color{blue}N}({\color{red}0},{\color{green}\sigma^2})\qquad {\color{orange}\text{indipendenti}}\qquad i=1,...,n $$

Assunzioni:

1.  Linearità
2.  Omoschedasticità
3.  Incorrelazione
4.  Normalità

$$ Y_i\sim{\color{blue}N}({\color{red}\beta_1+\beta_2x_i},{\color{green}\sigma^2}) $$

L(\theta_\sim)=L(\beta_1,\beta_2,\sigma^2)=\prod^n P(y_i;\beta_1,\beta_2,\sigma^2)=\prod^n\frac{1}{\sqrt{2\pi\sigma^2}}\exp\{-\frac{1}{2\pi^2}(y_i-(\beta_1+\beta_2x_i))^2\}

\alpha(\sigma^2)^{-n/2}\exp\{-\frac{1}{2\sigma^2}\underbrace{\sum(y_i-(\beta_1+\beta_2x_i))^2}_{S(\beta_1,\beta_2)}\}

\ell(\beta_1,\beta_2;\sigma^2)=-\frac{n}{2}\log\sigma^2-\frac{1}{2\sigma^2}S(\beta_1,\beta_2)

\frac{\partial(\theta_\sim)}{\partial\theta_\sim}=\ell’(\theta_\sim)=0

\ell’(\theta_\sim)=\left[\begin{matrix}\frac{\partial\ell}{\partial\beta_1} \\ \frac{\partial\ell}{\partial\beta_2} \\ \frac{\partial\ell}{\partial\sigma^2}\end{matrix}\right]=[\frac{1}{\sigma^2}\sum(y_i-\beta_1-\beta_2x_i) \\ \frac{1}{\sigma^2}\sum x_i(y_i-\beta_1-\beta_2x_i) \\ -\frac{}{}]

$$ ⁍ $$

Distribuzione di ($\hat{\beta}_1,\hat{\beta}_2$)

hat{\beta}_2=\sum w_iy_i

\hat

$S^2,\hat{\sigma}^2\quad\text{i.i.d.}\quad\hat{\beta}_1,\hat{\beta}_2$

Stimatori della variabilità e quelli del comportamento in media sono indipendenti in distribuzione.

**Inferenza sui parametri $\beta_1$ e $\beta_2$ ($\sigma^2$ non nota)**

-   Test di Wald

Quantità pivot $q_r=\frac{\hat{\beta}_r-\beta_r}{\sqrt{\widehat{V(\hat{\beta}_r)}}}\quad r=1,2$

Poiché $\widehat{V(\hat{\beta}_r)}=\frac{S^2}{\sigma^2}V(\hat{\beta}_r)$

$q_r=\frac{\hat{\beta}_r-\beta_r}{\sqrt{\widehat{V(\hat{\beta}_r)}}}=\frac{\hat{\beta}_r-\beta_r}{\sqrt{S^2{\sigma^2}V(\hat{\beta}_r)}}=\frac{\frac{\hat{\beta}_r-\beta_r}{\sqrt{V(\hat{\beta}_r)}}}{\sqrt{\frac{S^2}{\sigma^2}}}$

$$ ⁍ $$

Verifica di ipotesi

$H_0:\beta_r=\beta_r^{(0)}\quad H_1:\beta_r\neq \beta_r^{(0)}$

Sotto H_0

t_r=\frac{\hat{\beta}_r-\beta_r^{(0)}}

${\sqrt{\widehat{V(\hat{\beta}_r)}}}\ \underset{H_0} {\sim}\ t_{n-2}\quad r=1,2$

Rifiuto H_0 se

|t_r^{OSS}| GRANDE

|t_r^{OSS}>t_{n-2;1-\frac{\alpha}{2}}|

Livello di significatività osservato

Misura della coerenza dei dati con H_0

$\begin{aligned}\alpha^{OSS}&=2\min(P(t_{n-2\leq t_r^{OSS}}),P(t_{n-2}\geq t_r^{OSS})) \\ &\text{sfruttando la simmetria attorno a zero della t Student} \\ &=2P(t_{n-2},-|t_r^{OSS}|)=2P(t_{n-2}>t_r^{OSS})\end{aligned}$

Accetto H_0 al suo livello di significatività \alpha quando

\alpha_{OSS}>\alpha altrimenti rifiuto

Y_i=\beta_1+\beta_2x_i+\varepsilon_i\quad i=1,…,n

\begin{cases}H_0:\beta_2=0 \Longrightarrow Y_i=\beta_1+\varepsilon_i \\ H_1:\beta_2\neq 0\end{cases}

t_2=\begin{\hat{\beta}_2-0}{\sqrt{\widehat{V(\beta_2)}}}\underset{H_0}{\sim}t_{n-2}

(t_2^{OSS})^2

Grado di fiducia (livello di confidenza)

$\begin{aligned}1-\alpha&=P(t_{n-2,\frac{\alpha}{2}}<q_r<t_{n-2;1-\frac{\alpha}{2}}) \\ &=P\left(-t_{n-2;1-\frac{\alpha}{2}}<\frac{\hat{\beta}_r-\beta_r}{\sqrt{\widehat{V(\hat{\beta}_r)}}}<t_{n-2;1-\frac{\alpha}{2}}\right) \\ &\hat{\beta}_r\pm t{n-2;1-\frac{\alpha}{2}} \sqrt{\widehat{V(\hat{\beta}_r)}}\end{aligned}$

Test del log-rapporto di verosimiglianza

$H_0:\beta_2=0\quad H_1:\beta\neq 0$

Wilks

$\begin{aligned}M_1\quad &\text{Modello corrente o completo} \\ &Y_i=\beta_1+\beta_2x_i+\varepsilon_i \\ M_0\quad &\text{Modello ridotto (come definitivo da }H_0) \\ &Y_i=\beta_1+\varepsilon_i\end{aligned}$

$$ \begin{array}{c|c}M_1 & M_0 \\[0.3em] Y_i\sim N(\beta_1+\beta_2x_i,\sigma^2),\text{ indipendenti} & Y_i\sim N(\beta_1,\sigma^2),\text{ indipendenti} \\[0.3em] \theta=(\beta_1,\beta_2,\sigma^2)\in\Theta=\R^2\cdot]0,+\infty[ & \theta_0=(\beta_1,\sigma^2)\in\Theta_0\cdot]0,+\infty[ \\[0.3em] L(\theta)=(\sigma^2)^{-n/2}\exp\{-\frac{1}{2\sigma^2} \sum(y_i-\beta_i-\beta_2x_i)^2\} & L_0(\theta_0)=(\sigma^2)^{-n/2}\exp\{-\frac{1}{2\sigma^2}\sum(y_i-\beta_1)^2\} \\[0.3em] \ell(\theta)=-\frac{n}{2}\log\sigma^2-\frac{1}{2\sigma^2}\sum(y_i-\beta_1-\beta_2x_i)^2 & \ell_0(\theta_0)=-\frac{n}{2}\log\sigma^2-\frac{1}{2\sigma^2}\sum(y_i-\beta_1)^2\end{array} $$

Test del log-rapporto di verosimiglianza $W_p=W_p(\beta_2)|_{\beta_2=0}=2[\ell(\hat{\beta}_1,\hat{\beta}_2,\hat{\sigma}^2)-\ell_0(\tilde{\beta}_1,\tilde{\sigma}^2)]$

Rifiutiamo i valori grandi di

\frac{rf}{}

Legame tra t_2 e R^2

\begin{aligned}R^2&=1-\frac{SQ_{res}}{SQ_{tot}}=1-\frac{\sum e^2_i}{\sum(y_i-\bar{y})^2}=\frac{\sum e_1^2}{\sum \tilde{e}_i^2}\\ &\frac{SQ_{reg}}{}\end{aligned}

Per n grande rifiuto sempre R^2; costruiamo quindi intervalli di confidenza

Previsioni

\hat{Y}_f=\hat{\beta}_1+\hat{\beta}_2x_f

E(Y|X=x_f)=\beta_1+\beta_2x_f

\hat{Y}_f\sim N(\mu_f,\frac{\sigma^2}{n})

\hat{Y}_f-Y_f=[\hat{Y}_f-\mu_f]+[\mu_f-Y_f]\sim N(0,\sigma^2+\frac{\sigma^2}{n}+\frac{(x_f-\bar{x})^2}{\sum(x_i-\bar{x})^2}\sigma^2)

Otteniamo \frac{}{}

Intervallo di previsione è

$\left[\hat{Y}_f-t_{n-2,1-\alpha/2}S\sqrt{1+\frac{1}{n}+\frac{(x_f-\bar{x})^2}{\sum(x_i-\bar{x})^2}}, \hat{Y}_f+t_{n-2,1-\alpha/2}S\sqrt{1+\frac{1}{n}+\frac{(x_f-\bar{x})^2}{\sum(x_i-\bar{x})^2}}\right]$

### Dimostrare le assunzioni

usiamo $\varepsilon_1,…,\varepsilon_n$

$\underbrace{Y_i}_{\text{osservazione}}=\underbrace{\beta_1+\beta_2x_i}_{\text{segnale}}+\underbrace{\varepsilon_i}_{\text{rumore}}$

$\varepsilon_i=y_i-\beta_1-\beta_2x_i$ ERRORI

$e_i=y_i-\hat{\beta}_1-\hat{\beta}_2x_i$ RESIDUI

Analisi dei residui $e_1,…,e_n=$ verifica delle assunzioni

**Proprietà algebriche** (residui come determinazioni di v.c.)

Sempre soddisfatte

1.  I residui hanno media nulla $\sum_{i=1}^n e_i=0$
    
    $\sum(y_i-\hat{\beta}_1+\hat{\beta}_2x_i)=\sum e_i=0$ se c’è $\beta_1$ (intercetta)
    
2.  I residui sono ortogonali alla variabile esplicativa $\sum_{i=1}^n x_ie_i=0$
    
    $\sum x_i(y_i-\hat{\beta}_1+\hat{\beta}_2x_i)=\sum x_i e_i=0$
    
3.  I residui sono ortogonali ai valori stimati $\sum_{i=1}^n\hat{y}_ie_i=0$
    
    $\sum\hat{y}_ie_i=(\hat{\beta}_1+\hat{\beta}_2x_i)e_i=\hat{\beta}_1\sum e_i\hat{\beta}_2\sum x_ie_i=0$
    
4.  $SQ_{res}=SQ_{tot}-SQ_{reg}$
    

**Proprietà stocastiche** (residui come v.c.)

Dipende dalle assunzioni

$e_i=Y_i-\hat{Y}_i=Y_i-\hat{\beta}_i-\hat{\beta}_2x_i$

$Cov(Y_i,\hat{Y} -i)\neq 0$

$e_i\sim$ normale

$\begin{aligned}E(e_i)&=E(Y_i-\hat{\beta}_1-\hat{\beta}_2x_i)\\ &=E(Y_i)-\beta_1-\beta_2x_i=0\end{aligned}$

$\begin{aligned}V(e_i)&=V(Y_i-\hat{Y}_i)=V(Y_i-\hat{\beta}_1-\hat{\beta}_2x_i)\\ &\underset{\hat{\beta}_1=\bar{Y}-\hat{\beta}_{\bar{x}}}{=}V(Y_i-\bar{Y}-(x_i-\bar{x})\hat{\beta}_2)\\ &=V(Y_i)+V(\bar{Y})+(x_i-\bar{x})^2V(\hat{\beta}_2)-2Cov(Y_i-\bar{Y})-2(x_i-\bar{x})Cov(Y_i,\hat{\beta}_2)+2(x_i-\bar{x})Cov(\bar{Y},\hat{\beta}_2)\\ &=\sigma^2+\frac{\sigma^2}{n}+(x_i-\bar{x})^2\frac{\sigma^2}{\sum(x_i-\bar{x})}-2\frac{\sigma^2}{n}-2(x_i-\bar{x})\frac{x_i-\bar{x}}{\sum(x_i-\bar{x})^2}\sigma^2 \\ &=\sigma^2\left(1-\frac{1}{n}-\frac{(x_i-\bar{x})^2}{\sum(x_i-\bar{x})}\right)\\ &=\boxed{\sigma^2(1-h_i)}\end{aligned}$

$\begin{aligned}\end{aligned}$No omoschedasticità

All’aumentare di n aumenta

Non è un errore di previsione

**Residui semplici**

$$ ⁍ $$

**Residui standardizzati**

$$ ⁍ $$

**Residui studentizzati**

$$ r_i=\frac{e_i}{S\sqrt{1-h_i}}\quad i=1,…,n\\ \Longrightarrow e_i, \varepsilon\text{ dipendenti}\\ \text{approssimativamente una normale standard} $$

Ipotesi

Strumenti grafici

Strumenti inferenziali

Linearità

⁍

⁍

Omoschedasticità

⁍

Test di Bartlett

Normalità

Densità-istogramma

Test ⁍ di conformità

**Verifica dell’omoschedasticità**

Test di Bartlett

$\bar{e}_i\sim N(0,\sigma^2_g)\text{ se }\bar{e}_i\in\mathcal{G}_g\quad\text{indipendenti, }g=1,…,G$

Rifiuto se le stime locali sono molto lontane dalla stima complessiva, quindi se $T_B^{OSS}>\Chi^2_{G-1;1-\alpha}$

T_B=\frac{n-G\ln S^2_p-\sum(n_g-1)\ln S^2_g}{1+\frac{1}{3(G-1)}(\sum\frac{1}{n_g-1}-\frac{1}{n-G})}

I gruppi decisi albitrariamente non devono essere nè troppo piccoli nè troppo grandi

Il test risente dell’assunzione di normalità, quindi si può rifiutare per quello e non per eteroschedasticità

Verifica della normalità

Confrontiamo l’istogramma dei residui standardizzati con la densità di N(0,1)

$-\infty=b_0<b_1<b_2<…<b_G \quad\leftarrow$ scelta arbitraria degli intervalli

nP_g>5

Funzione di ripartizione empirica

V v.c. con FdR F_V(v)

Osservazioni v_1,…,v_n

\Longrightarrow \hat{F}_n(v)=\frac{1}{n}\sum(V_i\leq v)

E(\hat{F}_n(v))=F_V(v) correttezza

V(\hat{F}_n(v))=\frac{1}{n}F_V(v)(1-F_V(v))underset{n\rightarrow +\infty}{\rightarrow} 0

Stimatore consistente

Test di Kolmogorov-Smirnov

$\Phi$ FdR di N(0,1)

$D_n=\sup|\hat{F}_n(v)-\Phi(v)|$

Osservazioni v_1,…,v_n

Ordinabile v_{(1)},v_{(2)},…,v_{(n)}

Se normalità $F(v_{(i)})\approx\hat{F}_n(v_{(1)})=\frac{1}{n}$

\Phi(\frac{v_{(1)}-\mu}{\sigma})=\frac{1}{n}

\frac{v_{(1)}-\mu}{\sigma}\approx\Phi^{-1}(\frac{1}{n})

(\Phi^{-1}(\frac{i-1/2}{n}),r_{(i)})

Se linea retta N(\mu,\sigma^2)

Se bisettrice N(0,1)

Linea retta di riferimento passa per i punti (\Phi^{-1}(0.25),Q_I),(\Phi^{-1}(0.75),Q_{III})

Distribuzione leptocurtica

Assimetria a destra

Test Shapiro-Wilk

$W=\frac{(\sum a_ir_{(i)})^2}{\sum r_i^2}$ regione di rifiuto $\{W^{OSS}<w_\alpha\}$

Non ci sono gruppi albitrari da decidere

## Ch4. Regressione multipla
Molte variabili esplicative $\begin{cases}\text{qualitative} \\ \text{quantitative}\end{cases}$
$Y_i=\gamma_1+\gamma_2x_{i2}+\varepsilon_i$
$X_{i3}=a_1+a_2x_{i,2}+\varepsilon_i$
$e_{Y|x_2}=\delta_1+\delta_2e_{X_3|x_2;i}+\varepsilon_i$

$Y_i=N(\beta_1x_{i1}+\beta_2x_{i2}+...+\beta_\rho x_{i\rho},\sigma^2)\qquad i=1,...,n\quad\text{indipendenti}$

Assunzioni
1. Linearità $\mu_i=\beta_1x_{i1}+...+\beta_\rho x_{i\rho}$
2. Omoschedasticità
3. Incorrelazione
4. Normalità

$\varepsilon\sim N(0,\sigma^2)\qquad\text{i.i.d.}\quad i=1,...,n$

5. Indipendenza lineare tra le variabili esplicative
$\left(\begin{matrix}x_{1j}\\ x_{2j}\\ \vdots\\ x_{nj}\end{matrix}\right)\qquad j=1,...,\rho$

Sono linearmente indipendenti

**Definizione**
Ogni volta $a_1,...,a_\rho$ non sono tutti nulli, $\varepsilon_{}$ ha $a_1x_1+a_2x_2+...+a_\rho x_\rho\neq 0$
___
C'è dipendenza lineare se esistono $a_1,...,a_\rho$ non tutti nulli tali che $a_1x_1+a_2x_2+...+a_\rho x_\rho=0$

$x_\rho=-\frac{a_1}{a_\rho}x_1-...-\frac{a_{\rho-1}}{a_\rho} x_{\rho-1}$
$$\left(\begin{matrix}\mu_1\\ \mu_2\\ \vdots\\ \mu_n\end{matrix}\right)\begin{aligned}=\mu&=\beta_1x_1+...+\beta_\rho x_\rho\\ &=\beta_1x_1+...+\beta_{\rho-1}x_{\rho-1}+\beta_\rho\left(-\frac{a_1}{a_\rho}x_1-...-\frac{a_{\rho-1}}{a_\rho}x_{\rho-1}\right)\\ &=\left(\beta_1-\frac{a_1}{a_\rho}\beta_\rho\right)\end{aligned}$$

IDENTIFICABILITA'
	Non deve essere possibile esprimere una v.e. come combinazione lineare di una o più 1altre v.e.
Non deve esserci correlazione perfetta (=1).

In pratica:
1) NO stessa v.e. espressa in diverse unità di misura
2) NO una v.e. somma di altre v.e.
	Se c'è intercetta non devono esserci variabili che sommano a 1
3) NO $\rho>n$

NO $x_i=c\quad i=1,...,n$
se succede $\rightarrow\hat{\beta}_2=\frac{0}{0}$ indetterminato

Forte (ma non perfetta) relazione lineare tra le esplicative: MULTICOLLINEARITA'
$\Longrightarrow$ Aumenta variabilità stime

$\beta_j=E(Y|X_j=a+1,\text{fissate altre v.e.})$
Variazione attesa

### Rappresentazione matriciale
$$\begin{array}{cccccc}\left[\begin{matrix}Y_1\\ Y_2\\ \vdots\\ Y_n\end{matrix}\right]&=&\left[\begin{matrix}x_{11}&x_{12}&...&x_{1\rho}\\ x_{21}&x_{22}&...&x_{2\rho}\\ \vdots&\vdots&&\vdots\\ x_{n1}&x_{n2}&...&x_{n\rho}\end{matrix}\right]&\left[\begin{matrix}\beta_1\\ \beta_2\\ \vdots\\ \beta_\rho\end{matrix}\right]&+&\left[\begin{matrix}\varepsilon_1\\ \varepsilon_2\\ \vdots \\ \varepsilon_n\end{matrix}\right]\\ Y&=&X&\beta&+&\varepsilon\\ (n\ \text{x}\ 1)&&(n\ \text{x}\ \rho)&(\rho\ \text{x}\ 1)&&(n\ \text{x}\ 1)\end{array}$$
$Cov(\varepsilon_i,\varepsilon_j)=0\quad\forall\ i,j=1,...,n$

$X=\underbrace{[x_1\ x_2\ ...\ x_\rho]}_{\text{colonne indip. linearmente}}$

Stima dei parametri
$$S(\beta)=(y-X\beta)^T(y-X\beta)$$
$\hat{\beta}=\text{argmin}\  S(\beta)=\text{argmax}\ \ell(\beta,\sigma^2)$

Stima dei minimi quadrati
Stima della massima verosimiglianza

### Stima di $\beta$
$S(\beta)=y^Ty-2y^TX\beta+\beta^TX^TX\beta$
$\frac{\partial S(\beta)}{\partial\beta}=-2y^TX+2\beta^TX^TX\beta$

Ponendo $\frac{\partial S(\beta)}{\partial\beta}=0$ si ottengono _equazioni normali_
$(X^TX)\beta=X^Ty$

In virtù della disequazione di indipendenza lineare tra le variabiliesplicative, si ha che $x_\alpha\neq 0$ ogniqualvolta $\alpha\neq 0$.
Quindi $x^Tx$ 
Solo se $X^TX$ è invertibile
$$\boxed{\hat{\beta}=(X^TX)^{-1}X^Ty}$$
### Stima di $\sigma^2$
$\ell(\hat{\beta},\sigma^2)=-\frac{n}{2}\log(\sigma^2)-\frac{1}{2\sigma^2}(y-X\hat{\beta})^T(y-X\hat{\beta})=-\frac{n}{2}\log(\sigma^2)-\frac{1}{2\sigma^2}S(\hat{\beta})$

Massimi
$\ell(\hat{\beta},\sigma^2)=-\frac{n}{2}\log\sigma^2-\frac{1}{2\sigma^2}\sum e_i^2$
$(y-X\hat{\beta})^T()=()^T()$
$e^Te=\sum e_i^2$

Caso particolare: regressione lineare semplice
$$\begin{array}{cccccc}\left[\begin{matrix}Y_1\\ Y_2\\ \vdots\\ Y_n\end{matrix}\right]&=&\left[\begin{matrix}1&x_1\\ 1&x_2\\ \vdots&\vdots\\ 1&x_n\end{matrix}\right]&\left[\begin{matrix}\beta_1\\ \beta_2\end{matrix}\right]& +&\left[\begin{matrix}\varepsilon_1\\ \varepsilon_2\\ \vdots \\ \varepsilon_n\end{matrix}\right]\\ Y&=&X&\beta&+&\varepsilon\\ (n\ \text{x}\ 1)&&(n\ \text{x}\ 2)&(2 \text{x}\ 1)&&(n\ \text{x}\ 1)\end{array}$$ Quindi la trasposta
$X^TX=\left[\begin{matrix}1&...&1\\ x_1&...&x_n\end{matrix}\right]\left[\begin{matrix}1&x_1\\ 1&x_2\\ \vdots&\vdots\\ 1&x_n\end{matrix}\right]=\left[\begin{matrix}n&\sum x_i\\ \sum x_i&\sum x_i^2\end{matrix}\right]$

con determinante $|X^TX|=n\sum x_i^2-(\sum x_i)^2=n\sum x_i^2-n^2\bar{x}^2$
$(X^TX)^{-1}=$

Si ha la stessa soluzione dellla regressione lineare.

Modello solo intercetta
$Y_i=\beta_i+\varepsilon_i\quad i=1,...,n$
$$\begin{array}{cccccc}\left[\begin{matrix}Y_1\\ Y_2\\ \vdots\\ Y_n\end{matrix}\right]&=&\left[\begin{matrix}1\\ 1\\ \vdots\\ 1\end{matrix}\right]&\beta_1& +&\left[\begin{matrix}\varepsilon_1\\ \varepsilon_2\\ \vdots \\ \varepsilon_n\end{matrix}\right]\\ Y&=&X&\beta&+&\varepsilon\\ (n\ \text{x}\ 1)&&(n\ \text{x}\ 1)&(1)&&(n\ \text{x}\ 1)\end{array}$$La trasposta è $X^TX^{-1}=\frac{1}{n}$
$X^Ty=[1\ ...\ 1]\left[\begin{matrix}Y_1\\ Y_2\\ \vdots\\ Y_n\end{matrix}\right]=\sum y_i$
$(X^TX)=1$


Risultati
$$\hat{y}=\hat{\mu}=X\hat{\beta}=X(X^TX)^{-1}X^Ty=Py$$
La matrice $P_{(1\text{x}1)}=X(X^X)^{-1}X^T$ è chiamata _matrice di proiezione_
- $P^TP=P$ è simmetrica
- $P\cdot P=P$ è idempotente

Il vettore dei residui è $$e=y-\hat{y}=(I-P)y$$$X^T_{(p\text{x}n)}e_{(n\text{x}1)}=0_{(\rho\text{x}1)}$

Se il modello ha intercetta i residui sommano a 0
$\Longrightarrow x_{i1}=1\quad i=1,...,n$
$Cov(e,x_j)$

Devianza
$SQ_{tot}=\sum(y_i-\bar{y})^2$

Prendiamo prima in considerazione $\sum y_i^2=y^Ty$
$\begin{aligned}y^Ty&=y^T(P+I+P)y\\ &=y^TPy+y^T(I-P)y\\ &=y^TP^TPy+y^T(I-P)^T(I-P)y\\ &P,I\cdot P\text{ simmetr e idepot}\\ &=\end{aligned}$

---
$\begin{array}{ccccc}\sum(y_i-\bar{y})^2&=&2(\hat{y}_i-\bar{y})^2&+&\sum e_i^2\\ SQ_{tot}&=&SQ_{reg}&+&SQ_{res}\\ \text{dev. tot}&=&\text{dev. spiegata}&+&\text{dev. residua}\end{array}$

Se c'è intercetta
$R^2=\frac{SQ_{reg}}{SQ_{tot}}=1-\frac{SQ_{res}}{SQ_{tot}}$
Confronta l'adattamento tra i modelli annidati
Il modello con intercetta è un sottoinsieme del modello totale

Se non c'è intercetta, può succedere che $SQ_{res}>SQ_{tot}$ fornendo un $R^2$ negativo.

---
Formula alternativa per la somma dei quadrati dei residui
$$e^Te=y^Ty-(X\hat{\beta})^Ty$$
Varianza dei residui
$$V(e)=\sigma^2(1-P)$$
1. Residui standardizzati $\hat{e}_i=\frac{e_i}{\sqrt{1-p_{ii}}}$
2. Residui studentizzati $r_i=\frac{e_i}{S\sqrt{p_{ii}}}$

**Teorema di Gauss-Markov**
$$\hat{\beta}=\underset{{\beta}}{\text{argmin}}(y-X\beta)^T(y-X\beta)$$
1. $Y=X\beta+\varepsilon$
2. $E(\varepsilon)=0$ e $V(\varepsilon)=\sigma^2I$

Sotto le assunzioni di secondo ordine il $\hat{\beta}$ è uno stimatore lineare e corretto di $\beta$, quindi $V(\hat{\beta})\geq V(\beta)$
nel senso che $V(\hat{\beta})$

Distribuzione di $\hat{\beta}$
$Y\sim N_n(\mu,\sigma^2I)$
$n\hat{\sigma}^2=e^Te=((I-P)Y)^T(I-P)Y=Y^T(I-P)Y$
Rango di $I-P$?
Serve per i gradi di libertà
$E_r(I_n-P)=n-p$
$$\frac{n\hat{\sigma}^2}{\sigma^2}=\frac{e^Te}{\sigma^2}\sim\chi^2_{n-p}$$
$\hat{\beta}_\sim-\beta_\sim=(x^Tx)^{-1}x^Ty_{\sim}$

Test t di Student 2 campioni
$Y_i^A\sim N(\mu_A,\sigma^2)\quad i=1,...,n_A$
$Y_j^B\sim N(\mu_B,\sigma^2)\quad j=1,...,n_B$


Analisi post-hoc
$H_0:\mu_A=\mu-B=\mu_C$

Quando fai test multipli c'è la probabilità di sbagliare in almeno uno di quelli.
Correzione di Bonferroni $<\alpha$

ANOVA a 2 fattori
1. Effetto del primo fattore (veleno)
2. Effetto del secondo fattore (antidoto)
3. Effetto del primo fattore (veleno) condizionatamente all'effetto del secondo valore (antidoto)
4. Effetto del secondo fattore (antidoto) condizionatamente all'effetto del primo valore (veleno)
5. Interazione tra i fattori (antidoto e veleno)
	Si dice che c'è interazione tra i due fattori se l'effetto condizionato di un fattore cambia a seconda del livello (modalità) dell'altro fattore a cui mi condiziono

$\left.\begin{aligned}1.\ (sopravvivenza)&=f(veleno)+(errore)\\ 2.\ (sopravvivenza)&=g(antidoto)+(errore)\end{aligned}\right\}\text{ANOVA a 1 fattore}$
$3.\ (sopravvivenza)=f(veleno)+g(antidoto)+(errore)$
$4.\ (sopravvivenza)=f(veleno)+g(antidoto)+h((veleno)\cdot(antidoto))(errore)$
$\alpha\begin{cases}0&\text{se alla i-esima cavia viene somministrato l'antidoto}\\1&\text{altrimenti}\end{cases}$
