 ## IMPLEMENTATION OF RSA
 # AIM :
 To write a C program to implement the RSA encryption algorithm.

## ALGORITHM:
STEP-1: Select two co-prime numbers as p and q.

STEP-2: Compute n as the product of p and q.

STEP-3: Compute (p-1)*(q-1) and store it in z.

STEP-4: Select a random prime number e that is less than that of z.

STEP-5: Compute the private key, d as e *
mod-1
(z).

STEP-6: The cipher text is computed as messagee *

STEP-7: Decryption is done as cipherdmod n.

## PROGRAM:
```
import java.util.Scanner;

public class RSAEncryption {
    // Function to calculate greatest common divisor (GCD)
    static int gcd(int a, int b) {
        if (b == 0)
            return a;
        return gcd(b, a % b);
    }

    // Function to generate RSA keys
    static void generateRSAKeys(int[] n, int[] e, int[] d) {
        Scanner scanner = new Scanner(System.in);

        // Choose two prime numbers (p and q)
        System.out.print("Enter two prime numbers: ");
        int p = scanner.nextInt();
        int q = scanner.nextInt();
        // Calculate n = p * q
        n[0] = p * q;
        // Calculate Euler's totient function (φ(n))
        int phi = (p - 1) * (q - 1);
        // Choose a public exponent (e) such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
        e[0] = 5; // You can choose a different value for e, typically a prime number
        // Calculate the private exponent (d) such that (d * e) % φ(n) = 1
        d[0] = 0;
        while ((d[0] * e[0]) % phi != 1) {
            d[0]++;
        }
        scanner.close();
    }

    // Function to perform modular exponentiation (base^exponent % modulus)
    static int modExp(int base, int exponent, int modulus) {
        int result = 1;
        while (exponent > 0) {
            if (exponent % 2 == 1) {
                result = (result * base) % modulus;
            }
            base = (base * base) % modulus;
            exponent /= 2;
        }
        return result;
    }

    // Function to encrypt a message using the public key
    static int encrypt(int message, int publicKey, int modulus) {
        return modExp(message, publicKey, modulus);
    }

    // Function to decrypt a message using the private key
    static int decrypt(int ciphertext, int privateKey, int modulus) {
        return modExp(ciphertext, privateKey, modulus);
    }

    public static void main(String[] args) {
        int n = 0, e = 0, d = 0;
        int plaintext;
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter plaintext: ");
        plaintext = scanner.nextInt();

        generateRSAKeys(new int[]{0}, new int[]{0}, new int[]{0});

        System.out.println("Original message: " + plaintext);
        int ciphertext = encrypt(plaintext, e, n);
        System.out.println("Encrypted message: " + ciphertext);
        int decryptedMessage = decrypt(ciphertext, d, n);
        System.out.println("Decrypted message: " + decryptedMessage);

        scanner.close();
    }
}


```
## OUTPUT:
![Screenshot 2024-03-05 113517](https://github.com/AlluguriSrikrishnateja/19CS412---CRYPTOGRAPHY---ADVANCED-ENCRYPTION/assets/118343892/b96f8704-db74-4fb0-835d-078d58644625)


## RESULT :

Thus the C program to implement RSA encryption technique had been
implemented successfully





## IMPLEMENTATION OF DIFFIE HELLMAN KEY EXCHANGE ALGORITHM

## AIM:

To implement the Diffie-Hellman Key Exchange algorithm using C language.


## ALGORITHM:

STEP-1: Both Alice and Bob shares the same public keys g and p.

STEP-2: Alice selects a random public key a.

STEP-3: Alice computes his secret key A as g
a mod p.

STEP-4: Then Alice sends A to Bob.


STEP-5: Similarly Bob also selects a public key b and computes his secret
key as B and sends the same back to Alice.


STEP-6: Now both of them compute their common secret key as the other
one’s secret key power of a mod p.

## PROGRAM: 

```
import java.util.Scanner;

public class DiffieHellman {
    // Power function to return value of a ^ b mod P
    static long power(long a, long b, long P) {
        if (b == 1)
            return a;
        else
            return ((long) Math.pow(a, b)) % P;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        long P, G, x, a, y, b, ka, kb;

        // Both the persons will be agreed upon the
        // public keys G and P
        System.out.print("Enter the value of P: ");
        P = scanner.nextLong(); // A prime number P is taken
        System.out.println("The value of P: " + P);

        System.out.print("Enter the value of G: ");
        G = scanner.nextLong(); // A primitive root for P, G is taken
        System.out.println("The value of G: " + G + "\n");

        // Alice will choose the private key a
        a = 4; // a is the chosen private key
        System.out.println("The private key a for Alice: " + a);
        x = power(G, a, P); // gets the generated key

        // Bob will choose the private key b
        b = 3; // b is the chosen private key
        System.out.println("The private key b for Bob: " + b + "\n");
        y = power(G, b, P); // gets the generated key

        // Generating the secret key after the exchange
        // of keys
        ka = power(y, a, P); // Secret key for Alice
        kb = power(x, b, P); // Secret key for Bob

        System.out.println("Secret key for Alice: " + ka);
        System.out.println("Secret key for Bob: " + kb);

        scanner.close();
    }
}

```
## OUTPUT:

![Screenshot 2024-03-15 140647](https://github.com/AjaysuryaS/19CS412---CRYPTOGRAPHY---ADVANCED-ENCRYPTION/assets/114158396/5740410d-00b2-48a7-8354-f8cdaca28434)


## RESULT: 

Thus the Diffie-Hellman key exchange algorithm had been successfully
implemented using C.





## IMPLEMENTATION OF DES ALGORITHM

## AIM:
To write a program to implement Data Encryption Standard (DES)

## ALGORITHM :

STEP-1: Read the 64-bit plain text.

STEP-2: Split it into two 32-bit blocks and store it in two different arrays.

STEP-3: Perform XOR operation between these two arrays.

STEP-4: The output obtained is stored as the second 32-bit sequence and the
original second 32-bit sequence forms the first part.

STEP-5: Thus the encrypted 64-bit cipher text is obtained in this way. Repeat the
same process for the remaining plain text characters.

### PROGRAM :

```
 class DiffieHellman {
    public static void main(String args[]) {
        int p = 23; /* publicly known (prime number) */ int g = 5; /* publicly known (primitive root) */ int x = 4; /* only Alice knows this secret */
        int y = 3; /* only Bob knows this secret */ double aliceSends = (Math.pow(g, x)) % p;
        double bobComputes = (Math.pow(aliceSends, y)) % p; double bobSends = (Math.pow(g, y)) % p;
        double aliceComputes = (Math.pow(bobSends, x)) % p; double sharedSecret = (Math.pow(g, (x * y))) % p;
        System.out.println("simulation of Diffie-Hellman key exchange algorithm\n--");
                System.out.println("Alice Sends : " + aliceSends); System.out.println("Bob Computes : " + bobComputes); System.out.println("Bob Sends : " + bobSends); System.out.println("Alice Computes : " + aliceComputes); System.out.println("Shared Secret : " + sharedSecret);
                if ((aliceComputes == sharedSecret) && (aliceComputes == bobComputes)) System.out.println("Success: Shared Secrets Matches! " + sharedSecret);
        else
            System.out.println("Error: Shared Secrets does not Match");
    }
}
```
## OUTPUT:

![Screenshot 2024-03-15 135629](https://github.com/AjaysuryaS/19CS412---CRYPTOGRAPHY---ADVANCED-ENCRYPTION/assets/114158396/0a5e1cb1-ca5c-4ff3-a562-37c5e6377e6c)


## RESULT:

Thus the data encryption standard algorithm had been implemented
successfully.

