# Question:Build Tower
for example, a tower of 3 floors looks like below
```JavaScript
[
  '  *  ', 
  ' *** ', 
  '*****'
]
```
and a tower of 6 floors looks like below
```JavaScript
[
  '     *     ', 
  '    ***    ', 
  '   *****   ', 
  '  *******  ', 
  ' ********* ', 
  '***********'
]
```
## Sample Tests
```JavaScript
Test.assertDeepEquals(towerBuilder(1), ["*"]);
Test.assertDeepEquals(towerBuilder(2), [" * ","***"]);
Test.assertDeepEquals(towerBuilder(3), ["  *  "," *** ","*****"]);
```
## Solution
```JavaScript
function towerBuilder(nFloors) {
  let arr = [];
  for(let i=0;i<nFloors;i++){
      let space =  " ".repeat(nFloors-i-1) //single side composed of space
      arr.push(space+new String("*").repeat(2*i+1)+space)
  }
  return arr
}
```
