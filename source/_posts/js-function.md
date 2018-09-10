---
title: JS Function
top_img: false
date: 2018-09-10 09:14:59
tags:
  - js
  - frontend
categories:
  - js
---

# Function

```js
var sum = new Function('x', 'y', 'return x + y');

function sum(x, y) {
  return x + y;
}
```

- arguments (callee -> caller)
- this
- length

# anonymous function vs. closure

```js
var data = [];

for (var i = 0; i < 3; i++) {
  data[i] = function () {
    console.log(i);
  };
}

data[0]();
data[1]();
data[2]();
```

# First-class citizens

[First-class function](https://en.wikipedia.org/wiki/First-class_function)

# Currying

```js
var _ = {};

function curry(fn, args, holes) {
  length = fn.length;

  args = args || [];
  holes = holes || [];

  return function() {

    var _args = args.slice(0),
      _holes = holes.slice(0),
      argsLen = args.length,
      holesLen = holes.length,
      arg, i, index = 0;

    for (i = 0; i < arguments.length; i++) {
      arg = arguments[i];
      if (arg === _ && holesLen) {
        index++
        if (index > holesLen) {
          _args.push(arg);
          _holes.push(argsLen - 1 + index - holesLen)
        }
      }
      else if (arg === _) {
        _args.push(arg);
        _holes.push(argsLen + i);
      }
      else if (holesLen) {
        if (index >= holesLen) {
          _args.push(arg);
        }
        else {
          _args.splice(_holes[index], 1, arg);
          _holes.splice(index, 1);
        }
      }
      else {
        _args.push(arg);
      }
    }
    if (_holes.length || _args.length < length) {
      return curry.call(this, fn, _args, _holes);
    }
    else {
      return fn.apply(this, _args);
    }
  }
}
```

# Partial application

```js
var _ = {};

function partial(fn) {
  var args = [].slice.call(arguments, 1);

  return function() {
    var position = 0, len = args.length;
    for(var i = 0; i < len; i++) {
      args[i] = args[i] === _ ? arguments[position++] : args[i]
    }
    while(position < arguments.length) args.push(arguments[position++]);
    return fn.apply(this, args);
  };
};
```