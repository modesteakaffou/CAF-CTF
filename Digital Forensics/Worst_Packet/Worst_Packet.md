# WORST PACKET

## 1. Instructions

![Instructions](https://user-images.githubusercontent.com/94288725/233292389-4805fc12-0018-4c83-a566-edbdb4088f8e.png)

#### Resource :

Download  [challenge_file.zip](https://github.com/modesteakaffou/CAF_CTF/files/11283553/challenge_file.zip "download")


## 2. Solution

We have a pcap file in which we are asked to find the percentage of malformed packets. To do this, we will start by opening the challenge_file.pcap file contained inside the zip file with the wireshark tool :


![Wireshark capture](https://user-images.githubusercontent.com/94288725/233294313-d39fd62e-c2d3-47a6-87be-fb12063ba43f.png)

Click on the statistics menu and select protocol hierarchy. You will see the percentage of malformed packets.

![Statistics packet](https://user-images.githubusercontent.com/94288725/233299216-5f672075-7e2b-4b80-8b0b-0732f99b27c7.png)

And here is the work, we find the percentage of malformed packets which is 4.2

The flag is: CAF_{4.2}

Thank you.
