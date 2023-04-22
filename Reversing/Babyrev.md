# BABYREV

## 1. Instructions

![instructions](https://user-images.githubusercontent.com/94288725/233765548-9508d772-cc85-4e16-b3cf-450fd1bb55ea.png)

#### Resources :

Download [babyrev.zip](https://github.com/modesteakaffou/CAF_CTF/files/11300380/babyrev.zip)

## 2. Solution

First of all, you have to know the instructions in the challenge. What exactly does the instruction say? Here is what the instruction says: Can you pay your close attention to find out the flag?
It must be said that this is not really a clue as such since it tells us absolutely nothing about how to find the flag. Okay, never mind, let's continue.

once the zip file is downloaded, you will dezip it. We will proceed in a methodical way to find the flag.

- Let's start by using the "file" command in linux to find the file type


![Screenshot from 2023-04-22 06-13-25](https://user-images.githubusercontent.com/94288725/233766281-ee0dacff-a23b-4949-9c81-70bc9c4780cf.png)


- Let's use the "strings" command in linux to display the strings in babyrev

![Screenshot from 2023-04-22 06-19-19](https://user-images.githubusercontent.com/94288725/233766533-e7f8e8bc-511b-4dcd-b522-b710480ec0c4.png)

We found an interesting text hidden inside thanks to the strings command. In this text, we can see that it has the word "CAF", so it is a valuable clue. Let's try to decipher it to see if it is the flag.

![Screenshot from 2023-04-22 06-24-22](https://user-images.githubusercontent.com/94288725/233766820-cbf3c12f-3db6-4544-a428-dc48108a08e2.png)

With the cipher identifier tool of dcode, we are offered 15 decryption algorithms. Let's also test cyberchef to see what it gives.

![Screenshot from 2023-04-22 06-28-31](https://user-images.githubusercontent.com/94288725/233766954-48b46f99-b553-4f81-97d2-551eaa27b37d.png)

With the "Magic" tool of cyberchef, we could identify only one encoding which corresponds, it is the base85. As I said, we will have to test everything to see which one gives the most interesting result. Let's start by testing the base85 in cyberchef then we will test the others in dcode.

![Screenshot from 2023-04-22 06-35-12](https://user-images.githubusercontent.com/94288725/233767269-32a78b42-0a64-4340-a2ac-b6fe57bb6238.png)






