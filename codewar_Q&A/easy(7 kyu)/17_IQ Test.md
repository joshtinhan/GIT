# Question:List Filtering
Bob is preparing to pass IQ test. The most frequent task in this test is to find out which one of the given numbers differs from the others. Bob observed that one number usually differs from the others in evenness. Help Bob — to check his answers, he needs a program that among the given numbers finds one that is different in evenness, and return a position of this number.
! Keep in mind that your task is to help Bob solve a real IQ test, which means indexes of the elements start from 1 (not 0)
##Examples :
```JavaScript
iqTest("2 4 7 8 10") => 3 // Third number is odd, while the rest of the numbers are even
iqTest("1 2 1 1") => 2 // Second number is even, while the rest of the numbers are odd
```
## Sample Tests
```JavaScript
Test.assertEquals(iqTest("2 4 7 8 10"),3);
Test.assertEquals(iqTest("1 2 2"), 1);
```
## Answer
```JavaScript
function iqTest(numbers){
    let arr = numbers.split(" ");// turn numbers into an array seperated by space
    let even = arr.filter((value)=>{//filter array to all even number
        return value%2 == 0;
    })
    let odd = arr.filter((value)=>{//filter array to all odd number
        return value%2 == 1;
    })
    if(even.length == 1){
        return arr.indexOf(even[0])+1
    }else if(odd.length == 1){
        return arr.indexOf(odd[0])+1
    }
}
```
