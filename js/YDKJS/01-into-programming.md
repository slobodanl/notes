# 01 into programming
_Written by: Reza Shams Amiri_
# 01 into programming

## Code

1. Statements
2. Expressions  
    **getting input**
    ``` js
    age = prompt("Please tell me your age:");
    console.log(age);
    ```
3. Operators
    1. Assignment: ` = `
    2. Math: `+ - * /`
    3. Compound assignment: `+= -= /=`
    4. Increment/Decrement: `++ --`
    5. Object property access: `.` as in `console.log()`
    6. Equality:
        1. `==` loose-equal
        2. `===` strict-equals
        3. `!=` loose not-equal
        4. `!==` strict not-equal  
        ``` java
        var a = "22.22";
        var b = 22.22;
        console.log (a==b);     // true
        console.log (a===b);    // false
        ```
    7. Comparision: `< > <= >=`
    8. Logical: `&& ||`
1. Values & Types
    1. Converting between types  
    java script sometimes implicitly converts objects to eachother, this conversion is called `coercion`
    ``` js
    var a = "42"
    var b = Number ( a );
    ```

1. Code comments
1. Variables
    * javascript uses `dynamic typing` or `weak typing`, it allows a variable to holde any type  
    ``` java    
    var amount = 99.99;
    amount = amount * 2;
    amount = "$" + String( amount );
    ```
    * By convention constants are captial  
    ``` java
    var TAX_RATE = 0.08;// 8% sales tax
    ```
    or you can use ES6 const
    ``` java
    const TAX_RATE = 0.08;
    ```
    constants prevent accidentally changing value somewhere else after the initial settings
1. Blocks
1. Conditionals
1. Loops
    1. while  
    ``` js
    while(num>3){...}
    ```    
    1. do  
    ``` js
    do {...} while (num>3);
    ```
    1. for
    ``` java
    for ( var i=0;i<10;i++ ) { ... }
    ```
1. Functions
2. Scope
## Into Javascript
1. **Values & Types**: string, number, boolean, null and undefined, object, symbol (ES6)  
    ``` js
    var a;
    typeof a; // "undefined"
    
    a = "hello world";
    typeof a; // "string"
    
    a = 42;
    typeof a; // "number"
    
    a = true;
    typeof a; // "boolean"
    
    a = null;
    typeof a; // "object"--weird, bug
    
    a = undefined;
    typeof a; // "undefined"
    
    a = { b: "c" };
    typeof a; // "object"
    ```
1. **Objects**
    ``` java
    var obj = {
        a: "hello world",
        b: 42,
        c: true
    };
    obj.a;      // "hello world"
    obj['a'];   // "hello world"
    obj.b;      // 42
    obj['b'];   // 42
    obj.c;      // true
    obj['c'];   // true
    ```
1. **Arrays**  
    ``` js
    var arr = [
        "hello world",
        42,
        true
    ];
    arr[0];     // "hello world"
    arr[1];     // 42
    arr[2];     // true
    arr.length; // 3
  
    typeof arr; // "object"
    ```
1. **Functions**  
    functions are a subtype of objects.
    ``` js
    function foo() {
        return 42;
    }
    foo.bar = "hello world";

    typeof foo;     // "function"
    typeof foo();   // "number"
    typeof foo.bar; // "string"
    ```
1. **Built-In Type Methods**
1. **Comparing Values**
    1. Coercion
        1. implicit  
            ``` js
            var a = "42";
            var b = Number( a );
            a; // "42"
            b; // 42--the number!
            ```
        2. explicit
            ``` js
            var a = "42";
            var b = a * 1; // "42" implicitly coerced to 42 here
            a;  // "42"
            b;  // 42--the number!
            ```
    2. Truthy & falsy
        1. falsy  
            ``` js
            • "" (empty string)
            • 0 , -0 , NaN (invalid number )
            • null , undefined
            • false
            ```
        1. Truthy  
            Any value that's not falsy
            ``` js
            • "hello"
            • 42
            • true
            • [ ] , [ 1, "2", 3 ] (arrays)
            • { } , { a: 42 } (objects)
            • function foo() { .. } (functions)
            ```
    3. Equality  
        * avoid using `==` if either side of comparison could be true/flase
        * avoid using `==` if either side of comparison could be of these specific values (`0`,`""` or `[]` -- empty array)
        * In all other cases, you’re safe to use `==`.
        * If you are comparing two non-primitive values, like objects (including function and array), they are compared by reference and both `==` and `===` will result the same.
    4. Inequality
