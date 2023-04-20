# BABY HACKER

## 1. Instructions

![instructions](https://user-images.githubusercontent.com/94288725/233351115-3636fd42-21d1-4dc6-83f7-c2688e0cd764.png)

Link for challenge : http://51.178.18.146:40000/chall1_086ecf773bbd273e9005d731f743df5a/

## 2. Solution

Don't be shy, click on the link given in the challenge. here is : http://51.178.18.146:40000/chall1_086ecf773bbd273e9005d731f743df5a/

![challenge captre](https://user-images.githubusercontent.com/94288725/233352242-849b19be-5939-4375-a96d-38be09de389d.png)

The web application tells me that I need the PHP page, and says why did I accept anything else?
So I have to specify to the server that I want the PHP pages, it's through the accept header that I can tell the server that. Let's use Burpsuite.

![Screenshot from 2023-04-20 11-36-09](https://user-images.githubusercontent.com/94288725/233357103-f413208d-e842-431e-8998-17818ac575c9.png)

When you open burpsuite, go to the "target" tab and click on the "open a browser" button. This will open a browser on which we will be able to carry out our attack which will consist in blocking the http flow then to control it. Once the burpsuite browser is open, paste the link in the url field.


