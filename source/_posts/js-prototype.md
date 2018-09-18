---
title: JS Prototype
top_img: false
date: 2018-09-18 18:11:34
tags:
  - js
  - frontend
categories:
  - js
---

![JS Prototype](/imgs/js-prototype.png)

## 原型链继承

```js
function Parent () {
    this.name = 'kevin';
}

Parent.prototype.getName = function () {
    console.log(this.name);
}

function Child () {
}

Child.prototype = new Parent();

var child1 = new Child();

console.log(child1.getName())
```

## 借用构造函数(经典继承)

```js
function Parent () {
    this.names = ['kevin', 'daisy'];
}

function Child () {
    Parent.call(this);
}

var child1 = new Child();

child1.names.push('yayu');

console.log(child1.names);

var child2 = new Child();

console.log(child2.names);
```

## 组合继承

```js
function Parent (name) {
    this.name = name;
    this.colors = ['red', 'blue', 'green'];
}

Parent.prototype.getName = function () {
    console.log(this.name)
}

function Child (name, age) {
    Parent.call(this, name);
    this.age = age;
}

Child.prototype = new Parent();
Child.prototype.constructor = Child;

var child1 = new Child('kevin', '18');

child1.colors.push('black');

console.log(child1.name);
console.log(child1.age);
console.log(child1.colors);

var child2 = new Child('daisy', '20');

console.log(child2.name);
console.log(child2.age);
console.log(child2.colors);
```

## 原型式继承

```js
function createObj(o) {
    function F(){}
    F.prototype = o;
    return new F();
}

var person = {
    name: 'kevin',
    friends: ['daisy', 'kelly']
}

var person1 = createObj(person);
var person2 = createObj(person);

person1.name = 'person1';
console.log(person2.name);

person1.firends.push('taylor');
console.log(person2.friends);
```

## 寄生式继承

```js
function createObj (o) {
    var clone = Object.create(o);
    clone.sayName = function () {
        console.log('hi');
    }
    return clone;
}
```

## 寄生组合式继承

```js
function inheritPrototype(subType, superType) {
  var prototype = Object(superType.prototype);
  prototype.constructor = subType;
  subType.prototype = prototype;
}

function Parent (name) {
    this.name = name;
    this.colors = ['red', 'blue', 'green'];
}

Parent.prototype.getName = function () {
    console.log(this.name)
}

function Child (name, age) {
    Parent.call(this, name);
    this.age = age;
}

inheritPrototype(Child, Parent);

var child1 = new Child('kevin', '18');

console.log(child1);
```