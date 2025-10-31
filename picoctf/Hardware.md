# 1. IQ Test

> let your input x = 30478191278.
wrap your answer with nite{ } for the flag.
As an example, entering x = 34359738368 gives (y0, ..., y11), so the flag would be nite{010000000011}.


## Solution:
Changed the decimal to binary first and then I had to borroe Ipad from my friend to annotate the file and get the answer.
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 22-51-04" src="https://github.com/user-attachments/assets/8b64f197-f0ee-44fa-9563-517567b89776" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 23-17-58" src="https://github.com/user-attachments/assets/61eb09d1-80e6-40e0-911c-658c1f463876" />
<img width="1920" height="1080" alt="screenshot"
src="https://github.com/user-attachments/assets/0af298ef-07ef-4b64-8af3-5141a6fa94ea" />

## Flag:

```
niteCTF{100010011000}
```

## Concepts learnt:
LOGIC GATES

## Resources:
-nil-
***



# 2. I like logic

> i like logic and i like files, apparently, they have something in common, what should my next step be.


## Solution:
I just extracted the file but I didn't know what to do with them next I opened up the json file since I couldn't open any of the others, it showed some of the data I didn't know what it was I used AI and and it mentioned UART then i asked him how to dcode the files . It mentioned using Logic 2 and Async analyser to analyse files hidden data that is being sent over UART bus, setting up Logic 2 was a task  too but I did It while searching here there next it wasn't even taking the extracted folder I use zip file and then used Async for channel 3 that was the only one highlighted It gave me a full text in which the flag like text was present and then I did it.
```
chmod +x logic2.AppImage
chmod +x Logic-2.4.36-linux-x64.AppImage 
./Logic-2.4.36-linux-x64.AppImage 
sudo apt update
sudo apt install libnss3 libasound2 libxss1 libappindicator3-1 libindicator3-7 xdg-utils
./Logic-2.4.36-linux-x64.AppImage 
sudo apt update
sudo apt install libfuse2
./Logic-2.4.36-linux-x64.AppImage 
./Logic-2.4.36-linux-x64.AppImage --no-sandbox
```
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 23-49-22" src="https://github.com/user-attachments/assets/019c8130-e03e-4419-b934-7b5d907dd232" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 23-49-30" src="https://github.com/user-attachments/assets/be079243-15f7-431b-bb0b-8d252c8c4b32" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 23-49-38" src="https://github.com/user-attachments/assets/75a79eb6-5c3c-4b99-b759-eb32761a0dca" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 23-49-58" src="https://github.com/user-attachments/assets/3a6bede3-1276-4939-af10-507af58ce4ac" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-31 23-50-11" src="https://github.com/user-attachments/assets/b81b719a-2e3b-4cfc-a72f-1ee013e240e3" />

## Flag:

```
FCSC{b1dee4eeadf6c4e60aeb142b0b486344e64b12b40d1046de95c89ba5e23a9925}
```

## Concepts learnt:
Understanding File Formats

Extracting and Inspecting Archive Contents

Digital Logic Capture Files

UART (Universal Asynchronous Receiver/Transmitter)

Using Logic Analyzer

Linux & Debugging Concepts

