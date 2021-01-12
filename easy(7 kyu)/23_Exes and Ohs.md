# Question:Create Phone Number
Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.

Examples input/output:
```JavaScript
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false
```
## Sample Tests
```JavaScript
Test.assertEquals(XO('xo'),true);
Test.assertEquals(XO("xxOo"),true);
Test.assertEquals(XO("xxxm"),false);
Test.assertEquals(XO("Oo"),false);
Test.assertEquals(XO("ooom"),false);
```
## Answer
```JavaScript
function XO(str) {
    let arr = str.split("");
    let x = arr.filter((value)=> value.toLowerCase() == "x");//filter the array which value is x
    let o = arr.filter((value)=> value.toLowerCase() == "o");//filter the array which value is o
    return Boolean(x.length == o.length);
}
```
