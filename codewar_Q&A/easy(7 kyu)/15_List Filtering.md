# Question:List Filtering
In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.
Example
```JavaScript
filter_list([1,2,'a','b']) == [1,2]
filter_list([1,'a','b',0,15]) == [1,0,15]
filter_list([1,2,'aasf','1','123',123]) == [1,2,123]
```
## Sample Tests
```JavaScript
Test.assertSimilar(filter_list([1,2,'a','b']),[1,2])
Test.assertSimilar(filter_list([1,'a','b',0,15]),[1,0,15])
Test.assertSimilar(filter_list([1,2,'aasf','1','123',123]),[1,2,123])
```
## Answer
```JavaScript
function filter_list(l) {
  let notString = l.filter((value)=>{
    return typeof(value)!= "string";
  })
  return notString;
}
```