## Resources:
[Basic Definition](https://www.google.com/)
[Logic2](https://www.saleae.com/support)
[UART](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter)
Youtube
***


# 3. Bare Metal Alchemist

> my friend recommended me this anime but i think i've heard a wrong name.


## Solution:
I tried to execute it first but it didn't work then I searched how to analyse the file then I cam to know of Radare 2. Then I listed all the functions to look for some sort of main or decrypt_flag kinda function. Shifted to main using s main and I did ran A decompiler but didn't understand even a bit. The orphan loop is where the decryption was happening and 0x68 was the address were the decryption was being stored so tried printing that but failed. Then used psx 44 @ 0x68 which would print 44 bytes of the string. gave the output toapython script and ran that top get the flag.

```
psnova@FORBIDDEN-DIMENSION:~/Downloads$ sudo apt install radare2
[sudo] password for psnova: 
Installing:                     
  radare2

Installing dependencies:
  libcapstone-dev  libradare2-5.0.0t64  libuv1-dev     libzip5   ziptool
  liblz4-dev       libradare2-common    libxxhash-dev  zipcmp
  libmagic-dev     libradare2-dev       libzip-dev     zipmerge

Suggested packages:
  libuv1-doc

Summary:
  Upgrading: 0, Installing: 14, Removing: 0, Not Upgrading: 2
  Download size: 9,462 kB
  Space needed: 49.6 MB / 40.1 GB available

Continue? [Y/n] Y
Get:1 https://ftp.iitm.ac.in/ubuntu plucky/universe amd64 libcapstone-dev amd64 5.0.5-1 [1,039 kB]
Get:2 https://ftp.iitm.ac.in/ubuntu plucky/main amd64 libmagic-dev amd64 1:5.45-3build1 [105 kB]
Get:3 https://ftp.iitm.ac.in/ubuntu plucky/universe amd64 libzip5 amd64 1.11.3-2 [70.3 kB]
Get:4 http://ftp.iitm.ac.in/ubuntu plucky-updates/universe amd64 libradare2-common all 5.9.8+dfsg-2ubuntu0.25.04.1 [2,060 kB]
Get:5 http://ftp.iitm.ac.in/ubuntu plucky-updates/universe amd64 libradare2-5.0.0t64 amd64 5.9.8+dfsg-2ubuntu0.25.04.1 [5,177 kB]
Get:6 https://ftp.iitm.ac.in/ubuntu plucky/main amd64 libuv1-dev amd64 1.50.0-2ubuntu1 [145 kB]
Get:7 https://ftp.iitm.ac.in/ubuntu plucky/main amd64 libxxhash-dev amd64 0.8.3-2 [80.6 kB]  
Get:8 https://ftp.iitm.ac.in/ubuntu plucky/main amd64 liblz4-dev amd64 1.10.0-4 [92.3 kB]    
Get:9 https://ftp.iitm.ac.in/ubuntu plucky/universe amd64 zipcmp amd64 1.11.3-2 [16.0 kB]    
Get:10 https://ftp.iitm.ac.in/ubuntu plucky/universe amd64 zipmerge amd64 1.11.3-2 [9,072 B] 
Get:11 https://ftp.iitm.ac.in/ubuntu plucky/universe amd64 ziptool amd64 1.11.3-2 [17.6 kB]  
Get:12 https://ftp.iitm.ac.in/ubuntu plucky/universe amd64 libzip-dev amd64 1.11.3-2 [175 kB]
Get:13 http://ftp.iitm.ac.in/ubuntu plucky-updates/universe amd64 libradare2-dev amd64 5.9.8+dfsg-2ubuntu0.25.04.1 [247 kB]
Get:14 http://ftp.iitm.ac.in/ubuntu plucky-updates/universe amd64 radare2 amd64 5.9.8+dfsg-2ubuntu0.25.04.1 [227 kB]
Fetched 9,462 kB in 8s (1,245 kB/s)                                                          
Selecting previously unselected package libcapstone-dev:amd64.
(Reading database ... 332371 files and directories currently installed.)
Preparing to unpack .../00-libcapstone-dev_5.0.5-1_amd64.deb ...
Unpacking libcapstone-dev:amd64 (5.0.5-1) ...
Selecting previously unselected package libmagic-dev:amd64.
Preparing to unpack .../01-libmagic-dev_1%3a5.45-3build1_amd64.deb ...
Unpacking libmagic-dev:amd64 (1:5.45-3build1) ...
Selecting previously unselected package libzip5:amd64.
Preparing to unpack .../02-libzip5_1.11.3-2_amd64.deb ...
Unpacking libzip5:amd64 (1.11.3-2) ...
Selecting previously unselected package libradare2-common.
Preparing to unpack .../03-libradare2-common_5.9.8+dfsg-2ubuntu0.25.04.1_all.deb ...
Unpacking libradare2-common (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Selecting previously unselected package libradare2-5.0.0t64:amd64.
Preparing to unpack .../04-libradare2-5.0.0t64_5.9.8+dfsg-2ubuntu0.25.04.1_amd64.deb ...
Unpacking libradare2-5.0.0t64:amd64 (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Selecting previously unselected package libuv1-dev:amd64.
Preparing to unpack .../05-libuv1-dev_1.50.0-2ubuntu1_amd64.deb ...
Unpacking libuv1-dev:amd64 (1.50.0-2ubuntu1) ...
Selecting previously unselected package libxxhash-dev:amd64.
Preparing to unpack .../06-libxxhash-dev_0.8.3-2_amd64.deb ...
Unpacking libxxhash-dev:amd64 (0.8.3-2) ...
Selecting previously unselected package liblz4-dev:amd64.
Preparing to unpack .../07-liblz4-dev_1.10.0-4_amd64.deb ...
Unpacking liblz4-dev:amd64 (1.10.0-4) ...
Selecting previously unselected package zipcmp.
Preparing to unpack .../08-zipcmp_1.11.3-2_amd64.deb ...
Unpacking zipcmp (1.11.3-2) ...
Selecting previously unselected package zipmerge.
Preparing to unpack .../09-zipmerge_1.11.3-2_amd64.deb ...
Unpacking zipmerge (1.11.3-2) ...
Selecting previously unselected package ziptool.
Preparing to unpack .../10-ziptool_1.11.3-2_amd64.deb ...
Unpacking ziptool (1.11.3-2) ...
Selecting previously unselected package libzip-dev:amd64.
Preparing to unpack .../11-libzip-dev_1.11.3-2_amd64.deb ...
Unpacking libzip-dev:amd64 (1.11.3-2) ...
Selecting previously unselected package libradare2-dev.
Preparing to unpack .../12-libradare2-dev_5.9.8+dfsg-2ubuntu0.25.04.1_amd64.deb ...
Unpacking libradare2-dev (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Selecting previously unselected package radare2.
Preparing to unpack .../13-radare2_5.9.8+dfsg-2ubuntu0.25.04.1_amd64.deb ...
Unpacking radare2 (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Setting up libuv1-dev:amd64 (1.50.0-2ubuntu1) ...
Setting up libzip5:amd64 (1.11.3-2) ...
Setting up libradare2-common (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Setting up libmagic-dev:amd64 (1:5.45-3build1) ...
Setting up zipmerge (1.11.3-2) ...
Setting up libradare2-5.0.0t64:amd64 (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Setting up radare2 (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Setting up libxxhash-dev:amd64 (0.8.3-2) ...
Setting up zipcmp (1.11.3-2) ...
Setting up ziptool (1.11.3-2) ...
Setting up libcapstone-dev:amd64 (5.0.5-1) ...
Setting up libzip-dev:amd64 (1.11.3-2) ...
Setting up liblz4-dev:amd64 (1.10.0-4) ...
Setting up libradare2-dev (5.9.8+dfsg-2ubuntu0.25.04.1) ...
Processing triggers for man-db (2.13.0-1) ...
Processing triggers for libc-bin (2.41-6ubuntu1.2) ...
psnova@FORBIDDEN-DIMENSION:~/Downloads$ radare2
Usage: r2 [-ACdfjLMnNqStuvwzX] [-P patch] [-p prj] [-a arch] [-b bits] [-c cmd]
          [-s addr] [-B baddr] [-m maddr] [-i script] [-e k=v] file|pid|-|--|=
psnova@FORBIDDEN-DIMENSION:~/Downloads$ r2 firmware.elf 
WARN: Relocs has not been applied. Please use `-e bin.relocs.apply=true` or `-e bin.cache=true` next time
^C
[0x00000000]> 
^C
[0x00000000]> 
^C
[0x00000000]> 
[0x00000000]> q
psnova@FORBIDDEN-DIMENSION:~/Downloads$ r2 -a firmware.elf 
ERROR: Cannot find 'firmware.elf' arch plugin. See rasm2 -L or -LL
WARN: Cannot find asm.parser for firmware.elf.pseudo
ERROR: Missing file to open
psnova@FORBIDDEN-DIMENSION:~/Downloads$ r2 -A firmware.elf 
WARN: Relocs has not been applied. Please use `-e bin.relocs.apply=true` or `-e bin.cache=true` next time
INFO: Analyze all flags starting with sym. and entry0 (aa)
INFO: Analyze imports (af@@@i)
INFO: Analyze entrypoint (af@ entry0)
WARN: select the calling convention with `e anal.cc=?`
INFO: Analyze symbols (af@@@s)
INFO: Analyze all functions arguments/locals (afva@@@F)
INFO: Analyze function calls (aac)
INFO: Analyze len bytes of instructions for references (aar)
INFO: Finding and parsing C++ vtables (avrr)
INFO: Analyzing methods (af @@ method.*)
INFO: Emulate functions to find computed references (aaef)
INFO: Recovering local variables (afva@@@F)
INFO: Type matching analysis for all functions (aaft)
INFO: Propagate noreturn information (aanr)
INFO: Integrate dwarf function information
INFO: Use -AA or aaaa to perform additional experimental analysis
INFO: Finding xrefs in noncode sections (e anal.in=io.maps.x; aav)
WARN: Skipping aav because base address is zero. Use -B 0x800000 or aav0
[0x00000000]> afl
0x00000000    8     62 entry0
0x000000d4    1     14 sym.z1__
0x00000176   38    362 main
0x000000e2    4    148 sym.__vector_16
[0x00000000]> s main
[0x00000176]> pdc
 // callconv: r24 reg (r25, r24, r23, r22);
int main (int argc, char **argv, char **envp) {
    loc_0x00000176:
        // CALL XREF from entry0 @ 0xc8(x)
        push(r28)
        push(r29)
        goto 0x17c    // 0x17c(0x0, 0x0, 0x0, 0x0)
        // CALL XREF from main @ 0x17a(x)
        r28 = 0x3d    // IO SPL: Stack lower bits SP0-SP7
        r29 = 0x3e    // IO SPH: Stack higher bits SP8-SP10
        i = 1         // sph
        r24 = 0x24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 |= 0x02   // loc.__zero_reg__ // loc.__zero_reg__
        0x24 = r24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 = 0x24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        0x24 = r24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 = 0x25    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 |= 0x02   // loc.__zero_reg__ // loc.__zero_reg__
        0x25 = r24    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 = 0x25    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        0x25 = r24    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 = *(0x6e)
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x6e) = r24
        *(0x81) = r1
        r24 = *(0x81)
        r24 |= 0x02   // "K"
        *(0x81) = r24
        r24 = *(0x81)  // "K"
        r24 |= 0x01   // loc.__FUSE_REGION_LENGTH__
        *(0x81) = r24
        r24 = *(0x80)  // sph
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x80) = r24 // sph
        r24 = *(0xb1)
        r24 |= 0x04   // loc.__zero_reg__ // loc.__zero_reg__
        *(0xb1) = r24
        r24 = *(0xb0)
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0xb0) = r24
        r24 = *(0x7a)
        r24 |= 0x04   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        r24 = *(0x7a)
        r24 |= 0x02   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        r24 = *(0x7a)
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        r24 = *(0x7a)
        r24 |= 0x80   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        *(0xc1) = r1
        r24 = 0x0a    // IO UCSRB: USART Control and Status Register B.
        r24 |= 0xf8   // loc.__zero_reg__ // loc.__zero_reg__
        0xa = r24     // IO UCSRB: USART Control and Status Register B.
        r24 = 0x04    // IO ADCL: ADC Data Register Low byte.
        r24 |= 0x03   // loc.__zero_reg__ // loc.__zero_reg__
        0x4 = r24     // IO ADCL: ADC Data Register Low byte.
        cbi 0xa, 2    // IO UCSRB: USART Control and Status Register B.
        r24 = 0x0b    // IO UCSRA: USART Control and Status Register A.
        r24 &= 0x07
        0xb = r24     // IO UCSRA: USART Control and Status Register A.
        r24 = 0x05    // IO ADCH: ADC Data Register High byte.
        r24 &= 0xfc   // loc.__zero_reg__ // loc.__zero_reg__
        0x5 = r24     // IO ADCH: ADC Data Register High byte.
        r25 = 0xa5
        r11 = r25
        r18 = 0x00
        r12 = r18
        r18 = 0x00
        r13 = r18
    loc_0x0000022c:
        // CODE XREFS from main @ 0x286(x), 0x28c(x)
        r24 = 0x09    // IO UBRRL: USART Baud Rate Registers Low byte. A.k.a setting serial port speed.
        r25 = r24
        r25 <<= 1     // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
        r24 ^= r25    // loc.__zero_reg__
        sbrs r24, 2   // unlikely
        goto loc_0x00000236;
        goto loc_0x00000236;
        return r24;
    loc_0x00000236:
        goto 0x27e
    loc_0x0000027e:
        // CODE XREF from main @ 0x236(x)
        goto sym z1() // sym.z1__ // sym.z1__
        return r24;
    loc_0x00000238:  // orphan
         // CODE XREF from main @ 0x234(x)
         r24 = 0x68               // loc.__trampolines_end
         r14 = r24                // loc.__trampolines_end
         r24 = 0x00
         r15 = r24
         r16 = 0x00
    loc_0x00000242:  // orphan
         // CODE XREF from main @ 0x2de(x)
         r30+1:r30 = r14+1:r14
         r0 = z                   // 0x68 // loc.__trampolines_end
                                  Xf
         r24 &= r24
         if (!var) 
         goto loc_0x00000262
    loc_0x0000024a:  // orphan
         r30 = r24
         r30 ^= r11               // loc.__zero_reg__
         var = r24 - 0xa5         // loc.__zero_reg__ // loc.__zero_reg__
         if (!var) 
         goto loc_0x00000262
    loc_0x00000252:  // orphan
         r24 = 0x09               // IO UBRRL: USART Baud Rate Registers Low byte. A.k.a setting serial port speed.
         r25 = r24
         r25 <<= 1                // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         r24 ^= r25               // loc.__zero_reg__
         sbrc r24, 2              // likely
         goto loc_0x0000025e
    loc_0x0000025c:  // orphan
         goto loc_0x0000028e
    loc_0x0000025e:  // orphan
         // CODE XREF from main @ 0x25a(x)
    loc_0x00000262:  // orphan
         // CODE XREFS from main @ 0x248(x), 0x250(x)
         *(y+2) = r1
         *(y+1) = r1
    loc_0x00000266:  // orphan
         // CODE XREF from main @ 0x27c(x)
         r24 = *(y+1)
         r25 = *(y+2)
         var = r24 - 0x2c         // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         r25 -= (0x01 + carry)    // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         brcc 0x282               // unlikely
         goto loc_0x00000282
    loc_0x00000270:  // orphan
         r24 = *(y+1)
         r25 = *(y+2)
         r24+1:r24 += 0x01        // loc.__zero_reg__
         *(y+2) = r25
         *(y+1) = r24
         goto loc_0x00000266
    loc_0x0000027e:  // orphan
         // CODE XREF from main @ 0x236(x)
    loc_0x00000282:  // orphan
         // CODE XREF from main @ 0x26e(x)
         var = r12 - r1           // loc.__zero_reg__
         var = r13 - r1 - carry   // loc.__zero_reg__
         if (!var) 
         goto loc_0x0000022c
    loc_0x00000288:  // orphan
              // goto loc_0x22c
         goto loc_0x0000022c
    loc_0x0000028e:  // orphan
         // CODE XREF from main @ 0x25c(x)
         r30 -= 0x30              // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         r17 = 0x00
         var = r30 - 0x4e         // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         brcc 0x29e               // likely
         goto loc_0x0000029e
    loc_0x00000296:  // orphan
         r31 = 0x00
         r30 -= 0x00              // loc.__zero_reg__
         r31 -= (0xff + carry)    // loc.__zero_reg__ // loc.__zero_reg__
         r17 = *(z)
    loc_0x0000029e:  // orphan
         // CODE XREF from main @ 0x294(x)
              sbrc r17, 0              // likely
         goto loc_0x000002a6
    loc_0x000002a4:  // orphan
         sbi 0xb, 3               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002a6:  // orphan
         // CODE XREF from main @ 0x2a2(x)
         sbrc r17, 1              // likely
         goto loc_0x000002aa
    loc_0x000002a8:  // orphan
         sbi 0xb, 4               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002aa:  // orphan
         // CODE XREF from main @ 0x2a6(x)
         sbrc r17, 2              // likely
         goto loc_0x000002ae
    loc_0x000002ac:  // orphan
         sbi 0xb, 5               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002ae:  // orphan
         // CODE XREF from main @ 0x2aa(x)
         sbrc r17, 3              // likely
         goto loc_0x000002b2
    loc_0x000002b0:  // orphan
         sbi 0xb, 6               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002b2:  // orphan
         // CODE XREF from main @ 0x2ae(x)
         sbrc r17, 4              // likely
         goto loc_0x000002b6
    loc_0x000002b4:  // orphan
         sbi 0xb, 7               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002b6:  // orphan
         // CODE XREF from main @ 0x2b2(x)
         sbrc r17, 5              // likely
         goto loc_0x000002ba
    loc_0x000002b8:  // orphan
         sbi 0x5, 0               // IO ADCH: ADC Data Register High byte.
    loc_0x000002ba:  // orphan
         // CODE XREF from main @ 0x2b6(x)
         sbrc r17, 6              // likely
         goto loc_0x000002be
    loc_0x000002bc:  // orphan
         sbi 0x5, 1               // IO ADCH: ADC Data Register High byte.
    loc_0x000002be:  // orphan
         // CODE XREF from main @ 0x2ba(x)
         r24 = r16
         r24 &= 0x1f              // loc.__zero_reg__
         r24 -= 0xd3              // loc.__zero_reg__ // loc.__zero_reg__
    loc_0x000002c4:  // orphan
         // CODE XREF from main @ 0x2d4(x)
         r24 -= 0x01              // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         brcs 0x2d6               // likely
         goto loc_0x000002d6
    loc_0x000002c8:  // orphan
         r30 = 0x9f
         r31 = 0x0f
    loc_0x000002cc:  // orphan
         // CODE XREF from main @ 0x2ce(x)
         r30+1:r30 -= 0x01        // loc.__zero_reg__ // loc.__zero_reg__
         if (var) 
         goto loc_0x000002cc
    loc_0x000002d0:  // orphan
    loc_0x000002d2:  // orphan
         // CODE XREF from main @ 0x2d0(x)
         goto loc_0x000002c4
    loc_0x000002d6:  // orphan
         // CODE XREF from main @ 0x2c6(x)
         r31 = 0xff
         r14 -= r31               // loc.__zero_reg__ // loc.__zero_reg__
         r15 -= (r31 + carry)     // loc.__zero_reg__
         r16 -= 0xdb              // loc.__zero_reg__ // loc.__zero_reg__
         goto loc_0x00000242
}
[0x00000176]> ps @ 0x68

[0x00000176]> psx 44 @ 0x68
ERROR: Invalid command 'psx 44 @ 0x68' (0x16)
[0x00000176]> ps 44 @ 0x68
ERROR: Invalid command 'ps 44 @ 0x68' (0x16)
[0x00000176]> ps 44 @ 0x64
ERROR: Invalid command 'ps 44 @ 0x64' (0x16)
[0x00000176]> ps 44 @ 0x16
ERROR: Invalid command 'ps 44 @ 0x16' (0x16)
[0x00000176]> psx 44 @ 0x16
ERROR: Invalid command 'psx 44 @ 0x16' (0x16)
[0x00000176]> # 1. IQ test 
[0x00000176]> 
[0x00000176]> > let your input x = 30478191278.
[0x00000176]> 
[0x00000176]> wrap your answer with nite{ } for the flag.
[0x00000176]> 
[0x00000176]> As an example, entering x = 34359738368 gives (y0, ..., y11), so the flag would be nite{010000000011}.
ERROR: Invalid command 'As an example, entering x = 34359738368 gives (y0, ..., y11), so the flag would be nite{010000000011}.' (0x41)
[0x00000176]> 
[0x00000176]> ## Solution:
[0x00000176]> 
[0x00000176]> - Changed the decimal to binary first using an online tool.
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> <img width="1280" height="832" alt="Screenshot 2025-10-31 at 8 18 07 PM" src="https://github.com/user-attachments/assets/ba1933d4-4bb2-4fff-b6f1-1cdfb11e131b" />
ERROR: No output?
[0x00000176]> img width="1280" height="832" alt="Screenshot 2025-10-31 at 8 18 07 PM" src="https://github.com/user-attachments/assets/ba1933d4-4bb2-4fff-b6f1-1cdfb11e131b" /
[Memory]

[0x00000176]> - Took a printout the the png file to manually solve the problem 
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> ![WhatsApp Image 2025-10-31 at 20 20 02](https://github.com/user-attachments/assets/54b56542-3c3c-4fda-95bb-3b87bf1144f3)
sh: 1: Syntax error: "(" unexpected
[0x00000176]> 
[0x00000176]> ## Flag:
[0x00000176]> 
[0x00000176]> ```
ERROR: Invalid command '```' (0x60)
[0x00000176]> niteCTF{100010011000}
ERROR: Invalid command 'niteCTF{100010011000}' (0x6e)
[0x00000176]> ```
ERROR: Invalid command '```' (0x60)
[0x00000176]> 
[0x00000176]> ## Concepts learnt:
[0x00000176]> 
[0x00000176]> - Logic gates
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> ## Notes:
[0x00000176]> 
[0x00000176]> - NONE
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> ## Resources:
[0x00000176]> 
[0x00000176]> - NONE
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> 
[0x00000176]> ***
0x940c
[0x00000176]> 
[0x00000176]> # 2. I like logic 
[0x00000176]> 
[0x00000176]> > i like logic and i like files, apparently, they have something in common, what should my next step be.
[0x00000176]> 
[0x00000176]> 
[0x00000176]> ## Solution:
[0x00000176]> 
[0x00000176]> - Opened the file on `Logic2`
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> <img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 29 02 PM" src="https://github.com/user-attachments/assets/7821195b-9f36-41d6-bbbf-1796c0a1aa26" />
ERROR: No output?
[0x00000176]> img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 29 02 PM" src="https://github.com/user-attachments/assets/7821195b-9f36-41d6-bbbf-1796c0a1aa26" /- Started using random analyser till i get an output used `SPI` and `Async Serial` 
ERROR: Invalid command 'SPI' (0x53)
ERROR: Invalid command 'img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 29 02 PM" src="https://github.com/user-attachments/assets/7821195b-9f36-41d6-bbbf-1796c0a1aa26" /- Started using random analyser till i get an output used `SPI` and `Async Serial` ' (0x69)
[0x00000176]> <img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 31 41 PM" src="https://github.com/user-attachments/assets/f881a640-73ce-4369-ba15-f0dec7a01b3e" />
ERROR: No output?
[0x00000176]> img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 31 41 PM" src="https://github.com/user-attachments/assets/f881a640-73ce-4369-ba15-f0dec7a01b3e" /
[Memory]

[0x00000176]> - On the terminal there was the output from there retrieved the flag.
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> ## Flag:
[0x00000176]> 
[0x00000176]> ```
ERROR: Invalid command '```' (0x60)
[0x00000176]> FCSC{b1dee4eeadf6c4e60aeb142b0b486344e64b12b40d1046de95c89ba5e23a9925}
ERROR: Invalid command 'FCSC{b1dee4eeadf6c4e60aeb142b0b486344e64b12b40d1046de95c89ba5e23a9925}' (0x46)
[0x00000176]> 
[0x00000176]> ```
ERROR: Invalid command '```' (0x60)
[0x00000176]> 
[0x00000176]> ## Concepts learnt:
[0x00000176]> 
[0x00000176]> - Using Logic2
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> ## Notes:
[0x00000176]> 
[0x00000176]> - None
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> ## Resources:
[0x00000176]> 
[0x00000176]> - None
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> 
[0x00000176]> ***
0x940c
[0x00000176]> 
[0x00000176]> # 3. Bare metal Alchemist
[0x00000176]> 
[0x00000176]> > my friend recommended me this anime but i think i've heard a wrong name.
[0x00000176]> 
[0x00000176]> ## Solution:
[0x00000176]> 
[0x00000176]> - Started by reading or executing the file which was a big waste of time then loaded the file on `r2`
Usage: r2 [-ACdfjLMnNqStuvwzX] [-P patch] [-p prj] [-a arch] [-b bits] [-c cmd]
          [-s addr] [-B baddr] [-m maddr] [-i script] [-e k=v] file|pid|-|--|=
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> <img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 55 57 PM" src="https://github.com/user-attachments/assets/320bb070-3850-4e88-9246-69162e4736b2" />
ERROR: No output?
[0x00000176]> img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 55 57 PM" src="https://github.com/user-attachments/assets/320bb070-3850-4e88-9246-69162e4736b2" /
[Memory]

[0x00000176]> - First listed all the functions to look for some sort of `main` or `decrypt_flag` kinda function. 
ERROR: Invalid `a` subcommand, try `m?`
ERROR: no esil watchpoints defined
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> ```
ERROR: Invalid command '```' (0x60)
[0x00000176]> [0x00000000]> afl
ERROR: Invalid command '[0x00000000]> afl' (0x5b)
[0x00000176]> 0x00000000    8     62 entry0
[0x00000000]> 0x000000d4    1     14 sym.z1__
[0x000000d4]> 0x00000176   38    362 main
[0x00000176]> 0x000000e2    4    148 sym.__vector_16
[0x000000e2]> ```
ERROR: Invalid command '```' (0x60)
[0x000000e2]> - Shifted to main using `s main`.|
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> - Ran a decompiler but it was kinda confused coz code was in assembly.
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000176]> 
[0x00000176]> <img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 58 19 PM" src="https://github.com/user-attachments/assets/93fe53c1-fa6c-4740-8e4e-ee465e21ed26" />
ERROR: No output?
[0x00000176]> img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 58 19 PM" src="https://github.com/user-attachments/assets/93fe53c1-fa6c-4740-8e4e-ee465e21ed26" /
[Memory]

[0x00000176]> - The orphan loop is where the decryption was happening and `0x68` was the address were the decryption was being stored so tried printing that but failed.
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> 
[0x00000068]> <img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 59 58 PM" src="https://github.com/user-attachments/assets/c969adcd-1834-4d44-8a20-e355cba03341" />
ERROR: No output?
[0x00000068]> img width="1280" height="832" alt="Screenshot 2025-10-31 at 11 59 58 PM" src="https://github.com/user-attachments/assets/c969adcd-1834-4d44-8a20-e355cba03341" /
[Memory]

[0x00000068]> - Then used `psx 44 @ 0x68` which would print 44 bytes of the string
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> - Feeded the output to a python decrypter script to obtain the flag.
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> 
[0x00000068]> ```
ERROR: Invalid command '```' (0x60)
[0x00000068]> vishalsharan@Vishals-MacBook-Air Downloads % python3
ERROR: Invalid tmpseek address 'Vishals-MacBook-Air Downloads % python3'
ERROR: Invalid command 'vishalsharan@Vishals-MacBook-Air Downloads % python3' (0x76)
[0x00000068]> Python 3.9.6 (default, Aug  8 2025, 19:06:38) 
ERROR: Invalid `y` subcommand, try `P?`
[0x00000068]> [Clang 17.0.0 (clang-1700.3.19.1)] on darwin
ERROR: Invalid command '[Clang 17.0.0 (clang-1700.3.19.1)] on darwin' (0x5b)
[0x00000068]> Type "help", "copyright", "credits" or "license" for more information.
[0x00000068]> >>> encrypted_flag = b'\xf1\xe3\xe6\xe6\xf1\xe3\xdf\xf1\xcd\x94\xd6\xfa\x94\xd6\xfa\xd6\xca\xc8\x97\xfa\xd6\x94\xc8\xd5\xc9\x03\xfa\x91\xd7\xc1\xd0\x94\xcb\xca\xfa\xc3\x94\xd7\xc8\xd2\x91\xd7\xc0\xd8'
[0x00000068]> >>> key = 0xa5
[0x00000068]> >>> flag = ""
[0x00000068]> >>> for byte in encrypted_flag:
[0x00000068]> ...   flag += chr(byte ^ key)
[0x00000068]> ... 
[0x00000068]> >>> print(flag)
[0x00000068]> ```
ERROR: Invalid command '```' (0x60)
[0x00000068]> 
[0x00000068]> 
[0x00000068]> ## Flag:
[0x00000068]> 
[0x00000068]> ```
ERROR: Invalid command '```' (0x60)
[0x00000068]> FCCTF{Th1s_1s_som3_s1mpl3_4rdu1no_f1rmw4re}
ERROR: Invalid command 'FCCTF{Th1s_1s_som3_s1mpl3_4rdu1no_f1rmw4re}' (0x46)
[0x00000068]> 
[0x00000068]> ```
ERROR: Invalid command '```' (0x60)
[0x00000068]> 
[0x00000068]> ## Concepts learnt:
[0x00000068]> 
[0x00000068]> - Using the radare2 tool
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> - Xor encryption
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> - decompilation processes
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> - python scripting for decompiling 
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> 
[0x00000068]> ## Notes:
[0x00000068]> 
[0x00000068]> - reading the files was a waste of time
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> - using ` ps @ 0x68` command failed because it's looking for a standard, null-terminated (text) string. Your encrypted flag is just raw bytes, and it probably contains a \x00 (null) byte, which makes ps stop immediately.
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> 
[0x00000068]> ## Resources:
[0x00000068]> 
[0x00000068]> - Gemini
Usage: -  open editor and run the r2 commands in the saved document
| '-' '.-' '. -'   those three commands do the same
| -8              same as s-8, but shorter to type (see +? command)
| -a x86          same as r2 -a x86 or e asm.arch=x86
| -A[?]           same as r2 -A or aaa
| -b 32           same as e or r2 -e
| -c cpu          same as r2 -e asm.cpu=
| -e k=v          same as r2 -b or e asm.bits
| -h              show this help (same as -?)
| -H key          same as r2 -H
| -k kernel       same as r2 -k or e asm.os
| -f              block size = file size (b $s)
| -j              enter the js: repl
| -i [file]       same as . [file], to run a script
| -s [addr]       same as r2 -e asm.cpu=
| -L              same as Lo (or r2 -L)
| -p project      same as 'P [prjname]' to load a project
| -P patchfile    apply given patch file (see doc/rapatch2.md)
| -v              same as -V
| -V              show r2 version, same as ?V
| --              seek one block backward. Same as s-- (see `b` command)
[0x00000068]> 
[0x00000068]> 
[0x00000068]> ***
0x940c
[0x00000068]> 
[0x00000068]> keyq
ERROR: Invalid `e` subcommand, try `k?`
[0x00000068]> q
psnova@FORBIDDEN-DIMENSION:~/Downloads$ r2 -A firmware.elf 
WARN: Relocs has not been applied. Please use `-e bin.relocs.apply=true` or `-e bin.cache=true` next time
INFO: Analyze all flags starting with sym. and entry0 (aa)
INFO: Analyze imports (af@@@i)
INFO: Analyze entrypoint (af@ entry0)
WARN: select the calling convention with `e anal.cc=?`
INFO: Analyze symbols (af@@@s)
INFO: Analyze all functions arguments/locals (afva@@@F)
INFO: Analyze function calls (aac)
INFO: Analyze len bytes of instructions for references (aar)
INFO: Finding and parsing C++ vtables (avrr)
INFO: Analyzing methods (af @@ method.*)
INFO: Emulate functions to find computed references (aaef)
INFO: Recovering local variables (afva@@@F)
INFO: Type matching analysis for all functions (aaft)
INFO: Propagate noreturn information (aanr)
INFO: Integrate dwarf function information
INFO: Use -AA or aaaa to perform additional experimental analysis
INFO: Finding xrefs in noncode sections (e anal.in=io.maps.x; aav)
WARN: Skipping aav because base address is zero. Use -B 0x800000 or aav0
[0x00000000]> afl
0x00000000    8     62 entry0
0x000000d4    1     14 sym.z1__
0x00000176   38    362 main
0x000000e2    4    148 sym.__vector_16
[0x00000000]> s amin
ERROR: Cannot seek to unknown address 'amin'
[0x00000000]> s main
[0x00000176]> pdc
 // callconv: r24 reg (r25, r24, r23, r22);
int main (int argc, char **argv, char **envp) {
    loc_0x00000176:
        // CALL XREF from entry0 @ 0xc8(x)
        push(r28)
        push(r29)
        goto 0x17c    // 0x17c(0x0, 0x0, 0x0, 0x0)
        // CALL XREF from main @ 0x17a(x)
        r28 = 0x3d    // IO SPL: Stack lower bits SP0-SP7
        r29 = 0x3e    // IO SPH: Stack higher bits SP8-SP10
        i = 1         // sph
        r24 = 0x24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 |= 0x02   // loc.__zero_reg__ // loc.__zero_reg__
        0x24 = r24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 = 0x24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        0x24 = r24    // IO TCNT2: Timer/Counter2 (8 bits).
        r24 = 0x25    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 |= 0x02   // loc.__zero_reg__ // loc.__zero_reg__
        0x25 = r24    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 = 0x25    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        0x25 = r24    // IO TCCR2: Timer/Counter2 Control Register (8 bits).
        r24 = *(0x6e)
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x6e) = r24
        *(0x81) = r1
        r24 = *(0x81)
        r24 |= 0x02   // "K"
        *(0x81) = r24
        r24 = *(0x81)  // "K"
        r24 |= 0x01   // loc.__FUSE_REGION_LENGTH__
        *(0x81) = r24
        r24 = *(0x80)  // sph
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x80) = r24 // sph
        r24 = *(0xb1)
        r24 |= 0x04   // loc.__zero_reg__ // loc.__zero_reg__
        *(0xb1) = r24
        r24 = *(0xb0)
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0xb0) = r24
        r24 = *(0x7a)
        r24 |= 0x04   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        r24 = *(0x7a)
        r24 |= 0x02   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        r24 = *(0x7a)
        r24 |= 0x01   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        r24 = *(0x7a)
        r24 |= 0x80   // loc.__zero_reg__ // loc.__zero_reg__
        *(0x7a) = r24
        *(0xc1) = r1
        r24 = 0x0a    // IO UCSRB: USART Control and Status Register B.
        r24 |= 0xf8   // loc.__zero_reg__ // loc.__zero_reg__
        0xa = r24     // IO UCSRB: USART Control and Status Register B.
        r24 = 0x04    // IO ADCL: ADC Data Register Low byte.
        r24 |= 0x03   // loc.__zero_reg__ // loc.__zero_reg__
        0x4 = r24     // IO ADCL: ADC Data Register Low byte.
        cbi 0xa, 2    // IO UCSRB: USART Control and Status Register B.
        r24 = 0x0b    // IO UCSRA: USART Control and Status Register A.
        r24 &= 0x07
        0xb = r24     // IO UCSRA: USART Control and Status Register A.
        r24 = 0x05    // IO ADCH: ADC Data Register High byte.
        r24 &= 0xfc   // loc.__zero_reg__ // loc.__zero_reg__
        0x5 = r24     // IO ADCH: ADC Data Register High byte.
        r25 = 0xa5
        r11 = r25
        r18 = 0x00
        r12 = r18
        r18 = 0x00
        r13 = r18
    loc_0x0000022c:
        // CODE XREFS from main @ 0x286(x), 0x28c(x)
        r24 = 0x09    // IO UBRRL: USART Baud Rate Registers Low byte. A.k.a setting serial port speed.
        r25 = r24
        r25 <<= 1     // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
        r24 ^= r25    // loc.__zero_reg__
        sbrs r24, 2   // unlikely
        goto loc_0x00000236;
        goto loc_0x00000236;
        return r24;
    loc_0x00000236:
        goto 0x27e
    loc_0x0000027e:
        // CODE XREF from main @ 0x236(x)
        goto sym z1() // sym.z1__ // sym.z1__
        return r24;
    loc_0x00000238:  // orphan
         // CODE XREF from main @ 0x234(x)
         r24 = 0x68               // loc.__trampolines_end
         r14 = r24                // loc.__trampolines_end
         r24 = 0x00
         r15 = r24
         r16 = 0x00
    loc_0x00000242:  // orphan
         // CODE XREF from main @ 0x2de(x)
         r30+1:r30 = r14+1:r14
         r0 = z                   // 0x68 // loc.__trampolines_end
                                  Xf
         r24 &= r24
         if (!var) 
         goto loc_0x00000262
    loc_0x0000024a:  // orphan
         r30 = r24
         r30 ^= r11               // loc.__zero_reg__
         var = r24 - 0xa5         // loc.__zero_reg__ // loc.__zero_reg__
         if (!var) 
         goto loc_0x00000262
    loc_0x00000252:  // orphan
         r24 = 0x09               // IO UBRRL: USART Baud Rate Registers Low byte. A.k.a setting serial port speed.
         r25 = r24
         r25 <<= 1                // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         r24 ^= r25               // loc.__zero_reg__
         sbrc r24, 2              // likely
         goto loc_0x0000025e
    loc_0x0000025c:  // orphan
         goto loc_0x0000028e
    loc_0x0000025e:  // orphan
         // CODE XREF from main @ 0x25a(x)
    loc_0x00000262:  // orphan
         // CODE XREFS from main @ 0x248(x), 0x250(x)
         *(y+2) = r1
         *(y+1) = r1
    loc_0x00000266:  // orphan
         // CODE XREF from main @ 0x27c(x)
         r24 = *(y+1)
         r25 = *(y+2)
         var = r24 - 0x2c         // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         r25 -= (0x01 + carry)    // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         brcc 0x282               // unlikely
         goto loc_0x00000282
    loc_0x00000270:  // orphan
         r24 = *(y+1)
         r25 = *(y+2)
         r24+1:r24 += 0x01        // loc.__zero_reg__
         *(y+2) = r25
         *(y+1) = r24
         goto loc_0x00000266
    loc_0x0000027e:  // orphan
         // CODE XREF from main @ 0x236(x)
    loc_0x00000282:  // orphan
         // CODE XREF from main @ 0x26e(x)
         var = r12 - r1           // loc.__zero_reg__
         var = r13 - r1 - carry   // loc.__zero_reg__
         if (!var) 
         goto loc_0x0000022c
    loc_0x00000288:  // orphan
              // goto loc_0x22c
         goto loc_0x0000022c
    loc_0x0000028e:  // orphan
         // CODE XREF from main @ 0x25c(x)
         r30 -= 0x30              // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         r17 = 0x00
         var = r30 - 0x4e         // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         brcc 0x29e               // likely
         goto loc_0x0000029e
    loc_0x00000296:  // orphan
         r31 = 0x00
         r30 -= 0x00              // loc.__zero_reg__
         r31 -= (0xff + carry)    // loc.__zero_reg__ // loc.__zero_reg__
         r17 = *(z)
    loc_0x0000029e:  // orphan
         // CODE XREF from main @ 0x294(x)
              sbrc r17, 0              // likely
         goto loc_0x000002a6
    loc_0x000002a4:  // orphan
         sbi 0xb, 3               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002a6:  // orphan
         // CODE XREF from main @ 0x2a2(x)
         sbrc r17, 1              // likely
         goto loc_0x000002aa
    loc_0x000002a8:  // orphan
         sbi 0xb, 4               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002aa:  // orphan
         // CODE XREF from main @ 0x2a6(x)
         sbrc r17, 2              // likely
         goto loc_0x000002ae
    loc_0x000002ac:  // orphan
         sbi 0xb, 5               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002ae:  // orphan
         // CODE XREF from main @ 0x2aa(x)
         sbrc r17, 3              // likely
         goto loc_0x000002b2
    loc_0x000002b0:  // orphan
         sbi 0xb, 6               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002b2:  // orphan
         // CODE XREF from main @ 0x2ae(x)
         sbrc r17, 4              // likely
         goto loc_0x000002b6
    loc_0x000002b4:  // orphan
         sbi 0xb, 7               // IO UCSRA: USART Control and Status Register A.
    loc_0x000002b6:  // orphan
         // CODE XREF from main @ 0x2b2(x)
         sbrc r17, 5              // likely
         goto loc_0x000002ba
    loc_0x000002b8:  // orphan
         sbi 0x5, 0               // IO ADCH: ADC Data Register High byte.
    loc_0x000002ba:  // orphan
         // CODE XREF from main @ 0x2b6(x)
         sbrc r17, 6              // likely
         goto loc_0x000002be
    loc_0x000002bc:  // orphan
         sbi 0x5, 1               // IO ADCH: ADC Data Register High byte.
    loc_0x000002be:  // orphan
         // CODE XREF from main @ 0x2ba(x)
         r24 = r16
         r24 &= 0x1f              // loc.__zero_reg__
         r24 -= 0xd3              // loc.__zero_reg__ // loc.__zero_reg__
    loc_0x000002c4:  // orphan
         // CODE XREF from main @ 0x2d4(x)
         r24 -= 0x01              // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__ // loc.__zero_reg__
         brcs 0x2d6               // likely
         goto loc_0x000002d6
    loc_0x000002c8:  // orphan
         r30 = 0x9f
         r31 = 0x0f
    loc_0x000002cc:  // orphan
         // CODE XREF from main @ 0x2ce(x)
         r30+1:r30 -= 0x01        // loc.__zero_reg__ // loc.__zero_reg__
         if (var) 
         goto loc_0x000002cc
    loc_0x000002d0:  // orphan
    loc_0x000002d2:  // orphan
         // CODE XREF from main @ 0x2d0(x)
         goto loc_0x000002c4
    loc_0x000002d6:  // orphan
         // CODE XREF from main @ 0x2c6(x)
         r31 = 0xff
         r14 -= r31               // loc.__zero_reg__ // loc.__zero_reg__
         r15 -= (r31 + carry)     // loc.__zero_reg__
         r16 -= 0xdb              // loc.__zero_reg__ // loc.__zero_reg__
         goto loc_0x00000242
}
[0x00000176]> psx 44 @ 0x68
\xf1\xe3\xe6\xe6\xf1\xe3\xde\xf1\xcd\x94\xd6\xfa\x94\xd6\xfa\xd6\xca\xc8\x96\xfa\xd6\x94\xc8\xd5\xc9\x96\xfa\x91\xd7\xc1\xd0\x94\xcb\xca\xfa\xc3\x94\xd7\xc8\xd2\x91\xd7\xc0\xd8
[0x00000176]> -

```
<img width="1920" height="1080" alt="Screenshot From 2025-11-01 00-29-13" src="https://github.com/user-attachments/assets/9617e7f4-b9cd-4ba9-b82b-1075fd6ab058" />

## Flag:

```
FCCTF{Th1s_1s_som3_s1mpl3_4rdu1no_f1rmw4re}
```

## Concepts learnt:
Using the radare2 tool
Xor encryption
decompilation processes
python scripting for decompiling


## Resources:
[Basic Definition](https://www.google.com/)
AI 
Youtube
