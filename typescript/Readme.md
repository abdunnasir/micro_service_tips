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



