### 2.1.2 类修饰符

类修饰符是用以指明类的性质的关键字。用户在自定义类时，指定不同的修饰符，就可以让类具备不同的存取权限。一个类总能访问和调用它自己定义的成员变量和方法，但在这个类之外的其他类能否访问和调用，除与类的修饰符有关外，还与类的成员变量和方法的控制符有关。类修饰符有：abstruct\(抽象类，只是声明方法，没有具体实现方法\)、static（静态类，可以随便调用）、public（公共类，一个class文件中有且只能有一个publish的类）、protected（受保护）、private（私有，只能修饰内部类，不可以被其他class文件中的类调用）、default（默认类）、final（最终类，就是已经不可以再被继承了）。

使用的比较多的类修饰符是 public，private， abstract  三个。

访问修饰符public,private,protected,以及default的区别如下：

| 修饰符 | 当前类 | 同 包 | 子 类 | 其他包 |
| :---: | :---: | :---: | :---: | :---: |
| public | √ | √ | √ | √ |
| protected | √ | √ | √ | × |
| default | √ | √ | × | × |
| private | √ | × | × | × |

类的成员不写访问修饰时默认为default。默认对于同一个包中的其他类相当于公开（public），对于不是同一个包中的其他类相当于私有（private）。受保护（protected）对子类相当于公开，对不是同一包中的没有父子关系的类相当于私有。Java中，外部类的修饰符只能是public或默认，类的成员（包括内部类）的修饰符可以是以上四种。

注意点：

1\) public 修饰符

如果一个类被声明为 public（公共类），那么同一包中的类可自由取用此类，而别的包中的类也可通过 import 关键词来引入此类所属的包加以运用。 如果不被声明为 public，这个类就只能被同一个包中的类使用。

使用 public 修饰符的类有几个特性：

* 一个程序里只能有一个类被修饰为 public，否则编译会报错。

* 源程序文件中有用 public 修饰的类，则该源文件名必须同 public类名。

* 若程序中没有任何 public 类，则文件名可任取。

2\) 默认修饰符

如果一个类没有修饰符，就说明它具有默认的访问控制特性。默认修饰符的类只允许与类处于同一个包中的类访问和调用，而不允许被其他包中的类使用。

3\) abstract 修饰符

如果一个类被声明为 abstract，那么它是一个抽象的类，抽象类不需给出类中每个方法的完整实现。如果某个方法没有完整实现，必须要由子类的方法来覆盖，因此含有抽象型方法的类也必须声明为抽象的。 为了把一个类声明为抽象的，只需在类定义的 class 关键词前放置关键词 abstract。这些类不能直接用 new 操作符生成实例，因为它们的完整实现还没有定义。在类中不能定义抽象的构造函数或抽象的静态方法。被声明为 abstract 的抽象类往往包含有被声明为 abstract 的抽象方法，这些方法由它的非抽象子类完成实现细节。

abstract 类有下列特性：

* 一个抽象类里可以没有定义抽象方法。但只要类中有一个方法是被声明为 abstract，则该类必须为 abstract。抽象类中可以有抽象方法（只给出方法的定义）。

* 抽象类不能创建对象，只能用来派生子类。

* 抽象类不能被实例化，即不能被 new 成一个实例对象。

* 若一个子类继承一个抽象类，则子类需用覆盖的方式来实化该抽象超类中的抽象方法。若没有完全实化所有的抽象方法，则子类仍是抽象的。

4\) final 修饰符

如果一个类被声明为 final，则意味着它不能再派生出新的子类，不能作为父类被继承。因此一个类不能既被声明为 abstract 的，又被声明为 final的。 final 类是不能有子类的类，它可以避免盲目地继承，以提高系统的安全性。将一个类声明为 final 类可以提高系统安全性。使用 final 类，就意味着不能继承并覆盖其内容。用两个修饰符 public final 的意思是：此 final 类可被 import 来引用，但不能被继承。 System 类关系到系统级控制，为了安全性，故必须为 final 类，以避免被覆盖。

