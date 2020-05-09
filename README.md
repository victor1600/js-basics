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

### Constructor function
 - We use Date()

```javascript
// Constructor function

function Person(firstName, lastName, dob) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.dob = new Date(dob);
    this.getBirthYear = function () {
        return this.dob.getUTCFullYear();
    }
    this.getFullName = function () {
        return `${this.firstName} ${this.lastName}`;
    }
}

// Instantiate object
const person1 = new Person('John', 'Doe', '4-3-1980');

console.log(person1.getBirthYear());
console.log(person1.getFullName());
```


### Prototype
We use this to separate from object, and when we print it,
we don't see that functions

```javascript

function Person(firstName, lastName, dob) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.dob = new Date(dob);
}

Person.prototype.getBirthYear = function () {
    return this.dob.getFullYear();

}

Person.prototype.getFullName = function () {
    return `${this.firstName} ${this.lastName}`;
}

// Instantiate object
const person1 = new Person('John', 'Doe', '4-3-1980');

console.log(person1.getBirthYear());
console.log(person1);
```

### Classes(Best way) 

```javascript
class Person {
    constructor(firstName, lastName, dob) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.dob = new Date(dob);

    }

    getBirthYear() {
        return this.dob.getFullYear();
    }

    getFullName() {
        return `${this.firstName} ${this.lastName}`;
    }
}

// Instantiate object
const person1 = new Person('John', 'Doe', '4-3-1980');

console.log(person1.getBirthYear());
console.log(person1);
```

# Dom

### Selecting elements

#### Single element

- querySelector
We can select  pretty much everything, html tags, classes, ids, 
```javascript
// const form = document.getElementById('my-form');
// console.log(form)

const form = document.querySelector('.container');
console.log(form)
// Grabs the first h1 it finds.
const form2 = document.querySelector('h1');
console.log(form2)
```
#### Multiple elements
Gives us a Nodelist, something similar to an array. We can run array methods on it,
like for each.

```javascript
const form = document.querySelectorAll('h1');
console.log(form)

const items = document.querySelectorAll('h1');

items.forEach((item) => console.log(item));
```

### Modify elements

- Remove
```javascript
const ul = document.querySelector('.items');
// Remove elements
ul.lastElementChild.remove();
```

- Modify text
```javascript
const ul = document.querySelector('.items');
ul.firstElementChild.textContent = 'Hello';
ul.children[1].innerHTML = 'Brad';
```

- Modify HTML
```javascript
const ul = document.querySelector('.items');

ul.lastElementChild.innerHTML = '<h1>Hello</h1>'



const btn = document.querySelector('.btn')
btn.style.background = 'red';
```

## Events
Arguments:
- Event
- Function we want to run when that functions happens

- Example 1:
```javascript
const btn = document.querySelector('.btn')
// e is the event parameter
btn.addEventListener('click', (e) => {
    // preventDefault, to avoid flashing quickly
    e.preventDefault();
    console.log('click');
});
```

e holds the event, e.target holds the name of the element that triggered it 

- Example 2, seeing the e event:
```javascript
const btn = document.querySelector('.btn')
// e is the event parameter
btn.addEventListener('click', (e) => {
    // preventDefault, to avoid flashing quickly
    e.preventDefault();
    console.log(e.target.id);
});
```

- Example 3 (Changing background)
```javascript
const btn = document.querySelector('.btn')
// e is the event parameter
btn.addEventListener('click', (e) => {
    // preventDefault, to avoid flashing quickly
    e.preventDefault();
    document.querySelector('#my-form')
        .style.background = '#ccc';
});
```

- Example 4 (Adding a css class)

```javascript
const btn = document.querySelector('.btn')
// e is the event parameter
btn.addEventListener('click', (e) => {
    // preventDefault, to avoid flashing quickly
    e.preventDefault();
    document.querySelector('#my-form')
        .style.background = '#ccc';
    document.querySelector('body').classList.add('bg-dark');
});
```

- Example 5: Changing text
```javascript
const btn = document.querySelector('.btn')
// e is the event parameter
btn.addEventListener('click', (e) => {
    // preventDefault, to avoid flashing quickly
    e.preventDefault();
    document.querySelector('#my-form')
        .style.background = '#ccc';
    document.querySelector('body').classList.add('bg-dark');
    document.querySelector('.items')
        .lastElementChild.innerHTML = '<h1>Hello</h1>';
});
```

- Example 6: Mouse events

```javascript
const btn = document.querySelector('.btn')
//PUT MOUSE OVER IT
btn.addEventListener('mouseover', (e) => {
    // preventDefault, to avoid flashing quickly
    e.preventDefault();
    document.querySelector('#my-form')
        .style.background = '#ccc';
    document.querySelector('body').classList.add('bg-dark');
    document.querySelector('.items')
        .lastElementChild.innerHTML = '<h1>Hello</h1>';
});

// RELEASEING MOUSE
btn.addEventListener('mouseout', (e) => {
    // preventDefault, to avoid flashing quickly
    e.preventDefault();
    document.querySelector('#my-form')
        .style.background = '#ccc';
    document.querySelector('body').classList.add('bg-dark');
    document.querySelector('.items')
        .lastElementChild.innerHTML = '<h1>Hello</h1>';
});
```

## Functional Example: Grabbing elements from a form

> Append child appends something to that div

```javascript
const myForm = document.querySelector('#my-form');
const nameInput = document.querySelector('#name');
const emailInput = document.querySelector('#email');
const msg = document.querySelector('.msg');
const userList = document.querySelector('#users');

myForm.addEventListener('submit', onSubmit);

function onSubmit(e) {
    e.preventDefault();
    //GETTING VALUE FROM INPUT FIELD
    if (nameInput.value === '' || emailInput.value === '') {
        msg.classList.add('error')
        msg.innerHTML = 'Please enter all fields';
        // Disappear after timeout.
        setTimeout(() => msg.remove(), 300);
    } else {
        const li = document.createElement('li');
        li.appendChild(document.createTextNode(`${nameInput.value}: ${emailInput.value}`));
        userList.appendChild(li);

        // Clear Fields
        nameInput.value = '';
        emailInput.value = '';
    }
}
```
### Callbacks
```javascript
function doHomework(subject, callback) {
  alert(`Starting my ${subject} homework.`);
  callback();
}
function alertFinished(){
  alert('Finished my homework');
}
doHomework('math', alertFinished);
```

[Explanation of callbacks](https://codeburst.io/javascript-what-the-heck-is-a-callback-aba4da2deced)
