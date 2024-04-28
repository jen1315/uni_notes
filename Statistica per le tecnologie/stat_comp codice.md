## Ch1. Generazione variabili casuali
>💡**Obiettivo**: generale una sequenza di number (pseudo)-casuali indipendenti con distribuzione $f(\cdot)$.

#### 1.1 Variabili (pseudo-)causali uniformi
I calcolatori non riescono a generare valori totalmente casuali (sono perfettamente prevedibili). Possiamo simulare la casualità.

Simulare numeri casuali uniformemente distribuiti in $[0,1]$:

**Algoritmo congruenziale**
$$x_{i+1}=(ax_i+b)\mod m$$
```r
# mod = %% (resto)
generan -> function(n, x0, a, b, m) {
	x = rep(NA,n)
	x[1] = x0
	for(i in 2:n) {
		x[i] = (a*x[i-1]+b)%%m
	}
	return(list(int=x,unif=x/m))
}
```

$x_0$ seed del generatore

1.  Se $x_i=x_0$ la sequenza si ripete
2.  La sequenza è quindi periodica, il periodo è massimale ($m$)
3.  L’algoritmo sarà efficace se dobbiamo generare un numero di osservazioni minori del periodo

**Algoritmo di Wichmann-Hill del 1984**

Combina 3 generatori congruenziali.
$$\begin{aligned}x_1=(171\cdot x_{i-1})&\mod 30269 \\ y_1=(172\cdot y_{i-1})&\mod 30307 \\ z_i=(170\cdot z_{i-1})&\mod 30323\end{aligned}\qquad u_i=(\frac{x_i}{m_x}+\frac{y_i}{m_y}+\frac{z_i}{m_y})\mod 1$$
```r
.current.seed <- c(123,456,789) # scelta albitraria
runif.wh <- function(n) {
	a = c(171,172,170)
	b = c(30269,30307,30323) # 3 numeri primi
	s = .current.seed
	u = rep(0,n) # pre-allocazione è più efficiente
	for(i in 1:n) {
		s = (a*s)%%b
		u[i] = sum(s/b)%%1
	}
	.current.seed <<- s
	u
}
```

#### 1.2 Distribuzioni di v.a.
**Algoritmo di inversione**
Sia $F(\cdot)$ una FdR invertibile

-   $U\sim \text{Unif}(0,1)$
-   $F^{-1}:[0,1]\rightarrow\mathbb{R}$

Allora la v.a. $Y=F^{-1}(U)$ ha FdR $F(\cdot)$

**Algoritmo accetta/rifiuto**
$f(\cdot)$ nota, densità obiettivo
$g(\cdot)$ nota da cui riesco a generale, densità delle proposte

1.  Trovo una $k$ tale che $k\cdot g(x)\geq f(x)\quad\forall\ x$
2.  Genero $x$ da $g$
3.  Genero $u$ da $U(0,k\cdot g(x))$
4.  Se $u\leq f(x)$ accetto $x$ come valore generato da $f$, altrimenti rifiuto e riparto dal punto 2.

```r 
r.acc.rif <- function(n, f, g, rg, k, report=TRUE){
	y <- double(n)
	ntry <- 0
	for (i in 1:n){
	    done <- FALSE
	    while (!done){
		    ntry <- ntry + 1
		    z <- rg(1)
		    u <- k * g(z) * runif.wh(1)
		    if (u <= f(z)) done <- TRUE
		}
		y[i] <- z
	}
	if (report)
		cat("tentativi: ", ntry)
		y
}
```

## Ch2. Applicazioni
#### 2.1 Integrazione
**Monte Carlo**
1. Generare $n$ numeri casuali $y_i$ in distribuzione $f(\cdot)$
	`y <- f(runif(n))`
2. Fare la media di $y_i$
	`ybar <- mean(y)`

#### 2.2 Teorema del limite centrale
> **Obiettivo**: calcolare approssimazioni di $\psi_{\text{qualcosa}}(n,\alpha,f)$, la bontà di adattamento del TLC.

Funzione che simula $t_n$
```r
# rf: funzione generatrice
# mu: vera media
# B: n. replicazioni di Tn da simulare
molte.t <- function(n, rf, mu, B=10000) {
    y <- matrix(rf(n*B), n, B)
    ybar <- apply(y, 2, mean)
    s <- apply(y, 2, sd)
    sqrt(n)*(ybar-mu)/s
}
```

