title: 「JavaScript高级程序设计」JavaScript简介
date: 2015-01-09 16:32:17
tags: [JavaScript, 阅读笔记]
---

## 第一章  JavaScript 简介

1.1    JavaScript 简史
*  Javascript的来由
    1995年由Netscape公司开发的浏览器Netscape Navigator2中最早使用的一种脚本语言——LiveScript，它是Javascript的前身。当时为了迎合媒体热炒的Java，更名为JavaScript。后续微软也推出了基于IE的前端脚本——JScript。
    在这种标准混乱的情况下，1997年ECMA（欧洲计算机制造商协会）统一指定了基于浏览器的新脚本语言标准——ECMA-262。这个标准一直延续至今。

1.2  JavaScript 实现
*  在含义层面上，ECMA标准只是JavaScript的一个子集。
*  JavaScript语言涵盖了三大部分：
    1、核心——ECMA标准
    2、文档对象模型（DOM）
    3、浏览器对象模型（BOM）

1.2.1  ECMAScript
*  宿主环境
    Web浏览器是最常见的ECMA的宿主环境，其他宿主环境还有Node、Adobe Flash。
*  ECMAScript的版本
    ECMAScript1——1997年06月首版。
    ECMAScript2——1998年06月格式修正，与ISO/IEC16262国际标准一致。
    ECMAScript3——1999年12月强大的正则表达式，新的控制指令，异常处理等等。
    ECMAScript4——2008年7月中止4.0的开发，将新功能放入了ECMA3.1中发布。
    ECMAScript5——2009年12月正式发布。
    ECMAScript6(ECMAScript2015)——2015年6月17号发布。

1.2.2  文档对象模型（DOM）
*  DOM概念
    DOM是W3C组织推荐的处理可扩展标示语言的标准编程接口。简单说的话，DOM是HTML与XML的应用编程接口（API）。
*  W3C DOM标准分为三个大部分
    1、核心DOM——针对任何结构化文档的标准模型
    2、XML DOM——针对XML文档标准模型
    3、HTML DOM——针对HTML文档标准模型
*  DOM级别
    1、1级DOM：1998年10月提出，由DOM Core及DOM HTML两个模块组成。
    2、2级DOM：引进了几个新的DOM模块来处理新的接口类型。
    3、3级DOM：支持XML1.0规范，新增DOM加载和保存等等。

1.2.3  浏览器对象模型（BOM）
*  BOM概念
    由于BOM没有完全统一的规范标准，所以每个浏览器多少都会有一些差异。但是也有一些已经默认的标准规范，如window对象就是BOM的顶层对象，其他对象都是它的子对象。
*  HTML5与BOM的结合规范
    1、弹出新浏览器窗口的功能
    2、提供浏览器详细信息的navigator对象
    3、提供浏览器所加载页面的相信信息的location对象
    4、提供用户显示器分辨率详细信息的screen对象
    5、XMLHttpRequest与IE的ActiveXObject自定义对象

