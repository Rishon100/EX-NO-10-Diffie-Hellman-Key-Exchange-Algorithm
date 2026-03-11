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
# Function for modular exponentiation
def mod_exp(base, exp, mod):
    result = 1
    while exp > 0:
        # If exp is odd
        if exp % 2 == 1:
            result = (result * base) % mod

        # Divide exp by 2
        exp = exp >> 1   # same as exp = exp // 2
        base = (base * base) % mod

    return result


print("\n********* Diffie-Hellman Key Exchange Algorithm **********\n")

# Step 1: Public values
P = int(input("Enter a prime number P: "))
print("The value of P:", P)

G = int(input("Enter a primitive root G for P: "))
print("The value of G:", G, "\n")

# Step 2: Alice private key
a = int(input("Enter the private key for Alice (a): "))
x = mod_exp(G, a, P)  # Alice public key
print("The public key for Alice (x = G^a mod P):", x)

# Step 3: Bob private key
b = int(input("Enter the private key for Bob (b): "))
y = mod_exp(G, b, P)  # Bob public key
print("The public key for Bob (y = G^b mod P):", y, "\n")

# Step 4: Shared secret key
ka = mod_exp(y, a, P)  # Alice computes key
kb = mod_exp(x, b, P)  # Bob computes key

# Step 5: Display keys
print("Shared secret key for Alice (ka = y^a mod P):", ka)
print("Shared secret key for Bob (kb = x^b mod P):", kb)

if ka == kb:
    print("\nDiffie-Hellman Key Exchange successful. Both parties share the same key.")
else:
    print("\nError: The keys for Alice and Bob do not match.")
```


## Output:

<img width="816" height="704" alt="image" src="https://github.com/user-attachments/assets/1dfbe539-155c-4f2c-970e-8060e541264c" />


## Result:
  The program is executed successfully