Funzione per le stime di $\psi_{\text{qualcosa}}$
```r
conta.r <- function(n, rf, mu, B 10000, alpha=c(0.01, 0.05, 0.1)) {
    tn <- molte.t(n, rf, mu, B)
    
}
```

> Stima della media e della varianza di una v.c. normale quando il campione è "contaminato".


#### 2.3 Test multipli
Secondo Wald
Secondo Wilks
#### 2.4 Aumento di efficienza
**Campionamento di importanza**

`f(x)/psi(x)`

**Variabili casuali antitetiche**

**Metodo Rao-Blackwell**


## Ch3. Bootstrap
- Non conosciamo la distribuzione $F$ di $Y$
- Ci sono casi in cui vogliamo evitare ipotesi parametriche, quindi oltre ad essere ignoti i parametri, è ignota pure la distribuzione

#### 3.1 Generalità
**Bootstrap non parametrico**: La distribuzione $\bar{Y}^*|\hat{F}_n$ è il "corripondente bootstrap" della distribuzione di $\bar{Y}|F$.
1. a) simuliamo $B$ campioni da $\hat{F}_n$, quindi mediante estrazioni con reinserimento da $y_1,...,y_n$ (FdR empirica)

	```r 
	# trunc, rimuove tutto ciò che c'è dopo la virgola
	trunc(runif(B, 1, n+1)))
	floor(1+n*runif(n))
	
	# la funzione di ripartizione empirica con 
	# probabilità 1/n per ogni yi è
	y.bts <- y[trunc(runif(n, 1, n-1))]
	```

**Bootstrap parametrico**: La distribuzione $\bar{Y}^*|N(\bar{y},s^2)$ è il "corrispondente bootstrap" della distribuzione di $\bar{Y}|F$.
1. b) simuliamo $B$ campioni di numerosità $n$ da $N(\bar{y},s^2)$
	`y.bts <- rnorm(n, y.bar, sqrt(s2))`

2. calcoliamo $\bar{Y}$ e $Q$ su ciascun campione simulato, ottenendo $\bar{Y}_1^*,...,\bar{Y}_B^*\quad Q_1^*,...,Q_B^*$
	`ybar.bts <- replicate(B, mean(y.bts))`
3. usiamo questi ultimi come surrogati delle distribuzioni teoriche

La distribuzione risultante non sempre rappresenta bene la vera distribuzione (soprattutto quando ci sono poche $n$ osservazioni).

Distorsione media $\text{bias}_B=E(\bar{Y}^*|\hat{F}_n)-\hat{y}$
`mean(ybar.bts)-y.bar`
Distorsione varianza $\text{bias}_B=E(\sigma^2|F)-\sigma^2=\frac{n-1}{n}\sigma^2-\sigma^2$
```r
shat.bts <- sapply(rep(n, B), FUN = function(n, y) {
	x = y[trunc(runif(n, 1, n+1))]
	mean(x^2)-mean(x)^2
}, y=y)
s.hat <- mean(y^2)-mean(y)^2
mean(shat.bts)-s.hat # distorsione
```

#### 3.2 Regressione con Bootstrap
Punto di equilibrio E tale che con $X=E$, allora in media $Y=E$
$E=\beta_1+\beta_2E$
```r
equilibrio <- function(d) {
	beta <- coef(lm(I(d[,"y"])~I(d[,"x"])))
	(1-beta[2])/beta[1]
}
```

Trova l'errore di stima di E.
$E=\theta\qquad\frac{\sum\hat{\theta}_i^*}{B}=\hat{\theta}$  Vero parametro in bootstrap

```r
rE.hat <- function(ross, B=1000) {
	sapply(rep(1,B), function() equilibrio(ross()))
}
n <- NROW(d)
mean(rE.hat(ross()))-equilibrio(d)
```

**Soluzione completamente non parametrica**
Con bootstrap non parametrico, devo campionare a coppie $x,y$
```r
ross.np <- function() {
	index <- floor(1+n*runif(n))
	d[index,]
}
```

**Soluzione semi-parametrica**
$$Y_t^*=\left(\hat{\beta}_1+\hat{\beta}_2\frac{1}{X_t}+\varepsilon_t^*\right)^{-1}$$
- la soluzione è semi-parametrica perché non facciamo assunzioni sulla distribuzione di $\varepsilon$, ma ne facciamo sulla relazione tra $A_t\text{ e }G_t$
```r
res <- residuals(m)
ross.sp <- function() {
	index <- floor(1+n*runif(n))
	d.new <- d
	d.new[,"y"] <- 1/(beta[1]+beta[2]/d[,"x"]+res[index])
	d.new
}
```

