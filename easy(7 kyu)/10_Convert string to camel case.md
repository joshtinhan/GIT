# 題目: Convert string to camel case
Complete the method/function so that it converts dash/underscore delimited words into camel casing. The first word within the output should be capitalized only if the original word was capitalized (known as Upper Camel Case, also often referred to as Pascal case).

Examples
```JavaScript
toCamelCase("the-stealth-warrior") // returns "theStealthWarrior"
toCamelCase("The_Stealth_Warrior") // return
```
## 需符合測試
```JavaScript
    Test.assertEquals(toCamelCase(''), '', "An empty string was provided but not returned")
    Test.assertEquals(toCamelCase("the_stealth_warrior"), "theStealthWarrior", "toCamelCase('the_stealth_warrior') did not return correct value")
    Test.assertEquals(toCamelCase("The-Stealth-Warrior"), "TheStealthWarrior", "toCamelCase('The-Stealth-Warrior') did not return correct value")
    Test.assertEquals(toCamelCase("A-B-C"), "ABC", "toCamelCase('A-B-C') did not return correct value")

```
## 解答
```JavaScript
function toCamelCase(str){
    let ans = "";
    if(str.match("-") != null){//如果字串內含有"-"
      let hyphen = str.split("-");
      for(i=0;i<hyphen.length;i++){
          ans += hyphen[i].charAt(0).toUpperCase()+hyphen[i].slice(1)
      }
    }else if(str.match("_") != null){//如果字串內含有"_"
      let dash = str.split("_");
      ans += dash[0];
      for(i=1;i<dash.length;i++){
          ans += dash[i].charAt(0).toUpperCase()+dash[i].slice(1)
      } 
    }else if(str===null){//如果字串為空
      ans = str;
    }
  return ans;
}
```