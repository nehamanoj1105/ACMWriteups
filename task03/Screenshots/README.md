## Task 1-CTFLearn - Hidden
Think the flag is somewhere in there. Would you help me find it? https://mega.nz/#!OHohCbTa!wbg60PARf4u6E6juuvK9-aDRe_bgEL937VO01EImM7c

For this task first i downloaded the image provided

then using the command 'strings'
`strings 95f6edfb66ef42d774a5a34581f19052.jpg`

strings is used to scan the file and print the sequence of characters that are atleast 4 characters long


## Task 2-CTFLearn-Forensics 1

After downloading the file 'unopenable.gif`
we check `file unopenable.gif`

here we see that `unopenable.gif: GIF image data, version 89a, 244 x 244`

then we `hexedit unopenable.gif`

after that we change 39 61 f4 01... to 47 49 46 38 39 61 which makes it a proper gif image

then we extract the image as frames and from there we get a sequence of characters that are base64 encoded and once we decode it we get the flag

## Task 5-PicoCTF-Extensions
Glory of the Garden

After downloading the garden.jpg file 

we use the command 'strings garden.jpg | grep pico`

which yields the flag:
Here is a flag "picoCTF{more_than_m33ts_the_3y35a97d3bB}"

## Task 4
<img width="803" height="546" alt="image" src="https://github.com/user-attachments/assets/1fa4a876-1b50-45a2-a6ff-9f65aacec072" />

## Task 3,6 
The website kept redirected to https://ine.com/dive
(which is a paid site)
