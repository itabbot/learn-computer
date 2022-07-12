# JavaScript

JavaScript，简称 JS，是一种[高级的](../术语表/高级语言.md)、[解释型](../术语表/解释型语言.md)或[即时编译型](../术语表/即时编译型语言.md)的编程语言。它以作为开发 Web 页面的脚本语言而出名，但发展至今也被应用到了很多非浏览器的环境中，比如 [Node.js](../Node.js)。

当初 ECMA[^ecma] 组织在对 JavaScript 进行标准化时，由于商标等原因不得已将该标准规范命名为 ECMAScript，但是人们并不喜欢它，仍使用 JavaScript 来称呼这门语言，只有在描述这门语言的版本时，才会使用 ECMAScript，比如 ECMAScript 6 或 ECMAScript 2015。

关于 JavaScript 的演化历史，独特而精彩，参阅[《JavaScript: the first 20 years》](https://dl.acm.org/doi/10.1145/3386327)或中文翻译版[《JavaScript 二十年》](https://cn.history.js.org/)。这是由 JavaScript 之父 Brendan Eich[^brendaneich] 与 ES6 规范首席作者 Allen Wirfs-Brock 联合编写，详细记载和解读了自 1995 年语言诞生到 2015 年 ES6 规范制定为止，共计 20 年的 JavaScript 语言演化历程。

## 学习思路

本系列的学习以官方规格文档目录作为学习清单，再结合其他的语言使用教材和资料，着重学习语言的使用和原理，不涉及语言的实现。这样做有以下好处：

1. 可以比较系统全面地学习该语言，同时可避免市面上诸多二三手资料作者的主观加工；
2. 可以了解到该语言的基本实现过程和原理，有利于从更高层面去理解和应用这门语言；
3. 不通读规格以减少耗时，因为规格中很大部分是语言的实现细节，对于语言的使用者来说学习的必要性没那么大。

鉴于目前（2022.6）应用市场的实际情况[^req] 和主流引擎的支持程度[^compat]，本系列将以 ECMAScript 2015（ES6）作为学习的起点。后续的版本则是针对增量内容进行学习。

- [ECMAScript 2015（ES6）](./ECMAScript2015)
- ECMAScript 2016
- ECMAScript 2017
- ECMAScript 2018
- ECMAScript 2019
- ECMAScript 2020
- ECMAScript 2021

[^ecma]: 欧洲计算机制造商协会，详见：[官网](https://www.ecma-international.org/)、[百度百科](https://baike.baidu.com/item/欧洲计算机制造商协会?fromtitle=ECMA&fromid=1499618)、[中文维基](https://zh.wikipedia.org/wiki/Ecma国际)、[英文维基](https://en.wikipedia.org/wiki/Ecma_International)。
[^brendaneich]: JavaScript 的发明人，详见：[个人博客](https://brendaneich.com/)、[百度百科](https://baike.baidu.com/item/布兰登·艾奇?fromtitle=Brendan+Eich&fromid=561441)、[中文维基](https://zh.wikipedia.org/wiki/布蘭登·艾克)、[英文维基](https://en.wikipedia.org/wiki/Brendan_Eich)。
[^req]: 主要指企业对语言的应用情况以及对人才的需求情况。
[^compat]: 参考 [kangax](https://github.com/kangax) 的 ECMAScript [兼容表](https://kangax.github.io/compat-table)。
