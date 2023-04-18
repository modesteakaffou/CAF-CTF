# TOWER OF ENCRYPTION


## 1. Instructions

![Screenshot from 2023-04-16 07-08-39](https://user-images.githubusercontent.com/94288725/232712456-4637ab73-7e81-4e02-acc6-2fd88e8d5536.png)

#### Resources

Download  [challenge_file.txt](https://github.com/modesteakaffou/CAF_CTF/files/11259627/challenge_file.txt "download") <br>
Download  [key_file.txt](https://github.com/modesteakaffou/CAF_CTF/files/11259631/key_file.txt "download") <br>

## 2. Solution

First of all we will start by taking a good look at the instruction that is given. Let's pay attention to every detail because it will all be used in the resolution.
In the instruction, it says that Eliot tries << several times >> to decrypt but without success. On the other hand, we have two files, let's open these two files to see the content.

- challenge_file.txt : 
```text
JJFEMRKNKJFU4S2KIZKTIUZSJNEVUS2UJFKVUU2KJZCVMVKTGJKUURSLKZKVKMSLJJNEGVSNKZFVIR2KJRCVOVCTJRFVUS2WJNGVGSKKJJDEKR2WKNHEWWSGKZFVGS2PJFJEGVSLKZBVISSWIVLE2USDK5EVMSKUIVJTES2KJJCEKS2TJNLUUTSHIVLVOU2HJNNEKVSFJVJUYSSGJJCUOVSTJRFVESSVLFJVGU2JLJGEKS2VJJJUWNKGIZGVGS2VJFLEUVCFKMZEYSSKINCUWUZSKRFE4TCVKVKFGSCJKZGFMS2VGJEEUTSOIVEVMU2IJNGVURSBKNJUOSSKINLE6VSTKRFEERSWIVJVGVSMIZFFMR2WGJFEYSSHIVFU2U2WJJFEUVKXJZFUOSKVGJDEKTKTLBFEKMSVKVLEGRSLJZFFKUKTGIZESUSLKVLVKWSTJNHEIVKVKNJVMSZVJNDEOU2LJJFVUR2GJVJDEVSHJJCUKVKUKNHUSVSGKZGVKMSHJJFEYRKVKZFVUS2OJJKVOU2TJNEU4TCFGZLFGVCKJZDFIS2SKNLUWTSMKZDVEMSLJFNEMRSNKIZFKR2KIZCVSU2TJBEVMRSVGJKTEV2KJJDEKVKWJNMEUWSGKVHVGSZSJE2UYRKPKZFFGS22IZCU2VCDIZFVMTCFI5JFGTCKKZHEKS2WGJKUSTSGKVJVMU2EJNLEYVSLK5JVISSOJRCU2USKKVFVEQSWJVJVUVSKJZCEKT2VKJJUUSSGKZKVEMSHJJLEURCFKZBU2SSKIZDEWVSLKNFU4SCVKNLFGR2LLJDVMS2NKNFEUSSIIVHVMU2WJNFEMRSPKMZE6SK2IRCTEVJSKREU4RKVGRKEGRSHLJGEMR2WINGEWSSEIZFVES2TJNHEYVKTKZJUWS22IRLE2VJSJZFEMTSFJVJFGTSLJFNEMR2SGJFUSWSDKZJVKMSUJJBEKVSNKJJVOSJVI5LEOVRSJNFFURKFJNJDEU2KJZGUKVKXKNDUWVSIKZDU2U2YJJCTEVKZKJFUYS2SIZLESVCDINEVUQ2VK5KEWVCLLJDUKTKUINDEWNKMKVDVIQ2LJRFEIRKNKMZFMSSOJNCU6U2LGJEVMSSWI5KTERKKJZGEKWKWKNGEWNKKKZEVGU2OI5FEWVKTKZJUYS22IZKTIU2TK5FFMSSWKVLFGS2KLJBUKS2UGJLEOSSHIVKVGU2HJNNEWVSFJVJUQSSKJRCVKVSLLBFVUSSVKFJVGS2JJJGEKV2WKNGEWTSGKU2FEU2WJNHEYRSHKNBUYTCKIRLE2UJSKZDUUS2VKVJVGSKJKZBVMRKTGJHUUTSGIVCVMS22JNHEEVSNKIZDESSOINCUWVKDJNDVMRKGJNIEUNKIKU3FIMSQJE6Q====
```

- key_file.txt :
```text
n = 1000000016000000063 
e = 23
c = 471055156725181012
```
Let's copy the text from the challenge_file.txt file and paste it into cyberchef then use the <Magic> tool to be able to identify the encoding used.

just find cyberchef here : [Cyberchef](https://gchq.github.io/CyberChef/#recipe=Magic(3,false,false,''))

![Screenshot from 2023-04-18 14-31-06](https://user-images.githubusercontent.com/94288725/232810065-421463c9-492f-40db-a0a3-3d317524c2a3.png)

We can see that cyberchef proposes base32 as encoding. But this does not allow to fall directly on the flag. Let's look again below, we can see base32 spotted 3 times but there again, we don't have the flag. And if we were to spot the base32 decoding several times. Let's remember that the instruction mentions the word <<several times>>. Let's test to see.


![Screenshot from 2023-04-18 14-42-54](https://user-images.githubusercontent.com/94288725/232813342-d59a0691-36f6-424e-95db-d2cfd91d9bee.png)

I used the base32 encoding 8 times in a row to finally find something that looks like the flag. But it's not the flag yet. The flag is in the format CAF_{something}

So here is what we found: <strong> JAH_{I0Y_F4U_H4EU3H_WO3_W0TVH} </strong>

Now let's try to identify the encoding or encryption used to obtain this result. Let's try it with the magic tool of Cyberchef.

![Screenshot from 2023-04-18 15-23-32](https://user-images.githubusercontent.com/94288725/232825529-2002ebbf-aeb9-439c-8caf-81a75045e126.png)

there is no result even with the intensive mode you can test. We will use dcode with the cipher identifier tool to determine the encoding or encryption used. It should be remembered that the cipher identifier tool of the dcode platform is not 100% reliable. It can happen that it does not detect anything. Let's try it anyway.

just go to this link : [Cipher identifier dcode](https://www.dcode.fr/cipher-identifier)

![Screenshot from 2023-04-18 15-38-19](https://user-images.githubusercontent.com/94288725/232829573-578f6237-3366-4004-9c53-500ff17ab130.png)

Let's calm down for a moment, the cipher identifier tool gives us possibilities but we must know that it is not 100% reliable. Before trying to test the proposals, let's try to think a little. We have a second file called key_file.txt and in this file there are values used in the RSA encryption calculations. We can understand by this that we have to calculate and find the key. But what is this key used for? What are the encodings or ciphers that use a key? 

Here is a list of 10 historical encryption algorithms that use a key:

- Caesar's cipher
- Vigenère's cipher
- Playfair's cipher
- Hill's cipher
- Gronsfeld's cipher
- Porta's cipher
- The Beaufort cipher
- The Rail Fence cipher
- The Scytale cipher
- The Polibius cipher
 
These historical encryption algorithms have been widely used in the past to protect the confidentiality of messages. They are all based on the use of a key to encrypt and decrypt data. However, they are now considered weak in terms of security and have been replaced by stronger and more complex algorithms for the protection of sensitive data.

Historical encryption algorithms have been replaced by modern encryption algorithms that offer stronger security and better data protection. Some of the most widely used modern encryption algorithms include:

- AES (Advanced Encryption Standard)
- RSA (Rivest-Shamir-Adleman)
- DES (Data Encryption Standard)
- 3DES (Triple DES)
- Blowfish
- Twofish
- RC4 (Rivest Cipher 4)
- Camellia
- IDEA (International Data Encryption Algorithm)




