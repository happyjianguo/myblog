---
title: "reStructuredText 入门"
authors: [kiki]
tags: [rest]
categories: [blog]
draft: false
---

[原文](http://docutils.sourceforge.net/docs/user/rst/quickstart.html)

```rst
reStructuredText 入门
======================

:作者: kiki
:日期: 2019/11/6

翻译 原文__。

__ http://docutils.sourceforge.net/docs/user/rst/quickstart.html

:作者: Richard Jones
:修订: 5801
:版权: 此文档放置在公共域。

.. contents:: 目录

下面的文本包含看似 “(快速参考__)” 的链接。这些是指向 `快速学习 reStructuredText`_ 用户手册的相对链接。如果这些链接不生效，请参考 主快速参考_ 文档。

__
.. _快速学习 reStructuredText: http://docutils.sourceforge.net/docs/user/rst/quickref.html
.. _主快速参考: http://docutils.sourceforge.net/docs/user/rst/quickref.html

.. Note:: 此文档是对 reStructuredText 的一个非正式介绍。下面的章节 `下一步是什么?`_ 包含一些进一步的资源的链接，包含一个正式的参考。

结构
-----

一开始，让我说一下“结构化的文本”可能有一点用词不当。它更像使用一些一致模式的“松散的文本”。这些模式被一个 HTML 转换器解释生成“非常结构化的文本”，且能被 web 浏览器使用。

识别的最基本模式是 **段落** (快速参考__)。段落是使用空行(一个就足够)分隔的文本块。段落必须有相同的缩进——也就是说，同一段落的行左边是对齐的。开始缩进的段落会生成缩进的引用段。比如::

  这是一个段落。它非常
  短。

    这一段会生成一个缩进的文本块，通常用来引用其他文本。

  这是另一个段落。

生成:


  这是一个段落。它非常短。

    这一段会生成一个缩进的文本块，通常用来引用其他文本。

  这是另一个段落。

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#paragraphs

文本风格
--------

(快速参考__)

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#inline-markup

在段落和其他文本体内，你可以增加标记文本：使用 “``*斜体*``” 表示 *斜体*；使用 “``**粗体**``” 表示 **粗体**。这叫做“内联标记”。

如果你想使一些内容显示为固定空格的字面量，使用 “````双反引号````”。注意双反引号内部不支持进一步标记——因此星号 “``*``” 等不会被解释。

如果你发现 你想要在文本中使用其中一个“特殊的”字符，它通常是可以的—— reStructuredText 非常智能。比如，这个单独的星号 * 处理的很好，正如这个等式的星号：5*6=30。如果你想要 \*被星号包围的* 文本 **不要** 显示为斜体，那么你需要指明这个星号不是特殊的。你通过在星号之前放置一个反斜线实现，比如 “``\*``” (快速参考__)，或者通过使用双反斜线(内联标记)包围它，像这样::

  ``*``

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#escaping

.. Tip:: 将内联标记视作 (括号) 的一种形式，并按相同的方式使用它：在被标记的文本前后立即使用。内联标记本身(使用空格包围)或在一个单词中间的内联标记不会被解释。查看 标记规范__ 获取更多细节。

__ http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#inline-markup

列表
----

列表项有三种主要形式：**枚举的**、**符号的** 和 **定义**。在所有列表情形中，你可以有任意多的段落、子列表等，只要段落或其他内容和该列表项的第一行文本左对齐。

列表必须总是以新段落开始——也就是说，它们必须出现在一个空行之后。

**枚举** 列表(数字、字母或罗马数字；快速参考__)。

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#enumerated-lists

  开始一行，一个数字或字母，跟一个英文句号 “.”，或者右括号 “)”，或者使用括号 “()” 包围——选择你喜欢的。下面所有的格式都可以识别::

    1. 数组

    A. 大写字母
       且它可以跨很多行

       也可以有两个段落

    a. 小写字母

      3. 用一个不同的数字开始一个子列表
      4. 但是确保数字是正确的顺序

    I. 大写罗马数字

    i. 小写罗马数字

    (1) 又是数字

    1) 又是数字

  生成(注意：不同的枚举列表风格并不总是被每种 web 浏览器支持，因此你可能不会得到下面这样完全的效果)：

    1. 数组

    A. 大写字母
       且它可以跨很多行

       也可以有两个段落

    a. 小写字母

      3. 用一个不同的数字开始一个子列表
      4. 但是确保数字是正确的顺序

    I. 大写罗马数字

    i. 小写罗马数字

    (1) 又是数字

    1) 又是数字

**符号** 列表(快速参考__)

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#bullet-lists

  正如枚举列表，使用一个符号字符—— “-”、“+” 或 “*”::

    * 使用 “*” 的一个符号

      - 使用 “-” 的一个子列表

        + 另外一个子列表

      - 另一个项目
  
  导致:

    * 使用 “*” 的一个符号

      - 使用 “-” 的一个子列表

        + 另外一个子列表

      - 另一个项目

**定义** 列表(快速参考__)

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#definition-lists

  和其他两个列表不同，定义列表由术语和术语的定义组成。一个定义列表的格式如下::

    什么
      定义列表关联一个术语和一个定义。

    *如何*
      这个术语是一个单行短于，且定义是一个或多个
      段落或文档元素，相对术语进行缩进。
      空行不允许出现在术语和定义中间。
  
  生成:

    什么
      定义列表关联一个术语和一个定义。

    *如何*
      这个术语是一个单行短语，且定义是一个或多个
      段落或文档元素，相对术语进行缩进。
      空行不允许出现在术语和定义中间。

预格式化(代码示例)
------------------

(快速参考__)

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#literal-blocks

只想要包含一个预格式化的、永远不会被摆弄的文本块，使用 “``::``” 结束前一段。当文本和被预格式化块的前一段落缩进相同时，预格式化块结束。比如::

  一个例子::
  
      空格、换行、空行和所有类型的标记
        (比如 *这个* 或 \这个) 按照字面块保留。
    看这，我已经减少了一个缩进等级
    (但是不够远)
  
  没有其他例子

生成:

  一个例子::
  
      空格、换行、空行和所有类型的标记
        (比如 *这个* 或 \这个) 按照字面块保留。
    看这，我已经减少了一个缩进等级
    (但是不够远)
  
  没有其他例子

注意如果一个段落只包含 “``::``” ，那么它在输出时被删除::

  ::

    这是一个预格式化文本，且
    最后的 "::" 段被移除

生成:

  ::

    这是一个预格式化文本，且
    最后的 "::" 段被移除

章节
----

(快速参考__)

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#section-structure

想要将较长的文本分为整洁，你使用 **章节标题**。有一个单行的文本(一个或多个单词)带有修饰符：只有下换线，或者一个下划线和一个上划线一起，用破折号 “``-----``”、等号“``=====``”、波形号“``~~~~~``” 或任一你喜欢的非字母表字符 ``= - ` : ' " ~ ^ _ * + # < >``。一个只有下划线的修饰符和使用同一字符的上划线加下划线修饰符不同。下划线/上划线必须不短于标题文本。一致起见，因为所有使用同一个修饰符风格标记的章节被认为是同一等级::

  章 1 标题
  ===========

  节 1.1 标题
  -----------

  子节 1.1.1 标题
  ~~~~~~~~~~~~~~~

  节 1.2 标题
  -----------

  章 2 标题
  ==========

这会生成下面的结构，用一个简单的伪 XML 示意::

  <节>
    <标题>
      章 1 标题
    <节>
      <标题>
        节 1.1 标题
      <节>
        <标题>
          子节 1.1.1 标题
    <节>
      <标题>
        节 1.2 标题

  <节>
    <标题>
      章 2 标题

(伪 XML 使用缩进表示嵌套，且没有结束标记。不可能像其他例子一样展示实际的处理输出，因为章节不能再块引用中存在。对于一个抽象的自理，比较这个文档的源文本章节结构和处理的输出。)

注意章节标题可当做链接目标使用，只需要使用它们的名字。要链接到 列表_ 标题，我写入 “``列表_``”。如果标题中有一个空格，我们需要使用 “```列 表`_``” 引用标题。

文档标题/子标题
~~~~~~~~~~~~~~~

整个文档的标题和其他章节标题不同，且可能被不同地格式化(比如，HTML 默认显示为一个居中的标题)。

想要在 reStructuredText 中指明文档标题，在文档开头使用一个唯一的修饰符风格。需要指明文档的子标题，在文档标题之后立即使用另外一种唯一的修饰符风格。比如::

  ========
  文档标题
  ========
  ------
  子标题
  ------

  章节标题
  ========

  ...

注意上述的 “文档标题” 和 “章节标题” 都是要等号标记，但是是不同且不相关的风格。可出于美学插入上划线和下划线文本标题(而不是只有下划线)。

图像
-----

(快速参考__)

__ http://docutils.sourceforge.net/docs/user/rst/quickref.html#directives

想要在你的文档中包含一个图像，你使用 ``图像`` 指令__。比如::

  .. image:: images/biohazard.png

生成:

  .. image:: images/biohazard.png

``images/biohazard.png`` 部分 指示你希望出现在文本中的图像的文件名。对于图像(格式、大小等)没有限制。如果图像要出现在 HTML 中且你希望提供足够多的信息，你可以::

  .. image:: images/biohazard.png
    :height: 100
    :width: 200
    :scale: 50
    :alt: 可选文本

查看完整的 图像指令文档__ 获取更多信息

__ http://docutils.sourceforge.net/docs/ref/rst/directives.html
__ http://docutils.sourceforge.net/docs/ref/rst/directives.html#images

下一步是什么?
-------------

这篇入门介绍了 reStructuredText 最常见的特性，但是还有很多要探索。`快速学习 reStructuredText`_ 用户手册是下一步学习的好地方。获取完整的细节，去查看 `reStructuredText 标记规范`_ [#]_。

关于 Docutils 或 reStructuredText 有疑问或者需要帮助的用户应该提交一个信息到 `Docutils 用户`_ 邮件列表。

.. [#] 如果相关链接不生效，尝试主文档: http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html。

.. _reStructuredText 标记规范: http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html
.. _Docutils 用户: http://docutils.sourceforge.net/docs/user/mailing-lists.html#docutils-users
```