# EX-NO-10 — Diffie-Hellman Key Exchange Algorithm

## AIM:
To implement the Diffie–Hellman Key Exchange algorithm for secure shared key generation between two parties.

## ALGORITHM:

1. Diffie–Hellman is used to securely share a secret key over an insecure channel.
2. Select a large **prime number (P)** and a **primitive root (G)** modulo P — these are public.
3. **Key Exchange Process:**  
   - Each user selects a private key.  
   - They compute public keys using:  
     \[
     \text{Public Key} = g^{\text{private key}} \mod p
     \]
   - Public keys are exchanged.
4. **Secret Key Computation:**  
   - Each computes the shared secret key using:  
     \[
     \text{Secret Key} = (\text{Other's Public Key})^{\text{own private key}} \mod p
     \]
5. **Security:**  
   The shared key is secure because finding the private key from the public key requires solving discrete logarithms.

## PROGRAM:
```c
#include <math.h> 
#include <stdio.h> 

// Power function to return value of a^b mod P 
long long int power(long long int a, long long int b, long long int P) 
{
    if (b == 1)  
        return a;
    else
        return (((long long int)pow(a, b)) % P);
}

// Driver program  
int main() 
{ 
    long long int P, G, x, a, y, b, ka, kb; 

    printf("\n***** Diffie-Hellman Key Exchange Algorithm *****\n\n"); 

    printf("Enter the value of P: "); 
    scanf("%lld", &P);   // A prime number P 
    printf("The value of P: %lld\n", P); 

    printf("Enter the value of G (Primitive root of P): "); 
    scanf("%lld", &G);   // Primitive root G 
    printf("The value of G: %lld\n\n", G); 

    // Alice's private key 
    a = 4;
    printf("The private key a for Alice : %lld\n", a);  
    x = power(G, a, P);  // Alice's public key 

    // Bob's private key 
    b = 3;
    printf("The private key b for Bob : %lld\n\n", b); 
    y = power(G, b, P);  // Bob's public key 

    // Secret key computation 
    ka = power(y, a, P); 
    kb = power(x, b, P); 

    printf("Secret key for Alice is : %lld\n", ka); 
    printf("Secret key for Bob is   : %lld\n", kb); 

    return 0; 
}
```

## OUTPUT:

![Screenshot 2025-10-10 142426_page-0001](https://github.com/user-attachments/assets/5bfabfbe-0299-4664-9002-4221d0ce72f8)



## RESULT:
The Diffie–Hellman Key Exchange algorithm was implemented and executed successfully, generating a shared secret key for both parties.
