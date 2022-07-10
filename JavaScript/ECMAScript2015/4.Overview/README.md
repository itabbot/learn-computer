# 4. 概述（Overview）

[官方在线版](https://262.ecma-international.org/6.0/#sec-overview)

## 学习理解

本章节是 ECMAScript 语言的非规范性概述。章节的开始阐述了以下几个要点：

1. 本文档定义的 ECMAScript 并不是为了在计算上自给自足，而是期望程序的计算环境不仅将提供本规范中描述的对象和其他设施，还将提供某些特定于环境的对象。
2. 本文档定义的核心语言与任何特定的主机环境无关。
3. ECMAScript 最初的设计目的是作为一种脚本语言，现在已经发展成为一种功能齐全的通用编程语言。
4. ECMAScript 的一些功能与其他编程语言中使用的类似，特别是 C、Java、Self 和 Scheme。

## 子目录

- 4.1 [Web 脚本](./4.1.Web-Scripting)（[Web Scripting](https://262.ecma-international.org/6.0/#sec-web-scripting)）
- 4.2 [ECMAScript 概述](./4.2.ECMAScript-Overview)（[ECMAScript Overview](https://262.ecma-international.org/6.0/#sec-ecmascript-overview)）
  - 4.2.1 [对象](./4.2.ECMAScript-Overview/4.2.1.Objects)（[Objects](https://262.ecma-international.org/6.0/#sec-objects)）
  - 4.2.2 [ECMAScript 的严格变体](./4.2.ECMAScript-Overview/4.2.2.The-Strict-Variant-of-ECMAScript)（[The Strict Variant of ECMAScript](https://262.ecma-international.org/6.0/#sec-strict-variant-of-ecmascript)）
- 4.3 [术语和定义](./4.3.Terms-and-definitions)（[Terms and definitions](https://262.ecma-international.org/6.0/#sec-terms-and-definitions)）
  - 4.3.1 [类型](./4.3.Terms-and-definitions#431-%E7%B1%BB%E5%9E%8Btype)（[type](https://262.ecma-international.org/6.0/#sec-type)）
  - 4.3.2 [原始值](./4.3.Terms-and-definitions#432-原始值primitive-value)（[primitive value](https://262.ecma-international.org/6.0/#sec-primitive-value)）
  - 4.3.3 [对象](./4.3.Terms-and-definitions#433-对象object)（[object](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-object)）
  - 4.3.4 [构造函数](./4.3.Terms-and-definitions#434-构造函数constructor)（[constructor](https://262.ecma-international.org/6.0/#sec-constructor)）
  - 4.3.5 [原型](./4.3.Terms-and-definitions#435-原型prototype)（[prototype](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-prototype)）
  - 4.3.6 [普通对象](./4.3.Terms-and-definitions#436-普通对象ordinary-object)（[ordinary object](https://262.ecma-international.org/6.0/#sec-ordinary-object)）
  - 4.3.7 [异质对象](./4.3.Terms-and-definitions#437-异质对象exotic-object)（[exotic object](https://262.ecma-international.org/6.0/#sec-exotic-object)）
  - 4.3.8 [标准对象](./4.3.Terms-and-definitions#438-标准对象standard-object)（[standard object](https://262.ecma-international.org/6.0/#sec-standard-object)）
  - 4.3.9 [内置对象](./4.3.Terms-and-definitions#439-内置对象built-in-object)（[built-in object](https://262.ecma-international.org/6.0/#sec-built-in-object)）
  - 4.3.10 [未定义值](./4.3.Terms-and-definitions#4310-未定义值undefined-value)（[undefined value](https://262.ecma-international.org/6.0/#sec-undefined-value)）
  - 4.3.11 [未定义类型](./4.3.Terms-and-definitions#4311-未定义类型undefined-type)（[Undefined type](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-undefined-type)）
  - 4.3.12 [空值](./4.3.Terms-and-definitions#4312-空值null-value)（[null value](https://262.ecma-international.org/6.0/#sec-null-value)）
  - 4.3.13 [空类型](./4.3.Terms-and-definitions#4313-空类型null-type)（[Null type](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-null-type)）
  - 4.3.14 [布尔值](./4.3.Terms-and-definitions#4314-布尔值boolean-value)（[Boolean value](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-boolean-value)）
  - 4.3.15 [布尔类型](./4.3.Terms-and-definitions#4315-布尔类型boolean-type)（[Boolean type](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-boolean-type)）
  - 4.3.16 [布尔对象](./4.3.Terms-and-definitions#4316-布尔对象boolean-object)（[Boolean object](https://262.ecma-international.org/6.0/#sec-boolean-object)）
  - 4.3.17 [字符串值](./4.3.Terms-and-definitions#4317-字符串值string-value)（[String value](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-string-value)）
  - 4.3.18 [字符串类型](./4.3.Terms-and-definitions#4318-字符串类型string-type)（[String type](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-string-type)）
  - 4.3.19 [字符串对象](./4.3.Terms-and-definitions#4319-字符串对象string-object)（[String object](https://262.ecma-international.org/6.0/#sec-string-object)）
  - 4.3.20 [数值](./4.3.Terms-and-definitions#4320-数值number-value)（[Number value](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-number-value)）
  - 4.3.21 [数字类型](./4.3.Terms-and-definitions#4321-数字类型number-type)（[Number type](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-number-type)）
  - 4.3.22 [数字对象](./4.3.Terms-and-definitions#4322-数字对象number-object)（[Number object](https://262.ecma-international.org/6.0/#sec-number-object)）
  - 4.3.23 [无穷](./4.3.Terms-and-definitions#4323-无穷infinity)（[Infinity](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-infinity)）
  - 4.3.24 [非数值](./4.3.Terms-and-definitions#4324-非数值nan)（[NaN](https://262.ecma-international.org/6.0/#sec-terms-and-definitions-nan)）
  - 4.3.25 符号值（Symbol value）
  - 4.3.26 符号类型（Symbol type）
  - 4.3.27 符号对象（Symbol object）
  - 4.3.28 函数（function）
  - 4.3.29 内置函数（built-in function）
  - 4.3.30 特性（property）
  - 4.3.31 方法（method）
  - 4.3.32 内置方法（built-in method）
  - 4.3.33 属性（attribute）
  - 4.3.34 自有特性（own property）
  - 4.3.35 继承的特性（inherited property）
- 4.4 本规范的组织（Organization of This Specification）
