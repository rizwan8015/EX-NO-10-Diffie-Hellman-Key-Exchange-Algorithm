# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
~~
#include <stdio.h>
#include <math.h>
long long int power(long long int base, long long int exp, long long int mod) {
    long long int result = 1;
    for (int i = 0; i < exp; i++) {
        result = (result * base) % mod;
    }
    return result;
}
int main() {
    long long int P, G, a, b; 
    long long int A, B, secretA, secretB;
    printf("Enter a prime number (P): ");
    scanf("%lld", &P);
    printf("Enter a primitive root of %lld (G): ", P);
    scanf("%lld", &G);
    printf("Enter private key for Alice (a): ");
    scanf("%lld", &a);
    printf("Enter private key for Bob (b): ");
    scanf("%lld", &b);
    A = power(G, a, P);
    B = power(G, b, P);
    secretA = power(B, a, P);
    secretB = power(A, b, P);
    printf("\nPublic Key of Alice (A): %lld", A);
    printf("\nPublic Key of Bob (B): %lld", B);
    printf("\n\nSecret Key for Alice: %lld", secretA);
    printf("\nSecret Key for Bob: %lld\n", secretB);
    if (secretA == secretB)
        printf("\nhared secret key successfully established!\n");
    else
        printf("\nError: Keys do not match.\n");
    return 0;
}
~~



## Output:
<img width="1401" height="782" alt="image" src="https://github.com/user-attachments/assets/731af6bb-5242-44d4-9949-dd1fff129fad" />




## Result:
  The program is executed successfully

