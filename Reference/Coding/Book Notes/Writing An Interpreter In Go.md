---
type: reference
topic: tech
---

#go #thorstenball #book_note 

# Introduction 
* Most books are too mathematical and require prior knowledge to interpreters 
* Most blogs are short and abstract concepts behind other tools 
* In this book we'll write an interpreter from scratch 
	* No 3rd party tools or libraries 
	* The result won't be production ready 
* Interpreter vs. compiler: 
	* Interpreters take source code and evaluate it without producing some visible, intermediate result that can later be executed 
	* Compilers take source code and produce output in another language that the underlying system can understand 
* Interpreters work different ways. This book will build a tree-walking interpreter. We'll build a:
	* Lexer 
	* Parser 
	* Tree representation 
	* Evaluator 
* We'll see what "tokens" are, what an Abstract Syntax Tree (AST) is, how to build such a tree, how to evaluate it and how to extend our language with new data structures and built-in functions 

## The Monkey Programming Language and Interpreter 
* Every interpreter interprets a specific programming language 
* Our language will be called Monkey 
* Monkey has: 
	* C-like syntax 
	* Variable bindings 
	* Integers and booleans 
	* Arithmetic expressions 
	* Build-in functions 
	* First-class and higher-order functions 
	* Closures 
	* A string data structure 
	* An array data structure 
	* A has data structure 
Here is how we bind values to names in Monkey: 
```js
let age = 1;
let name = "Monkey";
let result = 10 * (20 / 2);
```

Arrays and hashes: 
```js
let myArray = [1, 2, 3, 4, 5];
```

Hash, where values are associated with keys:
```js
let thorsten = {"name": "Thorsten", "age": 28}; 
```

Accessing values in arrays and hashes is done with index expressions: 
```js
myArray[0]       // => 1
thorsten["name"] // => "Thorsten"
```

Let statements can be used to bind functions to names: 
```js
let add = fn(a, b) { return a + b; };
```

Implicit return values are possible, so we can leave out the return:
```js
let add = fn(a, b) { a + b; };
```

Calling the function: 
```js
add(1, 2);
```

A more complex function:
```js
let fibonacci = fn(x) {
  if (x == 0) {
    0
  } else {
    if (x == 1) {
      1
    } else {
      fibonacci(x - 1) + fibonacci(x - 2);
    }
  }
};
```

Note the recursive call to fibonacci itself! 

Monkey also supports a special type of functions, called higher order functions. These functions take other functions as arguments:
```js 
let twice = fn(f, x) {
  return f(f(x));
};

let addTwo = fn(x) {
  return x + 2;
};

twice(addTwo, 2); // => 6
```

* Functions are values just like integers and strings. This is called "first class functions." 
* Our interpreter will parse Monkey source code in a REPL, building up an internal representation of the code called an Abstract Syntax Tree and then evaluate this tree. It will have a few major parts:
	* The lexer 
	* The parser 
	* The AST 
	* The internal object system 
	* The evaluator 
* We'll build these parts in this order, from the bottom up. Starting with the source code and ending with the output. This approach's drawback is that it won't produce a simple "Hello World" after the first chapter. The advantage is that it's easier to understand how all the pieces fit together and how the data flows through the program 
* The language is called "Monkey" because monkeys are magnificent, elegant, fascinating and funny creatures, just like our interpreter 

## Why Go? 
* Thorsten likes writing Go and enjoys using the language 
* It also possesses a few attributes that make it a great fit for this book 
	* Easy to understand 
	* Easy to read
	* Provides great tooling 
	* It's simple. And closer to low-lever languages like C, C++, and Rust 

## How to Use this Book 
* This book isn't a reference, nor a theory-laden paper 
* It's meant to be read from start to finish 
	* Follow along by ready, typing out, and modifying the presented code 
* Each chapter builds upon its predecessor - in code and in prose 
* [Accompanying code folder](https://interpreterbook.com/waiig_code_1.3.zip) to follow along with 
* Recommends using [direnv](https://direnv.net/) 
	* It can change the env of your shell according to an .envrc file 
* Each sub-folder in the code folder accompanying this book contains such an .envrc file that sets the GOPATH correctly for this sub-folder 
	* This allows us to easily work with the code of different chapters 

# Chapter 1 - Lexing 
## 1.1 - Lexical Analysis 
* To work with source code we need to turn it into a more accessible form 
* We're going to change the representation of our source code two times before we evaluate it: 
	* Source code -> Tokens -> Abstract Syntax Tree 
* The first transformation is called "lexical analysis", or "lexing" for short 
	* It's done by a lexer (also called a tokenizer or scanner - some use one word or the other to denote subtle differences in behavior, which we can ignore in this book) 
* Tokens are small, easily categorizable data structures that are then fed to the parser, which does the second transformation and turns the tokens into an AST 
* Example given to lexer: 
	* `"let x = 5 + 5;"` 
* What comes out of the lexer looks kinda like this: 
```
LET,
IDENTIFIER("x"),
EQUAL_SIGN,
INTEGER(5),
PLUS_SIGN
INTEGER(5),
SEMICOLON
]
```

* What constitutes a token varies between different lexer implementations 
	* Some lexers convert "5" to an integer in the parsing stage, or even later, and not when constructing tokens 
* Whitespace characters don't show up as tokens 
	* In our case that's okay, because whitespace merely acts as a separator for other tokens 
* In languages like Python this isn't the case 
* A prod-ready lexer might also attach the line number, column number and filename to a token for better error messages (e.g. "Error at line 5, column 8 in file) 
	* We aren't going to bother with that 

## 1.2 - Defining Our Tokens 
* First thing to do is define tokens our lexer will output 
* We'll start with a  few, then add more when extending the lexer 

The subset of the Monkey language we're going to lex in our first step looks like this:
```js
let five = 5;
let ten = 10;

let add = fn(x, y) {
  x + y;
};

let result = add(five, ten);
```

* Which types of tokens does this example contain? 
	* Numbers - 5, 10
	* Variable names - x, y, add, result
	* Words, like `let` and `fn` 
	* Special characters - (, ), {, }, =, ,, ; 
* The numbers are just integers and we're going to treat them as such and give them a separate type 
* The same goes for variable names; we call them "identifiers" 
* There's also "keywords" (like `let` and `fn`)
	* We won't group these together since it **should** make a difference in the parsing stage whether we encounter `let` or `fn` 
* The same goes for special characters - we'll treat each of them separately 
Let's define our token data structure: 
```go
// token/token.go
package token

type TokenType string 

type Token struct {
    Type TokenType
    Literal string
}
```

