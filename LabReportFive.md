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
