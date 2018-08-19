# 30 分钟入门 LaTeX

> 原文：https://www.sharelatex.com/learn/Learn_LaTeX_in_30_minutes

本指南不需要你对 LaTeX 有任何准备知识，相反在阅读完该指南后，你将写出你的第一份 LaTeX 文档，并对 LaTeX 提供的基础功能有一个充分的了解。

[TOC]

## LaTeX 是什么？

LaTeX（发音：*LAY-tek* 或 *LAH-tek*）是一个用来创建具有专业感的文档的工具。基于 WYSIWYM（所见即所表）的理念，这意味着你可以专注于内容，而让计算机来做排版。不同于在 Microsoft Word 或 LibreOffice Writer 等软件中通过调节间距来控制排版，在 LaTeX 中，用户直接输入平文本，LaTeX 会做剩下的排版工作。

## 为什么学习 LaTeX

全世界的科学文档、书籍以及其它的出版物都广泛地使用 LaTeX 来出版，这不仅仅是因为它可以创建优秀排版文档，还让用户轻松地处理如输入数学公式、创建目录、引用文献和创建书目以及章节间的一致布局等复杂排版。因为有着大量的开源包（后续会做介绍），LaTeX 有着无限可能，如添加脚注、绘制原理图以及创建表格。

其中，最重要的原因是，把文档内容和展示格式分离，这意味着可以轻易地更换文档的外观。同时，可以把一份格式应用到多个文档上，科学期刊据此来创建投稿模版。事实上，有着大量的[模版][templates]，从普通的建立到站使用的幻灯片都有。

## 编写第一份 LaTeX 内容

首先创建一个 LaTeX 工程，这可以直接在自己电脑上创建一个 **.tex** 文件，或[在 ShareLaTeX 上创建一个项目][creating_a_document_in_ShareLaTeX]。下面从这个可用的示例开始：

```latex
\documentclass{article}

\begin{document}
First document. This is a simple example, with no
extra prameters or package included.
\end{document}
```

![Firstdocsmall.PNG](https://cdn.sharelatex.com/learn-scripts/images/0/01/Firstdocsmall.PNG)

可以看到，LaTeX 很好地完成了首行缩进的排版。下面详细地了解下各行代码的含义。

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/582dbc33f220531c2d4bda27/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_1&compiler=pdflatex)

第一行声明了文档类型，又称*类别（class）*。该类别控制了文档的所有外观。不同的文档类型需要使用不同的类别，如，简历使用的类别不同于科学论文。在上述示例中，使用的是 LaTeX 中最简单最常用的 **article** 类别。其它可能用到的类别有 **book** 和 **report**。

其后的文档内容包在 **\begin{document}** 和 **\end{document}** 标签中，这又称为文档 *主体（body）*。如果需要查看在主体里撰写的内容，可以重新编译来生成 PDF。这在 ShareLaTeX 平台中，只需要点击**_重新编译（Recompile）_**按钮。

如果是使用 gedit、emacs、vim、sublime 或记事本等简单文本编辑器来编辑文档，那么需要手动编译。这可以通过运行 **pdflatex < your document>** 命令来完成，更多详细信息可以阅读[该文档](https://en.wikibooks.org/wiki/LaTeX/Basics#Compilation)来获取。

如果是使用 TeXmaker 或 TeXworks 等 [LaTeX 集成编辑器](https://en.wikibooks.org/wiki/LaTeX/Installation#Editors)，只需要点击**_重新编译_**按钮。如果有不明确的地方，那么可以参考软件的文档。

前面展示了如何添加文档内容，下面将演示如何添加标题。但首先，需要简单了解下**导言（preamble）**。

## 文档导言

前面的示例中，文本内容位于 **\begin{document}** 命令后，而所有在这个命令前面的成为**导言**。在导言区域，可以定义文档类别、所使用的语言、使用的包以及其它元素。例如，一个普通的文档导言可能如下：

```latex
\documentclass[12pt, letterpaper]{article}
\usepackage[utf8]{inputenc}
```

下面详细讲述下每行作用：

**\documentclass[12pt, letterpaper]{article}**

正如前面所述，这定义了文档类型。还可以把在方括号中的以逗号（`,`）分隔的参数传递给该命令，例如，上面的参数指定了字体大小（**12pt**）以及纸张大小（**信纸（letterpaper）**）。当然，还可以使用其它字体大小（**9pt**、**11pt**、**12pt**），但如果没定义，那么默认使用 **10pt**。至于纸张大小，其它可用值有 **a4paper** 和 **legalpaper**，阅读[纸张大小和边距][page_size_and_margins]来获取更多信息。

**\usepackage[utf8]{inputenc}**

这行定义了文档编码。虽然可以不填或者设置为别的编码，但建议使用 utf-8。如果不需要设置别的编码，或者你对此不确定，那么把上面那行添加到文档中。

## 添加标题、作者和日期

如果需要在文档中添加标题、作者和日期，那么需要在导言区添加下面三行（注意不是主体部分）。

**\title{First document}**

这是标题

**\author{Hubert Farnsworth}**

这里添加作者姓名，同时，可以选择性地添加下面的命令作为该命令的参数。

**\thanks{fumed by ShareLaTeX team}**

这个命令可以添加到作者名称后面或者 **title** 命令的大括号内容里面。它会添加一个上标并且会把大括号里的内容作为脚注。这可用于添加感谢内容。

**\date{Feburary 2004}**

可以手动输入指定的日期或者使用 **\today** 命令来在每次编译时生成当前的时间。

添加了这三行后，导言区看起来是这样

```latex
\documentclass[12pt, letterpaper, twoside]{article}
\usepackage[utf8]{inputenc}

\title{First document}
\author{Hubert Farnsworth \thanks{funded by the ShareLaTeX tem}}
\date{February 2017}
```

现在给文档添加了标题、作者和日期，下一步通过 **maketitle** 来把这些信息展示在文档中。这个命令需要添加在文档主体中需要展示标题的地方。

```latex
\begin{document}

\maketitle

We have now added a title, author and date to our first \LaTeX{} document!

\end{document}
```

![Learnlatex1.PNG](https://cdn.sharelatex.com/learn-scripts/images/e/e9/Learnlatex1.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/582dbeacf220531c2d4bdaaa/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_2&compiler=pdflatex)

## 添加注释

