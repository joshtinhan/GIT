# 題目:Printer Errors
In a factory a printer prints labels for boxes. For one kind of boxes the printer has to use colors which, for the sake of simplicity, are named with letters from a to m.

The colors used by the printer are recorded in a control string. For example a "good" control string would be aaabbbbhaijjjm meaning that the printer used three times color a, four times color b, one time color h then one time color a...

Sometimes there are problems: lack of colors, technical malfunction and a "bad" control string is produced e.g. aaaxbbbbyyhwawiwjjjwwm with letters not from a to m.

You have to write a function printer_error which given a string will return the error rate of the printer as a string representing a rational whose numerator is the number of errors and the denominator the length of the control string. Don't reduce this fraction to a simpler expression.

The string has a length greater or equal to one and contains only letters from ato z.
## 需符合測試
```JavaScript
    Test.describe("printerError",function() {
    Test.it("Basic tests",function() {   
    var s="aaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbmmmmmmmmmmmmmmmmmmmxyz"
    Test.assertEquals(printerError(s), "3/56")
})})
```
## 解答
```JavaScript
    function printerError(s) {
        //把輸入字串按每個字拆成陣列
        let originalArr = s.split("");
        let basic = "abcdefghijklm";
        //正確的字串為a-m，一樣拆成陣列
        let correctArr = basic.split("");
        let errorArr = originalArr.filter((item,index)=>{
            //把correctArr陣列裡沒有的字母列出來
            return correctArr.indexOf(item) == -1;
        })
        return errorArr.length+"/"+originalArr.length;
    }
```
## 挑戰: 將error分組並列出各有幾個
```JavaScript
    let s = "aaabbbcxxdemxydddy";
    let basic = "abcdefghijklm";
    let correctArr = basic.split("");
    let errorArr = originalArr.filter((item,index)=>{
        return correctArr.indexOf(item) == -1;
    })
    //用reduce函數，accumulator的initialValue為{}
    let sort = errorArr.reduce((accumulator, currentValue)=>{
        //如果已經存在accumulator[currentValue]，則值+1
        if(accumulator[currentValue]){
            accumulator[currentValue]++;
        }
        //loop第一次出現的字母都會進else迴圈
        else{
            accumulator[currentValue] = 1;
        }
        return accumulator;
    },{})
    console.log(sort); //{x: 3, y: 3}
```
