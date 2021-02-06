# Question:Range Extraction
A format for expressing an ordered list of integers is to use a comma separated list of either

individual integers
or a range of integers denoted by the starting integer separated from the end integer in the range by a dash, '-'. The range includes all integers in the interval including both endpoints. It is not considered a range unless it spans at least 3 numbers. For example "12,13,15-17"
Complete the solution so that it takes a list of integers in increasing order and returns a correctly formatted string in the range format.
```JavaScript
solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20]);
// returns "-6,-3-1,3-5,7-11,14,15,17-20"
```
The results are tested after being rounded to 4 decimal places using Javascript's toFixed method.
## Sample Tests
```JavaScript
Test.assertEquals(solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20]), "-6,-3-1,3-5,7-11,14,15,17-20")
```
## My Solution
```JavaScript
function solution(a){
  let arr =[];
    let ans = new Array;
    for(let i=0;i<a.length;i++){
        if(a[i+1] -a[i] == 1 && a[i]- a[i-1] !=1 && a[i+2]- a[i+1] == 1){
            for(let j=1;j<a.length;j++){
                if(a[i+j]-a[i] == j){
                    arr = a[i]+"-"+a[i+j]
                }
            }
            ans.push(arr)
        }else if(a[i+1] -a[i] != 1 && a[i]-a[i-1] != 1 && i!= a.length-1){
            ans.push(a[i])
        }else if(a[i]- a[i-1] !=1 && a[i+1]-a[i] == 1 && a[i+2]-a[i+1]!=1){
            ans.push(a[i],a[i+1])
        }else if(i==a.length-1 && a[i]-a[i-1]!=1){
            ans.push(a[i])
        }
    }
  return ans.join(",")
}
```
## Clever Solution
```JavaScript
function solution(list){
   for(var i = 0; i < list.length; i++){
      var j = i;
      while(list[j] - list[j+1] == -1) j++;
      if(j != i && j-i>1) list.splice(i, j-i+1, list[i] +'-'+list[j]);
  }
  return list.join();
}
```
