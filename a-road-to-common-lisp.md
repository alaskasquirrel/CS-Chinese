---
title: '译📖A Road to Common Lisp'
date: 2020-11-06 20:05:48
tags: []
published: true
hideInList: false
feature: /post-images/a-road-to-common-lisp.png
isTop: false
---

» [Famous Programers on How Common Lisp Sucks](http://xahlee.info/comp/Common_Lisp_quotations.html) 😈

经验分享：[A Road to Common Lisp](https://irreal.org/blog/?p=7557)

免责声明：此文绝非学习Common Lisp的唯一路径，包含作者个人观点，期待你的新尝试。

>原文: <u>https://stevelosh.com/blog/2018/08/a-road-to-common-lisp/</u>  August 2018. Copyright©Steve Losh.

简译如下：

## Context

&emsp;&emsp;我认为，在学习Common Lisp之前，了解它的起源和发展很重要的。如果你已学习了现代的编程语言，古老的编程语言会看起来很奇怪，但如若你具有一些背景知识就会发现它的意义。

### History

&emsp;&emsp;Common Lisp有着悠久历史。我不打算在这里全部赘述 —— 如有兴趣，你可以参考如下资料:
- Wikipedia's [History of Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language)#History) and [History of Common Lisp](https://en.wikipedia.org/wiki/Common_Lisp#History).
- The [Where it Began section in Practical Common Lisp](http://www.gigamonkeys.com/book/introduction-why-lisp.html#where-it-began).
- The [History: Where did Lisp come from?](https://www.cs.cmu.edu/Groups//AI/lang/lisp/faq/lisp_2.faq) section of the comp.lang.lisp FAQ.
- [Common Lisp: the Untold Story](http://www.nhplace.com/kent/Papers/cl-untold-story.html) by Kent Pitman.
- [The Evolution of Lisp](https://www.dreamsongs.com/Files/HOPL2-Uncut.pdf) by Guy Steele and Richard Gabriel.

&emsp;&emsp;我猜想你大概不会阅读上述链接内容，那就在这里快速回顾一下Lisp六十载的风光吧。

&emsp;&emsp;Lisp 起始于上个世纪 50 年代，创始人是麻省理工大学（MIT）的 John McCarthy。此后的二十余年，多版本的 Lisp 方言涌现发展，其中知名的有 Maclisp, BBN Lisp/Interlisp, Franz Lisp, Spice Lisp, 以及Lisp Machine Lisp。它们有各自的实现方式，且在不同的领域枝繁叶茂。(Scheme也是在这个时间框架中诞生的，但采取了非常不同的路线，偏离了我们现在看到的路线。在这篇文章中，我不会涉及计划)

&emsp;&emsp;80年代初期，人们意识到一堆互不兼容的Lisp方言并非理想的状态，从而致力于将这些方言统一为一种通用语言，以满足每个人的需求。1984年，Guy Steele参与的<[*Common Lisp: the Language*](https://www.cs.cmu.edu/Groups/AI/html/cltl/cltl2.html)>首版发行。即便全书围绕着Lisp过往25年的实际应用、实验、经验和历史借鉴展开记述，而它并不能让每个人都满意。到了1986年，国际信息技术标准委员会为 Common Lisp 指定了 ANSI 规范。

&emsp;&emsp;正当委员会致力于标准化工作之时，< *Common Lisp: the Language*>第二版发行。这个版本更加全面，囊括了委员会正在做的一些事情。此时，Lisp语言家族已有超过30年的经验和历史可以借鉴。同期比较: Python第一次释出还要再等一年。

&emsp;&emsp;1992年，委员会发布了Common Lisp ANSI standard 的初稿以供开放审查。该草案在1994年得到批准，最终在1995年发布。此时Lisp已经超过35岁了。该版本至今仍在使用。

### Consequences

&emsp;&emsp;我希望你能够了解，Common Lisp是一种稳定、强大、实用、可扩展、而又奇怪的语言，理解这些特征会让你的学习过程更有意义。

* **Escaping the Hamster Wheel of Backwards Incompatibility**

&emsp;&emsp;兼容性是现代语言不得不面对的事情，但对于 Common Lisp 而言这都不是事，后面我会推荐一本 1990 年代写的书，我们可以不做修改的用最新版本的 Common Lisp 运行这本书里的代码。总的来说，Common Lisp社区在维护向后兼容性方面做得很好。

* **Practicality Begets Purity**

&emsp;&emsp;Common Lisp 是一种大型语言，< *Common Lisp: the Language*>第二版篇幅过千页。在没有太多额外支持的情况下，编写Pure Common Lisp 即可完成繁琐工作。在使用 Common Lisp 编程应用程序时，通常会依赖少量的稳定库，而库维护者通常会尽可能多地利用核心语言来最小化依赖关系。我的应用程序的依赖项不超过10个，库的依赖项不超过2个或3个，我可能比大多数人更保守一些。Common Lisp 的稳定性告诉我们这些库会一直持续，可不要小看了它们。

* **Extensibility**

&emsp;&emsp;Common Lisp 之所以如此实用得益于它的可扩展性。它有着强大的宏（Macros），宏允许我们编写库来实现在其他语言中的核心特性：
- Common Lisp 并没包含字符串插入，想要实现这个功能？只需要一个[库](https://edicl.github.io/cl-interpol/)。
- 想要尝试一些没有引用的不确定的编程吗？[看这里](https://nikodemus.github.io/screamer/)。
- 语法匹配可以使代码变漂亮，提高可读性。而 Common Lisp 自身并没有这个功能，我们可以看[这里](https://github.com/guicho271828/trivia/wiki/What-is-pattern-matching%3F-Benefits%3F)。
- 享受 Haskell 或 Scala 里的代数数据类型？[看这里](https://github.com/tarballs-are-good/cl-algebraic-data-type)。

&emsp;&emsp;所有这些库都依赖于宏来让使用它们感觉无缝。当然，您可以在没有宏的情况下完成所有这些工作，但是您必须添加一层来管理计算。如下:

```
(match foo
   '(list x y z) (lambda (x y z) (+ x y z))
   '(vector x y) (lambda (x y) (- x y)))
```
&emsp;&emsp;只是不会像这样：
```
(match foo
   ((list x y z) (+ x y z))
   ((vector x y) (- x y)))
```
&emsp;&emsp;没有人在 Common Lisp 标准版添加模式匹配，因为你可以将其写成库来获取 90% 以上的内容，语言本身给予您足够的自由来扩展。

* **Power**

&emsp;&emsp;宏绝对是Lisp具有高可扩展性的重要构成，因为它允许将源码转换为其他任意代码。对于C等语言中的宏也是如此，但是CommonLisp的宏不同，因为它们是语言的一部分。在C语言中，在顶层有一层宏，是用预处理器宏语言编写的。宏和语言层是相互独立的，宏提供了一个额外的抽象能力(请不要误解我的意思，这当然是有用的)。

&emsp;&emsp;在Common Lisp中，你在语言本身中编写宏。然后可以使用这些宏来编写函数，并使用这些函数来编写更多的宏。它不是两个分层的层，而是一个抽象力量的反馈循环。

&emsp;&emsp;但是宏并不是Common Lisp如此实用和可扩展的唯一因素。人们常常没有意识到的是，虽然由于宏的存在，Common Lisp是一种非常高级的语言，但它也有许多低级的工具作为语言的一部分。它永远不会像C、Rust或Forth那样低级，但是您可能会对ANSI规范包含的一些内容感到惊讶。并不是所有的Common Lisp实现都可执行这些优化，但是Common Lisp的设计者很有远见，包括了支持这些优化所需的语言特性。您可以编写标准定义的Common Lisp，并相信它将在任何地方运行，而支持这类事情的实现将利用优化机会。

&emsp;&emsp;这种使用宏支持非常高级的编程和合理数量的低级优化的组合意味着，尽管该规范已经有20多年的历史，但它仍然是今天构建的一个良好的坚实基础。三十年的经验和历史让设计师们得以创造出一种非常实用的语言，而它在未来依旧闪耀 。

* **Ugliness**

&emsp;&emsp;同等重要的是，即使Common Lisp已非常实用，但要适应现有用户和方言，这意味着有很多丑陋的地方。如果你买了< *Common Lisp:the Language* >第二版的纸质书，在索引中查找“kludges”，你会发现:

![](https://alaskasquirrel.github.io/post-images/1605720133113.jpeg)

&emsp;&emsp;Common Lisp并非完美的编程语言。‘匪夷所思’的历史包袱是当初为确保Common Lisp发展而付出的代价————旧方言的使用者通过合理的努力就可以采用Common Lisp。如果设计者‘一意孤行’使得它变得完美和漂亮，这可能招致他人的弃用。

## A Road to Learning Common Lisp

### Get a Lisp

&emsp;&emsp;第一步便需要安装一个Common Lisp实现。符合ANSI规范的实现有多种，您可以选择:
- 如果使用的是 MacOS，可以下载 GUI 界面的应用，在 App Store 找到 [ClozureCL](https://ccl.clozure.com/).(Clozure和Clojure迥然不同，切勿混淆)
- 其他系统请选择 [SBCL](http://www.sbcl.org/). (CLISP，并非你所需要的。CLISP 虽然是另一种 Lisp 实现，但它出现的时间并不长，没有 CCL 或 SBCL 普及，如果我们遇到问题的时候可能很难找到解决方案。)
- 不要使用Roswell，你现在(或者根本)不需要它。

### Pick an Editor

&emsp;&emsp;Emacs并非不可缺少，你可以在任何喜欢的文本编辑器中开始学习这门语言。如果你没有偏好，那么CCL本身与MacOS上的文本编辑器捆绑在一起。这个方法便是很好地开始。Emacs, Vim, Sublime Text, Atom, 它们都可以支持括号匹配、高亮代码注释以及自动缩排代码。

### Hello, Lisp

&emsp;&emsp;我们来创建文件 hello.lisp :
```
(defun hello ()
  (write-line "What is your name?")
  (let ((name (read-line)))
    (format t "Hello, ~A.~%" name)))
```
&emsp;&emsp;现在看不懂代码无妨，这里只是确认编程环境是否正常运行。

&emsp;&emsp;打开一个SBCL或CCL REPL([Read/Eval/Print Loop](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop))并通过输入(load "hello.lisp")加载文件，然后调用函数并确保它能工作。如果你选择SBCL，它应该是这样的:
```
$ sbcl
* (load "hello.lisp")

T
* (hello)
What is your name?
Steve
Hello, Steve.
NIL
*
```
&emsp;&emsp;如果你选择了CCL，但仍然想使用命令行，而不是MacOS应用程序(命令行程序可能被恼人的命名为ccl64，如果你在64位系统):
```
$ ccl64
Clozure Common Lisp Version ...

? (load "hello.lisp")
#P"/home/sjl/Desktop/hello.lisp"
? (hello)
What is your name?
Steve
Hello, Steve.
NIL
?
```
&emsp;&emsp;如果你的箭头键和退格键在REPL中不起作用，使用rlwrap来修复。sbcl会给你一个不错的反馈。无论如何，rlwrap都是您工具箱中一个方便的工具。

### A Gentle Introduction

&emsp;&emsp;我找到的最适合开始学习普通Lisp的书是< *[Common Lisp: A Gentle Introduction to Symbolic Computation](https://www.cs.cmu.edu/~dst/LispBook/)*>。即使您之前编写过程序，我仍然建议您从这里开始，因为它可以使您轻松地进入语言。(1990年版可以在网站上免费下载，2013年的重印修正了1990年版的一些小错误。如果你买得起，我建议你买2013年版，但1990年版也不错。)

&emsp;&emsp;通读全书，做完所有的练习。花费的时间，主要是为了让你开始克服一些主要的障碍，以适应Common Lisp，如:
- 我怎么才能记住所有这些奇怪的函数名呢?
- 为什么人们很少使用字符串?
- 我什么时候使用这个该死的引号?

&emsp;&emsp;there's also a [Discord server](https://discord.gg/tffeu2x) that some of us hang out in. Join the #common-lisp channel there and we'll be happy to help you.

### Getting Practical
&emsp;&emsp;接下来你可以阅读< *[Practical Common Lisp](http://www.gigamonkeys.com/book/)*>。

### Make Something
### Lisp as a System
### Learning Paradigms
### Switch Things Up
### Recipes for Success
### Final Patterns


## Where to Go From Here

### Macros
### Object-Oriented Programming with CLOS
### Low-Level Programming
### Web Development
### Game Development
### Window Management
### Unit Testing
### More Implementations
&emsp;&emsp;之所以强调使用SBCL和CCL，是因为它们是目前最流行的免费Common Lisp实现，但绝非唯一。还有很多值得你探索的:
- [ABCL](https://common-lisp.net/project/armedbear/) runs on the JVM.
- [ECL](https://common-lisp.net/project/ecl/main.html) can be embedded in a C program, and can translate Common Lisp code to C code.
- [CLASP](https://github.com/clasp-developers/clasp) is still under development, but is an implementation designed to be easy to interoperate with C++.
- [Lispworks](http://www.lispworks.com/) and [Allegro CL](https://franz.com/products/allegro-common-lisp/) are commercial implementations with a lot of extra features and support, but are not free.

&emsp;&emsp;我自己的项目中倾向于使用SBCL，并确保单元测试我所有的库在SBCL、CCL、ABCL和ECL中运行。这使我产生信心，自己正是在编写可移植的代码。

## Modern Common Lisp
&emsp;&emsp;Common Lisp一如稳健，但绝非停滞不前，它为你提供了足够的能力来进行程序构建。
### Structure
&emsp;&emsp;[简述文章](https://lobste.rs/s/fwhuz5/my_lisp_journey_1_getting_started_with#c_ebhvzq)
#### Packages
#### Systems
#### Projects
#### Recap

### Common Libraries

&emsp;&emsp;Common Lisp doesn't have as *large* of a community as some newer languages, but it still has a lot of libraries because it's had a community for a longer time. The stability of the core language means that many libraries written in portable Common Lisp ten or fifteen years ago can still run just fine today.

&emsp;&emsp;In this final section I'll give you a quick overview of some of the more popular libraries you might run into as you learn the language. You don't have to use all of them, but it's helpful to have some idea of what's available.

#### Alexandria

&emsp;&emsp;[Alexandria](https://common-lisp.net/project/alexandria/) is one of the most popular Common Lisp libraries (the name is a pun on the [Library of Alexandria](https://en.wikipedia.org/wiki/Library_of_Alexandria)), and it's a collection of all kinds of useful little utility functions like ```read-file-into-byte-vector``` and ```map-permutations```.

&emsp;&emsp;There are a *lot* of utility libraries for Common Lisp around — one rite of passage is building up your own personal utility library over time — but Alexandria is the most popular one. Most projects with any dependencies at all will eventually end up with Alexandria in the dependency graph somewhere.

#### Bordeaux Threads

&emsp;&emsp;[Bordeaux Threads](https://common-lisp.net/project/bordeaux-threads/) was mentioned earlier. Threads aren't part of the Common Lisp standard, but most implementations provide their own custom interface for working with them. Bordeaux Threads wraps all these implementation-specific interfaces and provides an API so you can write threaded code that will work portably.

&emsp;&emsp;If you're looking for something like Java's ```new Thread(() -> foo()).start()```, this is what you want.

#### CFFI

&emsp;&emsp;[CFFI](https://common-lisp.net/project/cffi/) is a foreign-function interface library that lets you load C libraries (e.g. ```foo.dylib``` or ```foo.so```) and call the functions in them. It works by wrapping implementation-specific interfaces, because this isn't part of the Common Lisp standard.

&emsp;&emsp;Unfortunately it has the same name as Python's FFI library, so if you're searching for documentation make sure you're looking at the right version.

#### CL-PPCRE

&emsp;&emsp;[CL-PPCRE](https://edicl.github.io/cl-ppcre/) is an implementation of Perl-compatible regular expressions. If you're looking to use regular expressions in Common Lisp, this is what you want.

#### Drakma

&emsp;&emsp;[Drakma](https://edicl.github.io/drakma/) is an HTTP client. If you need to make an HTTP request, this is what you want. There are other HTTP clients around, but Drakma is commonly used and is fine for almost anything you might need.

#### Iterate

&emsp;&emsp;[Iterate](https://common-lisp.net/project/iterate/) is a replacement for the ```loop``` macro. It works similarly, but has a more Lispy syntax and a well-defined API for extending it with new iteration constructs. I really like it myself, but beware: if you get used to ```iterate``` going back to vanilla ```loop``` will feel painful.

#### local-time

&emsp;&emsp;[local-time](https://common-lisp.net/project/local-time/) is a library for working with time and dates in Common Lisp. The standard has some basic support for times built in, but if you want to do much calculation with times (including timezones) this is probably what you want. If you're looking for something like Joda Time in Common Lisp, this is as close as you're going to get.

#### lparallel

&emsp;&emsp;[lparallel](https://lparallel.org/) is a library that builds on top of Bordeaux Threads to make common parallel processing operations much easier. Think of it as [GNU Parallel](https://www.gnu.org/software/parallel/) for Lisp, with a few extra features (e.g. channels and tasks).

&emsp;&emsp;For example: if you've got a big vector you're mapping over with ```(map 'vector #'work some-vector)``` you can split it into chunks and run in multiple threads by changing it to ```(lparallel:pmap 'vector #'work some-vector)```.

#### Named Readtables

&emsp;&emsp;[Named readtables](https://github.com/melisgl/named-readtables) is a library that adds namespaces for readtables.

&emsp;&emsp;One painful part of the standard is that reader macros are added and removed to the global readtable on the fly, so if you load multiple systems that define the same reader macros things can get messy. Named readtables adds some much-needed hygiene to that process. If you're working with reader macros at all you absolutely want to use this.

#### Roswell

&emsp;&emsp;[Roswell](https://github.com/roswell/roswell) is a couple of things rolled into one. It's a C program that handles installing and running multiple different Common Lisp implementations (kind of like NVM or rvm), and it also provides a unified way to write small shell scripts in Common Lisp and compile them into binaries.

&emsp;&emsp;I used Roswell for a little over a year, but I eventually stopped and now I don't think it's worth the trouble, for a couple of reasons.

&emsp;&emsp;First: if you write portable code you generally don't need to worry running a particular version of an implementation, because Common Lisp is so stable. I usually just install the latest version of each implementation I use with a package manager or by building from source.

&emsp;&emsp;Second: after using it for a while I found that Roswell was always very brittle to upgrade, and whenever things broke it would spew an almost JVM-sized stack trace without a decent error message.

&emsp;&emsp;For me, the negatives outweighed the positives. I'd recommend simply using the latest version of the implementations you care about and writing portable code. For the compiling-into-binaries functionality I'd recommend using your implementation's built-in support for this, or using UIOP's wrapper around that, or using a separate library like Deploy.

&emsp;&emsp;Of course your mileage might vary. If you find yourself really needing to run specific versions of specific Common Lisp implementations in rapid succession, you should look into Roswell.

#### SERIES

&emsp;&emsp;[SERIES](https://www.cliki.net/Series) was almost included in Common Lisp (it's in [Appendix A of CLtL2](https://www.cs.cmu.edu/Groups/AI/html/cltl/clm/node347.html)), but didn't quite make it. It's a library for writing functional code that looks like the traditional ```map``` and ```filter``` and ```reduce``` operations but which compiles down to efficient loops.

&emsp;&emsp;If you're looking for Clojure's transducers in Common Lisp, this is what you want.

#### st-json

&emsp;&emsp;JSON support in Common Lisp is a god damn mess. There are [an absurd number of JSON libraries](https://sites.google.com/site/sabraonthehill/home/json-libraries) and I don't really *like* any of them.

&emsp;&emsp;For me, the most important quality I need in a JSON library is an unambiguous, one-to-one mapping of types. For example: some libraries will deserialize JSON arrays as Lisp lists, and JSON ```true```/```false``` as ```t```/```nil```. But this means ```[]``` and ```false``` both deserialize to ```nil```, so you can't reliably round trip anything!

&emsp;&emsp;I've settled on using [st-json](https://marijnhaverbeke.nl/st-json/) and wrapping it up to be a little more ergonomic with some glue code. It's not the fastest solution out there, but it works for my needs. There are plenty of other options out there, so if you have different needs than me you should look into them.

#### usocket
&emsp;&emsp;[usocket](https://common-lisp.net/project/usocket/)is a library for networking sockets. Sockets and networking aren't part of the Common Lisp standard, but most implementations provide a custom interface for working with them. usocket wraps the implementation-specific interfaces and provides an API so you can write networking code portably.

&emsp;&emsp;If you want to make Lisp listen on a port and read streams of bytes from clients, or want to connect to a port and send raw bytes to it, this is what you want.

## Good Luck
&emsp;&emsp;Common Lisp是一门古老的编程语言，绝非轻而易举能够学会的，你为此花费的时间精力，必将获得回报。










