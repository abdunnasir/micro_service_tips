Type system is there in typescript

the type system helps us to catch errors during the development

the extra syntax added will never go to browser or node.js


Type script code => type script complier => plain old javascript

So typescript is a helper to catch errors.
It doesn't have any impact on the final code we run on the browser or node.js


tsc => typescript compiler

eg: tsc index.ts
that will generate a file named index.js
then run
node index.js 

ts-node => this command run both tsc and node command together

ts-node index.ts

*****************************************


if we have a todo object with the keys
id, title and completed then
we can define an interface

interface Todo {
    id: number;
    title: string;
    completed: boolean;
}


then

const todo = response.data as Todo;

if we do like that, then if we access data of the todo with soem wrong keys like

todo.ID, then you will see some error notifications in the editor.
that's the use of type script

*************************************************


const logTodo = (id, title, completed ) {
    console.log(`
        ID: {$id}
        Title: {$title}
        Is finished: {$completed}
    `)

};

if it's called as 
logTodo(id,completed,title )

it wil work, there won't be any error in the editor

But if we cahnge the function as

const logTodo = (id: number, title: string, completed: boolean ) {
    console.log(`
        ID: {$id}
        Title: {$title}
        Is finished: {$completed}
    `)
};

Then we will see error in the editor

*************************************************************


Every single value in type script has a type.

****************************************

We have Primitive types and Object types

Primitive types => number, string, boolean, void, null, undefined
Object Types => functions, arrays, classes and objects


Type script can list down the functions available for an object.

eg:
cost today = new Date();

then 
if we type

today. , then it will list all functions

if we type some functions not avilable for it, that will show error

eg:
today.xxxxsff()
will show error.

*******************************************

Type annotations with variables

const apples: number = 5;
it's saying that apples will have numbers.

if we write a code as shown below
const apples: number = true;
That will throw error.



const apples: number = 5;
apples = 'hhdhfdf';
The above variable update also will throw error.

Diffrent type annotation examples

let apple: number  = 5;
let speed: string  = 'fast';
let hasName: boolean = true;

let now: Date = new Date();

Type annotation example for array

 // arrays
let colors:  string[] = ['red', 'green', 'blue'];
let numbers: number[] = [1,2,3];

So the above statements are used to say colors will be storing an array of strings.


// classes

class Car {


}

let car: Car = new Car();


// object literal
a crazy example

let point = {
    x: 10,
    y: 20
}

If have to store to the varibale point x and values

then the annotation for that will be

let point = {x: number, y :number} =  {
    x: 10,
    y: 20
}

it's getting big!!



// function

Let's see something tough to understand

assume we have  afunction

cost lognumber = (i) => {
    console.log(i)
}

How to annotation for this?

cost lognumber: (i: number) => void = (i) => {
    console.log(i)
}

So everything afterthe first: till the first equal is the anootation.
Bit confusing to understand the code 


Type Inference
----------------------------------

// with annotation
const color: string = 'red'; 


If we define and assign a value to the variable in the same line
the type script will assume the variables type from the initial value

// eg of inference
const color = 'red';
so in the above example,  color is assigned with a string 'red',
so color will accept only strings


// any type,
if we create a variable in one line and assign value to it in the next line
as shown below, it's of any type and the variable will accept any values.
const color;
color = 5;


More about any type
-----------------------



Let's explain any type with an example

JSON.parse(true) return true

JSON.parse(4)  rteurn 4

So JSON.parse return any type depends on the value passed to the function.

If we pass a json value like  {"value": 5} it return {value: number}

So some functions return any type.


It's allways good to avoid using any type as much as possible as
it won't  throw any error if we try to access a not existing property of a any type 
value.



**********************************


So we said, we don't have to specify Type annotations in most of the cases,
but if a function is returning any type,
We can make some changes to avoid accessing not existing properties .


const json = '{"x": 10, "y": 20}';

const coordinates : {x: number, y: number} = JSON.parse(json);

then if we try to access
x.blablah, it will show some error.

So  it's an example of when we have to use type annotation over Type Inference.

*******************************************************************


Another example when we will use  type annotation


 When we declare a variable on one line  and initalizate it later

let words = ['red', 'green', 'blue'];
let foundWord;