1. **Variables**
1. **Function Scopes**
    1. Hoisting
        ``` js
        var a = 2;
        foo();              // works because `foo()`        
                            // declaration is "hoisted"
                        
        function foo() {
            a = 3;
            console.log( a ); // 3
            var a;          // declaration is "hoisted"
                            // to the top of `foo()`
        }
        console.log( a );   // 2        
        ```
    2. Nested scopes
        1. `let`  
            ES6 lets you declare variables to belong to **individual blocks** (pairs of `{ .. }` ), using the let keyword
            ``` js
            function foo() {
                var a = 1;
                if (a >= 1) {
                    let b = 2;
                    while (b < 5) {
                        let c = b * 2;
                        b++;
                        console.log( a + c );
                    }
                }
            }
            foo();
            // 5 7 9
            ```
            Because of using `let` instead of `var` , `b` will belong only to the if statement and thus not to the whole `foo()` function’s scope. Similarly, `c` belongs only to the while loop.  
1. **Conditionals**
1. **Strict Mode**  
    ES5 added a “strict mode” to the language, which tightens the rules for certain behaviors. One key difference (improvement!) with strict mode is disallowing the implicit auto-global variable declaration from omitting the var :
    ``` js
    function foo() {
        "use strict";   // turn on strict mode
        a = 1;          // `var` missing, ReferenceError
    }

    foo();
    ```
1. **Functions as Values**  
2. **Functions**
    1. Function definition
    2. Closures
    3. Modules
    4. Prototypes
3. **Polyfilling**  
    The word “polyfill” refer to taking the definition of a newer feature and producing a piece of code that’s equivalent to the behavior, but is able to run in older JS environments.
    For example, ES6 defines a utilty called `Number.isNaN(..)` to provide an accurate, non-buggy check for NaN values, deprecating the original `isNaN(..)` utility. But it’s easy to polyfill that utility so that you can start using it in your code regardless of whether the end user is in an ES6 browser or not:
    ``` js    
    if (!Number.isNaN) {
        Number.isNaN = function isNaN(x) {
            return x !== x;
        };
    }    
    ```
    Or better yet, use an already vetted set of polyfills that you can trust, such as those provided by [ES5-Shims][GESESE5CSFLAMJE] and [ES6-Shim][GESESE6HCSFLJE]
4. **Transpiling**
    So the better option is to use a tool that converts your newer code into older code equivalents. This process is commonly called "transpiling", a term for transforming + compiling.
    **Before:** “default parameter values” ES6 specific  
    ``` js
    function foo(a = 2) {
        console.log( a );
    }
    foo();      // 2
    foo( 42 );  // 42
    ```
    **After:**
    ``` js
    function foo() {
        var a = arguments[0] !== (void 0) ? arguments[0] : 2;
        console.log( a );
    }
    ```
    `void 0` is aka `undefined`, in this way you can also pass `undefined`!
    Two good transpilers are:  
    1. [Babel][BTCFNGJ]  
            Transpiles ES6+ into ES5
    1. [Traceur][GGTCTIAJNTJOTC]
            Transpiles ES6, ES7, and beyond into ES5
1. Non-Java Script  
    A good chunk of the stuff that you write in your code is, strictly speaking, not directly controlled by JavaScript. The most common non-JavaScript JavaScript you’ll encounter is the DOM API. For example:
    ``` js
    var el = document.getElementByID( "foo" );
    ```
    The document is not provided by js engine, but it's a special `object`, often called a `host object`.


Creation date: _2018/09/16_

[GESESE5CSFLAMJE]: https://github.com/es-shims/es5-shim
[GESESE6HCSFLJE]: https://github.com/es-shims/es6-shim
[BTCFNGJ]: https://babeljs.io/
[GGTCTIAJNTJOTC]: https://github.com/google/traceur-compiler