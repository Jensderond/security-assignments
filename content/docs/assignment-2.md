+++
title = "Assignment 2"
description = "RSA"
date = 2018-03-01T22:17:13+01:00
weight = 20
draft = false
bref = "Assignment 2"
toc = false
+++

## Assignment 2.1 Sniffing at RSA

### Assignment 2.1.1: do the encryption and decryption with message m = 289

Encryption is:   

p 	= 11, q = 29

n 	= 11  * 29 = 319

e 	= 3

d 	= 187

m 	= 289

E(m)	= 289^3 (mod) 319

= 115 

Decryption is:

c	= 115

D( c )	= 115^187 ( mod 319 ) = 289 

  

### Assignment 2.1.2: do it again now with message m = 5555. What is happening?

Als uw bericht groter is dan de modulus, dan zal m 'niet gelijk zijn aan m. In modulair rekenen kun je geen resultaat krijgen gelijk aan of groter dan de modulus.

### Assignment 2.1.3: Explain how RSA is applied in practice in order circumvent its limitation.

RSA wordt meestal gebruikt voor het versleutelen en ontsleutelen van kleine berichten. Zo’n bericht kan bijvoorbeeld een hash van iets zijn (een digitale handtekening) of een symmetrische sleutel die daarna kan worden gebruikt om grotere hoeveelheden data te versleutelen/ontsleutelen.

Exercise 1.4: now take message m = 143 and encrypt it with the *private* key and decrypt it with the *public* key. So the roles of public and private keys are swapped. Wow, it still works!

### Assignment 2.1.5:  In exercise 4, the roles of public and private key have been swapped. Explain what the use case is of this way of working

Nu kan alleen degene met de private key het berichten ontsleutelen.

	 	 	 	

## Assignment 2.2 Almost-real RSA

Output:

public  = 65537

private = 61143314813583623126488201288265321340524917525986992210453

modulus = 126900890614619181962841854763009316944566241336677391957593

Message = 1952805748

encrypted = 51880663617238795935884273520273101929576140016805577366307

decrypted = 1952805748

## Assignment 2.3 Certificates

### Assignment 2.3.1: What is a certificate?

Een certificaat is een digitaal bestand met informatie zoals: details van de identiteit, certificaat uitgever, serienummer, geldigheidsduur, enz. Daarnaast bevat een certificaat een public key en is een certificaat gesigneerd met een bovenliggend certificaat (of lees hier onder).

### Assignment 2.3.2: What is a self-signed certificate?

In plaats van dat het certificaat is gesigneerd met een bovenliggend certificaat, is het certificaat gesigneerd met zichzelf.

### Assignment 2.3.4

### ![image alt text](/img/image_1.png)

### Assignment 2.3.5

![image alt text](/img/image_2-1.png)

### Assignment 2.3.6

![image alt text](/img/image_2.png)

## Assignment 2.4 Cryptographic hash functions

### Assignment 2.4.1 which 3 properties are used to define the security level of a cryptographic hash function? Explain each of these in your own words.
Once one collision has been found, the hash function is considered broken.

1. Is de hashfunctie consistent? Genereert het dezelfde output bij dezelfde input

2. Is het (bijna) onmogelijk om terug te gaan van digest naar bericht?

3. Is een collision (bijna) onmogelijk?

### Assignment 2.4.2 use the openssl library to create a hash using SHA-256

Text I hashed: 
```
I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5.
```

**Hash:** `2d01cc3644ee4a73080d59230089451fd52899953291a3fecdd234a27d2d2bbc`

### Assignment 2.5.1 Change one character of the message and create SHA-256 Hash

Text I hashed: 
```
I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD5. I will not use MD6.
```

**Hash:** `9afda62f51154af4b0ae15999422f35b15fcaada681640587250e34874d38e9f`