for (let i = 0; i < words.length; i++) {
  if (words[i] === 'green') {
    foundWord = true;
  }
}


In the above case, foundWord decalred but it's value is assigned later.


So better code is

let words = ['red', 'green', 'blue'];
let foundWord: boolean;  // type annotation

for (let i = 0; i < words.length; i++) {
  if (words[i] === 'green') {
    foundWord = true;
  }
}


******************************************************

Some times one variable might be used for diffrenet types of 
values like boolean and number.

So if we define 

let numberAboveZero = false;

we cannot assign some numbers to it later.

so if we have some cases where we need to assign multiple types 
of values to a variable (not recommended),

we can use type annotation as shown below
let numberAboveZero: boolean | number = false;

Full example is given below


let numbers = [-10, -1, 12];
let numberAboveZero: boolean | number = false;

for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] > 0) {
    numberAboveZero = numbers[i];
  }
}

So in this case numberAboveZero can store both boolean and number.

********************************************



For a function, we had used something like this

cost lognumber: (i: number) => void = (i) => {
    console.log(i)
}


We can do it in a diffrent way too

const lognumber = (i: number) : void => {
  console.log(i)
};



For a function adding two numbers

const add = (a: number, b: number) : number => {
  return a + b;
};


We can remove the return type, as 
type script will automatcially identify the return type

from return a + b;


const add = (a: number, b: number)  => {
  return a + b;
};

But one issue is,  in the below code type script will assume return type as 
void, as there is no return .

const add = (a: number, b: number)  => {
  a + b;
};


***************************************************

Same syntax works with both named function and anonymus function

see the below examples

function divide(a: number, b: number): number {
  return a / b;
}

const multiply = function(a: number, b: number): number {
  return a * b;
};


*************************************************

We can use void, even when it will throw an exception in some cases
and in most cases it won't return anything

const throwError = (message: string): void => {
  if (!message) {
    throw new Error(message);
  }
};

****************************************************
 Destructuring with Annotations


const todaysWeather = {
  date: new Date(),
  weather: 'sunny'
};

const logWeather = (forecast: {
  date: Date;
  weather: string;
}): void => {
  console.log(forecast.date);
  console.log(forecast.weather);
};

logWeather(todaysWeather);

In the above example

We are using the function argumnet with annotaion as

forecast: {
  date: Date;
  weather: string;
}


Where forecast is the argumnet name and 
 {
  date: Date;
  weather: string;
}

is the type of the argumnet.

then we have to print
console.log(forecast.date);



What if we want to use Destructuring along with annotaion, then the function 
argumnet will be 

 ({
  date,
  weather
}: {
  date: Date;
  weather: string;
})

Then we can print 
 console.log(date);


full example is given below



const todaysWeather = {
  date: new Date(),
  weather: 'sunny'
};

const logWeather = ({
  date,
  weather
}: {
  date: Date;
  weather: string;
}): void => {
  console.log(date);
  console.log(weather);
};

logWeather(todaysWeather);


***********************

Annotations Around Objects


Let's first see how to define  a function within an object

const profile = {
  name: 'alex',
  age: 20,
  coords: {
    lat: 0,
    lng: 15
  },
  setAge(age: number): void {
    this.age = age;
  }
};

In the above sample code, setAge is a function defined within an
object.


from profile, get age and name along with type annotation for them.

Code for that is
const { age, name }: { age: number; name: string } = profile;


The next sample code is bit complicated 
const {
  coords: { lat, lng }
}: { coords: { lat: number; lng: number } } = profile;

******************************

benefits of uisng type annotation with arrays

When we don't initialize an aray with it's values

we can declare it with type as shown below
const carsByMake: string[][] = [];

now what's the benefits of uisng type annotation
is listed below with three benefits.


const carMakers = ['ford', 'toyota', 'chevy'];
const dates = [new Date(), new Date()];

const carsByMake: string[][] = [];

//1) Help with inference when extracting values
const car = carMakers[0];
const myCar = carMakers.pop();

//2) Prevent incompatible values
carMakers.push(100);

//3) Help with 'map'
carMakers.map(
  (car: string): string => {
    return car.toUpperCase();
  }
);



