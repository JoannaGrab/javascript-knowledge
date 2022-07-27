# Hoisting

## Variables

```js
// before
const a = 2;
var b = 3;
let c = 4;
let d;
const e;
var f;
g = 3;
// after

// before: Reference error, const is hoisted, but not initialized with a default value
// after:  2
console.log(a);
// before: undefined, hoisted as undefined
// after:  3
console.log(b);
// before: Reference error, let is hoisted, but not initialized with a default value
// after:  4
console.log(c);
// before: Reference error, let is hoisted, but not initialized with a default value
// after:  undefined
console.log(d);
// before: SyntaxError: Missing initializer in const declaration
// after:  SyntaxError: Missing initializer in const declaration
console.log(e);
// before: undefined
// after: undefined
console.log(f);
// before: Reference error, is not hoisted
// after: 3
console.log(g);
```

## Functions

```js
// before
function f1() {
  console.log(1);
}
var f2 = function () {
  console.log(2);
};
// after

// before: 1
// after: 1
f1();
// before: error according to used variable type, variable (f2) is hoisted, but function is not
// after: 2
f2();
```

Hoisting overrides previous declarations

```js
f(); // 2
function f() {
  console.log(1);
}
f(); // 2
function f() {
  console.log(2);
}
```

## Classes

```js
// before
class A {
  constructor() {
    console.log(1);
  }
}
var b = class {
  constructor() {
    console.log(2);
  }
};
// after

// before: it should be hoisted, however another rule is that class must be defined before usage so it returns reference error
// after: 1
new A();
// before: error according to used variable type, variable (b) is hoisted, but class is not
// after: 2
new b();
```

Hoisting overrides previous declarations as for functions
