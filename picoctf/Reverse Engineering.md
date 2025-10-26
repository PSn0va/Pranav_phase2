# 1. GDB baby step 1

Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.

## Solution:

Ahh!It was an easy challenge but hard at the same time since I did not know anything of rev engineering before this. First I thought the file wasn't executablea but it was so my chmod command was all for naught 
then I had to go for gdb where I first started the programs then I disassembled the whole thing then there was a block of info( I didn't know anything about it ) then I googled everything, I came to know we have to just move forward by using stepi untl I bypass the mov eax value which returns the value. Then final step info registers eax that shows the EAX register ..... Task isn't over yet the value was in hexadecimal convert that into decimal then you get the answer.  

```
chmod +x ./Downloads/debugger0_a
gdb ./Downloads/debugger0_a
(gdb) start
(gdb) disassemble main
(gdb) stepi
(gdb) stepi
(gdb) stepi
(gdb) info registers eax
```

## Flag:

```
picoCTF{549698}
```

## Concepts learnt:
GDB - GNU debugger - inspect and control program runtime(pause,step,inspect memory,register,disassemble)
EAX register- 32 bit general purpose register - tiny storage - holds return values of function
Disassembling of the program
GDB commands
Identifying type of data

## Resources:
[general definitions](https://google.com)
[GDB commands](https://www.gnu.org/software/gdb/documentation/)
[Reverse engineering](https://picoctf.org/resources)



***
# 2. ARMssembly1

For what argument does this program print `win` with variables 79, 7 and 3? File: chall_1.S Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

## Solution:

The hell now we have to learn a whole new language that also a low level one that is not meant for humans but the machines....For this challenge we were given a whole program arm assembly language consisting of function and the main. First let's go with the function (to decode I had to search every single line again and again) (sub sp, sp, #32 was for making 32 bytes space on the stack(notepad), then w0 is a register in which we store the input value by using str w0, [sp, 12] at position 12 then similiarly we stored 79 at 16 ,7 at 20 and 2 at 24 pos. Then ldr was used to load the value 7 in w0 and 79 in w1 and then lsl was used tp shift 79 to left by 7 position that means 79*128=10112 which was stored at pos 28 using w0. Then again ldr was used to load 10112 in w1 and 3 in w0 the sdiv was used to divide the 10112 by 3 which is equal to 3370 and was stored at pos 28 using w0. Now we use ldr again to load the input value in w0 and 3370 in w1 then sub was used subtract input value from 3370 and the result wa stored on pos 28 using w0 then at the end of the function we used ldr to load the result and returning it to main.
NOW Let's talk about what is going on in main function it takes the first number user typed in command kine turn it from text string into real number using ldr and bl atoi(used to conavert it into integer) then we load input value usiong ldr and run the function mentioned above, func gives us result which main compares with 0 and iid its not equal bne is ued for that condition to jump and give output You lose:( and if it is equal then we get win message. SO as mentioned in the question we have to get the win message so for that input will be 3370 which in hexadecimal is d2a for flag will be written in eight digit 00000d2a ,hence now we got the flag.
 
## Flag:

```
picoCTF{00000d2a}
```

## Concepts learnt:
ARM assembly- Programming language for ARM CPUs- low level language that directly controls the CPU.
ARM assembly  instructions (mov- assign value,add,sub,ldr-load a no. from memory,str- store into memory,bne- jump somwhere if not equal,ret-return from a function,cmp-compare,bne-conditional,bl-branch with link(call a function),bx lr- return from function)




## Resources:
[general definitions](https://google.com)
[assembly tutorial](https://thinkingeek.com/arm-assembler-raspberry-pi-tutorial/)

