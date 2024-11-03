“Appunti di programmazione ad oggetti” Francesco Ranzato
Esame scritto + Progetto

Un programma è costituito da
- Algoritmi
- Dati su cui operano gli algoritmi

Focus su **algoritmi** (*programmazione procedurale*)
Focus su **dati** (*programmazione ad oggetti*)

Qualità del software
- verificabile
- mantenibile <-
- riparabile <-
- riutilizzabile <-
- portabile

Un linguaggio si dice oggetti quando ha le 3 seguenti caratteristiche
INCAPSULAMENTO, un programma può essere usato dentro un altro
EREDITARIETÀ, un programma può ereditare le funzioni di un altro
POLIMORFISMO, la chiamata di funzione si basa a runtime

**Template** per programmazione generica, ovvero indipendente del tipo delle variabili. Si gestiscono le eccezioni.

C++
- compilato
- tipizzazione forte statica
- no garbage collector
- standardizzato
- efficiente
- operatori e il loro overloading

Java
- interpretato, portatile
- forte orientamento agli oggetti, semplice e familiare
- robusto e sicuro
- dinamico
- processi thread e porte

``` c++
#include <iostream.h>
using namespace std;

int main() {
	cout << "Hello world!" << endl;
}
```
`#` direttiva del pre-processore
`main` alla base del code stack
`<<` operatore di output
``` c++
#include <iostream.h>

int main() {
	std::cout << "Hello world!" << std::endl;
}// preferibile
```

**Namespace**
Quando due variabili hanno lo stesso nome, li possiamo distinguere dal loro scope.
``` c++
namespace ns_name{
	struct X;
}
```
Alias di namespace 
``` c++
namespace alias = ns_name;
```
Direttiva di uso 
``` c++
using namespace ns_name;
```
Dichiarazione di uso
``` c++
using ns_name::X;
```

Invocazione compilatore `> gcc -xc++`

#### Stringa
Array di caratteri
``` c++
char *str = "ecco una stringa c"; // automaticamente aggiunge /0
const char *st_c = "hello"; // a solo lettura

for(int i=0; *(str+i); i++)
```

Classe stringa (istantazione di templare di classe `typedef basic_string<char> string`)
``` c++
#include <string>

int main() {
	string str = "ecco una stringa c++";
	int length = str.size();
}
```

Un tipo di dato viene detto **astratto** (ADT), quando la sua semantica è separata dalla sua implementazione. La sua rappresentazione interna è inaccessibile.
ADT = Valori + Operazioni (metodi pubblici)

Struct non è un ADT, tutto è accessibile.

>Principio dell’*Information Hiding*
>Metodo progettuale di segregazione delle informazioni che hanno più possibilità di cambiare in modo da proteggere le altre parti del programma da modifiche estensive quando viene cambiato il design

Classe implementa gli ADT. La dichiarazione di classe consiste da
- campi dato
- metodi, funzione di una classe, uno di loro è costruttore

``` c++
 class orario {
  private:  // specificatore di accesso
	short int seconds;
	
  public:
	orario();
	orario(short int o, short int m=0, short int s=0);
	short int Ore();
	short int Minuti();
	short int Secondi();
	// hanno un argomento implicito oggetto di invocazione del metodo
	
	orario::orario() {
		sec = 0;
	}
	
	orario::orario(short int o, short int m, short int ) {
		if(o<24 && m<60 && s<60) {
			sec = s + m*60 + o*3600;
		}
	}
	
	short int orario::Ore() {
		return sec / 3600;
	}// preferibile scritta separatamente dalla dichiarazione perché sarebbe inline e potrebbe essere interpretata come macro
	
	short int orario::Minuti() {
		return (sec / 60) % 60;
	}
	
	short int orario::Secondi() {
		return sec % 60;
	}
	
	int main() {
		orario o1;
		orario o2(15, 30, 15);
		orario o3 = orario(14, 20, 05); // costruttore di copia
		orario *ptr = new orario; // new è la malloc di C++
	}
};
```
Le diverse istanze di oggetti sono salvati individualmente mentre i metodi sono salvati una sola volta.
Oggetto di invocazione e metodo invocato sono legati dal parametro implicito `*C this`.

