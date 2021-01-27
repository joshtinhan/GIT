# Simple Pig Latin
Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.
Examples
```JavaScript
pigIt('Pig latin is cool'); // igPay atinlay siay oolcay
pigIt('Hello world !');     // elloHay orldway !
```
## Sample Tests
```JavaScript
Test.assertEquals(pigIt('Pig latin is cool'),'igPay atinlay siay oolcay')
Test.assertEquals(pigIt('This is my string'),'hisTay siay ymay tringsay')
```
## Solution
```JavaScript
function pigIt(str){
        var letters = /[a-z]+/ig;
        let words = str.match(letters);
        console.log(words);
        let ans = new Object;
        let obj = new Object;
        let sentence = "";
        let arr = words.forEach((element,i) => {
            obj[i] = (element.split(""))
        })
        for(i=0;i<words.length;i++){
            obj[i].push(obj[i][0]+"ay");
            obj[i].shift();
            ans[i] = obj[i].join("");
            sentence += ans[i]+" ";
        }
        return sentence.trimRight();
}
```
