---
title: HTML5 语义化标签
categories:
- HTML
tags:
- 语义化
- HTML5
---
前端工程师在谈到 HTML5 与 HTML4 有什么不同的时候，首先想到的肯定是它新增了很多语义化标签。这篇文章简单介绍了一些语义化标签，并讨论了语义化的作用。

## 新增标签

### 结构相关
- header
  represents a group of introductory or navigational aids.
  代表一组引导或导航工具
- nav
  represents a section of the document intended for navigation
  代表文档中的导航部分，一般用在 header 内部
- main
  can be used as a container for the dominant contents of another element, such as the main content of the page.
  表示页面的主要内容，在一个页面中只用一次，并且将它们直接作为 body 的子元素。
- section
  represents a generic document or application section. It can be used together with the h1, h2, h3, h4, h5, and h6 elements to indicate the document structure.
  代表了文档或应用的一般部分。可以与 h 标签配合使用来显示文档的结构
- hgroup
  represents the header of a section
  用于将多个标题聚集到一起，比如正标题和副标题
- article
  represents an independent piece of content of a document, such as a blog entry or newspaper article.
  代表一个独立完整的相关内容块。虽然 section 也是带有主题性的一块内容，但是无论结构还是内容上，article 本身就是独立的，完整的。
  **判断是不是完整的内容，就看是不是脱离了所在的语境，是否还是完整的，独立的。**
- aside
  represents a piece of content that is only slightly related to the rest of the page.
  代表的是跟页面主体内容相关的一些内容，也可以被包含在主要内容中
- footer
  represents a footer for a section and can contain information about the author, copyright information, etc.
- figure
  represents a piece of self-contained flow content, typically referenced as a single unit from the main flow of the document.

总结：
1. 可以简单地将一个页面分为 header + main + footer
   header 内部可以包含 h1 和 nav
   main 内容可以包含 section/article + aside

2. div section article, 语义上是从无到有，逐渐增强的。div 无任何语义，仅仅作为样式化和脚本化的 hock（钩子）。section 和 article 的区分，重点就看这段内容脱离了整体是不是还能作为一个完整的、独立的内容而存在，这里的重点又在完整身上。因为 section 包含的内容也能算独立的一块，但是它只能算是组成整体的一部分，article 才是一个完整的整体。

3. 其实，nav aside 是特殊的 section，它们脱离环境后就没有意义了，是不完整的。但一篇文章，一篇博客就是一个完整的内容，可以用 article。其实，body 标签也是一种特殊的 article 标签。

### 其他
- video and audio
- embed
- canvas
- mark
- details
- datalist
- keygen
- output

The input element's type attribute now has the following new values:
- tel
- email
- url
- date
- time
- datetime
- datetime-local
- month
- week
- range
- number
- color
- search

**淘汰标签**
- big
- font
- dasefont
- center
- strike
- frame
- acronym >>> abbr
- applet >>> object
- dir >>> ul

## 语义化的含义和作用
语义化的含义就是，用带有正确语义的标签去标注相应的内容。

### 让机器读懂
HMTL 语义化就是让页面的内容结构化，在没有 CSS 的情况下内容也能以一种文档格式显示，便于浏览器解析渲染。
搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，标签语义化有利于 SEO

### 让人类读懂
使阅读网站源代码的人更容易将网站分块，便于阅读理解。


文章参考：
【1】[HTML5 中 div section article 的区别](https://www.qianduan.net/html5-differences-in-the-div-section-article/)
【2】[HTML 语义化](https://leohxj.gitbooks.io/front-end-database/content/html-and-css-basic/semantic-html.html)
【3】[如何理解 Web 语义化？](https://www.zhihu.com/question/20455165)
