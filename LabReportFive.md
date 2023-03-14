# Experimenting With StringServer (Lab 3)

## > I wanted to see how I can use JDB to find out variable names and their values as a way to debug a program. I think this is really useful because I find myself trying to print variables all the time when debugging, and JDB saves me a ton of print statements!

<hr> 

### Working example: print the string that's returned in the handle code:
![image](https://user-images.githubusercontent.com/43625295/224886298-72445afa-9d1b-4ba0-9e88-a988566f4bf6.png)

So in this example, I could notice really easily that my line-break character is at the start of the string rather than at the end, and that's why strings sent to the server look so weird.
Obviously, I could see that myself in my code BUT - what if I were on a remote machine without VScode open?

### Then I'd have to do something like this:
![image](https://user-images.githubusercontent.com/43625295/224886478-bfc6d094-b181-4d5e-8c60-a5ab46963095.png)

In this case, list would let me inspect the code myself and see where the escape character is.

<br>

### What about actually finding variables?

This part was tricky and took a bit of [documentation reading](https://docs.oracle.com/javase/7/docs/technotes/tools/solaris/jdb.html) and [Stack Overflow](https://stackoverflow.com/questions/42657693/debugging-java-get-list-of-objects-and-local-variables)
* Fortunately, that Stack Overflow post included some clues on the locals command not working properly - that is, using javac -g to make the file's information viewable.
* I also used the help method to discover some other useful options, like fields, which leads me to...

### Why was the field string not showing up as a local variable?

This part I had trouble with in terms of practicality. I want to know all the variables I can print in case I never see code, why not have an option to print all printable statements? Turns out I just had to make do with the fields and locals command:

![image](https://user-images.githubusercontent.com/43625295/224905893-040b0e93-5acd-45da-a0ec-1d0fed44af7b.png)

Notice how locals doesn't print string, a field of the class Handler.
The good lesson from this is, if I'm using JDB to ~~pirate software~~ figure out what variables exist at a breakpoint, I need to test with multiple options from the help menu.


<hr>

## Getting JDB to work in the first place

### I knew a breakpoint was reached when I saw this on the tab:
![image](https://user-images.githubusercontent.com/43625295/224887800-27eb8550-bba7-4cfe-bebf-37af98101c63.png)

The x and the moving dot on the left side of the tab meant the server was stuck - which is exactly what I wanted. Plus, the terminal told me the code reached the breakpoint anyway. I wonder if it's possible for breakpoints to be leftover in programs, and if it can cause frozen servers.
