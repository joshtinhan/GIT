# Question:Create Phone Number
You are going to be given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.

Examples 
```JavaScript
Kata.getMiddle("test") should return "es"

Kata.getMiddle("testing") should return "t"

Kata.getMiddle("middle") should return "dd"

Kata.getMiddle("A") should return "A"

```
## Sample Tests
```JavaScript
Test.describe("GetMiddle", function() {
  Test.it("Tests", function() {
    Test.assertEquals(getMiddle("test"),"es");
    Test.assertEquals(getMiddle("testing"),"t");
    Test.assertEquals(getMiddle("middle"),"dd");
    Test.assertEquals(getMiddle("A"),"A");
  });
});
```
## Answer
```JavaScript
function getMiddle(s)
{
  let length = s.split("").length;
  if(length%2 == 0){
    return(s[(length/2)-1]+s[(length/2)])
  }else{
    return (s[Math.floor(length/2)])
  }
    
}
```
