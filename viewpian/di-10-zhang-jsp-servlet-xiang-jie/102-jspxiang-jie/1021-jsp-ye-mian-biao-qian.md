### 10.2.1 JSP页面标签

 一般的JSP文件有3部分组成：HTML模版，元素，注释。

#### **HTML模板**

HTML模版一般指的是开发是由美工人员提供的HTML页面，这是一个静态页面，内容为基本的HTML代码。

#### **元素**

元素分为 3 种，包括脚本元素，指令元素与动作元素。

* 脚本元素，一般包含3种形式：声明，表达式，小脚本。

1.声明，声明中一般用来声明一个变量或方法。它的代码在中，记住有个感叹号。一般声明很少使用，更不会声明方法，如果需要方法，我们一般封装在JavaBean中，需要的时候访问调用。

2.表达式，表达式最后没有分号，其效果可以用小脚本中的out对象打印代替。

```
a = <%= a %> out: <%out.print(a);%><br>
b = <%= b %> out: <%out.print(b);%><br>
10+20=<%= sum(10, 20)%> out: <%out.print(sum(10, 20));%>
```

3. 小脚本，其中编写的就是普通的java代码。包括流程控制等语句。注意：在声明与小脚本中都可以声明变量。区别：转译后的java 类不同，声明部分声明的变量属于转译后的java类是全局的；小脚本声明的变量属于\_jspService 方法，是局部的。

* 指令元素，一些影响整个JSP页面的属性设置，比如编码格式等。 JSP指令的语法为:

&lt;%@ 指令名称 属性 1="属性值 1" … 属性 n="属性值 n"%&gt;

&lt;%@ 指令名称 属性 n="属性值 n"%&gt;


