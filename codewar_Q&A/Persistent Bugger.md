# 題目:Persistent Bugger.
Write a function, persistence, that takes in a positive parameter num and returns its multiplicative persistence, which is the number of times you must multiply the digits in num until you reach a single digit.

For example:
```JavaScript
 persistence(39) === 3 // because 3*9 = 27, 2*7 = 14, 1*4=4
                       // and 4 has only one digit

 persistence(999) === 4 // because 9*9*9 = 729, 7*2*9 = 126,
                        // 1*2*6 = 12, and finally 1*2 = 2

 persistence(4) === 0 // because 4 is already a one-digit number
```
## 需符合測試
```JavaScript
describe('Initial Tests', function () {
  Test.assertEquals(persistence(39),3);
  Test.assertEquals(persistence(4),0);
  Test.assertEquals(persistence(25),2);
  Test.assertEquals(persistence(999),4);
});
```
## 解答
```JavaScript
    function persistence(num) {
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
        let c = 0; //計算function執行幾次
        var outer = function calc(num){
            var res = 1; //給初值
            for(let i=digits(num);i>=0;i--){
                res *= quo(remain(num,i+1),i) //remain函數，除以大自己一位數的餘就是自己
            }
            if(res != 0){// 防止res為零導致結果無限大
            var time = digits(res);//time代表幾位數
            }else{
            var time = 0;
            }
            if(time>0){//當兩位數的時候
                c += 1;
                return res = outer(res);
            }else if(time == 0 && num>=10){//當只有個位數且輸入值大於等於10
                c += 1;
                return res %= 10;
            }else if(num<10){//避免輸入值<10的時候執行次數c會加1
                c = 0;
            }
        }
        console.log(outer(num));
        return c;
}
```
