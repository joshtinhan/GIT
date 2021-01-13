# Question:Playing with digits
Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.
```JavaScript
moveZeros([false,1,0,1,2,0,1,3,"a"]) // returns[false,1,1,2,1,3,"a",0,0]
```
## Sample Tests
```JavaScript
Test.assertEquals(
  JSON.stringify(moveZeros([1,2,0,1,0,1,0,3,0,1])),
  JSON.stringify([ 1, 2, 1, 1, 3, 1, 0, 0, 0, 0 ])
);
```
## Solution
```JavaScript
var moveZeros = function (arr) {
  let noZero = arr.filter((value)=> value !== 0);
  let zero = Array.from({length:arr.length - noZero.length},(v,i)=>i-i);//produce an array with all element is zero which length is diffrence between noZero and zero.
  return noZero.concat(zero); // concat two arrays
}
```
