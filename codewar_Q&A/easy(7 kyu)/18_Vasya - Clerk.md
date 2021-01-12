# Question:Vasya - Clerk
The new "Avengers" movie has just been released! There are a lot of people at the cinema box office standing in a huge line. Each of them has a single 100, 50 or 25 dollar bill. An "Avengers" ticket costs 25 dollars.

Vasya is currently working as a clerk. He wants to sell a ticket to every single person in this line.

Can Vasya sell a ticket to every person and give change if he initially has no money and sells the tickets strictly in the order people queue?

Return YES, if Vasya can sell a ticket to every person and give change with the bills he has at hand at that moment. Otherwise return NO.
Example
```JavaScript
tickets([25, 25, 50]) // => YES 
tickets([25, 100]) // => NO. Vasya will not have enough money to give change to 100 dollars
tickets([25, 25, 50, 50, 100]) // => NO. Vasya will not have the right bills to give 75 dollars of change (you can't make two bills of 25 from one of 50)
```
## Sample Tests
```JavaScript
Test.assertEquals(tickets([25, 25, 50, 50]), "YES");
Test.assertEquals(tickets([25, 100]), "NO");
```
## Answer
```JavaScript
function tickets(peopleInLine){
   let arr = [];
   let reduceArr = peopleInLine.reduce((accumulator,currentValue)=>{
            arr.push(currentValue - accumulator);//each value of arr represents change that clerk current could give
            return accumulator + currentValue //let accumulator = sum of previous values
        },25)
        for(i=arr.length-1;i>=0;i--){
            if(arr[i]-arr[i-1]<=25){//There's enough change to give
                return "YES"
            }else{
                return "NO"
            }
        }
}
```
