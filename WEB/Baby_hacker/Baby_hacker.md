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

![Screenshot from 2023-04-20 11-36-37](https://user-images.githubusercontent.com/94288725/233358288-3cf06e10-85ad-4198-8442-a7bffeee5f75.png)

![Screenshot from 2023-04-20 11-38-20](https://user-images.githubusercontent.com/94288725/233358385-44546a7e-b471-42b3-8c59-87485b903085.png)

After that return to burpsuite itself and you will see the information of the http query.

![Screenshot from 2023-04-20 11-38-33](https://user-images.githubusercontent.com/94288725/233358736-c05b0f25-d777-4aa0-a328-df00e42ecef6.png)

We are going to modify the information of the "accept" header so that it asks only for php pages. You will have noticed in the "accept" header that to ask for an html page, you have to type text/html; to ask for an image, you have to type image/my_image.png or for an application, type application/my_application. Logically, if we want to request php pages, we will type text/php.

![Screenshot from 2023-04-20 11-39-54](https://user-images.githubusercontent.com/94288725/233359801-f7ee93de-a9e8-49a4-914d-1e2c9fbfae2b.png)

If you want to modify the accept header, it's not in the "target" tab but in the "repeater" tab, don't ask me why.

![Screenshot from 2023-04-20 11-45-51](https://user-images.githubusercontent.com/94288725/233360240-249246e7-a8ce-4ab2-8a70-92ae3eb752e6.png)

And bim! Here is the flag:

The flag is: <strong> CAF_{H1tm4n_d035n0t_all0w_h3ad3r!} </strong>

Thanks
