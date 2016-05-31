---
title: "Clojure快速开始"
layout: article
---

这篇文档主要覆盖如下内容：

 * 准备工作（如Leiningen）和安装
 * 运行REPL
 * 创建一个工程
 * 交互式开发

本文遵从 <a rel="license"
href="http://creativecommons.org/licenses/by/3.0/">Creative Commons
Attribution 3.0 Unported License</a> （包括图片和css）。 源代码在
[Github](https://github.com/clojuredocs/guides)，翻译版在
[Github](https://github.com/casitnull/guides/tree/gh-pages)。


## 概要

Clojure是一门简单而优美的编程语言，希望通过阅读本文你会爱上它。

为了能够实践本文所列内容，请首先确保你的java环境已经正确安装。

然后安装 [Leiningen](http://leiningen.org/)，这是一个Clojure的项目管理工具。

> 原作者（John Gabriele）建议始终通过leiningen脚本来进行lein的安装
> （遵循leiningen.org上的文档操作即可），即使你的系统的包管理器提供leiningen，
> 这么做的好处是，脚本会确保你安装的是最新版的lein 2

通常来讲，Clojure工程是一个单独的目录，该目录的内容由 Leiningen 来管理。Lein会负责
帮你拉取所需的依赖jar包（包括Clojure本身的jar包），运行REPL，运行你的程序和测试，
以及程序的分发打包等，以及其他一些管理任务。运行 `lein help` 可以看到Lein所支持的所有
Task。

> 同样，你不必手动“安装”Clojure，Lein会帮你下载正确的包

## 尝试REPL

抛开lein管理下的Clojure工程，你可以在任何位置启动Clojure的REPL，前提是你必须安装
`lein` 工具。在命令行下，执行如下指令：

    $ lein repl

你会得到一个 "`user=>`" 的提示符。接下来可以在该REPL里继续尝试更多操作:

``` clojure
user=> (+ 1 1)
;; ⇒ 2
user=> (distinct [:a :b :a :c :a :d])
;; ⇒ (:a :b :c :d)
user=> (dotimes [i 3]
  #_=>   (println (rand-nth ["Fabulous!" "Marvelous!" "Inconceivable!"])
  #_=>            i))
;; Marvelous! 0
;; Inconceivable! 1
;; Fabulous! 2
;; ⇒ nil
```


## 你的第一个Clojure工程

用如下指令创建你的第一个clojure工程 `my-proj` ：

``` bash
lein new app my-proj
cd my-proj
# Have a look at the "-main" function in src/my_proj/core.clj.
lein run
```

在 my_proj/core.clj 里面有对 `println` 的调用，可以通过调用 `lein run`
观察其输出。


## 交互式开发

在工程目录下，启动一个repl（指令为`lein repl`），然后在repl下执行你的 `-main`
函数，会得到类似如下的输出：

    $ lein repl
    ...
    my-proj.core=> (-main)
    Hello, World!
    nil

（刚刚启动的repl的提示符已经从 "user=>" 变成了 "my-proj.core=>"，这是因为
你是在一个工程目录下启动的repl。在关于 ("namespaces") 的文档里会有更多介绍）

用编辑器打开 my-proj/src/my_proj/core.clj，修改函数调用`println`中的文本部分

再回到repl，重加载源文件并再次运行`-main`，并观察输出的变化：

    my-proj.core=> (require 'my-proj.core :reload)
    my-proj.core=> (-main)


## 参考资料

其他有用的快速起步文档：

  * [Clojure Distilled](http://yogthos.github.io/ClojureDistilled.html)：
    介绍了Clojure的核心概念
  * [A Brief Beginner's Guide to
    Clojure](http://www.unexpected-vortices.com/clojure/brief-beginners-guide/index.html)：
    包含更多的全局知识和背景资料，有助于你更好的从全局理解
  * [Starting Clojure screencast](http://cemerick.com/2012/05/02/starting-clojure/)：
    用Eclipse来开发webapp工程的大量截图


## 下一站

[Clojure基本语言教程](/articles/tutorials/introduction.html)



## 贡献者

John Gabriele <jmg3000@gmail.com> （原作者）

含德 <casit@outlook.com> （译者）
