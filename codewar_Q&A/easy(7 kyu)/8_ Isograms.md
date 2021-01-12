# 題目: Isograms
An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.
```JavaScript
isIsogram("Dermatoglyphics") == true
isIsogram("aba") == false
isIsogram("moOse") == false // -- ignore letter case
```
## 需符合測試
```JavaScript
        Test.assertSimilar( isIsogram("Dermatoglyphics"), true );
        Test.assertSimilar( isIsogram("isogram"), true );
        Test.assertSimilar( isIsogram("aba"), false, "same chars may not be adjacent" );
        Test.assertSimilar( isIsogram("moOse"), false, "same chars may not be same case" );
        Test.assertSimilar( isIsogram("isIsogram"), false );
        Test.assertSimilar( isIsogram(""), true, "an empty string is a valid isogram" );
```
## 解答
```JavaScript
    function isIsogram(str){
        let aArr = str.toLowerCase().split('');//字串變小寫轉陣列
        let empty = new Array;
        for(i of aArr){
            let compare = aArr.filter((value)=>{
                return value == i; //過濾出陣列中有value等於自己
            })
            if(compare.length>1){ //陣列中value等於自己的大於1就是重複的字母
                empty.push(compare);
            }
        }
        return (Boolean(empty.length<1)); 
    }
```

