# JavaScript

## Operators & Flow Control
### Numbers
JS has a single Number type
```js
// Arithmetic
1 + 1   // = 2
8 - 7   // = 1
10 * 3  // = 30
40 / 8  // = 5

// Modulo
22 % 2  // = 0
27 % 4  // = 3 
9 % 2.5 // = 1.5

// Infinity / non real numbers
Infinity
-Infinity
Number.POSITIVE_INFINITY    // alias for Infinity
Number.NEGATIVE_INFINITY    // alias for -Infinity
```

### Booleans / Comparisons

## Patterns
### Objects
- [Built-Ins](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects)


### Closures
```js
```

### Prototypal Inheritance
```js

```

### Factories
```js
const Player = (name, teamSymbol) => {
    let score = 0;
    const getName = () => name;
    const setName = (x) => name = x;
    const getTeamSymbol = () => teamSymbol;
    const setTeamSymbol = (x) => teamSymbol = x;
    const getScore = () => score;
    const incrementScore = () => { 
        score++;
    }

    const play = (x, y, gameBoard) => {
        console.log(`${name} played at [${x}, ${y}]!`);
    };

    return {getName, setName, getTeamSymbol, setTeamSymbol, getScore, incrementScore, play}
};
```

### Module Pattern

### Class Syntax
TODO: list of all class features
```js
class User {
  constructor(name) {
    this.name = name;
  }

  sayHi() {
    alert(this.name);
  }
}

let user = new User("John");
user.sayHi();
```

## DOM Manipulation

