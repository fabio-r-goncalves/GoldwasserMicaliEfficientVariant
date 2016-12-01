

#Goldwasser Micali Efficient Variant

Java implementation of Goldwasser Micali Efficient Variant http://eprint.iacr.org/2013/435

##Usage
The code includes a GUI to provide easier testing ![Alt text][id].

Using the code:

Key Generation: 
* GenerateKeys generateKeys = new GenerateKeys(k, keySize);
	* k -> Is the Security Parameter
	* keySize -> Is the size of the key to be generated;
* Then just call generateKeys.generateKeys();
* The above method returns a Keys object that contains the public and private keys generated;

Encryption:
* To encrypt a message just call keys.getPublicKey().encryptMessage([bytes to be encrypted]);
	* The method takes as an argument a byte array with the plain text message;
	* The method will return a byte array with the encrypted message;

Decryption:
* The decryption is very simmilar to the encryption: keys.getPrivateKey().decryptData([bytes to be decrypted], keys.getPublicKey().getY(), keys.getPublicKey().getK());
	* This method takes as arguments, a byte array with the encrypt message, the publick y and the public K;
	* It returns a byte array with the decrypted message;

[gui]: img/gui.jpg "Graphical User Interface"

##Analisys

Although the encryption and decryption process are quite fast, the key generation grows exponentially with the size of the key. Although it is
normal for an algorithm takes more time to find primes for bigger key sizes, the exceptional time it takes is probably due to the method used to
find them. The method used was Java's BigInteger.probablePrime which, is not very efficient.

It was found experimentally that sometimes the algorithm does not find a valid P value. In the experiments it was found that usually it takes
at most 500 tries to find a valid P. Usually when it is not found by then, the algorithm does not find one so, after that number is achieved,
the algorithm is reinitiated.

A jar file with the compiled application can be found in the jar folder.


