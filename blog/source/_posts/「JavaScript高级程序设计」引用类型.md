title: 「JavaScript高级程序设计」引用类型
date: 2015-01-14 21:11:12
tags: [JavaScript, 阅读笔记]
---

## 引用类型

#  前言
- 引用类型的值是引用类型的实例。在ECMAScript中，引用类型是一种数据结构。用于将数据和功能组织在一起。
- 引用类型其中的某一个对象置为null，会切断引用关系，另一个变量不变。

5.1  Object类型
- 创建Object实例的方式有两种，一种是使用new操作符，另一种是字面量的表示法，如下。
- new Object();  ||  {}

5.2  Array类型
- ECMAScript中的Array数组不同于其他语言，它的数组大小是可以动态调整的，即可以随着数据的添加而自动增长。
- 数组的创建有两种方式，一种是使用new操作符创建，另一种是字面量表示法，如下。
- new Array();  ||  []

5.2.1  监测数组
- 可以通过 value instanceof Array判断value是不是数组，但是仅限于一个全局作用域。
- ECMAScript5新增了Array.isArray()方法，解决了不同作用域下数组的检测。

5.2.2  转换方法
- 数组的toString()方法会返回有数组中每个值的字符串形式拼接而成的以逗号分隔的字符串。
- 调用valueOf()方法还是会返回数组。
- 核心点：toString()时为了创建字符串，会调用数组中每一项的toString()方法。toLocaleString()也同样。
  ``` javascript
      var person1 = {
          toLocaleString : function() { return "aaa" },
          toString: function() { return "bbb" }
      }
      var person2 = {
          toLocaleString : function() { return "ccc" },
          toString: function() { return "ddd" }
      }
      var people = [person1, person2];
      people.toString();    //  bbb,ddd
      people.toLocaleString();    //  aaa,ccc
  ```
- 如果数组中的其中一项的值是null或undefined，那么该值在join()，toString()的返回结果为空字符串。

5.2.3  栈方法
- 栈是一种LIFO(Last-In-First-Out，后进先出)的数据结构。
- ECMAScript中数组的行为可以表现的像栈一样。
- ECMAScript为数组提供了push()和pop()方法，以便实现类似栈的行为。
- 可以把栈理解为汉诺塔，后进先出。

5.2.4  队列方法
- 与栈相反，队列的数据结构的访问规则是FIFO(First-In-First-Out，先进先出)。
- 对于数据而言可以使用shift()与push()方法来模拟队列行为。
- 可以把队列理解为火车进站，先进先出。

5.2.5  重排序方法
- 数组中有两个可以直接用来重排序的方法：reverse()和sort()。
- reverse()方法用于翻转数组；sort()方法默认按升序排列数组项——即最小值在最前面。
- sort()方法特别之处，在于它还支持function作为参数(小于返回-1，大于返回1，等于为0)。
  ``` javascript
      // 例如：
      var arr = [0, 5, 1, 8];
      arr.sort(function(val1, val2) {
          if(val1 < val2)...
      });
  ```
5.2.6  操作方法
- concat()方法用于原有数组基础上创建一个副本，并将原数组的每一项添加至副本。
- slice()方法用于数组的截取。接受一个或两个参数，表示起始和结束位置。它不会影响原有数组。
- splice()方法可以用于删除、插入、替换。
    第一位参数为起始位置；第二位参数为要删除的项数；第三个参数为要插入的值，后位参数作用如第三位参数。

5.2.7  位置方法
- ECMAScript5中为数组实例添加了两个位置方法：indexOf()和lastIndexOf()。
- 这两个方法都接受两个参数的传递：第一位参数为要查找的项；第二位参数为查找起点位置的索引。
- indexOf()从数组的下标为0的位置开始查找，lastIndexOf()反之。

5.2.8  迭代方法
5.2.9  归并方法
- ECMAScript5中新增了两个归并数组的方法：reduce()和reduceRight()。
- reduce()方法会将数组项逐个相加，
  ``` javascript
      // 例如：
      var arrs = [1, 2, 3, 4, 5];
      var sum = arrs.reduce(function(prev, cur, index, array) {
          return prev + cur;
      });
      alert(sum);    //  结果为15，第一次执行回调时，prev是1，cur是2。第二次，prev是3（1加2的结果），cur是3（数组索引）。
  ```
5.3  Date类型
5.3.1  集成的方法
5.3.2  日期格式化方法
5.3.3  日期/时间组件方法

5.4  RegExp类型
5.4.1  RegExp实例属性
5.4.2  RegExp实例方法
5.4.3  RegExp构造函数属性
5.4.4  模式的局限性

5.5  Function类型
- ECMAScript中每个函数都是Function类型的实例。
- Function类型与其他引用类型一样，具有属性和方法。
- 声明方式有两种，
  ``` javascript
      // 例如：
      function sum() {}
      var sum = function() {}
  ```
5.5.1  没有重载
- 相同名称的函数，由上到下会被覆盖。

5.5.2  函数声明与函数表达式
- 函数声明的函数会被解析器率先解析执行，提升声明的过程中，解析器会将声明函数放到源代码树的顶部。
- 函数表达式会执行到所在行后再做解析执行。

5.5.3  作为值的函数
- 可以将函数做为参数传递。

5.5.4  函数内部属性
- 函数内部有两个特殊的对象：arguments和this。
- arguments是一个类数组，其中包含传入函数中的所有参数。arguments.callee指向当前函数。
- this关键字是函数当前执行环境对象。由谁调用，this便指向谁。
- arguments.callee.caller会指向函数的调用者。
  ``` javascript
      // 例如：
      function outer() {
          inner();
      }
      function inner() {
          arguments.callee.caller;    //    outer
      }
      outer();
  ```
5.5.5  函数属性和方法
- 每个函数都包含两个属性：length和prototype。
- length属性可以用来查询函数的传参个数。
- prototype属性用于原型扩展，在ES5中此属性是不可枚举的，因此无法通过for-in进行遍历。
- 每个函数都包含两个非继承而来的方法：call和apply。它们用于特定的作用域调用。
- apply方法接收两个参数，第一个是运行函数的作用域，第二个参数为一个数组。
- call方法与apply方法唯一不同是，除了第一位参数，之后的参数逐个直接传递。
- 总结，call和apply都是用于function函数调用，正常调用的同时改变其作用域(传入第一位作用域参数)。

5.6  基本包装类型