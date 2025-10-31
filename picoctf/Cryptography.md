# 1. rsa_oracle

> Can you abuse the oracle?
An attacker was able to intercept communications between a bank and a fintech company. They managed to get the message (ciphertext) and the password that was used to encrypt the message.
After some intensive reconassainance they found out that the bank has an oracle that was used to encrypt the password and can be found here nc titan.picoctf.net 56606. Decrypt the password and use it to decrypt the message. The oracle can decrypt anything except the password.

## Solution:

First I wasn't getting the challenge but then suddenly affter reading a RSA documentation a revelation stuck me first i did `cat secret.enc` and `cat password.enc` which printed the content in the files. I tried to decrypt the password using nc titan.picoctf.net 56606 which resulted in a failure, then finally came the time to use the things I learned from youtube first I encrypted 2 and got its value. Since oracle can decrypt everything other than password so it meant that I had to modify the password then decrypt it then reverse the modifications made.
So I made a Python program of multiplying the encrypted value of 2 with Password and ran that program and got the output. Then I decrypted the output with Oracle, the next thing I did was making the program of converting the hex to decimal and div the thing by 50(ASCII value of 2), Then converting it back to hex. And I ran the program and tada! I got the password. `openssl enc -aes-256-cbc -d -in secret.enc` and entered the output I got as Password......I got the flag.

```
cat secret.enc 
cat password.enc 
nc titan.picoctf.net 56606
python sum.py 
python3 sum.py 
nc titan.picoctf.net 56606
python3 convert.py 
openssl enc -aes-256-cbc -d -in secret.enc 
```
<img width="1911" height="953" alt="Screenshot From 2025-10-31 15-11-57" src="https://github.com/user-attachments/assets/eaff312b-ddc8-446c-bd30-8cd9ee424103" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 15-22-40" src="https://github.com/user-attachments/assets/b9c8f1ba-7140-496c-ac0d-a2cce179ead7" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 15-14-03" src="https://github.com/user-attachments/assets/7297a549-4d05-404e-bcc3-f41dd2cea368" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 15-18-21" src="https://github.com/user-attachments/assets/43f6ea6d-fe4b-484a-8ce7-a33d9e7d9d59" />



## Flag:

```
picoCTF{su((3ss_(r@ck1ng_r3@_3319c817}
```

## Concepts learnt:
RSA encryption has a special mathemathical property the encryption of (Message 1 × Message 2) is equal to (Encryption of Message 1 × Encryption of Message 2).

Basic Python 

Changing from hex to dec and dec to hex

RSA basics

Encrypted files formatt and applications

## Resources:

