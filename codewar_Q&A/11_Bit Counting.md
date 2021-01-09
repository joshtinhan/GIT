# Question: Bit Counting
Write a function that takes an integer as input, and returns the number of bits that are equal to one in the binary representation of that number. You can guarantee that input is non-negative.

Example: The binary representation of 1234 is 10011010010, so the function should return 5 in this case

## Sample Tests:
```JavaScript
Test.assertEquals(countBits(0), 0);
Test.assertEquals(countBits(4), 1);
Test.assertEquals(countBits(7), 3);
Test.assertEquals(countBits(9), 2);
Test.assertEquals(countBits(10), 2);
```
## Answer:
```JavaScript
var countBits = function(n) {
  let binary = n.toString(2); //turn n into binary
  let arr = binary.split("").filter((value)=>{ //filter binary array which including 1
      return value == 1;
  })
  return arr.length;
};
```