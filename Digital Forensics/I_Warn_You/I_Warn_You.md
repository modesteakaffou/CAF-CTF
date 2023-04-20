# I WARN YOU

## 1. Instructions

![instructions](https://user-images.githubusercontent.com/94288725/233300641-4a812db1-0df0-4c6f-8b26-f1622deadca2.png)

#### Statement :

```text
(1)  what is the malware name detected by McAfee that was bonded in the exe?
(2)  Find out the established malicious connection ASN Owner name?

Flag Format:  CAF_{answer1_answer2} 

Note 1: Don't run the exe file in your main machine. This is a malicious file and setted for the ctf task.

Note 2: The format of the flag is not case sensitive
```

#### Resources :

Download [Challenge_info.txt](https://github.com/modesteakaffou/CAF_CTF/files/11283858/Challenge_info.txt) <br>
Direct download .exe :  [challenge_file.zip](https://github.com/modesteakaffou/CAF_CTF/files/11283878/challenge_file.zip)

## 2. Solution

You are asked to answer two questions and the answers to these two questions will constitute the flag. Let's start with the first one: <br>
1- what is the malware name detected by McAfee that was bonded in the exe?

answer: <br>
Well, here we are asked to analyze the .exe file that contains viruses. Of course we are not going to run the .exe file on our machine, we have to look for a security tool to scan it.
I thought of VirusTotal which is a free online service that allows you to scan files and urls for viruses.
[virus total](https://www.virustotal.com/gui/home/upload)

![Virus total](https://user-images.githubusercontent.com/94288725/233317242-0a17def5-c0c7-4f45-bff9-19235f6012da.png)


We load the .exe file in VirusTotal and we wait for the end of the analysis.
Bim!!! Viruses have been found by the antivirus software in the file.
The question asks us the name of the virus detected by McAfee, and we can see that it is <strong>Artemis!0B80BC9C1E4B</strong> on the line of McAfee.

![Virus total detection](https://user-images.githubusercontent.com/94288725/233317647-39dc7487-8248-466d-aac6-b5c3d02dc111.png)

2- Find out the established malicious connection ASN Owner name?

First of all, it is important to know that the ASN (Autonomous System Number) is a unique number that identifies an autonomous network (Autonom system) on the Internet. To do this, VirusTotal gives us the possibility to see the network relations on our file. We go to the relation tab.

![Screenshot from 2023-04-20 09-13-16](https://user-images.githubusercontent.com/94288725/233320613-99f5816c-848d-4474-9066-4445f019d5c9.png)

![Screenshot from 2023-04-20 09-17-44](https://user-images.githubusercontent.com/94288725/233327787-c3ca69e7-c548-4baa-b70b-b529f7a3fd14.png)

When we click on the RELATION menu we see the IP address of the network and the number of the autonomous system. We click on the IP address to get the information about the owner of the ASN. Well, we see that the owner is <strong> MICROSOFT-CORP-MSN-AS-BLOCK </strong>

![Screenshot from 2023-04-20 09-14-28](https://user-images.githubusercontent.com/94288725/233328800-5c353c93-91a2-4af8-96af-4d5ca768ef38.png)


Finally we get our flag:

CAF_{Artemis!0B80BC9C1E4B_MICROSOFT-CORP-MSN-AS-BLOCK}

Thanks.






