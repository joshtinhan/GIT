# Question:Create Phone Number
In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

Example:
```JavaScript
highAndLow("1 2 3 4 5");  // return "5 1"
highAndLow("1 2 -3 4 5"); // return "5 -3"
highAndLow("1 9 3 4 -5"); // return "9 -5
```
## Sample Tests
```JavaScript
Test.assertEquals(highAndLow("4 5 29 54 4 0 -214 542 -64 1 -3 6 -6"), "542 -214");
```
## Answer
```JavaScript
function highAndLow(numbers){
  let arr = numbers.split(" ");
  let sort = arr.sort((a,b)=> -(a-b));//sort array descent
  return sort[0] +" "+sort[sort.length-1];
}
```
