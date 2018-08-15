---
title: JS 基础
date: 2018-08-14 20:47:25
tags:
  - js
  - frontend
categories:
  - js
top_img: false
---

- 核心 (ECMAScript)
- 文档对象模型 (DOM)
- 浏览器对象模型 (BOM)

---

- 区分大小写
- 标识符
  > 变量、函数、属性、参数
  > 第一个字符必须是一个字母、下划线或者$，其他字符可以是字母、下划线、$、数字
- 注释
  ```
  // 单行注释

  /*
   * 多行注释
   */
  ```
- [关键字和保留字](https://www.w3schools.com/js/js_reserved.asp)
- 变量
  ```
  var message;
  let message;
  const message;
  ```
- 数据类型
  > undefined, null, boolean, number, string, object
- 操作符
  - 一元操作符：--, ++, -, +
  - 位操作符：~, &, |, ^, <<, >>, <<<, >>>
  - 布尔操作符：!, &&, ||
  - 运算符：+, -, \*,  /, %
  - 关系操作符：<, >, <=, >=, ==, !=, ===, !==
  - 条件操作符：?:
  - 赋值操作符：=, +=, -=, \*=, /=, %=, <<=, >>=, >>>=
  - 逗号操作符：,
- 语句
  > 以分号结尾；如果省略分号，则由解释器断句

  ```javascript
  // if
  if (condition) {
    statement
  } else {
    statement
  }

  // do-while
  do {
    statement
  } while (expression)

  // while
  while (expression) {
    statement
  }

  // for
  for (initialization; expression; post-loop-expression) {
    statement
  }

  // for in
  for (property in expression) {
    statement
  }

  // label
  label: statement

  // break, continue
  break [label]
  continue [label]

  // with
  with (expression) {
    statement
  }

  // switch
  switch (expression) {
    case value:
      statement;
      break;
    default:
      statement
  }

  // function
  function functionName(arg0, arg1) {
    statement
  }

  // class
  class className {
    statement
  }
  ```