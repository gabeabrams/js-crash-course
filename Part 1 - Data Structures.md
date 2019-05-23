# Part 1: Data Structures

<style>
table {
    width:100%;
    box-shadow: 5px 5px 7px rgba(33,33,33,.7);
    border: 3px solid #ff9300;
}
th {
    background: #ff9300;
}
</style>

# Getting set up:

1. Install Node (LTS) via [nodejs.org](https://nodejs.org/en/)
2. Recommended: install [Atom](https://atom.io) and install the following plugins: `linter-eslint`, `todo-show`, `react`, `multi-cursor`, `atom-easy-jsdoc`

# ES6 Basics:

## Which ones are you already familiar with?

- int
- float
- String
- array
- boolean
- dict/HashMap

## In JS, we have pretty normal types:

- Number
- String
- Array
- Boolean
- Object

**But, JS is not a typed language. Be careful!**


## Creating variables:

Naming conventions:

| Rule: use camel case for normal variable names |
| --- |
| Good: `favoriteFruits`<br>Bad: `FavoriteFruits` or `favorite_fruits` or `favoritefruits` etc. |

| Rule: for global constants, use snake upper case |
| --- |
| Good: `ITEM_WIDTH`<br>Bad: `itemWidth` or `ItemWidth` or `ITEMWIDTH` etc. |

#### Number:

```js
const age = 25; // years
```

| Rule: for numbers with units, include units in the name or in a same-line comment |
| --- |
| `const heightFt = 5;`<br>or<br>`const height = 5; // feet` |

Number math:

```js
a + b
a - b
a * b
a / b
```

| Rule: always space math operations and add parentheses |
| --- |
| Good: `((a + b) * (c + d)) / e` or `a + (b / c)`<br>Bad: `a+b` or `a-b` or `a + b / c`

#### String:

```js
const name = 'Divardo';
```

| Rule: always use single quotes for strings |
| --- |
| Good: `'Hi'` Bad: `"Hi"`

#### Array:

```js
const fruits = ['Apple', 'Orange'];
```

| Rule: if more than three elements, put each element on its own line |
| --- |

```js
const fruits = [
    'Apple',
    'Orange',
    'Pineapple',
    'Mango',
];
```

| Rule: for lists on multiple lines, use training commas |
| --- |
| Exception: do not do this in `.json` files, this is not yet allowed (coming soon!) |

#### Object:

```js
const person = { name: 'Divardo' };
```

| Rule: put space around properties |
| --- |
| Good: `{ name: 'Divardo' }` Bad: `{name: 'Divardo'}`

| Rule: if more than three properties, put each prop on its own line |
| --- |

```js
const person = {
    name: 'Divardo',
    age: 25,
    height: 71, // inches
    favoriteFruits: [...],
};
```

| Rule: for objects on multiple lines, use training commas |
| --- |
| Exception: do not do this in `.json` files, this is not yet allowed (coming soon!) |

## `var` vs `let` vs `const`

Always use `const` unless re-assigning.

| Rule: never use `var`, only use `let` if reassigning |
| --- |

Re-assigning looks like this:

```js
...
varName = ...;
varName += ...;
varName *= ...;
varName /= ...;
varName -= ...;
```

This is **not** re-assigning:

```js
varName.something = ...;
varName.callThis();
```

Pop quiz: for each example, should we use `const` or `let`?

```js
___ height = 48; // inches
height += 4;
```

```js
___ person = { name: 'Divardo' };
person.name = 'Gabe';
```

```js
for (___ i = 0; i < 10; i++) {

}
```

| Rule: `++` and `--` not allowed except in a `for` loop |
| --- |

## Template Strings


Let's create a couple variables:

```js
const a = 5;
const b = '10';
```

These operations are permitted by JS, but we don't ever do them:

```js
const c = a + b; // results in '510'
const d = a - b; // results in -5
```

| Rule: never add or subtract strings, use template strings instead |
| --- |
| `'Hi there, ' + name` is not allowed |

To concatenate strings, _always_ use template strings:

```js
const message = `Hi there, ${name}`;
```

## Bonus: ternaries

```js
const timeOfDay = (hours >= 12 ? 'afternoon' : 'morning');
```

| Rule: always surround ternaries with parentheses |
| --- |

| Rule: no nested ternaries |
| --- |
| Bad:<br>```(hours >= 12 ? (hours > 5 'evening' : 'afternoon') : 'morning')```

## Challenge: Introducer

Create a script that welcomes the user.

- Create a `person` object
- The properties of `person` should be: `name` (string), `age` (number), `favoriteFruits` (string[]), and `height` (number)
- This person should have just one favorite fruit

Print using `console.log` the following message:

```bash
This is <name>! They are <age> years old and <height> inches tall. Their favorite fruit is <fruit>.
```

Run your script using `node myScript.js`

Make the following changes:

- Set their age to `1`
- Add two more fruits to their `favoriteFruits` array

## Functions

Functions that aren't methods of a class:

```js
const functionName = () => {
    // ...
};
```

| Rule: never use the `function` keyword |
| --- |

| Rule: always use arrow functions unless the function is a non-static method of a class |
| --- |

| Rule: always include parens, braces, and `return` (if returning something) in arrow functions |
| --- |
| Bad: `x => x + 1` Good: `(x) => { return x + 1; }` |

Accepting arguments:

```js
const functionName = (arg1, arg2, arg3) => {
    // ...
};
```

## Classes

```js
class MyClass {
    constructor() {
        // ...
    }
    
    myMethod() {
        // ...
    }
    
    _privateMethod() {
        // ...
    }
}

MyClass.staticFunction = () => {

};
```

| Rule: non-static methods must refer to `this` |
| --- |
| If the method doesn't refer to `this`, it must be made into a static method `

| Rule: private methods must start with an underscore (`_`) |
| --- |

| Rule: static methods must be assigned outside the class as arrow functions |
| --- |

## Deconstruction

```js
const person = {
    name: 'Divardo',
    age: 25,
    height: 71, // inches
    favoriteFruits: [...],
};
```

Later on, if we want to get the `age` out of the `person` object, we use deconstruction.

```js
const { age } = person;
```

| Rule: always use deconstruction if possible |
| --- |

If we have multiple items we want to take out:

```js
const { name, age } = person
```

| Rule: if deconstructing more than 3 items, put on multiple lines |
| --- |

```js
const {
    name,
    age,
    height,
    favoriteFruits,
} = person;
```

## Challenge: Re-write your Introducer using a Class

Create a `Person` class. In the constructor, take a `name`, `age`, `height`, and list of `favoriteFruits`.

Create a `sayYay` method of `Person` that just prints `'Yay!'` to the console.

Create a `getOlder` method of `Person` that increments the age by `1`.

Create a `setHeight` method of `Person` that takes a new height as an argument.

Create an `introduceSelf` method that prints the same introduction message as before.