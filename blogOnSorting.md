<h1> Sorting in javaScript </h1>

Most of the times, while solving any problems you will encounter the sorting of numbers, strings, array of objects, Different cases strings etc.

Javascript provide built in function to sort and also ability to write own sort functions. It provides two methods for sorting.

* sort() - sort an array of elements in ascending order
* reverse() - sort an array of elements in descending order

```
let array = [3,5,7,2,1,9,10,4];
array.sort();
console.log(array);      // [1,10,2,3,4,5,7,9]

```

In the above case, while sorting it is sorting based on the first digit and not on the whole numbers.To overcome this method by passing a callback function to the sort method and
passing two arguments to compare.

<b>Syntax :</b> sort((a,b) => { /* ..... */ });

if a < b , then it will return < 0, i.e,    a before b
if a > b , then it will return > 0, i.e,    a after b
if a == b, then it will return is 0, i.e,    a equal to b

sorting Integers : 

``` 
let array = [5,9,2,45,12,21,89];

array.sort((value1, value2) => {
    if(value1 < value2){
      return -1;
    }
    else if(value1 > value2){
      return 1;
    }
    else{
      return 0;
    }
});

console.log(array);      // [2,5,9,12,21,45,89]

```

In the above code, comparing one value with another value and if it's return less than 0, then value1 should before value2.  if it's greater than 0, then value1 should come after value2.
if both values are equal, it returns 0.

We can also use another method , while doing sorting with numbers. Let's take an example with array of floating point numbers.

Ascending order : 

```
let floatingPointNumbers = [7.345, 3.5678, 6.899, 7.467, 1.436568, 9.34505, 9.35405];

floatingPointNumbers.sort((value1, value2) => {
  return value1 - value2;
});

console.log(floatingPointNumbers);     //   [ 1.436568, 3.5678, 6.899, 7.345, 7.467, 9.34505, 9.35405 ]

```

Descending order : 

```
let floatingPointNumbers = [7.345, 3.5678, 6.899, 7.467, 1.436568, 9.34505, 9.35405];

floatingPointNumbers.sort((value1, value2) => {
  return value2 - value1;
});

console.log(floatingPointNumbers);     // [ 9.35405, 9.34505, 7.467, 7.345, 6.899, 3.5678, 1.436568 ]

```


While sorting an array of strings, it can also done by using sort() function. but it will consider the case sensitive and returns upper case letters first.

``` 
let stringsWithcaseSensitive = ["apple", "Apple", "Ball", "Foo", "foo", "bar"];

stringsWithcaseSensitive.sort();

console.log(stringsWithcaseSensitive);    // [ 'Apple', 'Ball', 'Foo', 'apple', 'bar', 'foo' ]

```

To compare the strings without any case sensitive, we can do this in two ways i.e., localeCompare method is available to compare without any case sensitive and the
another method is covert strings into lower case and compare. 

```

let stringsWithcaseSensitive = ["bar" , "Foo", "Ball", "dog", "foo"];

stringsWithcaseSensitive.sort((str1, str2) => {
    return str1.localeCompare(str2);
});

console.log(stringsWithcaseSensitive);     // [ 'Ball', 'bar', 'dog', 'foo', 'Foo' ]

```


Sorting an array of objects based on property is also similar to that of numbers sorting, where we take two arguments in callback and comapring the values i.e., 
less than or greater than.

```
let personDetails = [
                      {
                        "name" : "Alex",
                        "age" : 25,
                        "place" : "USA"
                      },
                      {
                        "name" : "bob",
                        "age" : 18,
                        "place" : "london"
                      },
                      {
                        "name" : "praveen",
                        "age" : 23,
                        "place" : "India"
                      }
                    ];
                   
 // Sort based on age property
                   
 personDetails.sort((person1, person2) => {
    return person1.age - person2.age;
 });
 
 console.log(personDetails);
 
 
 output: [
            { name: 'bob', age: 18, place: 'london' },
            { name: 'praveen', age: 23, place: 'India' },
            { name: 'Alex', age: 25, place: 'USA' }
         ]
         
         
         
 // Sort based on place property
                   
 personDetails.sort((person1, person2) => {
    return person1.place.localeCompare(person2.place);
 });
 
 console.log(personDetails);
 
 
 
 output: [
            { name: 'praveen', age: 23, place: 'India' },
            { name: 'Bob', age: 18, place: 'london' },
            { name: 'alex', age: 25, place: 'USA' }
         ]
 
 
 ```
 
 
 Sorting an array of objects based on multiple properties by using || in the sort function.
 
 ``` 
 
 let cricketData = [
                      { 
                        "name" : "sachin",
                        "centuries" : 47,
                        "highestScore" : 200
                      },
                      {
                        "name" : "virat kohli",
                        "centuries" : 47,
                        "highestScore" : 183
                      },
                      {
                        "name" : "MS Dhoni",
                        "centuries" : 34,
                        "highestScore" : 183
                      },
                      {
                        "name" : "Rohit sharma",
                        "centuries" : 34,
                        "highestScore" : 264
                      },
                      {
                        "name" : "Saurav ganguly",
                        "centuries" : 34,
                        "highestScore" : 182
                       }
                     ]
                     
 // Sorting based on centuries first and then highestScore.
 
 cricketData.sort((player1, player2) => {
    return player2.centuries - player1.centuries || player2.highestScore - player1.highestScore;
 });
 
 console.log(cricketData);
 
 
 
 output:   [
              { name: 'sachin', centuries: 47, highestScore: 200 },
              { name: 'virat kohli', centuries: 47, highestScore: 183 },
              { name: 'Rohit sharma', centuries: 34, highestScore: 264 },
              { name: 'MS Dhoni', centuries: 34, highestScore: 183 },
              { name: 'Saurav ganguly', centuries: 34, highestScore: 182 }
           ]
 
 
 ```
 
 The above data is sorted first based on the centuries and then sorted on highest score.
 
 <h2> Conclusion </h2>
 
 I hope this blog is very useful to understand how sorting done in javascript. Thank you.
                      


