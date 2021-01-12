# Question:Is this a triangle?
Implement a method that accepts 3 integer values a, b, c. The method should return true if a triangle can be built with the sides of given length and false in any other case.

(In this case, all triangles must have surface greater than 0 to be accepted).
## Sample Tests
```JavaScript
Test.describe("PublicTest", function() {
    Test.assertEquals(isTriangle(1,2,2), true);
    Test.assertEquals(isTriangle(7,2,2), false);
});
```
## Answer
```JavaScript
function isTriangle(a,b,c)
{
   let arr = [a,b,c];
        let boolean = [];
        for(i=0;i<arr.length;i++){
            let last = arr[(i+2)%arr.length]-1;//the rest one
            let plusNext = arr[i]+arr[(i+1)%arr.length];//current value plus next value
            if(plusNext > last){
            }else{
                boolean.push(false); // if false then push into boolean array
            }
        }
        return (Boolean(boolean<1)); 
}
```
