---
title: JS Style Guide
date: 2018-08-15 08:32:37
tags:
  - js
  - frontend
categories:
  - js
top_img: false
---

> [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)

# Source file basics

- filename: all lowercase, may include underscores (_) or dashes (-), but no additional punctuation
- encoding: UTF-8
- whitespace: line terminator sequence, space character (0x20)

# Source file structure

A source file consists of, in order:

1. License or copyright information, if present
2. @fileoverview JSDoc, if present
3. import module statement
4. The file’s implementation

Exactly one blank line separates each section that is present, except the file's implementation, which may be preceded by 1 or 2 blank lines.

# Naming
  - lowerCamelCase: package, method
  - UpperCamelCase: class, enum, parameter, field, variable
  - ALL_UPPERCASE: constant

# Formatting

- Block indentation: +2 spaces
- Braces
  - Braces are used for all control structures
  - Exception: `if (shortCondition()) return;`
  - Nonempty blocks
    > No line break before the opening brace.
    > Line break after the opening brace.
    > Line break before the closing brace.
    > Line break after the closing brace if that brace terminates a statement or the body of a function or class statement, or a class method. Specifically, there is no line break after the brace if it is followed by else, catch, while, or a comma, semicolon, or right-parenthesis.

    ```js
    method(foo) {
      if (condition(foo)) {
        try {
          something();
        } catch (err) {
          recover();
        }
      }
    }
    ```
  - Empty blocks
    > An empty block or block-like construct may be closed immediately after it is opened, with no characters, space, or line break in between (i.e. {}), unless it is a part of a multi-block statement (one that directly contains multiple blocks: if/else or try/catch/finally).

    ```js
    function doNothing() {}
    ```
- Statements
  - One statement per line
  - Semicolons are required
  - Column limit: 80
- Whitespace
  - Vertical whitespace
    > Between consecutive methods
    > Create logical groupings of statements, blank lines at the start or end of a function body are not allowed
  - Horizontal whitespace
    > Separating any reserved word
    > On both sides of any binary or ternary operator
    > After a comma (,) or semicolon (;)
    > After the colon (:) in an object literal.
    > On both sides of the double slash (//) that begins an end-of-line comment

# Language features

- Use const and let
- One variable per declaration
- Declared when needed, initialized as soon as possible
- Array literals
  - Destructuring
    ```js
    const [a, b, c, ...rest] = generateResults();
    let [, b,, d] = someArray;
    function optionalDestructuring([a = 4, b = 2] = []) { … };
    ```
  - Spread operator
    ```js
    [...foo, ...bar]
    ```
- Object literals
  - Use trailing commas
  - Do not mix quoted and unquoted keys
  - Computed property names `{[key]: 42}`
  - Method shorthand
    ```js
    {method() {… }}
    {method: () => {… }}
    ```
  - Shorthand properties `{foo, bar}`
  - Destructuring
    ```js
    function destructured(ordinary, {num, str = 'some default'} = {})
    ```
  - Enums
    ```js
    const TemperatureScale = {
      CELSIUS: 'celsius',
      FAHRENHEIT: 'fahrenheit',
    };
    ```
- Class
  - Constructors
    > Subclass constructors must call super() before setting any fields or otherwise accessing this
  - Fields
    > Private fields' name must start with an underscore
  - Getters and Setters
  - Interfaces
    > All non-static method bodies on an interface must be empty blocks. Fields must be defined after the interface body as stubs on the prototype.

    ```js
    /**
     * Something that can frobnicate.
     * @record
     */
    class Frobnicator {
      /**
       * Performs the frobnication according to the given strategy.
       * @param {!FrobnicationStrategy} strategy
       */
      frobnicate(strategy) {}
    }

    /** @type {number} The number of attempts before giving up. */
    Frobnicator.prototype.attempts;
    ```
- Function
  - Arrow functions
  - Generators
    > When defining generator functions, attach the * to the function keyword when present, and separate it with a space from the name of the function. When using delegating yields, attach the * to the yield keyword.

    ```js
    /** @return {!Iterator<number>} */
    function* gen1() {
      yield 42;
    }

    /** @return {!Iterator<number>} */
    const gen2 = function*() {
      yield* gen1();
    }

    class SomeClass {
      /** @return {!Iterator<number>} */
      * gen() {
        yield 42;
      }
    }
    ```
  - Parameters
    - Default parameters
      `function maybeDoSomething(required, optional = '', node = undefined) {}`
    - Rest parameters
      `function variadic(array, ...numbers) {}`
- String literals
  - Use single quotes
  - Template strings
    ```js
    `hello, ${name}`
    ```