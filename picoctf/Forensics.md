# 1. Trivial Flag Transfer Protocol

Figure out how they moved the flag.

## Solution:

So this was one hell of a challenge, I mean no way this was a medium level challenge can't imagine the hard one....
So to start the challenge gave us a file tftp.pcapng. For about 4 hours I was trying it with the CLI commands but hell nahh... I had to ask the mentor about it and he said we'll have to use Wireshark 4.4.2 but I use sudo apt install command to get and it downloaded the latest version 4.6.0 so I thought we can do with it just fine i tried to filter out TFTP and export files as tftp but the only thing I got was instructions.txt then what I was stuck again on it for 3 hr then I asked him again, He said get the older version solution is not compatible with newer version but it was not available for ububntu so i had to do it in windows then i got images, instructions, plan, program.deb.... since program.deb is for linux then I had to shift to ubuntu again. Then I ran cat for instructions and plan one by one and both of them were in ROT13 so had to decode them by decoder plan had some clues in it, Then I ran the sudo apt-get install ./program.deb it showed me something about steghide. I knew I was close then I searched online about it it was examining files and one of those files were bitmap files then what i got to know the commands for it one of those were steghide extract -sf which extracted the given files  I did it with picture1.bmp , it was aking for passphrase there goes my one hour..... I searched the whole file again and again and in the end by hit and trial it was DUEDILIGENCE it was even highlighted because it was after '-', I tried it with both pic1, pic2 and pic3 but the flag was in the pic3 which was automatically extracted as flag.txt.   


```
sudo apt install -y wireshark tshark binwalk foremost exiftool steghide imagemagick file zip unzip xxd 
Downloads/
cd tftp/
cat ./instructions.txt 
cat plan 
sudo apt-get install ./program.deb
steghide extract -sf picture1.bmp 
steghide extract -sf picture2.bmp 
steghide extract -sf picture3.bmp 
```
<img width="1920" height="1080" alt="Screenshot From 2025-10-28 23-14-53" src="https://github.com/user-attachments/assets/54bb366d-2236-4baf-93bd-77a6d963d0f7" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-28 23-16-27" src="https://github.com/user-attachments/assets/e2c26ec1-90dd-4d77-be68-5ceae9abd5b4" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-28 23-26-14" src="https://github.com/user-attachments/assets/47bd2a67-829b-4663-ab0c-02b7e61c84df" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-28 23-27-25" src="https://github.com/user-attachments/assets/6c1d6b3b-131d-4b86-8119-24c70d545e7a" />

## Flag:

```
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```

## Concepts learnt:
Analysis of pcapng file format. 

Wireshark working.

More about bitmap files

Steghide commands and working.

Extraction of files via different programs
 
ROT13 Decoding

Passphrase finding with clues

## Resources:

