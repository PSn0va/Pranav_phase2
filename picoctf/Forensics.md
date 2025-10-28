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


