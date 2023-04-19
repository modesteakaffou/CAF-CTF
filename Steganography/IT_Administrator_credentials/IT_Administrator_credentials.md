
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




