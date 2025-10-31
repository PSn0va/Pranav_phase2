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


# 2. Bare Metal Alchemist

> my friend recommended me this anime but i think i've heard a wrong name.


## Solution:

```

```

## Flag:

```
FCCTF{Th1s_1s_som3_s1mpl3_4rdu1no_f1rmw4re}
```

## Concepts learnt:


## Resources:
[Basic Definition](https://www.google.com/)
[Logic2](https://www.saleae.com/support)
[UART](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter)
Youtube
