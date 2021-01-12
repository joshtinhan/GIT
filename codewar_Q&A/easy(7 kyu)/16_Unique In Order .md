# Question:List Filtering
Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.
For example:
```JavaScript
uniqueInOrder('AAAABBBCCDAABBB') == ['A', 'B', 'C', 'D', 'A', 'B']
uniqueInOrder('ABBCcAD')         == ['A', 'B', 'C', 'c', 'A', 'D']
uniqueInOrder([1,2,2,3,3])       == [1,2,3]
```
## Sample Tests
```JavaScript
Test.assertSimilar(uniqueInOrder('AAAABBBCCDAABBB'), ['A','B','C','D','A','B'])
```
## Answer
```JavaScript
var uniqueInOrder=function(iterable){
  let arr = iterable.split('');
  let unique = [];
  for(i=0;i<arr.length;i++){
      if(arr[i]!=arr[(i+1)%arr.length]){ // if current value not equal next value, push into unique array
          unique.push(arr[i])
      }
  }
  return unique;
}
```