**Soluzione completamente parametrica**
Uguale alla soluzione semi-parametrica ma assumiamo che
- $\varepsilon$ ha distribuzione $\mathbb{N}(0,s^2)\qquad s^2=\frac{\sum e_i^2}{n-2}$
```r
sigma <- sqrt(sum(res^2)/(length(res)-length(beta)))
ross.par <- function() {
	d.new <- d
	d.new[,"y"] <- 1/(beta[1]+beta[2]/d[,"x"]+sigma*rnorm(n))
	d.new
}
```

Intervallo di confidenza
$\hat{\theta}^*-\hat{\theta}$
$P(\hat{\theta}-q_{\alpha/2}\leq\theta\leq \hat{\theta}-q^*_{1-\alpha/2})\approx 1-\alpha$

approccio con stime bootstrap
$q_{\alpha/2}^*=q_{\alpha/2}^{*'}$
$[2\cdot\hat{\theta}]$

Quantità studentizzata 
$T^*=\frac{\hat{\theta^*}-\theta}{\hat{\sigma}^*}$
Bootstrap su bootstrap 
Non conosciamo $\hat{\sigma}$
$\begin{array}{ccc}y_1,&...,&y_n\\ (y_1^*,...,y_n^*)_1,&...,&(y_1^*,...,y_n^*)_B\\ \hat{\theta}^*\end{array}$
Bootstrap dentro bootstrap
Metodo delta

##### Generazione conoscendo la correlazione
$\hat{\rho}-\rho$ Distribuzione assimmetrica a sx, a dx oppure simmetrica a seconda del valore di $\rho$
$r=\hat{\rho}$ coefficiente di correlazione

- per due variabili casuali incorrelate $X, U$
$$Y=\rho X+\sqrt{1-\rho^2}U\qquad (-1<\rho<1)$$
```r
rbivnorm <- function(n, rho) {
	x <- rnorm(n)
	cbind(x, rho*x+sqrt(1-rho^2)*rnorm(n))
}
dati <- rbivnorm(n, vero.rho)
```

Calcolare r-p con Monte Carlo 
```r
rrho <- function(dati, B=10000) {
	cor(dati[,1], dati[,2])
	sapply(rep(n,B), un.rho)
}
```

Calcolare r-p con bootstrap
```r
cor.boot <- function(dati, B=10000) {
	n <- nrow(dati)
	for(i in 1:B) {
		idx <- floor(1+n*runif(n))
		r[i] <- cor(dati[idx,1], dati[idx,2]))
	}
	r
}
```
## Ch4. Applicazioni bootstrap
### 4.1 Verifica di ipotesi
>💡**Obiettivo**: Con osservazioni indipendenti tra loro
>- $x$ determinazioni di v.a. $X\sim F_X(\cdot)$ con $\mu_X$
>- $y$ determinazioni di v.a. $Y\sim F_Y(\cdot)$ con $\mu_Y$
>
>Verifichiamo $H_0:\mu_X=\mu_Y$ contro $H_1:\mu_X\neq\mu_Y$

**Test di Welch**
- robustezza se $r^2_x\neq r^2_y$ (cade l'assunzione di omoschedasticità)
- potenza è di poco inferiore a quello del test t di Student tradizionale (anche se è vera l'omoschedasticità)
`t.test(x, y)`

Con numerosità campionarie molto piccole, risultati asintotici sulla distribuzione non hanno senso.
Nei test tradizionali assumiamo la normalità dei valori; quindi una analisi alternativa è capire quanto il test $t$ dipende da questa assunzione.
$$T=\frac{\bar{X}-\bar{Y}}{\sqrt{\frac{S^2_x}{n_x}+\frac{S^2_y}{n_y}}}$$
Il livello di significatività osservato è $lso=P_{H_0}(|T|\geq|t_{dati}|)$
```r
tstat <- function(x, y) (mean(x)-mean(y))/sqrt(var(x)/nx+var(y)/ny)
```

### 4.2 Bootstrap lisciato
Dato $Y_1,...,Y_n$ di variabili casuali i.i.d. con funzione di ripartizione $F$, lo stimatore empirico di $F$ è $$\hat{F}_n(y)=\frac{1}{n}\sum_{i=1}^n\mathbb{I}(Y_i\leq y)$$ dove $\mathbb{I}$(evento) vale 1 se è vero e 0 altrimenti. Questa è la FdR empirica del bootstrap non parametrico.

Lo stimatore della densità di $F$ $$\begin{aligned}\hat{f}(y)&=\frac{\hat{F}_n(y+h)-\hat{F}_n(y-h)}{2h} \\ &=\frac{1}{nh}\sum_{i=1}^n K\left(\frac{y-Y_i}{h}\right)\end{aligned}$$dove $h$ è il parametro di lisciamento e determina la distanza tra le osservazioni e $K$ è una funzione di densità qualsiasi
```r
library(sm)
h.select(y, method="cv")
h <- h.select(y, method="sj")
# decidiamo h non troppo grande nè troppo piccola
sm.density(y, h=h)
```

**FdR lisciata** $$\hat{F}(y)=\frac{1}{n}\sum\phi\left(\frac{y-y_i}{h}\right)$$ dove $\phi(\cdot)$ è la funzione di ripartizione normale standard
```r
pnucleo <- function(x, y, h) {
	# outer, operazione tra vettori
	a <- outer(x, y, "-")/h
	apply(pnorm(a), 1, mean)
}
```

**Generazione valori con bootstrap lisciato**
```r
rnucleo <- function(n, y, h) {
	ny <- length(y)
	idx <- floor(1+ny*runif(n))
	y[idx]+h*rnorm(n)
}
```

**Quantile**
$q_{1-\alpha}$ ignoto $\rightarrow$ Bootstrap

```r
yb <- matrix(rnucleo(n*B, y, h), n, B) 
q10.boot <- apply(yb, 2, function(x) quantile(x,0.1))
```
Stimatore con distorsione (non a media 0)

```r
dist <- mean(q10.boot)-q10.stima
quantile(y, 0.1)-dist
```
Stimatore "corretto"

Intervallo di confidenza unidirezionale destro
$\begin{aligned}P(\hat{\theta}-\theta<q_{1-\alpha}^*)\approx 1-\alpha\\ P(\underbrace{\hat{\theta}-q_{1-\alpha}^*}_{a(y)}<\theta)\approx 1-\alpha\end{aligned}$

$a(y)=\hat{\theta}-q^*_{1-\alpha}=2\cdot\hat{\theta}-q^{*'}_{1-\alpha}$
`2*quantile(y, 0.1)-quantile(q10.boot, 0.95)`

## Ch5. Ottimizzazione
### 5.1 SMV
SMV, soluzione numerica rispetto un'unica variabile
```r
# llik, funzione log-verosimiglianza
# campione, vettore di osservazioni
optimize(llik, y=campione, interval=c(0,5), maximum=TRUE, tol=1E-5)
```
Gli argomenti obbligatori di **`optimize`** 
- `f`, funzione obiettivo (llik in questo caso)
- `interval`, intervallo su cui compiere la ricerca
Ritorna il punto di massimo e il valore della funzione in tale punto.

**Intervalli di confidenza**
Wilks $I(\lambda)-I(\hat{\lambda})$ e Wald $I_2(\lambda)-I_2(\hat{\lambda})$
```r
# g, funzione IC
# smv.es, stimatore
ris.low <- optimize(g, lower=0, upper=smv.es, campione=campione)
ris.up <- optimize(g, lower=smtv.es, upper=5, campione =campione)
```

### 5.2 SMV con due parametri
```r
# ll, funzione log-verosimiglianza
# devo passare i parametri come un vettore
ll <- function(t, y) ...
t1.seq <- ... # parametro 1

z <- matrix(NA, 50, 50)
for(i in 1:50) {
	for(j in 1:50) {
		z[i,j] <- ll(c(t1.seq[i],t2.seq[j]),y)
	}
}
```

Rappresentazione grafica
```r
range(z)
contour(t1.seq, t2.seq, z, levels=seq(-3000,-1000,length=100))

# automatico ma non equispaziato
livelli <- quantile(z, prob=c(0.5, 0.7, 0.8, seq(0.9,1,by=0.01)))
contour(t1.seq, t2.seq, z, levels=livelli)
```

**Soluzione numerica: `optim`**
```r
nll <- function(t, y) -ll(t,y)

# optim$convergence = 0 quando è un successo
ris <- optim(fn=nll, par=c(1,1), y=y)
```
Gli argomenti obbligatori di **`optim`** sono 
- `fn`, funzione obiettivo
	Il campione viene passato con il nome in cui compare in `fn`
- `par`, valori di partenza

**Soluzione numerica: `nlm`**
```r
# nlm$code = 1 gradiente vicino a 0
# nlm$code = 2 al di sotto della tolleranza 

ris.nlm <- nlm(f=nll, p=c(1,1), y=y)
```

**Informazione osservata**
```r
# con hessian=TRUE, optim e nlm restituiscono anche la matrice hessiana
ris <- optim(fn=nll, par=c(1,1), y=y, hessian=TRUE)
vcov <- solve(ris$hessian) # matrice inversa
```

Regione di confidenza
$$\{\theta:(\hat{\theta}-\theta)'\Sigma^{-1}(\hat{\theta}-\theta)\leq\chi^2_{1-\alpha,2}\}$$
```r
liv.conf <- 0.9
theta.hat <- c(alfa.hat, mu.hat)
for(i in 1:50) {
	for(j in 1:50) {
		theta <- c(t1.seq[i], t2.seq[2])
		zn[i,j] <- t(theta.hat-theta) %*% solve(vcov) %*% (theta-theta)
	}
}
```

### 5.4 Tempi di guasto
Distribuzione di Weibull
Densità $$f(y;\alpha,\beta)=\frac{\beta}{\alpha}\left(\frac{y}{\alpha}\right)^{\beta-1}e^{-(y/\alpha)^\beta}$$FdR $\qquad F(y;\alpha,\beta)=1-e^{-(y/\alpha)^\beta}$

Log-verosimiglianza $$I(\alpha,\beta)=\sum_{i=1}^n[\log(\beta/\alpha)+(\beta-1)\log(y_i/\alpha)-(y_i/\alpha)^\beta$$
```r
dweib <- function(y, alpha, beta) {
	beta/alpha*(y/alpha)^(beta-1)*exp(-(y/alpha)^beta)
}
wei.loglik <- function(y, alpha, beta) {
	sum(log(beta/alpha)+(beta-1)*log(y/alpha)-(y/alpha)^beta)}
```

**SMV, riparametrizzazione**
$\alpha,\beta$ sono parametri positivi; imponiamo vincoli cosicché l'algoritmo non estenda la sua ricerca fuori dallo spazio parametrico

```r
lp[1] <- log(alpha)
lp[2] <- log(beta)

wei.nll.rip <- function(lp)
	-wei.loglik(y,exp(lp[1]),exp(lp[2]))
```

senza riparametrizzazione, `nlminb`
```r
wei.nll <- function(lp)
	-wei.loglik(y,lp[1],lp[2])

nlminb(objective=wei.nll, start=log(start))
```

nlminb non calcola la matrice hessiana
```r
library(nlme)
H <- fdHess(par, function(par) wei.loglik(y,par[1],par[2]))
```

**Intervallo di confidenza**

Verosimiglianza profilo

## Regressione non parametrica
$Y_i=m(x_i)+\varepsilon_i\qquad$ quindi $\qquad E(Y_i|X=x_i)=m(x_i)$

**Regressione spline**
```r
# df, grado di lisciamento, strettamente >1
spline.regression <- function(x, y, df=6, veal.points=seq(min(x),max(x)), lenght=100, deriv=0, display=T, add=F, ...) {
	m <- smooth.spline(x, y, df=df)
	estimate <- predict(m, eval.points, deriv=deriv)$y
	# rappresentazione grafica
	if(add=TRUE) { 
		lines(eval.points, estimate, ...) 
	}else if(display!="none") {
		if(deriv==0) {
			plot(x, y, main="spline.regression", xlab=substitute(x), 
			ylab=substitute(y), cex=0.5)
			lines(eval.points, estimate, col="red", ...)
		} else {
			plot(eval.points, estimate, type="l", main="spline.regression", 
			xlab=substitute(x), ylab=paste("D(",substitute(y),",",deriv,")", 
			sep=""))
		}
	}
	invisible(list(eval.points=eval.points, estimate=estimate, df=df, m))
}
```

$h$ piccolo $\rightarrow$ non liscio
$h$ grande $\rightarrow$ liscio
```r
# df strettamente >2
sm.regression(x,y,df)
```

### 6.3 Scelta di df (grado di lisciamento)
Convalida incrociata (**cross-validation**) $$s^2_{CV}(\text{df})
=\frac{1}{n}\sum_{i=1}^n[y_i-\hat{m}_{-i}(x_i;\text{df})]^2$$
```r
errgenstim <- rep(NA,49)
for(df in 2:50) {
	errore <- 0
	for i in 1:n {
		fit <- spline.regression(x[-i],y[-i],df=df, display="none",eval.points=x[i])
		errore <- errore+(y[i]-fit$estimate)^2
	}
	errgenstim[df-1] <- errore/length(x)
}
```