**Costruttore di Copia** `C(const T&)`
`orario o = orario(14, 20, 5);`
crea una istanza di oggetto anonimo e temporaneo (senza l-valore) che viene poi assegnato a un oggetto.

N.B. Diverso da `o = orario(14, 20, 5);` che è solo una assegnazione
``` c++
orario copia1 = o;
orario copia2(o); // preferibile
```

**Costruttore Standard**
quando non definiamo un costruttore, è già presente uno standard di default. Se definiamo un costruttore con argomenti, `orario o;` non è più un codice valido.

COMPCERT Xavier Lerox (compilatore ottimizzato che ritorna prova matematica)

new e delete in C++
malloc e free in C

**Argomenti di default**
`funzione func(int a, int b = 0, int c = 0);`
Tutti gli argomenti a destra di quello con default devono avere default.

**Conversione Implicita**
``` c++
orario s,t;
s = 8;    // equivale a s = orario(8);
t = 8+12; // equivale a t = orario(8+12);
```
Quando una variabile non è dello stesso tipo dell’oggetto a cui è assegnato, avviene una conversione implicita dove viene convertito in un oggetto ammissibile.

**Operatori Espliciti di Conversione**
``` c++
class orario {
public:
	operator int() {return sec;}
	. . .
}
orario o(12, 25);
int s = o; // richiama implicitamente int() su o
```
`explicit` blocca le conversioni implicite, utile quando non hanno senso.

Metodi e oggetti di invocazione costanti
``` c++
class orario {
public:
	. . .
	orario UnOraPiuTardi(); // sola lettura
	void AvanzaUnOra();  // lettura-scrittura
	
	orario orario::UnOraPiuTardi() const{ // non causa side-effects
		orario tmp;
		tmp.sec = (sec/3600) % 86400;
		return tmp;
	}
	
	void orario::AvanzaUnOra() {
		sec = (sec/3600) % 86400;
	}
}
const orario LE_TRE(15);
orario t;
t = LE_TRE.UnOraPiuTard();
```
Nei metodi costanti `this` è di tipo `const *C`. 
Ai oggetti costanti e nei metodi costanti si possono invocare solo metodi anche essi costanti.
L’eccezione sono i costruttori.
$$\boxed{\text{Make everything const, as much as possible.}}$$
**Riferimento**
``` c++
int x = 2;
int& a = x; // tipo rifermento, ALIAS
int& q = 4; // ILLEGALE

int y = 3;
a = y; // x=3

const int& r=x; // sola lettura
const int& rq=4; // LEGALE
```
Puntatori
``` c++
int *p1 = &x;
p1 = &y; // LEGALE
int *const p2 = &x; // costante l-valore
p2 = &y; // ILLEGALE
const int *p3 = &x; // protegge r-valore
p3 = &y; // LEGALE
*p3 = 5; // ILLEGALE

const int *const p = &x; // sola lettura
```
Differenza con i puntatori
- Non esiste riferimento `NULL`
- il riferimento è inizializzato a un oggetto e non può essere cambiato
- Alias non può essere definita senza inizializzazione.

*Passaggio dei parametri come riferimento* (invece dei puntatori)
modifica e legge le variabili passate.
``` c++
// PASSAGGIO PER RIFERIMENTO TIPO COSTANTE
void fun1(const Big& r);
void fun2(Big v); // per valore, da evitare

Big b(. . .);
fun1(b); // copia di riferimento a Big
fun2(b); // costruttore di copia di Big
```

*Ritornare un riferimento*
``` c++
int v[] = {3, 2, 6, 0, 5}; // variabile globale

int& setValue(int i) {
	return v[i];
}

int main() {
	setValue(2) = 5; // modifica v[2]
}
```
Non puoi ritornare un riferimento di una variabile locale.

*Ritorno di riferimento costante*
``` c++
const int& f() {return 4;}
int main() { f(); }

// warning: ritorna riferimento a un oggetto temporaneo

const int& f(int* p) {return *p;}
int main() { f(new int(4)); } // LEGALE
```

