# 30 分钟入门 LaTeX

> 原文：https://www.sharelatex.com/learn/Learn_LaTeX_in_30_minutes

本指南不需要你对 LaTeX 有任何准备知识，相反在阅读完该指南后，你将写出你的第一份 LaTeX 文档，并对 LaTeX 提供的基础功能有一个充分的了解。

[TOC]

## LaTeX 是什么？

LaTeX（发音：*LAY-tek* 或 *LAH-tek*）是一个用来创建具有专业感的文档的工具。基于 WYSIWYM（所见即所表）的理念，这意味着你可以专注于内容，而让计算机来做排版。不同于在 Microsoft Word 或 LibreOffice Writer 等软件中通过调节间距来控制排版，在 LaTeX 中，用户直接输入平文本，LaTeX 会做剩下的排版工作。

## 为什么学习 LaTeX

全世界的科学文献、书籍以及其它的出版物都广泛地使用 LaTeX 来出版，这不仅仅是因为它可以创建优秀排版文档，还让用户轻松地处理如输入数学公式、创建目录、引用文献和创建书目以及章节间的一致布局等复杂排版。因为有着大量的开源包（后续会做介绍），LaTeX 有着无限可能，如添加脚注、绘制原理图以及创建表格。

其中，最重要的原因是，把文档内容和展示格式分离，这意味着可以轻易地更换文档的外观。同时，可以把一份格式应用到多个文档上，科学期刊据此来创建投稿模版。事实上，有着大量的[模版](templates)，从普通的建立到站使用的幻灯片都有。

## 编写第一份 LaTeX 内容

首先创建一个 LaTeX 工程，这可以直接在自己电脑上创建一个 **.tex** 文件，或[在 ShareLaTeX 上创建一个项目](creating_a_document_in_ShareLaTeX)。下面从这个可用的示例开始：

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

其后的文档内容包在 `\begin{document}` 和 `\end{document}` 标签中，这又称为文档 *主体（body）*。如果需要查看在主体里撰写的内容，可以重新编译来生成 PDF。这在 ShareLaTeX 平台中，只需要点击**_重新编译（Recompile）_**按钮。

