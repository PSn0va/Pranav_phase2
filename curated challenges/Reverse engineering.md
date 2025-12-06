# 1. Joydivision

## Solution:
So this challenge was good. In this cghallenge first i opened flag.txt it was quite obvious thiat it was encrypted. So then I used `file` command for identifying disorder it was ElF executable file. Then I ran it `.\disorder` it showed me omme text I thing that was the hint but it ended with segmentation  faullt I used `string` command on sidorder it was a buunch of thing but i got to know that there is a main I knew to tear apart the whole thing I will need a extra program where I used Ghidra......From which I got to know that it was taking input from a file palatinepackflag.txt and encrypting by the help of gpt I wrote down the code to reverse the whole thing. Then I ran th command and TA DA i got hthe flag.
```
def flipBits(data):
    # Re-implements the C logic exactly to reverse the XOR/NOT operations
    chars = list(data)
    key = 0x69
    toggle = False
    for i in range(len(chars)):
        if toggle:
            chars[i] ^= key
            key = (key + 0x20) & 0xFF
        else:
            chars[i] = (~chars[i]) & 0xFF
        toggle = not toggle
    return bytes(chars)

def shrink(data):
    # Reverses the 'expand' function by combining nibbles
    output = []
    toggle = False
    for i in range(0, len(data), 2):
        byte1 = data[i]
        byte2 = data[i+1]
        if not toggle:
            # Even logic: Lower nibble is in byte1, Upper in byte2
            val = (byte2 & 0xF0) | (byte1 & 0x0F)
        else:
            # Odd logic: Upper nibble is in byte1, Lower in byte2
            val = (byte1 & 0xF0) | (byte2 & 0x0F)
        output.append(val)
        toggle = not toggle
    return bytes(output)

# Execution flow
with open("flag.txt", "rb") as f:
    encrypted = f.read()

stage1 = shrink(encrypted) # Reverse 3rd expand
stage2 = shrink(stage1)    # Reverse 2nd expand
stage3 = shrink(stage2)    # Reverse 1st expand
flag = flipBits(stage3)    # Reverse flipBits

print(flag.decode())
```

<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-06-51" src="https://github.com/user-attachments/assets/f24f39c7-2247-46fd-af14-43ef673a2814" />

<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-07-31" src="https://github.com/user-attachments/assets/d1936787-ae1d-413f-8e6f-771126444fb0" />

<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-07-43" src="https://github.com/user-attachments/assets/1c8e9b1f-456f-4dc7-9c83-e690e4d4b771" />

<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-07-54" src="https://github.com/user-attachments/assets/f8be31f4-7985-4acb-af67-a78a0eb5ecd3" />

<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-28-40" src="https://github.com/user-attachments/assets/08067a2b-8e24-433b-914b-1f09839070e8" />

<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-44-03" src="https://github.com/user-attachments/assets/e56355c3-becf-460a-a643-af7b2ea22f46" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-44-14" src="https://github.com/user-attachments/assets/1c1f7c77-fb01-4535-a00f-3afd2e5426cd" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 18-47-51" src="https://github.com/user-attachments/assets/323502e4-0ad8-4bdc-8d06-3034c99ed5ac" />

```
psnova@FORBIDDEN-DIMENSION:~/Downloads$ file disorder 
disorder: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=f889e30b5b0d5265c47d47f04584385c9e25fee6, for GNU/Linux 3.2.0, not stripped
psnova@FORBIDDEN-DIMENSION:~/Downloads$ file flag.txt 
flag.txt: data
psnova@FORBIDDEN-DIMENSION:~/Downloads$ ./disorder

May Jupiter strike you down Caeser before you seize the treasury!! You will have to tear me apart
for me to tell you the flag to unlock the Roman Treasury and fund your civil war. I, Lucius Caecilius
Metellus, shall not let you pass until you get this password right. (or threaten to kill me-)

Segmentation fault (core dumped)
psnova@FORBIDDEN-DIMENSION:~/Downloads$ strings disorder | less
psnova@FORBIDDEN-DIMENSION:~/Downloads$ sudo snap install ghidra
[sudo] password for psnova: 
ghidra 11.4 from David Lane (dclane) installed
psnova@FORBIDDEN-DIMENSION:~/Downloads$ python 3 rev\ disorder.py 
Command 'python' not found, did you mean:
  command 'python3' from deb python3
  command 'python' from deb python-is-python3
psnova@FORBIDDEN-DIMENSION:~/Downloads$ python3 rev\ disorder.py 
sunshine{C3A5ER_CR055ED_TH3_RUB1C0N}
```

