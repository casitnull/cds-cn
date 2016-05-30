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

## Trying out the REPL

Although lein facilitates managing your projects, you can also run it
on its own (outside of any particular project directory). Once you
have the `lein` tool installed, run it from anywhere you like to get a
repl:

    $ lein repl

You should be greeted with a "`user=>`" prompt. Try it out:

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


## Your first project

Create your first Clojure program like so:

``` bash
lein new app my-proj
cd my-proj
# Have a look at the "-main" function in src/my_proj/core.clj.
lein run
```

and see the output from that `println` function call in
my_proj/core.clj!


## Interactive Development

In your project directory, start up a repl (`lein repl`) and
run your `-main` function to see its output in the repl:

    $ lein repl
    ...
    my-proj.core=> (-main)
    Hello, World!
    nil

(The prompt is now "my-proj.core=>" instead of "user=>" because lein
has started the repl in an app project. More about that ("namespaces")
in the topical guides.)

From elsewhere, open up your my-proj/src/my_proj/core.clj file
in your editor. Modify the text in that `println` call.

Back in the repl, reload your source file and run `-main` again:

    my-proj.core=> (require 'my-proj.core :reload)
    my-proj.core=> (-main)

to see your changes.


## See Also

Other getting started documentation you might find useful:

  * [Clojure Distilled](http://yogthos.github.io/ClojureDistilled.html):
    introduction to core concepts necessary for working with Clojure
  * [A Brief Beginner's Guide to
    Clojure](http://www.unexpected-vortices.com/clojure/brief-beginners-guide/index.html):
    contains a bit more overview and background material for learning your way
    around the landscape.
  * [Starting Clojure screencast](http://cemerick.com/2012/05/02/starting-clojure/):
    an extensive getting-started screencast using Eclipse to develop a webapp project.


## Next Stop

Next stop: [the basic Clojure language tutorial](/articles/tutorials/introduction.html).



## Contributors

John Gabriele <jmg3000@gmail.com> (original author)
