/////

```js
function join(separator, ...values) {
  return values.join(separator);
}

let start = 'ABCDEFGHI';
let middle = 'JKLMNOPQR';
let end = 'STUVWXYZ';

// output: A + B + C + D + E + F + G + H + I + J + K + L ...
join(' + ', ...start, ...middle, ...end);
```

### Works with any iterable objects
### Can be used multiple times as well!  <!-- .element: class="fragment" -->

NOTES:
- Take a look at this example
- What's a string? Well in ES6, it's just an iterable of characters
- And remember our `join` function?
- We're spreading _multiple_ strings to pass all the letters as parameters to `join`
- But the fun doesn't stop there!

/////

```js
let arrayFromConstructor = new Array('A', 'B', 'C', 'D');
let arrayFromLiteral = ['A', 'B', 'C', 'D'];
```

### Equivalent!

```js
let start = 'ABCDEFGHI';
let middle = 'JKLMNOPQR';
let end = 'STUVWXYZ';

let alphabetFromConcat = start.concat(middle).concat(end);
let alphabetFromConstructor = new Array(...start, ...middle, ...end);
let alphabetFromLiteral = [...start, ...middle, ...end];

// output: ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', ...]
console.log(alphabetFromLiteral);
``` 
<!-- .element: class="fragment" -->

NOTES:
- An array literal is a shortened form of multiple parameters to a constructor function
- So when we spread multiple arrays 

=====

## Classes

```js
class Person {
  constructor(name) {
    this._name = name;
  }
  toString() {
    return this._name;  
  }
}
```

```js
class Student extends Person {
  constructor(name, grade) {
    super(name);
    this._grade = grade;
  }
  toString() {
    return `${this._grade} grade student: ${super.toString()}`;
  }
}
```

```js
let student = new Student('Annie Walker', '5th');

// output: 5th grade student: Annie Walker
console.log(student.toString()); 
```

NOTES:
_[28 minutes]_

- Here's an example of new class syntax in ES6
- You can create a classes and derived classes via `extends`
- You can define a constructor and methods
- You can call base class constructor and methods via `super`
- All pretty straightforward
- You can declare a method static by adding `static` keyword
- No way to define instance or static properties, but there's alread a proposal in the works
- It's just syntactic sugar over prototype constructors in ES5
- So in theory it should work w/ existing class, but in practice it doesn't

=====

## Subclassable built-ins

```js
class MyArray extends Array {
  
}
```

```js
class FancyString extends String {

}
```

```js
class CustomError extends Error {

}
```

NOTES:
_[29 mintues]_

- ES6 also adds the ability to derive from built in classes like `Array`, `String` & `Error`
- Not really possible with ES5

=====

## Promises

```js
function wait(delay) {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, delay);
  });
}

wait(3000).then(() => {
    console.log('3 seconds have passed!');
});
```

Promises/A+

NOTES:
_[29.5 minutes]_

- ES6 introduces native Promise API
- Similar to jQuery Deferred objects except they follow the Promises/A+ standard
- Main difference is how errors & exceptions are handled within a promise
- Libraries like Q are Promises/A+
- Deferreds in jQuery 3 will be Promises/A+

=====

## Maps & Sets

```js
let dateLookup = new Map([ [new Date('11/14/2015'), 'Nodevember'] ];

if (!capMap.has(new Date('1/1/2016')))
    capMap.set(new Date('1/1/2016', `New Year's`);

console.log(capMap.size);

for (let [state, capital] of capMap)
    console.log(`${capial}, ${state}`);  
```

```js
let set = new Set('Ben Ilegbodu');

set.add('A').add('l').add('Y');
console.log(set.size);

if (set.has('g'))
    set.delete('g');

for (let letter of set) {  }
```

NOTES:
_[30 minutes]_

- There are new `Map` & `Set` collections
- Maps are dictionaries with keys of any type, not just strings
- Sets are unique set of values of any type
- They are iterable so they work with `for-of`
- They maintain their size & can be cleared

=====

# Quick Hits

NOTES:
- Only have a few minues left so let's quickly talk about some other noteworthy features

=====

## Object API

`Object.assign`

`Object.is`

`Object.setPrototypeOf`

/////

## Math API

`Math.sign`

`Math.trunc`

`Math.cbrt`

`Math.log2`

/////

## Number API

`Number.isInteger`

`Number.isFinite`

`Number.EPSILON`


