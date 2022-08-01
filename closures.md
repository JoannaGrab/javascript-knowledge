# Closures

A closure is the combination of a function and the lexical environment within which that function was declared. This environment consists of any local variables that were in-scope at the time the closure was created.

Closures are useful because they let you associate data (the lexical environment) with a function that operates on that data.

## Use cases

On the web, when some behavior (function) is attached to event that is later triggered by user.

## Closure scope chain

Every closure has three scopes:

- Local scope (Own scope)
- Enclosing scope (can be block, function, or module scope)
- Global scope

## Example

```js
var g = "global";

function outerFunc() {
  var o = "outer (enclosing)";
  console.log(g); // global
  console.log(o); // outer

  // closure
  function innerFunc() {
    var l = "local";
    console.log(g); // global
    console.log(o); // outer
    console.log(l); // local
  }
  innerFunc();
}
outerFunc(); // global, outer, global, outer, local
```

## Scope with var

### Function scope

```js
function f() {
  var x = "foo";
  console.log(x); // foo
}
console.log(x); // ReferenceError, x is not defined
```

### Global scope

```js
if (Math.random() > 0.5) {
  var x = 1;
} else {
  var x = 2;
}
console.log(x); // 1 or 2 depending on condition
// x is global variable, since blocks don't create scopes for var
```

## Scope with const or let

```js
if (Math.random() > 0.5) {
  const x = 1;
} else {
  const x = 2;
}
console.log(x); // ReferenceError, x is not defined
// x is local variable inside block, blocks create scopes for const and let
```
