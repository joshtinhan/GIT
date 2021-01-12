# Question:Buddy Pairs
You know what divisors of a number are. The divisors of a positive integer n are said to be proper when you consider only the divisors other than n itself. In the following description, divisors will mean proper divisors. For example for 100 they are 1, 2, 4, 5, 10, 20, 25, and 50.

Let s(n) be the sum of these proper divisors of n. Call buddy two positive integers such that the sum of the proper divisors of each number is one more than the other number:

(n, m) are a pair of buddy if s(m) = n + 1 and s(n) = m + 1

For example 48 & 75 is such a pair:

Divisors of 48 are: 1, 2, 3, 4, 6, 8, 12, 16, 24 --> sum: 76 = 75 + 1
Divisors of 75 are: 1, 3, 5, 15, 25 --> sum: 49 = 48 + 1
Task
Given two positive integers start and limit, the function buddy(start, limit) should return the first pair (n m) of buddy pairs such that n (positive integer) is between start (inclusive) and limit (inclusive); m can be greater than limit and has to be greater than n

If there is no buddy pair satisfying the conditions, then return "Nothing" or (for Go lang) nil or (for Dart) null; (for Pascal) [-1, -1].

##Examples
(depending on the languages)
```JavaScript
buddy(10, 50) returns [48, 75] 
buddy(48, 50) returns [48, 75]
or
buddy(10, 50) returns "(48 75)"
buddy(48, 50) returns "(48 75)"
```
## Sample Tests
```JavaScript
describe("Buddy Pairs", ()=>{
  it("Example Tests", ()=>{
    Test.assertDeepEquals( buddy(23, 4669), [48, 75] );
    Test.assertDeepEquals( buddy(4952, 6539), [5775, 6128] );
    Test.assertDeepEquals( buddy(381, 4318), [1050, 1925] );
    Test.assertDeepEquals( buddy(2382, 3679), "Nothing" );
  });
});
```
## Answer
```JavaScript
function buddy(start,limit) {
    var divisors = n=>[...Array(n+1).keys()].slice(1).reduce((s, a)=>s+(!(n % a) && a), 0)-n;
    /* [...Array(n+1).keys()].slice(1) produce an array from 1 to n
        reduce(s,a), parameter s means accumulations while loop to number a; parameter a means current value while loop to number a
        !(n%a) means whether a is n's divisor or not, will return true/false
        (!(n%a) && a) will return a/false
    */
    let arrange = (a,b)=>[...Array(b+1).keys()].slice(a);//produce an array from a to b
    let filter = arrange(start,limit).filter((value)=>value == divisors(divisors(value)-1)-1)//find out which value matchs the condition 
    if(filter.length >= 2){
        return filter.filter((value)=> value == filter[0] || value == divisors(filter[0])-1)
    }else{
        return "Nothing";
    }
}
```
