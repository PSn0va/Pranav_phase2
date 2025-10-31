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
[0x00000176]> ps @ 0x68
[0x00000176]> psx 44 @ 0x68
\xf1\xe3\xe6\xe6\xf1\xe3\xde\xf1\xcd\x94\xd6\xfa\x94\xd6\xfa\xd6\xca\xc8\x96\xfa\xd6\x94\xc8\xd5\xc9\x96\xfa\x91\xd7\xc1\xd0\x94\xcb\xca\xfa\xc3\x94\xd7\xc8\xd2\x91\xd7\xc0\xd8
[0x00000176]> -

```
<img width="1920" height="1080" alt="Screenshot From 2025-11-01 00-29-13" src="https://github.com/user-attachments/assets/9617e7f4-b9cd-4ba9-b82b-1075fd6ab058" />

## Flag:

```
TFCCTF{Th1s_1s_som3_s1mpl3_4rdu1no_f1rmw4re}
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
