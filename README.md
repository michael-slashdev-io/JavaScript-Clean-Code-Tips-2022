# JavaScript-Clean-Code-Tips-2022

There are several principles that can help engineers write more clean and efficient JavaScript code. In this article I highlight the use of multiple parameters, template literals, avoiding callbacks, using shorthand, the spread extension operator, arrow functions, and object destructuring.

## Use Multiple Parameters

When writing a function, it is better to use multiple input parameters instead of using a single object as an input. This way developers understand how many inputs are needed just by looking at the method. In addition this improved performance since there is no need to create an object parameter or collect garbage.

This of course has a limit. Once you reach a certain number of parameters you should switch back to using the object so that your code does not become unnecessarily complex.

'''
//clean-code
function CustomerDetail (CustomerName, CustomerValue, Purchase){    
  console.log('This is ${CustomerName} of ${CustomerValue} and need ${Purchase}');
} 

//bad-code
function CustomerDetail (User){    
  console.log('This is ${User.CustomerName} of ${User.CustomerValue} and need ${User.Purchase}');
'''

## Use Template Literals for String Concatenations/

Template literals help you to cut out unnecessary concatenations.

'''
//before
var name = 'Michael’';
var message = 'Growth Pro'+ name + ',';

//after
var name = 'Michael';
var message = `Growth Pro ${name},`;
'''

## Avoid Callbacks/

Callbacks for a long time were the most popular way to express asynchronous functions in JavaScript programs. However, if you are using them now you will know the pain of having multiple nested callbacks. The following example has 5 callback functions:

'''
function1(function (err, data) { 
  ...  
  function2(user, function (err, data) {
    ...
     function3(profile, function (err, data) {
      ...
      function4(account, function (err, data) {
        ....
        function4(address, function (err, data) {
        ....
        }); 
      }); 
    }); 
  });
});
'''

## ES6 and ES7 introduced, Promises and Async/Await to handle asynchronous functions, and they are much easier to use and make your code easily understandable to others. See below:

'''
// Promises

function1() 
.then(function2) 
.then(function3) 
.then(function4) 
.then(function5) 
.catch((err) => console.error(err));

// Async/Await

async function myAsyncFunction() {  
try {    
  const data1= await function1();    
  const data2= await function2(data1);    
  const data3= await function3(data2);
  const data3= await function4(data3);    
  return function5(data5);  
} 
catch (e) {    
  console.error(err);  
}}
'''

## Use Shorthand/

Shorthand can take some time to learn, but it will help to clean up your codebase and cut down on unneeded code. if you write a condition to check empty, null and undefined conditions for a variable, you must write 2 conditions within the if statement.

'''
//without-shorthand
if (x !== “” && x !== null && x !== undefined) { ... }

//with-shorthand
if ( !!x ) { ... }
Use The Spread Extension Operator/
The spread extension operator (…) is another feature introduced with ES6. It is capable of expanding the literals like arrays into individual elements with a single line of code. This is really useful when we need to put an array or object into a new array or object or to combine multiple parameters in the array.
'''

The below code shows how to combine 2 arrays using the spread operator. As you can see, it makes the code clean and easy to understand since we don’t need to use loops or conditions.

'''
let x = [skateboard,scooter,truck];
let y = [bike, car, ..x, horse]
console.log (y);
// bike,car,skateboard,scooter,truck,horse
'''

## Use Arrow Functions When Possible/

Arrow functions create a more simple way of writing JavaScript functions. They also help to resolve the problem of accessing properties inside of callbacks. 

If you are using arrow functions, curly braces, parenthesis, function, and return keywords become optional. 

The below example shows a comparison between a single-line arrow function without and a regular function.

'''
// Arrow Function

const myJob = job => console.log(`I need to do a ${job}`);

// Regular Function

function(job){
   console.log(`I need to do a ${job}`);
}
'''

Arrow functions make your code simple but they should not always be used. Arrow functions are not the best when working with object prototypes, classes, or object literals. 

## Make Use of Object Destructuring/

Object Destructuring helps to shorten the amount of code needed when creating an object with variables. It is obviously most useful when an object has multiple variables. It can also be very helpful when a property is deeply nested in an object or you are using the same property multiple times.

'''
const user = {name: ‘john’, email: ‘john@example.com’, phone:’123'};

//with Object Destucturing

const {name, email, phone} = user;

//Without Object Destucturing

const name = user.name;
const email = user.email;
const phone = user.phone;
'''
