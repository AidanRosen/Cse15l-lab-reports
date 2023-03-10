# Part One

Here's the code behind my StringServer:

![image](https://user-images.githubusercontent.com/43625295/218667712-901286a9-245f-45f3-a751-b0f32b72eea5.png)


To start the server, the Server.start method triggers on the port, 3000 which was written in directly.

## Before adding a string:
- The url has no add-string written in, so the page defaults to show the empty, default string. This is within the handleRequest method.

![image](https://user-images.githubusercontent.com/43625295/215659393-5ce916d7-25c4-4f70-9d3d-d9d5df968a92.png)

Interestingly, there's a bar of space above the "hello". This is from going to the add-string route and putting in a blank parameter, which appended a "/n" character to my empty string.

## After adding "hello":

![image](https://user-images.githubusercontent.com/43625295/215659475-7e01477c-6d54-454b-8df8-c77aae0c24b9.png)

Inside the handleRequest method, my servers string is now "/n" + hello. The String string field is what retains the input, and the field is modified by the parameters element at index 1 in the inputted string args.


## After adding "how are you":

![image](https://user-images.githubusercontent.com/43625295/215659536-631ec4e9-f5a9-453f-86d8-783d0683177d.png)

Like before, the server string is now ```"/n" + Hello + "/n" + How are you```. Since the code is literally ```string += "\n" + parameters[1]```, the string field only ever builds on itself without resetting.


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

The non-failure inducing input, {1}, which produced {1} as expected:

```
@Test
public void TestReverseInPlace(){
  
  int[] input = {1};
  ArrayExample.reverseInPlace(input);
  assertArrayEquals(new int[]{1}, input);
}
```


Error with input {1, 2, 3} versus no errors with input {1}:

![image](https://user-images.githubusercontent.com/43625295/218663353-99c4aab7-3867-4541-aef9-3859ef848ecf.png)



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
 
 By creating a temp variable, I prevented the loss of information from setting the current indexed element to something else. In other words, I saved the changed data to be used again at ```arr[arr.length - i - 1] = temp```. By changing the loop to go up to arr.length/2, I swap elements around the middle, not swapping all the way through and ending up with what I originally started with.
 
 
 # Part 3
 
 I learned that JUnit can be prone to heap errors - both my partner and I experienced heap issues when working with array comparisons that were just a little too big. I also learned about Github Desktop and having issues with my terminal saying "main classpath not found" and some relation it may have to Github Desktop.
 
