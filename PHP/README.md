# PHP<!-- omit in toc -->

## 目录<!-- omit in toc -->

- [1. 概述](#1-概述)
- [2. 发展历程](#2-发展历程)

## 1. 概述

[官方网站](https://www.php.net) | [Github](https://github.com/php)

PHP，英文全称 “PHP: Hypertext Preprocessor”，译为 “超文本预处理器”，是一种开源的[脚本语言](../术语表/脚本语言.md)。尤其适用于服务器端 Web 开发并可嵌入到 HTML 中。PHP 能够在所有的主流操作系统上使用、支持大多数的 Web 服务器，并支持很大范围的数据库：

- 操作系统：包括 Linux、Unix 的各种变种、Microsoft Windows、macOS 以及 RISC OS 等。
- Web 服务器：包括 Apache、Microsoft IIS、Personal Web Server（PWS）、Netscape、iPlant server、Oreilly Website Pro Server、Caudium、Xitami 以及 OmniHTTPd 等。
- 数据库：使用针对某数据库的扩展（例如 mysql）、使用抽象层如 PDO、通过 ODBC 扩展连接到任何支持 ODBC 标准的数据库，或用 cURL 或者 sockets 连接（例如 CouchDB）。

PHP 脚本主要用于以下三个领域：

- 服务端脚本：这是 PHP 最传统，也是最主要的目标领域。开展这项工作需要具备以下三点：PHP 解析器（CGI 或者服务器模块）、web 服务器和 web 浏览器。需要在运行 Web 服务器时，安装并配置 PHP，然后用 web 浏览器来访问 PHP 程序的输出，即浏览服务端的 PHP 页面。
- 命令行脚本：可以编写一段 PHP 脚本，并且不需要任何服务器或者浏览器来运行它。通过这种方式，仅仅只需要 PHP 解析器来执行。这种用法对于依赖 cron（Unix 或者 Linux 环境）或者 Task Scheduler（Windows 环境）的日常运行的脚本来说是理想的选择。
- 桌面应用程序：对于有着图形界面的桌面应用程序来说，PHP 或许不是一种最好的语言，但是如果用户非常精通 PHP，并且希望在客户端应用程序中使用 PHP 的一些高级特性，可以利用 PHP-GTK 来编写这些程序。用这种方法，还可以编写跨平台的应用程序。PHP-GTK 是 PHP 的一个扩展，在通常发布的 PHP 包中并不包含它，如果对 PHP-GTK 感兴趣，请访问 [其网站](http://gtk.php.net/) 以获取更多信息。

## 2. 发展历程

PHP 的开发始于 1993 年，当时 Rasmus Lerdorf 用 C 语言编写了几个通用网关接口（CGI）程序，并将它们扩展为支持使用 Web 表单以及与数据库通信，用来维护自己的个人主页。他将此实现称为 “Personal Home Page/Forms Interpreter”，简称 “PHP/FI”，这也是 PHP 最初的名称。

为了加速错误报告和改进代码，Rasmus Lerdorf 于 1995 年 6 月 8 日在 Usenet 讨论组上宣布发布 PHP/FI 为 “Personal Home Page Tools (PHP Tools) version 1.0”，即 PHP1，这个版本已经具备了 PHP 今天所具有的基本功能。早期的 PHP 并不打算成为一种新的编程语言，而是有机地成长，Rasmus Lerdorf 在回顾时指出：“我不知道如何阻止它，从来没有任何意图编写一种编程语言，完全不知道如何编写编程语言，我只是在途中不断添加下一个合乎逻辑的步骤。”。

在 1997 年，任职于 Technion IIT 公司的两个以色列程序员：Zeev Suraski 和 Andi Gutmans，重写了 PHP 的语法分析器，成为 PHP 3 的基础，而 PHP 也在这个时候改称为 “PHP: Hypertext Preprocessor”。经过几个月测试，开发团队在 1997 年 11 月发布了 PHP/FI 2，随后就开始 PHP 3 的开放测试，最后在 1998 年 6 月正式发布 PHP 3。

PHP3 发布后不久，Andi Gutmans 和 Zeev Suraski 开始重新改写 PHP 的核心。目标是增强复杂程序运行时的性能和 PHP 自身代码的模块性。经过不懈努力，Zend 引擎研发成功并且实现了设计目标，在 1999 年中期引入 PHP。基于该引擎并结合了更多新功能的 PHP4 于 2000 年 5 月 22 日正式发布。除了更高的性能以外，PHP4 还包含一些关键功能，比如：支持更多的 web 服务器、HTTP Sessions 支持、输出缓冲、更安全的用户输入和一些新的语言结构。

PHP5 于 2004 年 7 月正式发布，它的核心是 Zend 引擎 2 代，引入了新的对象模型和大量新功能，开始支持面向对象编程。随着 PHP6 经历长时间的开发流产后，PHP5 发布了 6 个版本顽强的支撑着开源社区的发展，直到 2015 年 12 月 3 日那天迎来了 PHP 7.0 的发布，其实 PHP5.6 已经包含了很多 PHP6 想实现的特性，它为 PHP7 的研发争取了宝贵的时间。不负众望 PHP7.0 对比 PHP5.6 性能整整提升了 2 倍，PHP7 的成功发布让很多核心开发成员回归到 PHP 社区，并且在 2020 年 11 月 26 发布了 PHP8，和 php7 系列相对比，PHP8 对各种变量判断和运算采用更严格的验证判断模式，这点有利后续版本对 jit 的性能优化。