Esercizio
``` c++
class C {
private:
	int x;
public:
	C(int n=0);
	C F(C obj);
	C G(C obj) const;
	C H(C& obj);
	C I(const C& obj);
	C J(const C& obj) const;
	
	C::C(int n=0) { x=n; }
	C C::F(C obj) { C r; r.x = obj.x + x; return r; }
	C C::H(C& obj) { obj.x += x; return obj }
	// r è temp, C è senza l-valore
	C C::G(C obj) const { C r; r.x = obj.x + x; return r; }
	C C::I(const C& obj) { C r; r.x = obj.x + x; return r; }
	C C::J(const C& obj) const { C r; r.x = obj.x + x; return r; } // ha l-valore
};

int main() {
	C x, y(1), z(2), const C v(2);
	z=x.F(y);
	// v.F(v) non funziona, const può usare solo metodi const
	v.G(y);
	(v.G(y)).F(x); // G() ritorna C, quindi F() funziona
	(v.G(y)).G(x); // conversione C a const C
	// x.H(v) non funziona, cerca funzione c::H(const C&)
	// x.H(z.G(y)) non funziona, riferimento vuole l-valore
	x.I(z.G(y)); // riferimento const non ha bisogno di l-valore
	x.J(z.G(y));
	v.J(z.G(y));
}
```

### Metodi e dati static (di classe)

Metodo che non fa uso di `this` e dato di una classe utilizzabile ovunque
``` c++
class orario {
public:
	static orario OraDiPranzo();
	static int Sec_di_una_ora; // invece delle variabili globali
	static int Sec_di_un_giorno;
	
	orario orario::OraDiPranzo() {
		return orario(13,15);
	}
};

// da inizializzare fuori
int orario::Sec_di_una_ora = 3600;
int orario::Sec_di_un_giorno = 86400;

```

Nel caso vuoi rendere i dati statici costanti, si possono inizializzare inline dentro la classe.
``` c++
class orario {
public:
	. . .
	static const int Sec_di_una_ora = 3600;
	. . .
};
```

I metodi di una classe hanno accesso della parte privata anche delle istanze della classe passati per parametro.

### Overloading degli operatori

Funzionano come i metodi usati finora.
``` c++
class orario {
public:
	...
	orario operator+ (orario) const;
	
	orario orario::operator+(orario o) const {
		orario aux;
		aux.sec = (sec + o.sec) % 86400;
		return aux;
	}
};

int main {
	...
	orario ora(22,45);
	orario DUE_ORE_E_UN_QUARTO(2,15);
	ora = ora + DUE_ORE_E_UN_QUARTO;
}
```

**Regole di overloading**
1. Non si possono cambiare
	- posizione
	- numero operandi
	- precedenze e associatività (* prima di +)
2. Deve esserci un tipo definito dall'utente
3. Gli operatori "=", "\[ \]" e "->" si possono sovraccaricare solo come metodi
4. Non si possono overload ".", "::", "sizeof", "typeid", i cast e "? :"
5. Gli operatori "=", "&" e "," hanno versione standard
6. Non può essere metodo statico.

Se è un metodo allora l’oggetto d’invocazione è il primo argomento.

```
[OPERATORS]
+ - * / % == != < <= > => ++ --
<< >> = -> [] () & new delete
```
Gli operatori `“=“, “[]” e “->”` devono avere parametro `this`, quindi il loro overload è metodo interno

`++b` incrementa e ritorna b
`b++` ritorna b e incrementa

xcasa
- Definizione degli operatori `-, ==, > e <` per la classe orario
- Definizione degli operatori `+, -, ==, > e <` per la classe complesso

**Operatore di assegnazione =**
`C& operator =(const C&)`
> L’operatore di assegnazione per una classe, fa assegnamento membro per membro e i suoi sotto-oggetti. Ogni sotto-oggetto è assegnato in un modo appropriato per tipo.

