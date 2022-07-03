# 4.2 ECMAScript 概述（ECMAScript Overview）

[官方在线版](https://262.ecma-international.org/6.0/#sec-ecmascript-overview)

## 学习理解

本小节是对 ECMAScript 语言的细节概述，而在 [第 4 章节的开头](../) 则是对其宏观的概述。同样的，这也是一个非正式的概述，同时还强调了并没有描述该语言的所有部分。本节的开头阐述了以下几个要点：

1. ECMAScript 是基于对象的。

   - 基本语言和宿主环境设施都是由对象提供的。
   - 对象是 0 个或多个属性（property）的集合。
   - property 是指对象的属性，而 attribute 更像是属性的配置项。
   - 属性是容纳其他对象、原始值或函数的容器。
   - 对象是内置类型 Object 的成员。
   - 原始值是下列内置类型之一：Undefined、Null、Boolean、Number、String 和 Symbol。
   - 函数是可调用对象，通过属性与对象相关联的函数称为方法。

2. ECMAScript 定义了一系列的内置对象，包括：

   - 全局对象。
   - 作为语言运行时语义基础的对象：Object、Function、Boolean、Symbol 和 Error。
   - 表示和操作数值的对象：Math、Number 和 Date。
   - 文本处理对象：String 和 RegExp。
   - 索引集合对象：Array 和 9 种不同类型的数组。
   - 键值集合对象：Map 和 Set。
   - 支持结构化数据的对象：JSON、ArrayBuffer 和 DataView。
   - 支持控制抽象的对象：generator 和 Promise。
   - 反射对象：Proxy 和 Reflect。

3. ECMAScript 定义了一系列的内置操作符：各种一元操作符、乘法操作符、加法操作符、位移位操作符、关系操作符、相等操作符、二进制位操作符、二进制逻辑操作符、赋值操作符和逗号操作符。

4. ECMAScript 支持将程序拆分为多个“模块”。

5. ECMAScript 语法有意地类似于 Java，但更加宽松，所以更易于使用。

### Property 和 Attribute

property 和 attribute 翻译为中文都是 “属性” 的意思，但是在 ECMAScript 中，property 才是对象的属性，attribute 更像是 property 的配置项，从 `Object.defineProperty` 方法可以看出这点，以下是其语法定义（更多细节可参见[第 19.1.2.4 章节](https://262.ecma-international.org/6.0/#sec-object.defineproperty)），该方法的作用是给指定对象定义一个新的属性，从方法名称中使用 “Property” 关键字即可看出它代表属性，方法的第三个形参为 “Attributes”，则可以理解为给 “O” 对象添加 “P” 属性时所附加的配置信息。

```JavaScript
Object.defineProperty ( O, P, Attributes )
```

以下是原文对 property 和 attribute 的相关描述：

> In ECMAScript, an object is a collection of zero or more properties each with attributes that determine how each property can be used —— for example, when the Writable attribute for a property is set to false, any attempt by executed ECMAScript code to assign a different value to the property fails.

> 在 ECMAScript 中，对象是零个或多个属性（property）的集合，每个属性（property）的属性（attribute）决定如何使用它 —— 例如，当属性（property）的 Writable 属性（attribute）设置为 false 时，执行的 ECMAScript 代码为属性（property）分配不同值的任何尝试都会失败。
