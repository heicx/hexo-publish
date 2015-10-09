title: 「JavaScript高级程序设计」在HTML中使用JavaScript
date: 2015-01-11 13:10:17
tags: [JavaScript, 阅读笔记]
---

## 第二章  在HTML中使用JavaScript

2.1  <[script]>元素
*  <[script]>元素最早由Netscape创造并在浏览器Netscape Navigator2中实现，后来被W3C加入到HTML规范中，同时还定义了6个相关属性。
    1、async——可选，表示立即下载脚本[异步]。
    2、charset——可选，设置src属性中相应的代码的字符集，大多数浏览器忽略此属性。
    3、defer——可选，表示在页面完全解析完成后（一直解析到<[/html]>为止），再执行src外部文件。IE7及更早版本也支持此属性。
    4、language——已废弃，大多数浏览器忽略此属性。
    5、src——可选，表示要执行的外部代码文件。
    6、type——可选。可以认为是language的代替属性。用来设置脚本内容类型(MIME类型)，很多人还在沿用text/javascript 和 text/ecmascript，但是它们都已经不被推荐使用了。服务端在加载脚本文件时使用的MIME类型为application/x-javascript。默认值为text/javascript。
*  此小节需要注意的点：
    1、<[script]><[/script]>元素中的javascript代码里如果出现<[/script]>需要转义为<\/script>。
    2、引入外部脚本文件时应该避免如下写法：<[script] type="text/javascript" src="xxx.js" />，这种写法得不到某些浏览器（尤其IE）的正确解析，应该使用正确的<[script]><[/script]>闭合。

2.1.1  标签的位置
*  传统做法，<[script]>元素应该在<[head]>元素中，但是这种做法会导致呈现页面时出现明显的延迟/俗称白屏。为了避免这个问题，现代Web应用程序一般把外部JavaScript代码放在<[body]>元素中内容的后面。

2.1.2  延迟脚本
*  HTML5规范中明确规定，给嵌入式脚本设置defer属性会被忽略；如果是外部脚本，那么会在文档完全load完成之后，按照它们的上下文引入顺序加载执行。

2.1.3  异步脚本
*  与defer类似，只适用于外部脚本。与defer不同的是，async属性设置了之后会立即下载相应的外部脚本，并且不一定按照指定先后顺序执行，脚本一定会在页面的load事件前执行。（建议：异步脚本不要在加载期间修改DOM）

2.1.4  在XHTML中的用法
*  XHTML只是一个过渡性的标准，2000年由W3C提出，属于HTML4.0的一个子集。写法更加严谨。
*  如内嵌式脚本代码中有任意字符都会被解析。需要在代码片段中加入<[![CDATA[***]]]>，防止代码误解析，但是有个问题，有的浏览器并不支持CDATA格式，所以需要将CDATA标记注释掉，起到hack作用。
*  目前大肆推广HTML5标准，XHTML已经平稳退化。

2.2  嵌入代码与外部文件
*  可维护性——嵌入式脚本会对HTML页面增大维护成本，外部文件更利于维护。
*  可缓存——外部文件可以通过缓存的方式，缩减请求次数，加快页面加载速度。
*  适应未来——外部文件内不需要涉及到XHTML或注释hack。

2.4  <[noscript]>元素
*  顾名思义，当浏览器环境不支持JavaScript或者脚本被禁用时，<[noscript]>中的内容才会执行。













