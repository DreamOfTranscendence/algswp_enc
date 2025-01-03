# algswp_enc
Algorithm with Swapping Encryption, ( Written in javascript, a series of lightweight symmetric encryption algorithms that work in nodejs and web-browsers )


   A T T E N T I O N :

WARNING: This algorithm was written simply for a web development hobby so it might not be cryptographically secure.


2025Jan2
Algswp12 uses a 4-bit-overlapping 12-bit replacement cypher together with a sort-of-randomized key scrambler for the 6144-octet long (12 bits times number of possible values of a 12 bit number, divided into 8-bit-long-bytes for convenience) encryption and decryption keys.

The 12-bit replacement cipher keys MUST be shuffled starting from the ordered sequence of 12-bit numbers 0 through 4095, and all possible values of 12-bit numbers must remain somewhere in the key, though any value can be anywhere within it.

The data to `crypt MUST be at least 24 bits (3 bytes) long, because the encryption is overlapping and the replacement is of 12 bits at a time of the data.

Any potential security it MIGHT provide is based on the idea that it's infeasible to run the key scrambler over and over again or to shuffle the 12 bit values around in every possible combination sequentially until a password or 6144 bit key is discovered.

 Feel free to try to crack the algorithm by randomly generating passwords, encrypting data with and forgetting the passwords, keeping encrypted and unencrypted copies of the data and trying to find the correlations.


Algswp12 Usage require("./algswp12.js"); or <script src="algswp12.js"></script>
Uint8Array data Ark12( Uint8Array data_to_crypt, String password, Bool runAsDecrypt );
//Ark12 returns the same Uint8Array that was passed to it but all the values of the array have been modified
example: var data=new Uint8Array(64,56,10,20,30,40), key="Password"; Ark12(data,key)&&null; 
//data has been encrypted
Ark12(data,key,true)&&null;
//data has been decrypted
//in this example &&null was added to mute annoying console output of return value in nodejs consoles and similar environments

 