[Basic Definitions](https://google.com)
[RSA Algorithm in Cryptography](https://www.geeksforgeeks.org/computer-networks/rsa-algorithm-cryptography/)
[RSA theory](https://doc.sagemath.org/html/en/thematic_tutorials/numtheory_rsa.html)
youtube
***



# 2. Custom Encryption

> Can you get sense of this code file and write the function that will decode the given encrypted file content.
Find the encrypted file here flag_info and code file might be good to analyze and get the flag.

## Solution:

The biggest challenge in this schallenge was understanding the encryption code and how it works, even making the decryption code was difficult but once you fully understand the working of the encryption code you can make a a code for decryption pretty easily. So while understanding I understood that Encryption basically had three steps reversing the string , XOR encryption and multiplication with a special number and key. So Decryption must have these thing (1.) It should divide the values in cipher by ```key*311``` (2.) XOR decryption and even though the strring was reversed but XOR is self inverse so there is no need for anything else ran the code and got the flag.


enc_flag:
```
a = 89
b = 27
cipher is: [33588, 276168, 261240, 302292, 343344, 328416, 242580, 85836, 82104, 156744, 0, 309756, 78372, 18660, 253776, 0, 82104, 320952, 3732, 231384, 89568, 100764, 22392, 22392, 63444, 22392, 97032, 190332, 119424, 182868, 97032, 26124, 44784, 63444]
```
custom_encryption.py:
```
from random import randint
import sys


def generator(g, x, p):
    return pow(g, x) % p


def encrypt(plaintext, key):
    cipher = []
    for char in plaintext:
        cipher.append(((ord(char) * key*311)))
    return cipher


def is_prime(p):
    v = 0
    for i in range(2, p + 1):
        if p % i == 0:
            v = v + 1
    if v > 1:
        return False
    else:
        return True


def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def test(plain_text, text_key):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    a = randint(p-10, p)
    b = randint(g-10, g)
    print(f"a = {a}")
    print(f"b = {b}")
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
    cipher = encrypt(semi_cipher, shared_key)
    print(f'cipher is: {cipher}')


if __name__ == "__main__":
    message = sys.argv[1]
    test(message, "trudeau")
```
decypt.py:
```
from custom_encryption import is_prime, generator
def leak_shared_key(a, b):
    p = 97
    g = 31
    if not is_prime(p) and not is_prime(g):
        print("Enter prime numbers")
        return
    u = generator(g, a, p)
    v = generator(g, b, p)
    key = generator(v, a, p)
    b_key = generator(u, b, p)
    shared_key = None
    if key == b_key:
        shared_key = key
    else:
        print("Invalid key")
        return
    return shared_key 
def decrypt(ciphertext, key):
    semi_ciphertext = []
    for num in ciphertext:
        semi_ciphertext.append(chr(round(num / (key * 311))))
    return "".join(semi_ciphertext)
def dynamic_xor_decrypt(semi_ciphertext, text_key):
    plaintext = ""
    key_length = len(text_key)
    for i, char in enumerate(semi_ciphertext):
        key_char = text_key[i % key_length]
        decrypted_char = chr(ord(char) ^ ord(key_char))
        plaintext += decrypted_char
    return plaintext[::-1]
if __name__ == "__main__":
    a = 89
    b = 27
    ciphertext_arr = [33588, 276168, 261240, 302292, 343344, 328416, 242580, 85836, 82104, 156744, 0, 309756, 78372, 18660, 253776, 0, 82104, 320952, 3732, 231384, 89568, 100764, 22392, 22392, 63444, 22392, 97032, 190332, 119424, 182868, 97032, 26124, 44784, 63444
    ]
    text_key = "trudeau"
    shared_key = leak_shared_key(a, b)
    semi_ciphertext = decrypt(ciphertext_arr, shared_key)
    plaintext = dynamic_xor_decrypt(semi_ciphertext, text_key)
    print(plaintext)
```
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 18-38-02" src="https://github.com/user-attachments/assets/ef7e6342-dd27-4951-989f-a8409a2b8a5c" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 18-38-15" src="https://github.com/user-attachments/assets/b5f2e89f-c828-4a4e-816f-7819902c8522" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 18-38-28" src="https://github.com/user-attachments/assets/cd129c83-520b-460e-b078-39d59fb32c7a" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 18-56-20" src="https://github.com/user-attachments/assets/60fac88e-89c5-4091-83fc-6d2a0478ace1" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 18-56-33" src="https://github.com/user-attachments/assets/36ce9e35-30c9-4bae-a8d7-7472024f86ed" />


## Flag:

```
picoCTF{su((3ss_(r@ck1ng_r3@_3319c817}
```

## Concepts learnt:
Python Programming Concepts 

XOR Encryption / Decryption

Modular Arithmetic

String Reversal

generating a shared secret key 

## Resources:

[Basic Definitions](https://google.com)
[XOR Encryption and Decryption](https://www.geeksforgeeks.org/xor-cipher/)
[Modular Arithmetic](https://cryptohack.org/courses/modular/)
[Network Security](https://www.classcentral.com/course/youtube-network-security-diffie-hellman-key-exchange-algorithm-189975)
***



# 3. miniRSA

> Let's decrypt this: ciphertext? Something seems a bit small.

## Solution:

It took me sometime to understand what should I do , first thing I did was try to execute the ciphertext, it didn't have the permission ehen i used `chmod` command to make it executable but that didn't do much then I read the file using `cat` command it gave me something and that was value of N, e and ciphertext(c). The value of e is very small in this so if we take the assumption that m is significantly smaller, if m^3 is significantly smaller than N then according to RSA algorithm c=m^e mod(N), c would become m^3. Then what I had to made a program that find integer cuberoot of c and turns into hex, and then decode it. I ran the program and got the flag. 

```
./Downloads/ciphertext
chmod +x ./Downloads/ciphertext
/Downloads/ciphertext
cat Downloads/ciphertext 
python3 ./Downloads/Decipher.py 
```
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 19-31-18" src="https://github.com/user-attachments/assets/6b22e9a2-b50d-4ae7-adc4-42a721e07fcd" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 19-44-28" src="https://github.com/user-attachments/assets/aea7dcb1-8a82-415d-a7da-c835f28ca89d" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 19-44-46" src="https://github.com/user-attachments/assets/d65df341-bff2-4c5a-b741-ad5c7f8448ce" />


## Flag:

```
picoCTF{n33d_a_lArg3r_e_ccaa7776}
```

## Concepts learnt:
RSA Algorithm Basics

Basic Python 

Hexadecimal Encoding

RSA basics

Python and Data Encoding

## Resources:

[Basic Definitions](https://google.com)
[RSA Algorithm Basics](https://youtu.be/trkJnhFmKDE)
[Hexadecimal Encoding](https://www.geeksforgeeks.org/java-program-to-implement-the-rsa-algorithm/)
youtube
***