``` c++
int x=1, y=4, z=7;
x = y = z;

cout << x << " " << y << " " << z; // ritorna 7 7 7
 ```
 
 Il costruttore di copia viene invocato
 1. quando una istanza di oggetto viene dichiarata e inizializzata con un altro oggetto della stessa classe
 2. quando un oggetto viene **passato per valore**
 3. quando una funzione **ritorna per valore**
	 Lo standard propone una ottimizzazione a questo punto: evita di creare un temporaneo anonimo che è usato per inizializzare un altro oggetto dello stesso tipo (questo cambia a seconda del compilatore usato).
``` c++
C fun(C a) { return a; }
C f(C a) {
	C b(a);
	C c=b;
	return c;
}

int main() { // con g++ ottimizzato quante invocazioni di c. di copia?
	C c;
	fun(c); // 2 invocazioni
	
	C y = fun(c); // 2 invocazioni, non 3
	
	C z; z = fun(c); // 2 invocazioni
	
	fun(fun(c)); // 3 invocazioni, non 4
	
	C x;
	C y = f(f(x)); // 7 invocazioni
}
```
`> g++ -fno-elide-constructors` al compilatore rimuove questa ottimizzazione

**Funzionalità di stampa**
Viene definito facendo overloading dell’operatore di output `<<`.
Non funziona come metodo di una classe perché sarebbe obbligato ad avere il `this` come primo parametro. È funzione esterna.
``` c++
// deve essere invocato a cascata, quindi ritorna lo stream
ostream& operator<<(ostream& os, const orario& o) {
	return os << o.Ore() << ":" << o.Minuti() << ":" 
			  << o.Secondi();
}
```
Possiamo raggrupparlo insieme alla classe con un namespace.

(Martedì iniziamo alle 14:00)

**Operatore di somma +**
Come metodo interno
``` c++
class orario {
public:
	orario orario::operator+(const orario& o) const;
}

int main() {
	orario t(12,20), s;
	s = t+4; // FUNZIONA
	s = 4+t; // l’ordine è importante: 4 è un temp anonimo, NON FUNZIONA
}
```
Come funzione esterna
``` c++
orario operator+(const orario& t, const orario& s);

int main() {
	orario t(12,20), s;
	s = 4+t;
	s = 4+5;
}
```
MA! L’operatore non ha più accesso ai parametri interni di orario. 
``` c++
// File Point.h
class Point{
private:
	double _x, _y, _z;
public:
	Point(double x, double y, double z);
	Point();
	double getX() const;
	double getY() const;
	double getZ() const;
	void negate();
	double norm() const;
};

// File Point.opp
#include "Point.h"

// conversione double => Point
Point::Point(double x=0.0, double y=0.0, double z=0.0) {
	_x=x; _y=y; _z=z;
}

double Point::getX() const { return _x; }
double Point::getY() const { return _y; }
double Point::getZ() const { return _z; }

void Point::negate() {
	_x=-_x; _y=-_y; _z=-_z;
}

double Point::norm() const {
	return sqrt(_x^2+_y^2+z^2);
}
```

Preprocessore, sostituzione sintattica
- Direttive al preprocessore
- `#include`: direttive di inclusione
- `#define`: direttive di macro
- direttive di compilazione condizionale

-> Inclusione multipla di file header
``` c++
#ifdef ORARIO_H
#define ORARIO_H
class orario {
	...
};
#endif
```

`> g++ -c orario.cpp`
Compila e non linka, produce il file .o
Source —-> Object file
Source <-/- Object file
Impossibile ottenere source esatto, ma esistono decompiled per reverse engineering
Code obfuscation, codice inutile usato per offuscare il source code dal reverse engineering.

Qt Creator
Valgrind, Valkyria

### Modularizzazione delle classi
Relazione *has-a*
Un oggetto è campo dato di un altro oggetto.
``` c++
#ifndef TELEFONATA_H
#define TELEFONATA_H
#include <iostream>
#include "orario.h"

class Telefonata {
private:
	orario inizio, fine;
public:
	telefonata(orario,orario,int);
	telefonata();
	orario Inizio() const;
	orario Fine() const;
	bool operator==(const telefonata&) const;
};
ostream& operator<<(ostream&, const telefonata&);
#endif
```
La posizione in memoria dipende dall’ordine di dichiarazione.
Parametri oggetto sono sempre costruiti di default.