# 每周总结可以写在这里
总结JavaScript中所有特殊对象的部分（JavaScript中有哪些对象是我们没有办法去模拟实现出来的？他都有什么特性？（在标准中挖信息）） 
JavaScript中几个特殊的对象： 
1.window对象： 
在全局作用域中声明的变量、函数都是window对象的属性和方法。

2.this对象： 
this对象是在运行时基于函数的执行环境绑定的：在全局函数中，this等于window；当函数被作为某个对象的方法调用时，this等于那个对象。 
特别注意：匿名函数的执行环境具有全局性，因此匿名函数中的this对象通常指向window对象。 
任何一个用作方法的函数都会得到一个额外的实际参数，即调用该函数的对象。由于方法通常是对那个对象执行某种操作，所以要表达函数作用于对象这一事实，最好采用方法的调用语法。 
虽然有区别地对待函数和方法比较有用，但实际上它们之间的差别并不大。回忆一下，函数是存储在变量中的值，而那个变量也不过是全局对象的一个属性。因此，当你调用一个函数时，实际上调用的是全局对象的一个方法。 
在这样的函数中，关键字this引用的是全局对象。所以函数和方法之间在技术上没有差别，真正的差别在于设计和目的上，方法是用来对this对象进行操作的，而函数通常会是独立的，并不需要使用this对象。
 
3.Global对象： 
1)所有在全局作用域内定义的属性和方法，都是Global对象的属性。 
2)Global对象不能直接使用，也不能用new运算符创建。 
3)Global对象在JavaScript引擎被初始化时创建，并初始化其方法和属性。 
4)浏览器把Global对象作为window对象的一部分实现了，因此，所有的全局属性和函数都是window对象的属性和方法。 
5）在控件进入任何执行上下文之前创建。没有[construct]内部方法;它不能与新操作符一起用作构造函数。没有[[Call]]内部方法;它不能作为函数调用。有一个[[Prototype]]内部槽，其值依赖于实现。除了本规范中定义的属性外，还可以具有主机定义的属性。这可能包括其值为全局对象本身的属性。
6)Global对象的属性； 
Object        构造函数Object 
Function    构造函数Function 
Date        构造函数Date 
Array        构造函数Array 
RegExp        构造函数RegExp 
Error        构造函数Error 
String        构造函数String 
Boolean        构造函数Boolean 
Number        构造函数Number 
undefined    特殊值undefined 
NaN            特殊值NaN 
7)Global对象的方法： 
encodeURI()： 
1)对整个URI进行编码。 
2)只对空格进行编码，不会对冒号、正斜杠、问号、井号等进行编码。 
3)编码后的结果：除了空格被替换成了%20之外，其它的都没有发生变化。 
4)对应的解码方法：
decodeURI() 
encodeURIComponent()： 
1)对部分URI(指除去协议、主机地址、端口后的部分)进行编码。 
2)对任何非标准字符进行编码。 
3)对应的解码方法：decodeURIComponent()         
URI编码方法说明： 
       1)有效的URI中不能包含某些字符(例如：空格等)。 
        2)用特殊的UTF-8编码替换所有无效的字符，从而让浏览器能够接受和理解。 
eval()：当解析器发现代码中调用eval()方法时，它会将传入的参数当作实际的JavaScript语句来解析。 

4.isFinite(number)对象：
等有限函数是%isFinite%固有对象。当使用一个参数调用isFinite函数时采取以下步骤:
1)让num ?当时(数值)。”
2)如果num为NaN、+∞或-∞， 则返回false。
3)否则，返回true。

5.isNaN(编号)
isNaN函数是%isNaN%固有对象。当使用-一个参数号调用isNaN函数时，需要执行以下步骤:
1)让num ?当时(数值)。”
2)如果num是NaN，则返回true。
3)否则，返回false。
ECMAScript代码测试值X是否是NaN的可靠方法是使用表单X !== X的表达式。当且仅当X是NaN时，结果才为真。

6.parseFloat(字符串)
parseFloat函数通过将字符串参数的内容解释为十进制文字来生成-一个数字值。

7.parseInt(字符串，基数)
parseInt函数根据指定的基数解释字符串参数的内容，生成-一个整数值。字符串中的前导空白将被忽略。如果基数未定义或为0，则假定基数为10，除非数字以代码单元对0x或0x开头，在这种情况下假定基数为16。如果基数是16，数字也可以选择以代码单元对0x或0x开头。parseInt函数是%parseInt%内部对象.

8.Arguments
arguments与函数的参数有关，js函数的参数与其他语言中函数的参数有所不同，js不介意传递进来多少个参数，也不在乎传进来的参数是什么数据类型，这样一听，貌似重载没得救了，因为似乎无论形参设置多少个，都没关系，调用该函数时肯定会调用他。而实参传递多少似乎函数都可以获得，这就要通过arguments啦.
可以通过 arguments.length的值来判断实参的个数。进而可以通过if语句来判断语句的执行情况。
需要注意的是，即使形参可有可无，但是，既然提供了这个功能，那么他必然和arguments之间有一定的关系，即二者之中哪一个被修改了，都会影响到对方的值，但是二者并不是指向同一个内存空间。
arguments这个对象还有一个属性：callee，该属性是一个指针，指向拥有arguments对象的函数。
