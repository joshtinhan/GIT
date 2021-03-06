# 題目: Take a Ten Minute Walk
You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. The city provides its citizens with a Walk Generating App on their phones -- everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']). You always walk only a single block for each letter (direction) and you know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).

## 需符合測試
```JavaScript
        //some test cases for you...
        Test.expect(isValidWalk(['n','s','n','s','n','s','n','s','n','s']), 'should return true');
        Test.expect(!isValidWalk(['w','e','w','e','w','e','w','e','w','e','w','e']), 'should return false');
        Test.expect(!isValidWalk(['w']), 'should return false');
        Test.expect(!isValidWalk(['n','n','n','s','n','s','n','s','n','s']), 'should return false');
```
## 解答
```JavaScript
    function isValidWalk(walk) {
        let countN = walk.filter(function (item,index,array) {
            if(item == 'n'){//過濾成陣列裡都是n
                return true;
            }
          })
        let countS = walk.filter(function (item,index,array) {
        if(item == 's'){//過濾成陣列裡都是s
            return true;
        }
        })
        let countE = walk.filter(function (item,index,array) {
        if(item == 'e'){//過濾成陣列裡都是e
            return true;
        }
        })
        let countW = walk.filter(function (item,index,array) {
        if(item == 'w'){//過濾成陣列裡都是w
            return true;
        }
        })
        return(Boolean(countN.length == countS.length && countE.length == countW.length && countN.length < 6 && countE.length < 6));
    }
```

