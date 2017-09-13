## 12.2 CSS 高级语法

你可以对选择器进行分组，这样，被分组的选择器就可以分享相同的

h1,h2,h3,h4,h5,h6 {

color: green;

}

根据 CSS 规则，子元素可以从父元素继承属性， 但是它并不总是按此

body {

font-family: Verdana, sans-serif;

}

根据上面这条规则，站点的 body 元素将使用 Verdana 字体（假如访

继承，它不仅忽略继承，而且也忽略应用于 body 元素的规则。 IE/Windows

幸运地是，你可以通过使用我们称为"Be Kind to Netscape 4"的冗余法

body {

font-family: Verdana, sans-serif;

}

p, td, ul, ol, li, dl, dt, dd {

font-family: Verdana, sans-serif;

}

4.0 浏览器无法理解继承，不过他们可以理解组选择器。这么做虽然

body {

font-family: Verdana, sans-serif;

}

td, ul, ol, ul, li, dl, dt, dd {

font-family: Verdana, sans-serif;

}

 

p

font-family: Times, "Times New Roman", serif;

}

CSS 派生选择器， 通过依据元素在其位置的上下文关 系来定义样 式，

派生选择器允许你根据文档的上下文关系来确定某个标签的样式。通

li strong {

font-style: italic;

font-weight: normal;

}

&lt;p&gt;&lt;strong&gt;粗体字不是斜体，因为我不在列表当中&lt;/strong&gt;&lt;/p&gt;

&lt;ol&gt;

&lt;li&gt;&lt;strong&gt;斜体字。 因为 strong 元素位于 li 元素内&lt;/strong&gt;&lt;/li&gt;

&lt;li&gt;我是正常的字体。 &lt;/li&gt;

&lt;/ol&gt;

在上面的例子中，只有 li 元素中的 strong 元素的样式为斜体字，无需

上面所介绍的都是直接用标签作为选择器，实际上还可以用 id、 class

☞ id 选择器， id 选择器可以为标有特定 id 的 HTML 元素指定特定的

\#red {color:red;}

\#green {color:green;}

下面的 HTML 代码中， id 属性为 red 的 p 元素显示为红色，而 id 属性

&lt;p id="red"&gt;这个段落是红色。 &lt;/p&gt;

&lt;p id="green"&gt;这个段落是绿色。 &lt;/p&gt;

在现代布局中， id 选择器常常用于建立派生选择器，如下：

\#sidebar p {

font-style: italic;

text-align: right;

margin-top: 0.5em;

}

上面的样式只会应用于出现在 id 是 sidebar 的元素内的段落。这个

id 选择器即使不被用来创建派生选择器，它也可以独立发挥作用：

\#sidebar {

border: 1px dotted \#000;

padding: 10px;

}

根据这条规则， id 为 sidebar 的元素将拥有一个像素宽的黑色点状边框，

同时其周围会有 10 个像素宽的内边距（ padding，内部空白）。老版本的

Windows/IE 浏览器可能会忽略这条规则，除非你特别地定义这个选择器所

属的元素，如下表示 id 为 sidebar 的 div 元素：

div\#sidebar {

border: 1px dotted \#000;

padding: 10px;

}

☞ CSS 类选择器， 在 CSS 中，类选择器以一个点号显示，如下

.center{text-align: center}

在上面的例子中，所有拥有 center 类的 HTML 元素均为居中。在下面的

HTML代码中， h1 和 p 元素都有 center 类。这意味着两者都将遵守 ".center"

选择器中的规则。

&lt;h1 class="center"&gt;This heading will be center-aligned&lt;/h1&gt;

&lt;p class="center"&gt;This paragraph will also be center-aligned.&lt;/p&gt;

注意：类名的第一个字符不能使用数字，它无法在 Mozilla 或 F irefox 中

起作用。

和 id 一样， class 也可被用作派生选择器，如下：

.fancy td {

color: \#f60;

background: \#666;

}

在上面这个例子中，类名为 fancy 的更大的元素内部的表格单元都会

以灰色背景显示橙色文字。（名为 fancy 的更大的元素可能是一个表格或者

一个 div）

元素也可以基于它们的类而被选择，如下：

td.fancy {

color: \#f60;

background: \#666;

}

在上面的例子中，类名为 fancy的表格单元将是带有灰色背景的橙色。

&lt;td class="fancy"&gt;

你可以将类 fancy 分配给任何一个表格元素任意多的次数。那些以

fancy 标注的单元格都会是带有灰色背景的橙色， 那些没有被分配名为

fancy 的类的单元格不会受这条规则的影响。这都是由于我们书写这条规则

的方式，这个效果被限制于被标注为 fancy 的表格单元（即使用 td 元素来

选择 fancy 类）。

☞ CSS 属性选择器， 可以为拥有指定属性的 HTML 元素设置样式，

而不仅限于 class 和 id 属性。 Internet Explorer 7（以及更高版本）在规定

了!DOCTYPE 的情况下支持属性选择器。 IE6 及更低的版本不支持属性选

择器。下面的例子为带有 title 属性的所有元素设置样式：

\[title\]{

color:red;

}

另外还可以为属性指定值，称为属性和值选择器。 下面的例子为

title="W3School"的所有元素设置样式：

\[title=W3School\]{

border:5px solid blue;

}

属性和值选择器中还可以指定多元素选择， 下面的例子为包含指定值

的 title 属性的所有元素设置样式。 该例适用于由空格分隔的属性值：

\[title~=hello\] { color:red; }

如下， 由空格分隔后第一种含有 hello，可以应用样式，第二种不行：

&lt;h2 title="hello world"&gt;可以应用样式&lt;/h2&gt;

&lt;h2 title="world"&gt;无法应用样式&lt;/h2&gt;

下面的例子为带有包含指定值的 lang 属性的所有元素设置样式。 该例

适用于由连字符分隔的属性值：

\[lang\|=en\] { color:red; }

如下， 由连字符分隔后第一种含有 en，可以应用样式，第二种不行：

&lt;p lang="en-us"&gt;可以应用样式&lt;/p&gt;

&lt;p lang="zh"&gt;无法应用样式&lt;/p&gt;

属性选择器在为不带有 class 或 id 的表单设置样式时特别有用，如下：

input\[type="text"\]{

width:150px;

display:block;

margin-bottom:10px;

background-color:yellow;

font-family: Verdana, Arial;

}

input\[type="button"\]{

width:120px;

margin-left:35px;

display:block;

font-family: Verdana, Arial;

}