如果是使用 gedit、emacs、vim、sublime 或记事本等简单文本编辑器来编辑文档，那么需要手动编译。这可以通过运行 **pdflatex < your document>** 命令来完成，更多详细信息可以阅读[该文档](https://en.wikibooks.org/wiki/LaTeX/Basics#Compilation)来获取。

如果是使用 TeXmaker 或 TeXworks 等 [LaTeX 集成编辑器](https://en.wikibooks.org/wiki/LaTeX/Installation#Editors)，只需要点击**_重新编译_**按钮。如果有不明确的地方，那么可以参考软件的文档。

前面展示了如何添加文档内容，下面将演示如何添加标题。但首先，需要简单了解下**导言（preamble）**。

## 文档导言

前面的示例中，文本内容位于 `\begin{document}` 命令后，而所有在这个命令前面的成为**导言**。在导言区域，可以定义文档类别、所使用的语言、使用的包以及其它元素。例如，一个普通的文档导言可能如下：

```latex
\documentclass[12pt, letterpaper]{article}
\usepackage[utf8]{inputenc}
```

下面详细讲述下每行作用：

**`\documentclass[12pt, letterpaper]{article}`**

正如前面所述，这定义了文档类型。还可以把在方括号中的以逗号（`,`）分隔的参数传递给该命令，例如，上面的参数指定了字体大小（`12pt`）以及纸张大小（**信纸（letterpaper）**）。当然，还可以使用其它字体大小（**9pt**、**11pt**、**12pt**），但如果没定义，那么默认使用 **10pt**。至于纸张大小，其它可用值有 `a4paper` 和 `legalpaper`，阅读[纸张大小和边距](page_size_and_margins)来获取更多信息。

**`\usepackage[utf8]{inputenc`}**

这行定义了文档编码。虽然可以不填或者设置为别的编码，但建议使用 utf-8。如果不需要设置别的编码，或者你对此不确定，那么把上面那行添加到文档中。

## 添加标题、作者和日期

如果需要在文档中添加标题、作者和日期，那么需要在导言区添加下面三行（注意不是主体部分）。

**`\title{First document}`**

这是标题

**`\author{Hubert Farnsworth}`**

这里添加作者姓名，同时，可以选择性地添加下面的命令作为该命令的参数。

**`\thanks{fumed by ShareLaTeX team}`**

这个命令可以添加到作者名称后面或者 `title` 命令的大括号内容里面。它会添加一个上标并且会把大括号里的内容作为脚注。这可用于添加感谢内容。

**`\date{Feburary 2004}`**

可以手动输入指定的日期或者使用 `\today` 命令来在每次编译时生成当前的时间。

添加了这三行后，导言区看起来是这样

```latex
\documentclass[12pt, letterpaper, twoside]{article}
\usepackage[utf8]{inputenc}

\title{First document}
\author{Hubert Farnsworth \thanks{funded by the ShareLaTeX tem}}
\date{February 2017}
```

现在给文档添加了标题、作者和日期，下一步通过 `maketitle` 来把这些信息展示在文档中。这个命令需要添加在文档主体中需要展示标题的地方。

```latex
\begin{document}

\maketitle

We have now added a title, author and date to our first \LaTeX{} document!

\end{document}
```

![Learnlatex1.PNG](https://cdn.sharelatex.com/learn-scripts/images/e/e9/Learnlatex1.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/582dbeacf220531c2d4bdaaa/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_2&compiler=pdflatex)

## 添加注释

注释是指不会打印出来也不会对文档产生任何影响的文本，可用来组织结构、添加备忘或者在调试时注释掉某些行或块。添加注释很简单，只需要在行迁添加 `%` 符号即可，如下：

```latex
\begin{document}

\maketitle

We have now added a title, author and date to our first \LaTeX{} document!

% This line here is a comment. It will not be printed in the document.

\end{document}
```

![Learnlatex1.PNG](https://cdn.sharelatex.com/learn-scripts/images/e/e9/Learnlatex1.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a308db13712fef4e9deff7/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_3&compiler=pdflatex)

## 粗体、斜体和下划线

现在来看几个简单的文本格式化命令：

- **粗体**：`\textbf{...}`
- *斜体*：`\textit{...}`
- <u>下划线</u>：`\underline{...}`

示例如下：

```latex
Some of the \textbf{greatest} discoveries in \underline{science} were made by \textbf{\textit{accident}}.
```

![Biu1.png](https://cdn.sharelatex.com/learn-scripts/images/a/a9/Biu1.png)

另外一个很有用的命令是 `\emph{...}`。`\emph` 命令的效果由其所在的上下文来决定，如果是在普通文本中，那么输出斜体，如果在斜体中，那么输出普通文本。

```latex
Some of the greatest \emph{discoveries}
in science
were made by accient.

\textit{Some of the greatest
\emph{discoveries}
in sciense
were made by accident.}

\textbf{Some of the greatest
\emph{discoveries}
in science
were made by accident.}
```

![Biu5.png](https://cdn.sharelatex.com/learn-scripts/images/5/5d/Biu5.png)

另外，像 [Beamer](beamer) 之类的包可以改变 `\emph` 命令的行为。

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a30a6813712fef4e9df06b/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_4&compiler=pdflatex)

## 添加图片

现在来看看如果给 LaTeX 添加图片。如果是在 ShareLaTeX 平台，那么需要先[上传图片](including_images_in_ShareLaTeX)。

下面展示如何添加图片。

```latex
\documentclass{article}
\usepackage{graphicx}
\graphicspath{ {images/} }
 
\begin{document}
The universe is immense and it seems to be homogeneous, 
in a large scale, everywhere we look at.
 
\includegraphics{universe}
 
There's a picture of a galaxy above
\end{document}
```

![InsertingImagesEx1.png](https://cdn.sharelatex.com/learn-scripts/images/9/9d/InsertingImagesEx1.png)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a30b7413712fef4e9df0a8/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_5&compiler=pdflatex)

LaTeX 本身并不能处理图片，所以需要使用别的包。包能改变 LaTeX 文档的外观或者添加更多的功能。在本例中需要使用 `graphicx` 包来添加图片到文档中。在导言区使用 `usepackage{graphicx}` 来使用该包，引入后提供了 `\includegraphics{...}` 和 `\graphicspath{...}` 命令。

`graphicspath{ {images/} }` 告诉 LaTeX 在当前目录的 *images* 文件夹里查找图片。

`includegraphics{universe}` 则是具体添加图片的命令，其中 *universe* 是不含扩展名的图片名称，即可表示 *universe.PNG*。其中，图片的文件名不应包含空白符或多个点号（`.`）。

提示：*虽然可以添加扩展名，但不建议这么做。如果忽略扩展名，LaTeX 会自动寻找所有支持的格式，详见生成[高分辨率和低分辨率图片](#Generating_high-res_and_low-res_images)*。

### 标题、标签和引用

通过 `figure` 环境来给图片添加标题、标签或引用图片，如：

```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.25\textwidth]{mesh}
    \caption{a nice plot}
    \label{fig:mesh1}
\end{figure}
 
As you can see in the figure \ref{fig:mesh1}, the 
function grows near 0. Also, in the page \pageref{fig:mesh1} 
is the same example.
```

![InsertingImages.PNG](https://cdn.sharelatex.com/learn-scripts/images/2/25/InsertingImages.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a30c5613712fef4e9df0e8/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_6&compiler=pdflatex)

上面用到了三个重要的命令：

- `\caption{a nice plot}`：会如你所料的那样给图片添加一个标题，其和 `includegraphics` 的位置决定了标题在图片的上方还是下方。
- `\label{fig:mesh1}`：给图片添加标签，同时进行编号，配合下面的命令，可以在文档别的位置引用该图片。
- `\ref{fig:mesh1}`：会被替换成具体的被引用的图片的编号。

在使用图片时，建议总是放在 `figure` 或其它类似的环境中，这样可以让 LaTeX 自动把图片以及其它内容做合适的排版。

注意：*如果是在自己及其上使用了标题以及引用，那么需要编译两次才会生效。ShareLaTeX 上只需要点击一次「重新编译」。*

## 在 LaTeX 中创建列表

LaTeX 中只需要使用列表*环境*即可轻松创建列表。环境是指 LaTeX 中和其它文档展示可以有所不同的部分，使用 `\begin{...}` 和 `\end{...}` 命令来包裹。

有有序列表和无序列表两种，各自有各自的环境。

### 无序列表

使用 `itemize` 环境来创建无序列表，列表中的每项使用 `\item` 前缀来声明。

```latex
\begin{itemize}
  \item The individual entries are indicated with a black dot, a so-called bullet.
  \item The text in the entries may be of any length.
\end{itemize}
```

![Itemize.png](https://cdn.sharelatex.com/learn-scripts/images/e/ea/Itemize.png)

列表中的每项默认使用子弹（bullet）来指示，每项的内容可以任意长。

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/52fe74766a6237452e000088/download/zip&templateName=Lists-Examples&compiler=pdflatex)

### 有序列表

有序列表内部使用同样的语法，除了使用 `enumerate` 环境来声明有序列表。

```latex
\begin{enumerate}
  \item This is the first entry in our list
  \item The list numbers increase with each entry we add
\end{enumerate}
```

![Enumerate.png](https://cdn.sharelatex.com/learn-scripts/images/3/3a/Enumerate.png)

和无序列表一样，每项必须前置 `\item` 来声明，这样就会生成从 1 开始的自增数字序列。

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/52fe74766a6237452e000088/download/zip&templateName=Lists-Examples&compiler=pdflatex)

## 添加数学公式

LaTeX 的一个主要优点是书写数学公式变得很简单。LaTeX 中的数学公式有两种书写模式，行内模式（**inline mode**）和行间模式（**display mode**）。前者是和其它文本放在一起，后者是独立成行。下面展示一个行内模式示例：

```latex
In physics, the mass-energy equivalence is stated 
by the equation $E=mc^2$, discovered in 1905 by Albert Einstein.
```

![Einstein1.png](https://cdn.sharelatex.com/learn-scripts/images/d/db/Einstein1.png)

行内模式公式可以根据习惯使用 `\( ... \)`、`$ ... $` 和 `\begin{math} ... \end{math}` 任一分隔符来插入即可。

而*行间模式*有两个版本，编号公式和不编号公式。

```latex
The mass-energy equivalence is described by the famous equation
 
$$E=mc^2$$
 
discovered in 1905 by Albert Einstein. 
In natural units ($c = 1$), the formula expresses the identity
 
\begin{equation}
E=m
\end{equation}
```

![Einstein2.png](https://cdn.sharelatex.com/learn-scripts/images/3/3a/Einstein2.png)

行间模式可以使用后面其中一个分隔符来来声明：`\[ ... \]`、`$$ ... $$`、`\begin{displaymath} ... \end{displaymath}` 以及 `\begin{equation} ... \end{equation}`。

重点提示：*equation 环境是由 amsmath 包提供的，请参考 [amsmath 文档](aligning_equations)。*

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/52ec4e44b43917a25a000e96/download/zip&templateName=MathExpressions&compiler=pdflatex)

很多数学模式的命令依赖于 **amsmath** 包，书写公式时确保引用这个包。下面这个例子展示了一些基础的数学模式命令。

```latex
Subscripts in math mode are written as $a_b$ and superscripts are written as $a^b$. These can be combined an nested to write expressions such as
 
$$T^{i_1 i_2 \dots i_p}_{j_1 j_2 \dots j_q} = T(x^{i_1},\dots,x^{i_p},e_{j_1},\dots,e_{j_q})$$
 
We write integrals using $\int$ and fractions using $\frac{a}{b}$. Limits are placed on integrals using superscripts and subscripts:
 
$$\int_0^1 \frac{1}{e^x} =  \frac{e-1}{e}$$
 
Lower case Greek letters are written as $\omega$ $\delta$ etc. while upper case Greek letters are written as $\Omega$ $\Delta$.
 
Mathematical operators are prefixed with a backslash as $\sin(\beta)$, $\cos(\alpha)$, $\log(x)$ etc.
```

![Math.PNG](https://cdn.sharelatex.com/learn-scripts/images/2/22/Math.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a30cfd13712fef4e9df123/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_7&compiler=pdflatex)

LaTeX 中数学公式相关的内容很多，无法在这里一一列举，可以参考以下文章：

- [数学公式](mathematical_expressions)
- [上标和下标](subscripts_and_superscripts)
- [括号和参数](brackets_and_Parentheses)
- [分数和二项式](fractions_and_Binomials)
- [公式对齐](aligning_equations)
- [运算符](operators)
- [数学模式中的空白](spacing_in_math_mode)
- [积分、求和以及极限](integrals_sums_and_limits)
- [数学模式中的样式](display_style_in_math_mode)
- [希腊字母和数学符号](list_of_Greek_letters_and_math_symbols)
- [数学字体](mathematical_fonts)

## 基本格式

现在来看下如何撰写摘要、章节以及段落。

### 摘要

科学文献中，一般都会包含文章主题的简要概述。在 LaTeX 中，用 `abstract` 环境来处理这部分内容，用特殊的样式来处理，并放到文档开头。

```latex
\begin{document}
 
\begin{abstract}
This is a simple paragraph at the beginning of the 
document. A brief introduction about the main subject.
\end{abstract}
\end{document}
```

![Abstractsmall.PNG](https://cdn.sharelatex.com/learn-scripts/images/d/db/Abstractsmall.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a30dd713712fef4e9df14e/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_8&compiler=pdflatex)

### 段落和换行

```latex
\begin{document}
 
\begin{abstract}
This is a simple paragraph at the beginning of the 
document. A brief introduction about the main subject.
\end{abstract}
 
Now that we have written our abstract, we can begin writing our first paragraph.
 
This line will start a second Paragraph.
\end{document}
```

![Abstractnonewline.PNG](https://cdn.sharelatex.com/learn-scripts/images/d/d3/Abstractnonewline.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a30dd713712fef4e9df14e/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_8&compiler=pdflatex)

撰写文章时，如果需要起一个新段落，那么必须按两次回车键（插入一个双空行）。可以看到，LaTeX 会自动做段落缩进。

如果需要新起一行而不是被当作新段落来处理，那么可以通过添加 `\\` 或 `\newline` 命令来完成。

阅读[段落和换行](paragraphs_and_new_lines)来或取更多信息。

### 章节

组织文档的命令根据文档类而不同，最简单的组织形式是在所有格式中都通用的章节。

```latex
\chapter{First Chapter}
 
\section{Introduction}
 
This is the first section.
 
Lorem  ipsum  dolor  sit  amet,  consectetuer  adipiscing  
elit.   Etiam  lobortisfacilisis sem.  Nullam nec mi et 
neque pharetra sollicitudin.  Praesent imperdietmi nec ante. 
Donec ullamcorper, felis non sodales...
 
\section{Second Section}
 
Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem.  Nullam nec mi et neque pharetra 
sollicitudin.  Praesent imperdiet mi necante...
 
\subsection{First Subsection}
Praesent imperdietmi nec ante. Donec ullamcorper, felis non sodales...
 
\section*{Unnumbered Section}
Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem
```

![Sections1.PNG](https://cdn.sharelatex.com/learn-scripts/images/7/7c/Sections1.PNG)

[在 ShareLaTeX 上打开示例](https://www.sharelatex.com/project/new/template?zipUrl=/project/58a30e7b13712fef4e9df182/download/zip&templateName=Learn_LaTeX_in_30_minutes:_Part_9&compiler=pdflatex)

用 `\section{}` 命令来声明新节，大括号内的内容作为其标题。节会被自动编号，如果不需要编号则使用 `\section*{}`。还可以用 `\subsection{}`、`\subsubsection{}` 来声明子节和小节。基本的层级如下：

| -1   | `\part{part}`                   |
| ---- | ------------------------------- |
| 0    | `\chapter{chaper}`              |
| 1    | `\section{section}`             |
| 2    | `\subsection{subsection}`       |
| 3    | `\subsubsection{subsubsection}` |
| 4    | `\paragraph{paragraph}`         |
| 5    | `\subparagraph{subparagraph}`   |

注意 `\part` 和 `\chapter` 只在 *report* 和 *book* 文档类中可用。

关于文档结构完整的讲述可以参考[关于章节的文章](sections_and_chapters)。

## 添加表格



