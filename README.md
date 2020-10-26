## 1. LaTeX 介绍


### 1.1 LaTeX 是什么

LaTeX基于TeX，目的主要是为了方便排版。在学术界的论文，尤其是数学、计算机等学科论文都是由LaTeX编写。

### 1.2 如何学习LaTeX

1. 简单入门可以看Overleaf的[30分钟了解LaTeX](https://cn.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
2. 最快学习方式是在了解了基本概念后，拿着别人写好的例子修改，遇到问题时翻看书籍、上网搜索或者问人。[Overleaf模板](https://www.overleaf.com/latex/templates)
3. 需要深度学习地话，可以看一些youtube或B站的视频，或者是拿书啃。

### 1.3 LaTeX支持中文吗？

LaTeX不能直接使用中文编辑，若要用中文编辑，需要安装特定的宏包。



## 2. LaTeX 安装


### 2.1 LaTeX 编辑器

##### 1. [Oveleaf中国](https://cn.overleaf.com/project)

网页版LaTex编辑器，不用安装，但是编译速度比较慢。

##### 2. TeXworks

TeXlive自带的编辑器，轻量级的LaTeX编辑器。

##### 3. TeXShop

MacTeX自带的编辑器，Mac平台上比较轻量级的LaTeX编辑器。

##### 4. TeXstudio

它很简洁，而且有即时预览功能，是一个非常务实高效的解决方案。

### 2.2 安装

1. 根据平台下载TeX发行版进行安装

   - TeXLive for windows （[科大镜像](http://mirrors.ustc.edu.cn/CTAN/systems/texlive/Images/texlive.iso)）

   - [MacTeX](http://tug.org/mactex/) for Mac

   *Mac上也可以下载BasicTeX，相当于MacTeX的阉割版*

2. 下载编辑器



## 3. 示范


1. 在Overleaf上**创建一个新项目**，输入**项目名称**
2. 一个简单的例子：

```latex
\documentclass[12pt, letterpaper]{article}
\usepackage[utf8]{inputenc}

\title{First document}
\author{Rongjian Yang \thanks{supported by all members of my team}}
\date{October 2020}

\begin{document}

\maketitle

First document. This is a simple example, with no 
extra parameters or packages included.

% This line here is a comment. It will not be printed in the document.

\end{document}
```

#### Preamble

代码的前6行（`\begin{document}`之前的内容）被称作preamble，包括了文件类型、语言、需要使用的包（packages）以及其它要素。

第1行表明该文件的类型（class），类型控制文件的整体格式。不同种类的文件对应不同的类型。在这个例子中，类型是`article`，这是LaTeX中最简单也是最常用的类型。此外还有例如`book`或者`report`等类型。此外，可以在[ ]中加入字体大小（`12pt`）、纸张尺寸（`letterpaper`）等要素。

第2行是文件的编码，可以**省略**或更改为其他编码（但建议使用utf-8）。

第4行是文章的标题。

第5行是文章的作者。可以加入附加选项`\thanks{}`，它将在作者后面添加一个上标，并在最后添加脚注。如果需要在文章中感谢一个机构，这很有用。

第6行是日期。日期既可以手动添加，也可以使用`\date{\today}`自动地填充今天的日期。

**在你给定了标题、作者和日期之后，你需要在body部分加入`\maketitle`命令行才能将这些内容显示在文章当中。**

#### Body

在Preamble之后是文件的内容，置于`\begin{document}`和`\end{document}`之间，这被称为文件的主体（body）。编辑器的右侧是文件的pdf格式显示，默认情况不会自动编译，需要手动点击`重新编译`才会进行编译。（重新编译旁边有选项，可以打开**自动编译**。）

#### Comments

第15行是注释，在需要注释的内容前面添加`%`即可。

#### Text format

- **粗体**：`\textbf{...}`
- *斜体*：`\textit{...}`
- <u>下划线</u>：`\underline{...}`

```latex
Some of the \textbf{greatest}
discoveries in \underline{science} 
were made by \textbf{\textit{accident}}.
```

另外一个非常有用的命令行是 `\emph{...}`，它能自动“强调”某一部分内容：

```
Some of the greatest \emph{discoveries} 
in science 
were made by accident.

\textit{Some of the greatest \emph{discoveries} 
in science 
were made by accident.}

\textbf{Some of the greatest \emph{discoveries} 
in science 
were made by accident.}
```

#### Images

Overleaf要使用图片，需要先将图片上传。然后必须使用扩展包`graphicx`才能够展示图片，下面是一个例子：

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{graphicx}

\title{A project with images}
\author{Rongjian Yang}
\date{}

\graphicspath{{images/}}

\begin{document}

\maketitle

\section{Introduction}
\begin{figure}[htp]
    \centering
    \includegraphics[width=10cm]{pic1.jpg}
    \caption{An image}
    \label{fig:street}
\end{figure}

As you can see in the figure \ref{fig:street}, it is one 
street in Shanghai. Also, in the page \pageref{fig:street} 
is the same example.

\end{document}
```

第3行`\usepackage{graphicx}`是使用了绘图的扩展包；

第9行`graphicspath{...}`表示要使用的图片所在地址；

第16～21行是插入图片的所有信息，第17行表示居中，第18行`includegraphics{...}`填写插入图片文件的名字（参数规定了图片的宽度），第19行是图片在文章中的标题，第20行赋予图片标签以便后文引用（第23～25行即引用图片的例子）。

*关于第16行的参数，可以参考[这里](https://www.cnblogs.com/yongjiuzhizhen/p/5772962.html?utm_source=itdadao&utm_medium=referral)*

#### Lists

- ###### Unordered lists

```latex
\begin{itemize}
  \item The individual entries are indicated with a black dot, a so-called bullet.
  \item The text in the entries may be of any length.
\end{itemize}
```

- ##### Ordered lists

```latex
\begin{enumerate}
  \item This is the first entry in our list
  \item The list numbers increase with each entry we add
\end{enumerate}
```

#### Math

LaTeX的优势之一就是非常便于编写数学表达式。许多数学模型的命令行都需要一个包`amsmath`，所以请在编写数学表达式之前确保引用了这个包。

数学表达式可以是*内嵌*在语句当中，也可以是单独*陈列*出来的，我们看一下下面这个例子：

```latex
In physics, the mass-energy equivalence is stated 
by the equation $E=mc^2$, discovered in 1905 by Albert Einstein.

In physics, the mass-energy equivalence is stated 
by the equation \(E=mc^2\), discovered in 1905 by Albert Einstein.

In physics, the mass-energy equivalence is stated by the equation 
\begin{math} E=mc^2 \end{math}, discovered in 1905 by Albert Einstein.

The mass-energy equivalence is described by the famous equation
\[ E=mc^2 \]
discovered in 1905 by Albert Einstein. 
In natural units ($c = 1$), the formula expresses the identity
\begin{equation}
E=m
\end{equation}
```

#### Basic formatting

我们直接举例来看：

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{graphicx}

\title{A project about basic formatting}
\author{Rongjian Yang}
\date{}


\begin{document}

\maketitle

\begin{abstract}
This is a simple paragraph at the beginning of the 
document. A brief introduction about the main subject.
\end{abstract}
 
Now that we have written our abstract, we can begin writing our first paragraph.
 
This line will start a second Paragraph.

\section{Introduction}

This is the first section.

\section{Background}

This is the second section.

\subsection{Attention}

This is the first subsection.

\section*{Unnumbered Section}

As you can see.

\end{document}
```

- ##### Abstracts

代码中的第14～17行。

- ##### Paragraphs and newlines

在代码中使用两次“Enter”键表示不同的段落（即空一行）。

- ##### Chapters and Sections

| 等级 | 代码                            |
| :--: | ------------------------------- |
|  -1  | `\part{part}`                   |
|  0   | `\chapter{chapter}`             |
|  1   | `\section{section}`             |
|  2   | `\subsection{subsection}`       |
|  3   | `\subsubsection{subsubsection}` |
|  4   | `\paragraph{paragraph}`         |
|  5   | `\subparagraph{subparagraph}`   |

注意：`\part`和`\chapter`只有在文件类型是*report*或者*book*时才生效。

#### Tables

LaTeX中的基础图表功能如下例所示：

```latex
\begin{center}
\begin{tabular}{|| l | c | c | r ||} 
 \hline
 Col1 & Col2 & Col2 & Col3 \\ [0.5ex] 
 \hline\hline
 1 & 6 & 87837 & 787 \\ 
 \hline
 2 & 7 & 78 & 5415 \\
 \hline
 3 & 545 & 778 & 7507 \\
 \hline
 4 & 545 & 18744 & 7560 \\
 \hline
 5 & 88 & 788 & 6344 \\ [1ex] 
 \hline
\end{tabular}
\end{center}
```

第1行和第17行之间表示居中的内容，第2行和第16行表示表格的内容。

第2行当中的`{|| l | c | c | r ||}`表示了表格每一行的格式，`|`是边框，`l`、`r`和`c`分别表示左对齐、右对齐和居中。第3行`\hline`表示横向的边框。

**用代码编写表格比较麻烦，所以建议使用在线工具（例如[TablesGenerator.com](https://www.tablesgenerator.com)）中直接在表格上操作，然后把对应代码复制过来。**

另外，表格的标题和引用与图片类似：

```latex
Table \ref{table:data} is an example of referenced \LaTeX{} elements.

\begin{table}[h!]
\centering
\begin{tabular}{||c c c c||} 
 \hline
 Col1 & Col2 & Col2 & Col3 \\ [0.5ex] 
 \hline\hline
 1 & 6 & 87837 & 787 \\ 
 2 & 7 & 78 & 5415 \\
 3 & 545 & 778 & 7507 \\
 4 & 545 & 18744 & 7560 \\
 5 & 88 & 788 & 6344 \\ [1ex] 
 \hline
\end{tabular}
\caption{Table to test captions and labels}
\label{table:data}
\end{table}
```

#### Contents

LaTeX的插入目录操作非常简单，命令行`\tableofcontents`就能帮你完成所有工作。

#### 下载pdf文件

![Downloadpdf.PNG](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/6/6c/Downloadpdf.PNG)



## 4. 其它相关


### 4.1 电子文档

- [Learn LaTeX in 30 minutes (Overleaf)](https://cn.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
  这是Overleaf上的一个简易教程，除了该教程意外，在Overleaf上还有非常详细的LaTeX相关知识，包括：Overleaf guides, LaTeX Basics, Mathematics, Figures and tables, References and Citations, Languages, Document structure, Formatting, Fonts, Presentations, Commands, Field specific, Class files, Advanced TeX/LaTeX。
- [LaTeX Turorials: A Primer](http://www.tug.org/twg/mactex/tutorials/ltxprimer-1.0.pdf)
  这个是印度TeX用户组编写的手册，成文于2003年，不过因为内容限定在最核心的LaTeX基础命令与宏包用法，所以目前仍是很好的参考。篇幅只有155页，内容包括了使用LaTeX写论文投稿所需要的各种基础知识。对于面向学术论文投稿的人来说非常实用，选材精当、编排合理、叙述准确，是不可多得的入门参考。（比名声在外的某Ishort之流要好得多。）

### 4.2 书籍

- 刘海洋《LaTeX入门》
- 胡伟《LaTeX2e 完全学习手册》第二版
- 机械工业出版社《A Guide to LaTeX》第四版
  这本书是LaTeX的经典教材之一。
- [《cwTeX排版系统》](http://homepage.ntu.edu.tw/~ntut019/cwtex/cxbook3.pdf)第三版
  这是台湾cwTeX的手册，同时也是正式出版的书籍，375页的篇幅，对LaTeX基础内容的讲解比较详细。这是目前能找到的最详细的有关LaTeX的正版电子参考材料。

### 4.3 社区

- [TeX - LaTeX Stack Exchange](http://tex.stackexchange.com) 

### 4.4 推荐网站

- [Detexify LaTeX handwritten symbol recognition](http://detexify.kirelabs.org/classify.html)

通过手写识别LaTeX符号，识别率很高。尤其是当看到一个符号却不知道其LaTeX命令的时候它很有用。只要画出记忆中符号的样子，就会自动出现各种可能想要的表示方法。

- [TablesGenerator](https://www.tablesgenerator.com)

在线编辑表格，会自动生成其对应的latex代码。

