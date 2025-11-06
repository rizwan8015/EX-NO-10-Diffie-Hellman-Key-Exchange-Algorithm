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
```
#include <stdio.h>
#include <math.h>

long long int mod_exp(long long int base, long long int exp, long long int mod) {
    long long int result = 1;
    base = base % mod;

    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;
        exp = exp >> 1; 
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    long long int P, G;     
    long long int a, b;     
    long long int x, y;     
    long long int ka, kb;   

    printf("=== Diffie-Hellman Key Exchange ===\n");

    printf("Enter a prime number (P): ");
    scanf("%lld", &P);

    printf("Enter a primitive root modulo P (G): ");
    scanf("%lld", &G);

    printf("Enter Alice's private key (a): ");
    scanf("%lld", &a);

    printf("Enter Bob's private key (b): ");
    scanf("%lld", &b);

    
    x = mod_exp(G, a, P);  
    y = mod_exp(G, b, P);  

    printf("\nPublicly shared values:\n");
    printf("Prime number (P)      : %lld\n", P);
    printf("Primitive root (G)    : %lld\n", G);
    printf("Alice's Public Key    : %lld\n", x);
    printf("Bob's Public Key      : %lld\n", y);

    
    ka = mod_exp(y, a, P);  
    kb = mod_exp(x, b, P);  

    printf("\nShared Secret Key computed by Alice: %lld\n", ka);
    printf("Shared Secret Key computed by Bob  : %lld\n", kb);

    if (ka == kb)
        printf("\nKey exchange successful! Shared secret = %lld\n", ka);
    else
        printf("\nKey exchange failed. Keys do not match.\n");

    return 0;
}
```


## Output:

<img width="420" height="355" alt="Screenshot 2025-11-05 112019" src="https://github.com/user-attachments/assets/639db98b-b252-475e-beee-6a3417e9d35b" />


## Result:
  The program is executed successfully

