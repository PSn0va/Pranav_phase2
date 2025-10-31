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
