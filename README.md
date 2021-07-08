# React

## Intro

### What is React?

- [react](https://reactjs.org)
- React is a JavaScript library for building user interfaces.
- A client-side JavaScript Library
- All about building modern, reactive user interfaces for the web.

### Why React instead of Just Javascript

- It makes building modern, rich, complex user interfaces easier by giving a higher lever syntax where we write code in a declarative, component focused way.
- imperative one is plain javascript

### Single Page Applications

- React can be used ot control parts of HTML pages or entire pages.
- React can also be used to control the entire frontend web application.

### React.js Alternatives

- Angular
- Vue

### Topics Overview

- Basics & Foundation
  - Components & Building UIs
  - Working with Events & Data: "props" and "state"
  - Styling React Apps & Components
  - Introduction into React Hooks
- Advanced Concepts
  - Side Effects, Refs & more React Hooks
  - React's Context API & Redux
  - Forms, Http Requests & Custom Hooks
  - Routing, Deployment, NextJS & More
- Summaries & Refreshers
  - JavaScript Refresher
  - ReactJS Summary

## JavaScript Summary

### let & const

- [Read more about let :](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [Read more about const :](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
- let and const basically replace var . You use let
  instead of var and const instead of var if you plan on
  never re-assigning this "variable" (effectively turning it into a constant therefore).

### ES6 Arrow Functions

- [Read more:](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

- Arrow functions are a different way of creating functions in JavaScript. Besides a shorter syntax, they offer advantages when it comes to keeping the scope of the this keyword.

- [(see here).](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#No_binding_of_this)
- Arrow function syntax may look strange but it's actually
  simple.
  ```js
  function callMe(name) {
    console.log(name);
  }
  ```
  which you could also write as:
  ```js
  const callMe = function (name) {
    console.log(name);
  };
  ```
  becomes:
  ```js
  const callMe = (name) => {
    console.log(name);
  };
  ```
- **Important:**
  When having no arguments, you have to use empty
  parentheses in the function declaration:
  ```js
  const callMe = () => {
    console.log("Max!");
  };
  ```
  When having exactly one argument, you may omit the
  parentheses:
  ```js
  const callMe = (name) => {
    console.log(name);
  };
  ```
  When just returning a value, you can use the following
  shortcut:
  ```js
  const returnMe = (name) => name;
  ```
  That's equal to:
  ```js
  const returnMe = (name) => {
    return name;
  };
  ```

### Exports & Imports

- In React projects (and actually in all modern JavaScript
  projects), you split your code across multiple JavaScript
  files - so-called modules. You do this, to keep each file/
  module focused and manageable.
- To still access functionality in another file, you need export (to make it available) and import (to get
  access) statements.

- You got two different types of
  exports: default (unnamed) and namedexports:
  - default => export default ...;
  - named => export const someData = ...;
- You can import default exports like this:

  - import someNameOfYourChoice from './path/to/file.js';

- Surprisingly, someNameOfYourChoice is totally up to you.
- Named exports have to be imported by their name:
- import { someData } from './path/to/file.js';
- A file can only contain one default and an unlimited amount of named exports. You can also mix the one default with any amount of named exports in one and the same file.
- When importing named exports, you can also import all
  named exports at once with the following syntax:
- import \* as upToYou from './path/to/file.js';
  upToYou is - well - up to you and simply bundles all
  exported variables/functions in one JavaScript object.
- For example, if you export const someData = ... (/path/
  to/file.js ) you can access it on upToYou like
  this: upToYou.someData .

### Classes

- Classes are a feature which basically replace constructor
  functions and prototypes. You can define blueprints for
  JavaScript objects with them.
  Like this:

  ```js
  class Person {
    constructor() {
      this.name = "Max";
    }
  }

  const person = new Person();
  console.log(person.name); // prints 'Max'
  ```

- In the above example, not only the class but also a property of that class (=> name ) is defined. They syntax you see there, is the "old" syntax for defining properties. In modern JavaScript projects (as the one used in this course), you can use the following, more convenient way of defining class properties:

  ```js
  class Person {
    name = "Max";
  }

  const person = new Person();
  console.log(person.name); // prints 'Max'
  ```

  You can also define methods. Either like this:

  ```js
  class Person {
    name = "Max";
    printMyName() {
      console.log(this.name); // this is required to refer to the class!
    }
  }

  const person = new Person();
  person.printMyName();
  ```

  Or like this:

  ```js
  class Person {
    name = "Max";
    printMyName = () => {
      console.log(this.name);
    };
  }

  const person = new Person();
  person.printMyName();
  ```

  The second approach has the same advantage as all arrow
  functions have: The this keyword doesn't change its
  reference.

- You can also use inheritance when using classes:

  ```js
  class Human {
    species = "human";
  }

  class Person extends Human {
    name = "Max";
    printMyName = () => {
      console.log(this.name);
    };
  }

  const person = new Person();
  person.printMyName();
  console.log(person.species); // prints 'human'
  ```

## Spread & Rest Operator

- The spread and rest operators actually use the same
  syntax: ...
- Yes, that is the operator - just three dots. It's usage
  determines whether you're using it as the spread or rest
  operator.

- **Using the Spread Operator:**
  - The spread operator allows you to pull elements out of an
    array (=> split the array into a list of its elements) or pull the
    properties out of an object. Here are two examples:
  ```js const oldArray = [1, 2, 3];
  const newArray = [...oldArray, 4, 5]; // This now is[1, 2,3, 4, 5];
  ```
  Here's the spread operator used on an object:
  ```js
  const oldObject = {
    name: "Max",
  };
  const newObject = { ...oldObject, age: 28 };
  ```
  newObject would then be
  ```js
   {
   name: 'Max',
   age: 28
   }
  ```
- The spread operator is extremely useful for cloning arrays and objects. Since both are reference types (and not
  primitives), copying them safely (i.e. preventing future
  mutation of the copied original) can be tricky. With the
  spread operator you have an easy way of creating a
  (shallow!) clone of the object or array.

### Destructuring

- Destructuring allows you to easily access the values of
  arrays or objects and assign them to variables.
  Here's an example for an array:

```js
const array = [1, 2, 3];
const [a, b] = array;
console.log(a); // prints 1
console.log(b); // prints 2
console.log(array); // prints [1, 2, 3]
```

And here for an object:

```js
const myObj = {
  name: "Max",
  age: 28,
};
const { name } = myObj;
console.log(name); // prints 'Max'
console.log(age); // prints undefined
console.log(myObj); // prints {name: 'Max', age: 28}
```

- Destructuring is very useful when working with function
  arguments. Consider this example:

```js
const printName = (personObj) => {
  console.log(personObj.name);
};
printName({ name: "Max", age: 28 }); // prints 'Max'
```

- Here, we only want to print the name in the function but we pass a complete person object to the function. Of course
  this is no issue but it forces us to call personObj.name
  inside of our function. We can condense this code with
  destructuring:

```js
const printName = ({ name }) => {
  console.log(name);
};
printName({ name: "Max", age: 28 }); // prints 'Max')
```

- We get the same result as above but we save some code.
  By destructuring, we simply pull out the name property and store it in a variable/ argument named name which we then can use in the function body.

---

## React Basics & Working With Components

### What are Components and why is react all about them

- React is all about Component.
  Because all user interfaces in the end are made up of components.

- Why Components?
  - Reusabliliy - Don't repeat yourself.
  - Separation of Concerns - Don't do too many things in one and the same place ( function ).

### How is a Component Built?

- React allows you to create re-usable and reactive components consisting of HTML and JavaScript

- Declarative Approach - define the desired target state and let React figure out the actual JavaScript DOM instructions.

### How to Create a React Project

- Also need to install NodeJS

- [Create-React-App](https://create-react-app.dev/)

```js
npx create-react-app my-app-name
```

Above code will create react app with some default code and will create good dev environment.

```js
npm start
```

- above code will start server and it will start on localhost:3000

### Analyzing a Standard React Project

- import React-dom from react-dom
- import react from react

```js
ReactDOM.render(<App />, document.getElementById("root"));
```

- JSX
- App here is a Component

### Introducing JSX

```js
function App() {
  return (
    <div>
      <h2>Let's get started!</h2>
    </div>
  );
}
export default App;
```

### How React Works

### Building First Custom Component

```js
function ExpenseItem() {
  return (
    <div>
      <h2>Expense item!</h2>
    </div>
  );
}

export default ExpenseItem;
```

```js
import ExpenseItem from "./components/ExpenseItem";
```

### Adding More JSX code

```js
function ExpenseItem() {
  return (
    <div>
      <div>Match 28th 2021</div>
      <div>
        <h2>Car Insurance</h2>
        <div>$294.56</div>
      </div>
    </div>
  );
}

export default ExpenseItem;
```

### Adding Basic CSS Styling

### Outputting Dynamic Data & Working with expressions in JSX

```js
function ExpenseItem() {
  const expenseDate = new Date(2021, 2, 28);
  const expenseTitle = "Car Insurance";
  const expenseAmount = 294.24;

  return (
    <div className="expense-item">
      <div>Match 28th 2021</div>
      <div className="expense-item__description">
        <h2>{expenseTitle}</h2>
        <div className="expense-item__price">$294.56</div>
      </div>
    </div>
  );
}
```

### Passing Data via Props

```js
function App() {
  return (
    <div>
      <h2>Let's get started!</h2>
      <ExpenseItem
        title={expenses[0].title}
        amount={expenses[0].amount}
        date={expenses[0].date}
      ></ExpenseItem>
    </div>
  );
}
```
