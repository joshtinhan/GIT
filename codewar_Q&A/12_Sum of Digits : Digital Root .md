# Question:Sum of Digits / Digital Root
Digital root is the recursive sum of all the digits in a number.

Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.

Examples
    16  -->  1 + 6 = 7
   942  -->  9 + 4 + 2 = 15  -->  1 + 5 = 6
132189  -->  1 + 3 + 2 + 1 + 8 + 9 = 24  -->  2 + 4 = 6
493193  -->  4 + 9 + 3 + 1 + 9 + 3 = 29  -->  2 + 9 = 11  -->  1 + 1 = 2
## Sample Tests
```JavaScript
Test.assertEquals( digital_root(16), 7 )
Test.assertEquals( digital_root(456), 6 )
```
## Answer
```JavaScript
function digital_root(n) {
    split = (n)=>{
    return n.toString().split("");//turn n into an array
    }
    function calc(n) {
        var res = 0;// init value = 0;
        for (let index = 0; index < split(n).length; index++) {
            res += parseInt(split(n)[index]); // res = sum of each digit of array
        }
        return res
    }
    if(split(n).length>1){
        return calc(calc(n)); //recursive function when digits > 1
    }else if(split(n).length == 1){
        return n // final value
    }
}
```
