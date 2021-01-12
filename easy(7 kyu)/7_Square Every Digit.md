# 題目: Does my number look big in this
Welcome. In this kata, you are asked to square every digit of a number and concatenate them.

For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

Note: The function accepts an integer and returns an integer
## 需符合測試
```JavaScript
    Test.assertEquals(squareDigits(9119), 811181);
```
## 解答
```JavaScript
function squareDigits(num){
     function digits(num) { //取幾位數
            return Math.floor(Math.log10(num));
     }
     function denominator(n) { //做為分母
            return Math.pow(10,n)
     }
     function quo(a,n) { //除以10的n次方取商
        return Math.floor(a/denominator(n))
     }
     function remain(a,n){ //除以10的n次方取餘
            return Math.floor(a%denominator(n))
     }
     let a = 9119;
     let val = 0;
     let square = "";
     for(let i=digits(a);i>=0;i--){
        val = Math.pow(quo(remain(a,i+1),i),2)  //remain函數，除以大自己一位數的餘就是自己
        square += val.toString();
     }
     return parseInt(square);
}
```