## Flag:

```
sunshine{C3A5ER_CR055ED_TH3_RUB1C0N}
```

## Concepts learnt:

ELF analysis

Using strings

using Ghidra

Python program

## Resources:
[general definitions](https://google.com)
[Ghidra](https://ghidra-sre.org/)
[Reverse engineering](https://picoctf.org/resources)



***
# 2. worthy.knight

## Solution:
Doing the Previous challenge made this easier It was easy after identifying the ffile type I directly jumped into ghidra.I ran the programn It was asking for a Phrase od 10 letter that was what we had to find out. After running the file in ghidra I came to know that program was doping literal character match with half charactter directly given and restod them by XOR. i manually did that and got many  output but the final that worked was 
NjkSfTYaIi.
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-20-22" src="https://github.com/user-attachments/assets/31d6e6ec-e5cf-4212-aaca-72380144408f" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-20-26" src="https://github.com/user-attachments/assets/be6fc252-a5f5-4cb0-a653-6745397cb44c" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-20-33" src="https://github.com/user-attachments/assets/8d0f4e88-a3b7-4a76-9089-92b563eaea46" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-22-01" src="https://github.com/user-attachments/assets/561d7eae-bbad-4251-987d-1b801bcecbe7" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-25-47" src="https://github.com/user-attachments/assets/b5224966-450e-40c5-a631-cb28990915a9" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-25-56" src="https://github.com/user-attachments/assets/75694e9a-bcaf-48b1-9b19-e46c1d18f210" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-26-04" src="https://github.com/user-attachments/assets/1ca46b13-d2ba-4ecd-b48e-62ebac79e6fa" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-26-12" src="https://github.com/user-attachments/assets/d4fc303e-acca-4216-aee7-a1f514305f20" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-26-22" src="https://github.com/user-attachments/assets/fc605ee1-9503-4ab9-82f9-4d32f68864e5" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-26-29" src="https://github.com/user-attachments/assets/c889c7ac-e986-4df4-a423-69c1390c8b45" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-26-40" src="https://github.com/user-attachments/assets/8a1ca54d-e463-4767-8361-a6b7e3eb619e" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-27-04" src="https://github.com/user-attachments/assets/bb0ff714-d213-4a01-a475-de2d87f3a4a0" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-27-13" src="https://github.com/user-attachments/assets/dd847c34-5ac3-473e-98ea-030e1caf6246" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-27-23" src="https://github.com/user-attachments/assets/bd90f23c-b859-47f7-b030-f072430e9153" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-27-32" src="https://github.com/user-attachments/assets/1c44a905-f688-46e6-b06e-8374d25326a7" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-27-39" src="https://github.com/user-attachments/assets/8ca91734-9a01-4733-a6eb-8ddc48dcf924" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-35-07" src="https://github.com/user-attachments/assets/aee89f3b-89fa-4626-b106-6d1cf2f219ed" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-35-20" src="https://github.com/user-attachments/assets/33787e49-846c-4c5a-80fa-6c5ace0f83b2" />
<img width="1920" height="1080" alt="Screenshot From 2025-12-06 19-35-27" src="https://github.com/user-attachments/assets/b2ada991-a3aa-4e72-bbbd-4b53c20b590c" />
<img width="654" height="537" alt="Screenshot From 2025-12-06 19-35-35" src="https://github.com/user-attachments/assets/e14d282e-cba3-421d-a772-f25d32c5517f" />
```
psnova@FORBIDDEN-DIMENSION:~/Downloads$ file worthy.knight 
worthy.knight: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=777ca166efbe8a9cbfdf18c865bad856843d9318, for GNU/Linux 4.4.0, stripped
psnova@FORBIDDEN-DIMENSION:~/Downloads$ ./worthy.knight
bash: ./worthy.knight: Permission denied
psnova@FORBIDDEN-DIMENSION:~/Downloads$ strings worthy.knight | less
psnova@FORBIDDEN-DIMENSION:~/Downloads$ chmod +x worthy.knight 
psnova@FORBIDDEN-DIMENSION:~/Downloads$ ./worthy.knight 
```

## Flag:

```
KCTF{NjkSfTYaIi}
```

## Concepts learnt:

ELF analysis

XOR based constraints

using Ghidra

Brute forcing

## Resources:
[general definitions](https://google.com)
[Ghidra](https://ghidra-sre.org/)
[Reverse engineering](https://picoctf.org/resources)


***
# 3. time

## Solution:
started with ```file time``` to learn its an unstripped linux ex. ran it and figured out it needed me to guess a random number. it then printed out the random number and gave the correct/incorrect message by comparing the random number. the best method here was to use gdb and set a breakpoint after the number was generated and before it asked for the input.

``` 


(gdb) disas main
Dump of assembler code for function main:
   0x000000000040092b <+0>:     push   %rbp
   0x000000000040092c <+1>:     mov    %rsp,%rbp
   0x000000000040092f <+4>:     sub    $0x20,%rsp
   0x0000000000400933 <+8>:     mov    %edi,-0x14(%rbp)
   0x0000000000400936 <+11>:    mov    %rsi,-0x20(%rbp)
   0x000000000040093a <+15>:    mov    %fs:0x28,%rax
   0x0000000000400943 <+24>:    mov    %rax,-0x8(%rbp)
   0x0000000000400947 <+28>:    xor    %eax,%eax
   0x0000000000400949 <+30>:    mov    $0x0,%edi
   0x000000000040094e <+35>:    call   0x400750 <time@plt>
   0x0000000000400953 <+40>:    mov    %eax,%edi
   0x0000000000400955 <+42>:    call   0x400730 <srand@plt>
   0x000000000040095a <+47>:    call   0x400790 <rand@plt>
   0x000000000040095f <+52>:    mov    %eax,-0xc(%rbp)
   0x0000000000400962 <+55>:    lea    0x1c7(%rip),%rdi        # 0x400b30
   0x0000000000400969 <+62>:    call   0x4006e0 <puts@plt>
   0x000000000040096e <+67>:    lea    0x1e3(%rip),%rdi        # 0x400b58
   0x0000000000400975 <+74>:    call   0x4006e0 <puts@plt>
   0x000000000040097a <+79>:    lea    0x207(%rip),%rdi        # 0x400b88
   0x0000000000400981 <+86>:    call   0x4006e0 <puts@plt>
   0x0000000000400986 <+91>:    lea    0x21b(%rip),%rdi        # 0x400ba8
   0x000000000040098d <+98>:    mov    $0x0,%eax
   0x0000000000400992 <+103>:   call   0x400710 <printf@plt>
   0x0000000000400997 <+108>:   mov    0x2006ea(%rip),%rax        # 0x601088 <stdout@@GLIBC_2.2.5>
   0x000000000040099e <+115>:   mov    %rax,%rdi
   0x00000000004009a1 <+118>:   call   0x400760 <fflush@plt>
   0x00000000004009a6 <+123>:   lea    -0x10(%rbp),%rax
   0x00000000004009aa <+127>:   mov    %rax,%rsi
--Type <RET> for more, q to quit, c to continue without paging--break *0x400992
   0x00000000004009ad <+130>:   lea    0x208(%rip),%rdi        # 0x400bbc
   0x00000000004009b4 <+137>:   mov    $0x0,%eax
   0x00000000004009b9 <+142>:   call   0x400780 <__isoc99_scanf@plt>
   0x00000000004009be <+147>:   mov    -0x10(%rbp),%eax
   0x00000000004009c1 <+150>:   mov    %eax,%esi
   0x00000000004009c3 <+152>:   lea    0x1f5(%rip),%rdi        # 0x400bbf
   0x00000000004009ca <+159>:   mov    $0x0,%eax
   0x00000000004009cf <+164>:   call   0x400710 <printf@plt>
   0x00000000004009d4 <+169>:   mov    -0xc(%rbp),%eax
   0x00000000004009d7 <+172>:   mov    %eax,%esi
   0x00000000004009d9 <+174>:   lea    0x1f3(%rip),%rdi        # 0x400bd3
   0x00000000004009e0 <+181>:   mov    $0x0,%eax
   0x00000000004009e5 <+186>:   call   0x400710 <printf@plt>
   0x00000000004009ea <+191>:   mov    0x200697(%rip),%rax        # 0x601088 <stdout@@GLIBC_2.2.5>
   0x00000000004009f1 <+198>:   mov    %rax,%rdi
   0x00000000004009f4 <+201>:   call   0x400760 <fflush@plt>
   0x00000000004009f9 <+206>:   mov    -0x10(%rbp),%eax
   0x00000000004009fc <+209>:   cmp    %eax,-0xc(%rbp)
   0x00000000004009ff <+212>:   jne    0x400a14 <main+233>
   0x0000000000400a01 <+214>:   lea    0x1e0(%rip),%rdi        # 0x400be8
   0x0000000000400a08 <+221>:   call   0x4006e0 <puts@plt>
   0x0000000000400a0d <+226>:   call   0x400877 <giveFlag>
   0x0000000000400a12 <+231>:   jmp    0x400a20 <main+245>
   0x0000000000400a14 <+233>:   lea    0x1fd(%rip),%rdi        # 0x400c18
   0x0000000000400a1b <+240>:   call   0x4006e0 <puts@plt>
   0x0000000000400a20 <+245>:   mov    0x200661(%rip),%rax        # 0x601088 <stdout@@GLIBC_2.2.5>
   0x0000000000400a27 <+252>:   mov    %rax,%rdi
   0x0000000000400a2a <+255>:   call   0x400760 <fflush@plt>
   0x0000000000400a2f <+260>:   mov    $0x0,%eax
   0x0000000000400a34 <+265>:   mov    -0x8(%rbp),%rdx
   0x0000000000400a38 <+269>:   xor    %fs:0x28,%rdx
   0x0000000000400a41 <+278>:   je     0x400a48 <main+285>
   0x0000000000400a43 <+280>:   call   0x400700 <__stack_chk_fail@plt>
--Type <RET> for more, q to quit, c to continue without paging--c
   0x0000000000400a48 <+285>:   leave
   0x0000000000400a49 <+286>:   ret
End of assembler dump.
(gdb) break *0x400992
Breakpoint 1 at 0x400992
(gdb) run
Starting program: /mnt/c/Users/chatu/OneDrive/Desktop/jtp2/challenge_files/reveng/time/time
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Welcome to the number guessing game!
I'm thinking of a number. Can you guess it?
Guess right and you get a flag!

Breakpoint 1, 0x0000000000400992 in main ()
(gdb) x/d $rbp-0xc
0x7fffffffdfb4: 2088080361
(gdb) c
Continuing.
Enter your number: 2088080361
Your guess was 2088080361.
Looking for 2088080361.
You won. Guess was right! Here's your flag:
Flag file not found!  Contact an H3 admin for assistance.
[Inferior 1 (process 2170) exited normally]
(gdb)




```

i figured when the random number was being stored, and then set a breakpoint and ran the code. 
``` (gdb) break *0x400992 ```
next, i had to print the stored random number. this was doing using
``` (gdb) x/d $rbp-0xc ```

giving me the number 2088080361 
i then inputted this number in the program giving me the success message.

no flag was generated here but the success message was enough to pass.
## Flag: 
n/a
## Concepts Learnt: 

## Notes:

## Resources: 
gdb


x------------------------------------------------------------------------------------------------------x

# 4. Verdis Quo

## Solution:
started with installing the apk and launching the app. i realised it opened and closed instantly, prompting a too slow message. next i opened the file up in jadx to look at the source code. i looked at the main function(entry point function) called mainactivity.java
The program immediately calls ```util.cleanUp()``` before setting a default failure message.
looking at the decompiled code in Utilities.java. The cleanUp() function contains some lines of code all setting parts of the flag to ' '
or basically erasing it. this meant the flag had to be stored somewhere. i next went to the layout file res/layout/activity_main.xml

here i found the flag hardcoded, but looking at the letters, they were jumbled up. i put this in gpt to figure out a possible readable combination, and got the flag.

## Flag: 
byuctf{decryption_is_difficult_4u}

## Concepts Learnt: 
reading jdk and android development.

## Notes:

## Resources: 
jdk
bluestacks


# 5. Dusty

## Solution:




## Flag: 

## Concepts Learnt: 

## Notes:

## Resources: 

