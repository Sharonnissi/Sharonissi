---
title: "Decrypting Encryption: Simplifying a Complex Topic"
datePublished: Fri Feb 21 2025 22:06:40 GMT+0000 (Coordinated Universal Time)
cuid: cm7fbmelv000008l76upvh1uz
slug: decrypting-encryption-simplifying-a-complex-topic
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740175532935/e30a0e63-46d7-42f8-b3f7-1c5f5966c754.webp
tags: encryption, cryptography, cybersecurity-1

---

Before understanding about the encryption, let me first talk about confidentiality, integrity, authenticity and non -repudiation.

**<mark>Confidentiality</mark>** is making sure the information is protected and only authorized persons can view the information.

**<mark>Integrity</mark>** is making sure that the information is not changed and we would know if the information is changed using hashing.

**<mark>Authenticity</mark>** is knowing who sent or created the information.

**<mark>Non repudiation</mark>** is making sure that the persons involved in communicating information digitally don't deny the actions at a later point of time.

Okay let's talk about encryption now.

**<mark>What is encryption?</mark>** It is a method used to change the plaintext data to unreadable data and which can only be read once it is decrypted.

**<mark>Types of encryption?</mark>** One is asymmetric and the other is symmetric encryption.

In **<mark>Symmetric encryption</mark>** you use only one key to encrypt and decrypt the data.

**<mark>Example :</mark>** When A wants to send a message to B then A and B will use a key that both of them agreed upon to use. So, A encrypts the message using the shared key and sends it to B and B can decrypt the message using the same key.

In this the main problem is the exchange of shared key. It can only be shared using a secured channel. And if any hacker hacks the channel, will be able to get the shared key and can decrypt the message. To overcome this, the asymmetric encryption came into picture.

**<mark>Asymmetric encryption</mark>** is the one in which you have two keys which is public and private key for encryption and decryption.

**<mark>Example:</mark>** When A wants to send a message to B then A will encrypt the message using B's public key and sends it to B. B then decrypts it using B's private key.

This way we can make sure that confidentiality is achieved. Asymmetric encryption will only ensure confidentiality. It will ensure integrity using hashing and digital signatures.

However, how can B be sure that the message he received is from A and not anyone else? Here comes the **<mark>digital signatures</mark>** into picture. Digital signatures will be helpful in identifying who the sender is.

Taking the same example as above, A needs to send a message to B. A will generate a hash for his message and encrypts the hash using his private key and here we need to note that the message is not encrypted, it is sent as a plain text only along with the digital signature. Now the plain text along with the digital signature is sent to B. B will now decrypt the digital signature with A's public key. This way, B can be sure that the message was sent by A only because he is able to decrypt the digital signature using A's public key and if the hash matches then B can be sure of integrity as well.

Through this we can also achieve non repudiation because A cannot deny that the message is not sent by him because the message can be decrypted using his public key only.

However, while asymmetric encryption provides strong security, it has limitations. It's slow due to complex mathematical operations, and there’s a size limit on the data it can handle efficiently, typically around 250 bytes. This is why asymmetric encryption is mainly used to exchange a symmetric key, which is then used for encrypting larger volumes of data.

But if we notice one point here, through the digital signatures confidentiality cannot be achieved because the message here is sent in a plain text format only and not encrypted and the digital signature can be decrypted using A's public key which is easily available publicly. So in that case if we want to achieve confidentiality, integrity and authenticity then we need to use something called **<mark>hybrid encryption</mark>** were we can use both the symmetric and asymmetric encryption.

Before going ahead with hybrid encryption, let us know how keys are exchanged in symmetric encryption in a secured way and that is were these mathematical algorithms come into picture which is <mark>Diffie-Hellman Key Exchange</mark> and <mark>Elliptic Curve Diffie-Hellman</mark> using which we can derive a shared key share by combining senders private key with the receiver's public key and generate a shared key. Mostly DHKEY method is mostly followed for key exchange which uses modular exponentiation method to generate a shared key.

**<mark>Hybrid Encryption:</mark>** In this the asymmetric encryption is used for the exchange of symmetric keys and symmetric encryption is used for encrypting the actual message. So, what happens here is that sender A will generate a random symmetric key and uses this to encrypt the message. Then, A uses B's public key to encrypt the randomly generated symmetric key and the encrypted message and the encrypted symmetric key to B. B now decrypts the symmetric key using B's private key and using the symmetric key B will decrypt the encrypted message.

Only in this encryption is that the random symmetric key is generated which is encrypted using the receiver's public key and is used to encrypt the message. Receiver will use the private key to decrypt the symmetric key encryption and use the symmetric key to decrypt the encrypted message.