[Basic Definitions](https://google.com)
[wireshark](https://www.wireshark.org/)
[steghide](https://www.kali.org/tools/steghide/)
[more commands](https://steghide.sourceforge.net/)
[ROT13 decoding](https://rot13.com/)

***



# 2. tunn3l v1s10n

We found this file. Recover the flag.

## Solution:

I think I know by now that I don't likle Forensics domain like how can every medium level problem can be so hard. But I did it anyways and I still don't know nothing about it. First I ran fille command on the file itself it gave me type as data(nothing specific) then I used exiftool command and gave me file details such as dimension and main its format which was bmp then I thought maybe is I change the extension I will be able to open the file itself but how stupid of me, but it was saying something like header is too big or something which I had no clue about, so I googl;ed it instantly luckily I stumbled upon a website which showed me the whole format of bitmap file and I also got to know that we can edit the image configuration by use of hexedit command which I then installed by help of sudo apt install then I ran the command. Guess what I didn't know what to do at all, so I just saw the basic BITMAP file format line by line the first thing I had to check was the header because it was mentioned while opening the file. I noticed at an offset of 14 bytes, InfoHeader begins with 28 00 00 00  but it was BA D0 00 00 which I changed when I opened the file it was showing notaflag{sorry}, at that moment I knew I'm almost done with the challenge. Then I checked it thoroughly and i saw BA D0 00 00 at offset of 10 bytes which meant 53434bytes whch meant that it covers upto 53434 bytes which was large for that much data I changed that to 36 00 00 00 which i generally for the normal size even though the dimension was 1134*306 I thought maybe this is cropped vesion of file then I increased its height by changing 32 01 00 00 to 32 03 00 00 which was at offset of 22 bytes which did show me the flag but not completely thhen I increased it again to 32 04 00 00 which gave me the flag.

```
cd Downloads/
file tunn3l_v1s10n 
exiftool tunn3l_v1s10n
sudo apt update
sudo apt install hexedit
hexedit tunn3l_v1s10n 
```


## Flag:

```
picoCTF{qu1t3_a_v13w_2020}
```
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 02-19-07" src="https://github.com/user-attachments/assets/0131af02-6865-4725-8cc7-65d1416d15ad" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 02-15-49" src="https://github.com/user-attachments/assets/5416d6b9-d962-4eb6-8221-6c096a63b48c" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 02-22-23" src="https://github.com/user-attachments/assets/040a263e-952b-4680-8bbb-287b071221fd" />
<img width="525" height="44" alt="Screenshot From 2025-10-29 02-27-12" src="https://github.com/user-attachments/assets/9019186d-883c-4af8-b45d-a134269833ab" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 02-47-11" src="https://github.com/user-attachments/assets/1c6722de-f48c-4bda-aef0-72ae9a417a26" />
<img width="523" height="33" alt="Screenshot From 2025-10-29 02-32-55" src="https://github.com/user-attachments/assets/2ef13a66-8999-4a07-ace1-560800da7838" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 02-48-49" src="https://github.com/user-attachments/assets/56248146-3ed7-408a-9ca6-fece9688da69" />
<img width="528" height="29" alt="Screenshot From 2025-10-29 02-36-53" src="https://github.com/user-attachments/assets/41f8c99f-a06d-4ac2-b399-ef0996613abb" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 02-50-58" src="https://github.com/user-attachments/assets/927f8460-cc19-4a99-808f-55f49645219a" />

## Concepts learnt:
Using ExifTool 

Use of HexEdit

More about bitmap files

Hex form of the image itself.

How to make changes in hex form of the file itself.
 
BITMAP image file fpormat

More about dimension and Info regarding file format 

## Resources:

[Basic Definitions](https://google.com)
[bmp format](https://www.ece.ualberta.ca/~elliott/ee552/studentAppNotes/2003_w/misc/bmp_file_format/bmp_file_format.htm)
[Hexedit](https://hexed.it/)
[Hexedit Info and commands](https://linux.die.net/man/1/hexedit)

***



# 3. m00nwalk
Decode this message from the moon.

## Solution:

Either I'm getting the hang for Forensics domain or this challenge was easy, It was like what ever I wanted to do in this challenge came to me on its own. This challenge gave me audio file which was nothing but static voice I guess but then I used the first hint which was How did pictures from the moon landing get sent back to Earth? I just googled it and I got the Apollo 11, Apollo 11 used slow-scan television (TV) incompatible with broadcast TV. The next thing I searched was SSTV I came to know we can transmit picture via sound through this then what the only thing I had to do was decoding it then when I searched I decoding SSTV I stumbled upon tools called qsstv and pavucontrol, that website was the one that guided me through thewhole process of decoding SSTV then I opened qstv buit when ever was trying to open pavucontrol from the same terminal it was not possible so I had to use multiple terminal windows then according to steps on the website I'll have to set up a virtual connection in beteen the computer for connecting Pavucontrol and qsstv I dids set that by pactl commans using pulseaudio.There were settings here and there thatneeded some modifications first Pavucontrol - we had to change qsstv connection to virtual in recordings tab and set input and output dev on qsstv enable auto and Auto slant(still don't know what it does). Then I played the audio using paplay. It started generating the image and in the end we got the whole image on which the flag was written. In the end I searched the CMU mascot I came to know that it was sstv type but qsstv auto detected it so there was no need of it.

```
sudo apt install qsstv && sudo apt install pavucontrol -y
qsstv
qsstv && pauvcontrol
pavucontrol
qsstv && pavucontrol
qsstv
pavucontrol
pactl load-module module-null-sink sink_name=virtual-cable
sudo apt update
sudo apt install pulseaudio-utils
pactl load-module module-null-sink sink_name=virtual-cable
paplay -d virtual-cable message.wav
cd Downloads/
paplay -d virtual-cable message.wav
```
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-06-46" src="https://github.com/user-attachments/assets/7090f946-b14b-4480-8701-98a5b94eab74" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-15-09" src="https://github.com/user-attachments/assets/ea67d62a-2ecf-4406-99b2-3327e3aafe6a" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-18-05" src="https://github.com/user-attachments/assets/97419ce1-51be-451e-92f0-033afa9c909e" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-19-41" src="https://github.com/user-attachments/assets/b3ab7124-ee0f-40b7-bb34-457285126de3" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-23-17" src="https://github.com/user-attachments/assets/ed111d51-1fb2-47b3-92f4-82ea775f9397" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-23-24" src="https://github.com/user-attachments/assets/221af4ef-a71c-41db-ac91-be42cecc5d2d" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-23-32" src="https://github.com/user-attachments/assets/9aa4b816-2e76-4e55-aae1-dd9fb092c28c" />
<img width="1920" height="1080" alt="Screenshot From 2025-10-29 08-24-05" src="https://github.com/user-attachments/assets/897d9197-c3a4-44a0-ade8-257c2b2b0c9a" />


## Flag:

```
picoCTF{beep_boop_im_in_space}
```

## Concepts learnt:
Transfer of images via audio files 

SSTV and Apollo 11

Sattelites mode of transmission

Audio Decoding

Decoding of SSTV

working of qsstv and Pavucontrol

Modes of sstv

## Resources:

[Basic Definitions](https://google.com)
[Decoding Qsstv](https://charlesreid1.com/wiki/Qsstv#Connecting_audio_out_to_audio_in)
[PulseAudio](https://www.freedesktop.org/wiki/Software/PulseAudio/)

***
