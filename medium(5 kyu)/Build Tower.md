# Question:Calculate Variance
Write a function which will accept a sequence of numbers and calculate the variance for the sequence.

The variance for a set of numbers is found by subtracting the mean from every value, squaring the results, adding them all up and dividing by the number of elements.

For example, in pseudo code, to calculate the variance for [1, 2, 2, 3].
```JavaScript
mean = (1 + 2 + 2 + 3) / 4
=> 2

variance = ((1 - 2)^2 + (2 - 2)^2 + (2-2)^2 + (3 - 2)^2)  /  4
=> 0.5
```
The results are tested after being rounded to 4 decimal places using Javascript's toFixed method.
## Sample Tests
```JavaScript
describe("Attempts to validate the  Khan example set", function() {
  var numbers1 = [-10, 0, 10, 20, 30];
  var numbers2 = [8, 9, 10, 11, 12];
  var numbers3 = [1.5, 2.5, 4, 2, 1, 1];
  
  it("Calculates a variance of 200 for example 1", function() {
    return Test.assertEquals(variance(numbers1).toFixed(4), "200.0000", "Variance for the first example set is not correct");
  });
  it("Calculates a variance of 2 for example 2", function() {
    return Test.assertEquals(variance(numbers2).toFixed(4), "2.0000", "Variance for the second example set is not correct");
  });
  it("Calculates a variance of 1.0833333333333333 for example 3", function() {
    return Test.assertEquals(variance(numbers3).toFixed(4), "1.0833", "Variance for the third example set is not correct");
  });
});
```
## Solution
```JavaScript
var variance = function(numbers) {
  let sum = (acc,val) => acc + val; //return sum of each element of numbers array
  let mean = (numbers.reduce(sum,0)/numbers.length).toFixed(4); //the mean is dividing by the number of elements of numbers array
  let variance = (acc,val)=> acc + Math.pow((val-mean),2) 
  return numbers.reduce(variance,0)/numbers.length
};
```
