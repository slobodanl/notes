# Functions
_Written by: Reza Shams Amiri_
# Functions

## Function definition
Functions are values, you can pass them along.

1. anonymous functions  
    ``` js
    var foo = function(){
        //...
    };
    ```
1. named functions  
    ``` js
    var foo = function bar(){
        //...
    };
    ```
    
## Immediately Invoked Function Expressions (IIFEs)

The above functions are defined but are not executed. There’s another way to execute a function expression, which is typically referred to as an _immediately invoked function expression_ (IIFE):
``` js
(function IIFE(){
    console.log( "Hello!" );
})();
// "Hello!"
```
Or simply
``` js
(function(){console.log( "Hello!" );})(); // "Hello!"
```

## Closure

You can think of closure as a way to “remember” and continue to access a function’s scope (its variables) even once the function has finished running.

``` js
function makeAdder(x) {
  // parameter `x` is an inner variable
  // inner function `add()` uses `x`, so
  // it has a "closure" over it
  function add(y) {
    return y + x;
  }

  return add;
}

var pluseOne = makeAdder(1);
var pluseTen = makeAdder(10);

console.log(pluseOne(13)); // 13 + 1    = 14
console.log(pluseTen(13)); // 13 + 10   = 23
```
The reference to the inner `add(..)` function that gets returned with each call to the outer `makeAdder(..)` is able to remember whatever `x` value was passed in to `makeAdder(..)`.

## Modules

``` js
function User(sex) {
  let username, password;

  function doLogin(user, pw) {
    username = user;
    password = pw;
    // do the rest of the login work
  }

  function whoAmI() {
    console.log("you are " + username + ", your password is: " + password + ", you are a "+ (sex==='f'?"female":"male"));
  }

  const publicAPI = {
    login: doLogin,
    whoAmI: whoAmI
  };

  return publicAPI;
}

// create a `User` module instance
var karin = User('f');
var reza = User('m');
karin.login("karin", "12Battery34!");
reza.login("reza", "KherKher$#doost");
karin.whoAmI(); //you are karin, your password is: 12Battery34!, you are a female
reza.whoAmI();  //you are reza, your password is: KherKher$#doost, you are a male
```
## Prototypes

When you reference a property on an object, if that property doesn’t exist, JavaScript will automatically use that object’s internal prototype reference to find another object to look for the property on. You could think of this almost as a fallback if the property is missing.
The internal prototype reference linkage from one object to its fall-back happens at the time the object is created. The simplest way to illustrate it is with a built-in utility called `Object.create(..)` .
``` js
let foo = {
  a: 42,
  b: "reza"
};
// create `bar` and link it to `foo`
let bar = Object.create(foo);
bar.b = "hello world";
console.log(bar.b); // "hello world"
console.log(bar.a); // 42 <-- delegated to `foo`
```

``` uml
skinparam monochrome true

class foo {
    a: 42
}
class bar {
    b: "hello world"
}
foo <|-- bar
```
* * *
Creation date: _2018/09/16_
