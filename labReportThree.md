# Part One

Here's the code behind my StringServer:
![image](https://user-images.githubusercontent.com/43625295/215660005-f2446b12-d2d7-4f04-b8ab-0ee75cda588f.png)


To start the server, the Server.start method triggers on the port, 3000 which was written in directly.

##Before adding a string:
- The url has no add-string written in, so the page defaults to show the empty, default string. This is within the handleRequest method.

![image](https://user-images.githubusercontent.com/43625295/215659393-5ce916d7-25c4-4f70-9d3d-d9d5df968a92.png)

Interestingly, there's a bar of space above the "hello". This is from going to the add-string route and putting in a blank parameter, which appended a "/n" character to my empty string.

## After adding "hello":

![image](https://user-images.githubusercontent.com/43625295/215659475-7e01477c-6d54-454b-8df8-c77aae0c24b9.png)

Inside the handleRequest method, my servers string is now "/n" + hello.


## A fter adding "how are you":

![image](https://user-images.githubusercontent.com/43625295/215659536-631ec4e9-f5a9-453f-86d8-783d0683177d.png)

Like before, the server string is now "/n" + Hello + "/n" + How are you


# Part Two

For the array reverse in place method, the input {1, 2, 3} did not produce {3, 2, 1} as expected.:
```
@Test
public void TestReverseInPlace(){
  
  int[] input = {1, 2, 3};
  ArrayExample.reverseInPlace(input);
  assertArrayEquals(new int[]{3, 2, 1}, input);
}
```

The non-failure inducing input:

```
@Test
public void TestReverseInPlace(){
  
  int[] input = {1};
  ArrayExample.reverseInPlace(input);
  assertArrayEquals(new int[]{1}, input);
}
```


Error with input {1, 2, 3}:
![image](https://user-images.githubusercontent.com/43625295/215668791-d135e22a-2464-41ca-b1cd-cf4d13fa115b.png)

No error with input {1}:
![image](https://user-images.githubusercontent.com/43625295/215668747-2927d0f9-b71c-4677-aef6-b86027213f45.png)



The original code:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
  
 ```
  
 The fix : 
 
 ```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {

      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1]; //[0 1 2] --> length = 3 [2 1 0] <-- has duplicates though after modifying over time: [ 2 1 2] is the first swap
      arr[arr.length - i - 1] = temp; 

      //[0 1 2 3] length == 4, 4/2 == 2;
      //[0 1 2] lenght == 3, 3/2 rounds down to 1, will swap as expected 
    }
  }
 ```
 
 By creating a temp variable, I prevented the loss of information. By changing the loop to go up to arr.length/2, I swap elements around the middle, not swapping all the way through and ending up with what I originally started with.
 
 
 # Part 3
 
 I learned that JUnit can be prone to heap errors - both my partner and I experienced heap issues when working with array comparisons that were just a little too big. I also learned about Github Desktop and having issues with my terminal saying "main classpath not found" and some relation it may have to Github Desktop.
 
