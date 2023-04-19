
# IT ADMINISTRATOR CREDENTIALS

## 1. Instructions

![instructions](https://user-images.githubusercontent.com/94288725/233026092-b1d5942e-a570-4670-bfe9-0fc5d033a038.png)

#### Resources :

Download [Administrator.zip](https://github.com/modesteakaffou/CAF_CTF/files/11271280/Administrator.zip "download")

## 2. Solution

First of all, let's try to open the word file inside the zip file you downloaded.

![document content](https://user-images.githubusercontent.com/94288725/233033193-c2c7c89c-6428-4234-b719-310592d1681a.png)

We can see that the document is encrypted. A password is required before the content can be read. Of course, we don't have the password. What are we going to do? Don't be afraid, there is a solution. We will try to find the password by doing password bruteforce. Password bruteforce is a technique that allows you to test several thousand passwords to find the right one. To perform the brute force, there are tools like hashcat or john the ripper. This is done in two steps, first find the hash of the file and then perform the brute force attack.

To find the hash of the document, we use office2john which is a tool from John the ripper. Here is how to do it: 

![document hash generating](https://user-images.githubusercontent.com/94288725/233036601-1d4ebff4-90a1-449e-bd3d-eb28d5541f04.png)

Basically, John the ripper and Hashcat tools are already preinstalled on kali linux. If this is not the case for you, try to install them. So here is the hash of the Administrator.docx file that John generates :

```text
Administrator.docx:$office$*2013*100000*256*16*504fbe77359c707a81ae26d89f031d59*4a5a4834554b31de39f464c5cd963721*ec8a42ee5c5238b6c93d00a7028548d53ea8e5f3650adbff01a84d5b43c89a62
```

Now that we have managed to find the hash of the file, the hardest part is still to come. We need to find a Wordlist that could contain the password of the document.
Here is a list of 10 popular wordlists commonly used in penetration testing and security audits:


- Rockyou.txt: this is one of the most popular and widely used wordlists. It contains over 14 million passwords of hacked accounts and is often used to test the strength of passwords.
- CrackStation: a wordlist containing over 1.5 billion passwords collected from data leaks.
- Hashcat - a wordlist included in the Hashcat password cracking software, which contains a wide variety of commonly used passwords and other possible combinations.
- Probable-Wordlists: a collection of wordlists created from documents, books, speeches, etc.
- SecLists - a collection of wordlists including commonly used passwords, usernames, email addresses, vulnerabilities and more.
- Kali Linux Wordlists: a collection of wordlists included in the Kali Linux distribution, used for penetration testing and security audits.
- DarkWebLink Wordlists: a collection of wordlists from the dark web.
- LinkedIn Breach Wordlist: a wordlist created from the LinkedIn data leak in 2012.
- Offensive Security Wordlists: a collection of wordlists published by Offensive Security, the company behind Kali Linux and the OSCP and OSCE certifications.
- CeWL: a tool included in Kali Linux that allows you to create custom wordlists from web pages by extracting keywords and phrases.


Let's be clear, there is no miracle recipe to find the right wordlist, the only solution is to test several but we must do it intelligently if we do not want to spend forever waiting. You should know that the most popular wordlist rockyou contains almost 14 million passwords, so logically its launch requires enough time and resources especially if the password you are looking for is located at the 10 million position. Here is what I would recommend: 
When faced with a big problem, break it down into smaller problems. And so we can subdivide rockyou in several so that the bruteforce is faster. Even if most of the time, the password is in rockyou, it can happen that it is not there. In this case, you have to switch to another wordlist.

There are also small wordlists (< 5 million passwords) which are also called SecLists. The advantage is that with these wordlists, the bruteforce is faster and therefore we can test several SecLists.

In this tutorial, we will obviously not test all the wordlists. I will choose a SecList in which I am sure to find the password. The purpose of this tutorial is to show you how to do a bruteforce. So the SecList we use is called merged.  The wordlist in question is there : [SecList Merged](https://github.com/danielmiessler/SecLists/blob/601038eb4ea18c97177b43a757286d3c8a815db8/Passwords/merged.txt.tar.gz)

Now that we have the hash of the document file and the wordlist to use, we can proceed to the bruteforce attack. For this we have the choice between hashcat and John. For this tutoriel, we will use hashcat. Here is the hashcat command that you need to type: 

```bash
$ hashcat -m <hash type> -a <attack method> <hash file> <dictionary file>
```
```text
Here is a list of the most common options you can use with Hashcat:
-m: specifies the type of hash to crack (0 for MD5, 100 for SHA1, 400 for SHA2-256, etc.)
-a: specifies the attack mode (0 for dictionary, 3 for brute-force, 6 for rules, etc.)
-w: specify the number of threads to use for cracking (by default, Hashcat uses all available threads)
-O: enable kernel optimization for modern graphics cards
-p: enables Hashcat's pause and resume feature, which allows you to suspend cracking and resume it later
-r: specifies a custom rule file for the rule-based attack
-1: specifies a custom character file for the mask attack
-2: specifies a second custom character file for the mask attack
--session: specify a custom session name for cracking
--status: enable real-time display of cracking status
--potfile-path: specify the location of the pot file to store the cracking results
```

NB : In the hash file generated by office2john, delete the header which contains the file name and keep only the part : 
"$office$*2013*100000*256*16*504fbe77359c707a81ae26d89f031d59*4a5a4834554b31de39f464c5cd963721*ec8a42ee5c5238b6c93d00a7028548d53ea8e5f3650adbff01a84d5b43c89a62". When you use hashcat, it recognizes only this part

For more information on the hashcat command, type hashcat --help or -h. In our case, we want to perform a dictionary attack since we will use a wordlist (option -a 0). Then we have to determine the type of hash that hashcat will use. To do this, we need to use the hashid tool. Here is how to do it:

![Screenshot from 2023-04-19 13-22-58](https://user-images.githubusercontent.com/94288725/233088519-02868218-ea63-4b4d-8c9d-82ea090b063b.png)

And so the -m option must be 9600. So our hashcat command is finally ready. Here we go:

![Screenshot from 2023-04-19 13-31-36](https://user-images.githubusercontent.com/94288725/233091868-03b98638-d8eb-430b-a460-adf2bd3ad89a.png)

![Screenshot from 2023-04-19 13-31-55](https://user-images.githubusercontent.com/94288725/233091899-ab5d0d2c-97a4-4d74-8ed6-15f7734ef20b.png)

![Screenshot from 2023-04-19 13-32-28](https://user-images.githubusercontent.com/94288725/233091937-42735804-8cfe-4208-80ec-67e4ded7abdc.png)

![Screenshot from 2023-04-19 13-34-37](https://user-images.githubusercontent.com/94288725/233091973-99428385-a436-44d1-b258-b8ee73067d2b.png)

The password of the document is: <strong> !a@s#d$f%g555 </strong>

Now let's try to open the document to see what it contains: 

![Screenshot from 2023-04-19 13-42-20](https://user-images.githubusercontent.com/94288725/233094158-cedbce1c-6e9b-4bc1-af29-b2912876c9b5.png)

There is nothing? don't be afraid, there must be a hidden text only the naked eye can't see it. Let's try to select all the text and color or change the color of the document. This should show us something.

![Screenshot from 2023-04-19 13-46-05](https://user-images.githubusercontent.com/94288725/233095306-40f618fb-89c3-4352-b066-27bfa28f1801.png)

![Screenshot from 2023-04-19 13-45-50](https://user-images.githubusercontent.com/94288725/233095346-f02721b8-9e25-457c-a13d-8262d6e826d3.png)

Bingo! Let's copy the text. Here is what we get: <strong> ildfk=YlyvXpJxc;mxpptloa=T@x8(&'#12m <strong>
all that's left is to decrypt the message and it's done.

Let's paste the text in the cipher identifier tool of the dcode platform to analyze the encoding used. Let's test all the proposals to see if there is an encoding that will allow us to decipher the text message.
Here is the link of the tool : [cipher identifier dcode](https://www.dcode.fr/cipher-identifier)

![Screenshot from 2023-04-19 13-57-51](https://user-images.githubusercontent.com/94288725/233099444-0cc1a51e-3374-479e-8001-11557b065463.png)

![Screenshot from 2023-04-19 14-01-19](https://user-images.githubusercontent.com/94288725/233099596-bf797dec-4d34-4800-bc45-f8780031c17c.png)

We can see the shift cipher allows us to reach the flag which, as stated in the instructions, must be in the format CAF_{login:password}

The flag is: CAF_{BobyAsMaf:W@a8(&'#12p}

Thanks
