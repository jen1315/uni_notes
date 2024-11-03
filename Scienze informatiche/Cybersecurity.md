SPRITZ Group(Security and PRIvacy … Through Zeal)

SSL protocol, autenticato e confidenziale (https)

```
  .———————————————————-.
  |————————————-——.    |k4
  |————————-.    |k3   |
  |———-.    |k2  |     |
  |    |k1  |    |     |
( S )-(n1)-(n2)-(n3)-( D )

TOR(The Onion Routing)
```
$E(E(E(E(M)_{k4})_{k3})_{k2})_{k1}$

Topics
- Cryptography
	Ciphers; hash functions; encryption
- Web Vulnerabilities
	Bad programming practices; injections; language vulnerabilities
- Reverse Engineering
	Reversing patching; anti-debug
- Pwning
	Buffer overflow

**What is security?**
It's not only a product but a process. 
Nothing is 100% secure (we don't need it, it would cost too much).

The security of a system is the security of its weakest component.
1. Security by obscurity never works.
2. Cryptography is only a building block

To define security, you have to specify its $\begin{cases}\text{adversaries}\\ \text{properties}\end{cases}$
*Basic security properties*
- Confidentiality
	leaking, loss of confidentiality
- Integrity
	corruption, loss of integrity
- Availability
	unavailability
- Authentication

The adversary can be classified by
- type of attacker
	insider or outsider of the security domain
- type of attack 
	passive, only reading
	active, taking action like modifying, denerating or destroying information

Even countermesures can have vulnerabilities.
### Encoding
Transforming data so that it can be used by a different type of system.
Encoding can be easily reversed (decoding).

base64 for web communication
- length always multiple of 4
- special alphabet \[A-Z, a-z, 0-9, +, /, =\]
- padding in the end "=\=" or "="

hexadecimal, used form MAC address and memory dumps

UUEncoding
```
begin <mode> <file_name>
<
  text
>
end
```

### Cryptography
Caesar Cypher
- every character is translated of $n$ in the alphabet
- brute force

**Message Authentication**
- protection from an active attack
- verifies that the received message is authentic
- conventional encryption
	a key known only between sender and receiver
- authentication mechanism
	appends an authentication tag to clear text message (fingerprint)

MAC algorithm generates a digest of the full message with a key. This fingerprint is added to the message and sent.
The receiver uses the MAC algorithm to the message then compares this with the fingerprint.

*Hash function*
- always returns a value of fixed length
- is only one-way, you can't reverse it
- has weak collision resistance, 
	computationally impossible to find y!=x such that H(y)=H(x)
- has strong collision resistance,
	computationally impossible to find (x, y) such that H(x)=H(y)
This can be attacked if you know the algorithm weaknesses or with brute force.

*Public-key encryption*
Asimmetric key
Confindentiality
- encrypt with the public key
- decrypt with the private key
Authentication
- encrypt with the private key
- decrypt with the public key

Public Keys certificated are given by a certifying authority.
![[Pasted image 20241017171139.png]]

**User Authentication**
Identification, get an id
Verification, bind a identifier to a user

Authentication based on user
- *Knows*, e.g. password
- *Posseses*, e.g. smartcard
- *Is* (static biometrics), e.g. fingerprint
- *Does* (dynamic biometrics), e.g. voice

Password hash, can be cracked with brute force
- salt, a small string added to the password before hashing

### Web Vulnerabilities
Who develops a system focuses not on security but on
- functionality
- performance
To find a web vulnerability, gather as much information as possible on how it's written.

Port is an server access point.
A web 
HTTP is the web transfer protocol. HTTPS in the "secure" version that has a TLS connection between two hosts.
HTTP is stateless, cookies are used to save user information per session.
Cookies can be harmful when used for session injection
They can be used to trace a user, as we give cookies everytime we connect to a website, they can can connect your new session with an old one via saved cookie. Servers can continue to trace the user even when the user doesn't want to store the cookie: the internet operator can secretly send the cookie anyway.

- GET is used to request data from a specific resource
  get parameters are written in open on the website url
- POST is used to send data to a server to create/update a resource
Input validation and sanitisation is necessary to avoid injiection attacks.
We have to decide carefully on where to code it
-> on the client side: it can be easily bypassed
-> on the server side: increase the server overhead (weak to DDOS)

### Language vulnerabilities
Who thinks about the securities of the programming language?
Every language has vulnerabilities:
for example C with pointers and memory allocation