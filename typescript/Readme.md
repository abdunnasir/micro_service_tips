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












