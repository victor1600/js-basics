# Basic JS


- At the bottom, so it loads first.
- use ctrl + alt + l to reformat file.

## Ways to use it in HTML Files

1. Embedded in code

```html
<script >
    alert('Hello World');
 </script>
```

2. Call it from another file:

```html
<script src="main.js"></script>
```


## Printing
```javascript
console.log('Hello World');
log('hello');
```

## Variables

1. var: Its globally scope 
2. let: Block level scope
3. const: constant

```javascript
const x = 5
let z;

console.log(typeof x);
```

### Concatenate

#### Template Strings
```javascript
const name = 'John';
const age =30;
const hello = `My name is ${name} and i am ${age}`;
console.log(hello);
```

#### Utils 

- Length
```javascript
const s = 'Hello World';
console.log(s.length)
```
- Upper/Lower
```javascript
const s = 'Hello World';
console.log(s.toLowerCase())
```
- Substring

```javascript
const s = 'Hello World';
console.log(s.substring(0,5))
```

- Split

```javascript
const s = 'Hello World';
console.log(s.split(' '))
```

#### Arrays
   
```javascript
const myArray = ['apples', 3, true]
console.log(myArray);
```

- Appending to array
```javascript
const myArray = ['apples', 3, true]
myArray.push('Kiwito')
console.log(myArray);
``` 

- Appending at the start
```javascript
myArray.unshift('strawberries');
```

- pop
 ```javascript
fruits.pop()
```
- IndexOf

```javascript
myArray.indexOf('kiwito')
```

## Object literals (Dictionaries)

```javascript
const person = {
    firstName: 'John',
    hobbies: ['music', 'movies'],
    address: {
        street: '50 main st',
        city: 'Boston',
        state: 'MA'
    }
}

console.log(person)

// Create variables pulling things out of the object
const { firstName, lastName, address: {city} } = person;
console.log(city)

// Add properties
person.email = 'john@gmail.com';
console.log(person)
```

### Array of objects

```javascript
const todos = [
    {
        id:1,
        text: 'Take Out trash',
        isCompleted: true
    },
    {
        id:2,
        text: 'Meeting with boss',
        isCompleted: true
    },,
    {
        id:3,
        text: 'Dentist appt',
        isCompleted: false
    },
]

console.log(todos[1].text)
```


## Json 

```javascript
const todos = [
    {
        id:1,
        text: 'Take Out trash',
        isCompleted: true
    },
    {
        id:2,
        text: 'Meeting with boss',
        isCompleted: true
    },,
    {
        id:3,
        text: 'Dentist appt',
        isCompleted: false
    },
]

const todoJSON = JSON.stringify(todos);
console.log(todoJSON);
```

## Loops
```javascript
const todos = [
    {
        id: 1,
        text: 'Take Out trash',
        isCompleted: true
    },
    {
        id: 2,
        text: 'Meeting with boss',
        isCompleted: true
    }, ,
    {
        id: 3,
        text: 'Dentist appt',
        isCompleted: false
    },
]

let i = 0
while (i < 10) {
    console.log(i)
    i++;
}

for (let i = 0; i < todos.length; i++) {
    console.log(todos[i].text);
}


for (let todo of todos){
    console.log(todo.text);
}
```

## High order array methods
Take in a function as a parameter

### forEach

```javascript
// forEach,
todos.forEach(function (todo) {
    console.log(todo.text);
});
```

### Map

```javascript
// map (returns an array from array)
const todoText = todos.map(function (todo) {
    return todo.text;
});

```

### Filter

```javascript
const todoFiltered = todos.filter(function (todo) {
    return todo.isCompleted === true;
});

console.log(todoFiltered);
```

>They do different things: . filter() returns a subset of the elements from the original array, while . map() produces an array with new, different entries based on the elements in the original array.

- Combinations

```javascript
const todoCompleted = todos.filter(function (todo) {
    return todo.isCompleted === true;
}).map(function (todo) {
    return todo.text;
});

console.log(todoCompleted);
```

### Conditionals

- === compares content and data type.

```javascript
const x = 10;

if (x === 10) {
    console.log('equal')
} else if (x === 5) {
    console.log('test')
} else {
    
}
```

- Ternary operator

```javascript
const x = 10;

const color = x > 10 ? 'red' : 'blue'

console.log(color)
```

- switch

```javascript
const x = 11;

const color = x > 10 ? 'red' : 'blue'

switch (color) {
    case 'red':
        console.log('color is red');
        break
    case 'blue':
        console.log('color is blue')
        break
    default:
        console.log('color is NOT red or blue')
        break
}
```

## Functions

```javascript
function addNums(num1 = 1, num2 = 1) {
    return num1 + num2;
}

let result = addNums(5, 4);
console.log(result)
```

#### Arrow Functions
Instead of using keyword function we would
name it as variable, put equal sign, then parameters, and then arrow to function's body
```javascript
const addNums = (num1 = 1, num2 = 1) => {
    return num1 + num2;
}

let result = addNums(5, 4);
console.log(result)
```

- If there are no variables created or more than one line inside the arrow function, then we can
```javascript
const addNums = (num1 = 1, num2 = 1) => num1 + num2;


let result = addNums(5, 4);
console.log(result)
```

# OOP

