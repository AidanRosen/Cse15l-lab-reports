# How to log into your ieng6 account

***

## Installing VS Code
- I used the lab computer, so I didn't need to download VS Code. 
- However, installing is straightforward - follow the instructions given by the installer!
- * The installer is [here](https://code.visualstudio.com/Download)

The end result, after installing and opening, should look like this:
![image](https://user-images.githubusercontent.com/43625295/215300187-897176f9-7cac-47fd-a93c-e6410cf71be9.png)


***

## Remotely Connecting
- First you need to open a terminal in VS code. 
-  * _For both Mac and Windows, the command is_ control (**not** command) + "\`" <-- in the upper left, on tilde "~"
- Before logging in, you _**MUST**_ reset your password online!
-  * Remember where you found your 15l account? [It was here](https://jpolitz.github.io/cse-15l-lab-report/index.html).
-  * Press "reset your password" at the top of the 15l area, regardless of whether your current password works
-  * Resetting sets the password up for ssh. Don't worry, you can reuse your old one.
- Now, go to the terminal and type in the command: 
- '''
- ssh [your 15l username]@ieng6.ucsd.edu //<-- replace the brackets part with your username
- '''
- It should look like this:
![image](https://user-images.githubusercontent.com/43625295/211910009-765fcbab-e838-42c1-b14a-3b1d8f6fdcc4.png)


Note: Type "yes" even though the server can't establish security. You won't see any changes while typing in your password, just type in your password. If your password doesn't work, try resetting


***


## Trying some commands:

- Now that you're logged in, it should look like this (yes, it will say last failed login):

![image](https://user-images.githubusercontent.com/43625295/211909592-bbaaec64-621c-46fd-b519-ea1a25589f7d.png)

- This terminal acts like any old one, except that you're accessing a remote directory. Try listing the directory! Try navigating around it.


# You may even get some interesting results!

![image](https://user-images.githubusercontent.com/43625295/211910481-b13246e6-585b-47e7-9620-ba6e7ef32b54.png)


