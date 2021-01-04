# 題目:Stop gninnipS My sdroW!
Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.

Examples: spinWords( "Hey fellow warriors" ) => returns "Hey wollef sroirraw" spinWords( "This is a test") => returns "This is a test" spinWords( "This is another test" )=> returns "This is rehtona test"

## 需符合測試
```JavaScript
    Test.assertEquals(spinWords("Welcome"), "emocleW");
    Test.assertEquals(spinWords("Hey fellow warriors"), "Hey wollef sroirraw");
    Test.assertEquals(spinWords("This is a test"), "This is a test");
    Test.assertEquals(spinWords("This is another test"), "This is rehtona test");
    Test.assertEquals(spinWords("You are almost to the last test"), "You are tsomla to the last test");
    Test.assertEquals(spinWords("Just kidding there is still one more"), "Just gniddik ereht is llits one more");
    Test.assertEquals(spinWords("Seriously this is the last one"), "ylsuoireS this is the last one");
```

## 解答
```JavaScript
    function spinWords(phrase){
        let arr = phrase.split(' ');//先將字串變成以空格隔開的陣列
        let str = '';//令str為空字串
            for(let j=0;j<arr.length;j++){
                if(arr[j].length>4){//如果句子中第j個單字的字元長度大於4個
                    for(let i=arr[j].length-1;i>=0;i--){//用i--的方式將單字倒過來
                            str += arr[j][i];
                    }
                }else{//如果句子中的第j個單字的字元長度小於等於4個
                    str += arr[j];//維持原樣
                }
                str += ' ';//給每個字加一個空格
            }
        return str.trimRight();//去除最後一個字的空格
     }
```