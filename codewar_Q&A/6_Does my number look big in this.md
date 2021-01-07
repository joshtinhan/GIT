# 題目: Does my number look big in this
A Narcissistic Number is a positive number which is the sum of its own digits, each raised to the power of the number of digits in a given base. In this Kata, we will restrict ourselves to decimal (base 10).

For example, take 153 (3 digits), which is narcisstic:
    1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153
and 1652 (4 digits), which isn't:

    1^4 + 6^4 + 5^4 + 2^4 = 1 + 1296 + 625 + 16 = 1938
The Challenge:

Your code must return true or false depending upon whether the given number is a Narcissistic number in base 10.

Error checking for text strings or other invalid inputs is not required, only valid positive non-zero integers will be passed into the function.
## 需符合測試
```JavaScript
    describe( "Narcissistic Function", function() {
    it( "should find small numbers are all narcissistic", function() {
        Test.assertEquals(narcissistic( 7 ), true, "7 is narcissistic" );
    });
    
    it( "should find these numbers are narcissistic", function() {
        Test.assertEquals(narcissistic( 371 ), true, "371 is narcissistic" );
    });
    });
```
## 解答
```JavaScript
    function narcissistic(value) {
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
        let ans = 0;
        for(let i=digits(value);i>=0;i--){
            ans += Math.pow(quo(remain(value,i+1),i),digits(value)+1)  //remain函數，除以大自己一位數的餘就是自己
        }
        return Boolean(value == ans);
}
```