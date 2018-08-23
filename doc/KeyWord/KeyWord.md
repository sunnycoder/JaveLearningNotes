Java 关键字详解

--------

## 访问控制

### private 

    private 关键字是访问控制修饰符，可以应用于类、方法或字段（在类中声明的变量）。 只能在声明 private（内部）类、方法或字段的类中引用这些类、方法或字段。在类的外部或者对于子类而言，它们是不可见的。 所有类成员的默认访问范围都是 package 访问，也就是说，除非存在特定的访问控制修饰符，否则，可以从同一个包中的任何类访问类成员。

### protected 

    protected 关键字是可以应用于类、方法或字段（在类中声明的变量）的访问控制修饰符。可以在声明 protected 类、方法或字段的类、同一个包中的其他任何类以及任何子类（无论子类是在哪个包中声明的）中引用这些类、方法或字段。所有类成员的默认访问范围都是 package 访问，也就是说，除非存在特定的访问控制修饰符，否则，可以从同一个包中的任何类访问类成员。

### public 

    public 关键字是可以应用于类、方法或字段（在类中声明的变量）的访问控制修饰符。 可能只会在其他任何类或包中引用 public 类、方法或字段。所有类成员的默认访问范围都是 package 访问，也就是说，除非存在特定的访问控制修饰符，否则，可以从同一个包中的任何类访问类成员。

##  类、方法和变量修饰符

### abstract 

    abstract关键字可以修改类或方法。
    
- abstract类可以扩展（增加子类），但不能直接实例化。
- abstract方法不在声明它的类中实现，但必须在某个子类中重写。

有abstract方法的类本来就是抽象类，并且必须声明为abstract。

### class

    class 关键字用来声明新的 Java 类，该类是相关变量和/或方法的集合。
    类是面向对象的程序设计方法的基本构造单位。
    类通常代表某种实际实体，如几何形状或人。
    类是对象的模板。每个对象都是类的一个实例。
    要使用类，通常使用 new 操作符将类的对象实例化，然后调用类的方法来访问类的功能。

### extends 

    extends 关键字用在 class 或 interface 声明中，用于指示所声明的类或接口是其名称后跟有 extends 关键字的类或接口的子类。
    子类继承父类的所有 public 和 protected 变量和方法。 
    子类可以重写父类的任何非 final 方法。
    一个类只能扩展一个其他类。

### final

- 修饰类：表示该类不能被继承; final类中的所有成员方法都会被隐式地指定为final方法。
- 修饰方法：表示方法不能被重写；
- 修饰变量：表示变量只能一次赋值以后值不能被修改（常量）。

在使用final修饰类的时候，要注意谨慎选择，除非这个类真的在以后不会用来继承或者出于安全的考虑，尽量不要将类设计为final类。

使用final方法的原因有两个。第一个原因是把方法锁定，以防任何继承类修改它的含义；第二个原因是效率。在早期的Java实现版本中，会将final方法转为内嵌调用。但是如果方法过于庞大，可能看不到内嵌调用带来的任何性能提升。在最近的Java版本中，不需要使用final方法进行这些优化了。

因此，如果只有在想明确禁止 该方法在子类中被覆盖的情况下才将方法设置为final的。

类的private方法会隐式地被指定为final方法。

修饰变量是final用得最多的地方

对于一个final变量，如果是基本数据类型的变量，则其数值一旦在初始化之后便不能更改；如果是引用类型的变量，则在对其初始化之后便不能再让其指向另一个对象。

引用变量被final修饰之后，虽然不能再指向其他对象，但是它指向的对象的内容是可变的。

### implements

    implements 关键字在 class 声明中使用，以指示所声明的类提供了在 implements 关键字后面的名称所指定的接口中所声明的所有方法的实现。
    类必须提供在接口中所声明的所有方法的实现。
    一个类可以实现多个接口。

### interface 

    interface 关键字用来声明新的 Java 接口，接口是方法的集合。

    接口是 Java 语言的一项强大功能。任何类都可声明它实现一个或多个接口，这意味着它实现了在这些接口中所定义的所有方法。 

    实现了接口的任何类都必须提供在该接口中的所有方法的实现。
    一个类可以实现多个接口。

### native 

    native 关键字可以应用于方法，以指示该方法是用 Java 以外的语言实现的。

### new 

    new 关键字用于创建类的新实例。 

    new 关键字后面的参数必须是类名，并且类名的后面必须是一组构造方法参数（必须带括号）。 

    参数集合必须与类的构造方法的签名匹配。 

    = 左侧的变量的类型必须与要实例化的类或接口具有赋值兼容关系。

### static

    static方法就是没有this的方法。在static方法内部不能调用非静态方法，反过来是可以的。而且可以在没有创建任何对象的前提下，仅仅通过类本身来调用static方法。这实际上正是static方法的主要用途。

    　方便在没有创建对象的情况下来进行调用（方法/变量）。

#### static方法

    static方法一般称作静态方法，由于静态方法不依赖于任何对象就可以进行访问，因此对于静态方法来说，是没有this的，因为它不依附于任何对象，既然都没有对象，就谈不上this了。并且由于这个特性，在静态方法中不能访问类的非静态成员变量和非静态成员方法，因为非静态成员方法/变量都是必须依赖具体的对象才能够被调用。

    要注意的是，虽然在静态方法中不能访问非静态成员方法和非静态成员变量，但是在非静态成员方法中是可以访问静态成员方法/变量的。

    如果说想在不创建对象的情况下调用某个方法，就可以将这个方法设置为static。我们最常见的static方法就是main方法，至于为什么main方法必须是static的，现在就很清楚了。因为程序在执行main方法的时候没有创建任何对象，因此只有通过类名来访问。

#### static变量

    static变量也称作静态变量，静态变量和非静态变量的区别是：
    静态变量被所有的对象所共享，在内存中只有一个副本，它当且仅当在类初次加载时会被初始化。
    
    而非静态变量是对象所拥有的，在创建对象的时候被初始化，存在多个副本，各个对象拥有的副本互不影响。

　　static成员变量的初始化顺序按照定义的顺序进行初始化。

#### static代码块

    static关键字还有一个比较关键的作用就是 用来形成静态代码块以优化程序性能。
    static块可以置于类中的任何地方，类中可以有多个static块。在类初次被加载的时候，会按照static块的顺序来执行每个static块，并且只会执行一次。

    为什么说static块可以用来优化程序性能，是因为它的特性:只会在类加载的时候执行一次

    因此，很多时候会将一些只需要进行一次的初始化操作都放在static代码块中进行。

#### 注意事项

    静态成员变量虽然独立于对象，但是不代表不可以通过对象去访问，所有的静态方法和静态变量都可以通过对象访问（只要访问权限足够）。

    在Java中切记：static是不允许用来修饰局部变量，这是Java语法的规定

### strictfp 

    strictfp的意思是FP-strict，也就是说精确浮点的意思。在Java虚拟机进行浮点运算时，如果没有指定strictfp关键字时，Java的编译器以及运行环境在对浮点运算的表达式是采取一种近似于我行我素的行为来完成这些操作，以致于得到的结果往往无法令人满意。而一旦使用了strictfp来声明一个类、接口或者方法时，那么所声明的范围内Java的编译器以及运行环境会完全依照浮点规范IEEE-754来执行。因此如果想让浮点运算更加精确，而且不会因为不同的硬件平台所执行的结果不一致的话，那就请用关键字strictfp。

可以将一个类、接口以及方法声明为strictfp，但是不允许对接口中的方法以及构造函数声明strictfp关键字

### synchronized

    synchronized 关键字可以应用于方法或语句块，并为一次只应由一个线程执行的关键代码段提供保护。 

    synchronized 关键字可防止代码的关键代码段一次被多个线程执行。 

- 如果应用于静态方法，那么，当该方法一次由一个线程执行时，整个类将被锁定。 

- 如果应用于实例方法，那么，当该方法一次由一个线程访问时，该实例将被锁定。 

- 如果应用于对象或数组，当关联的代码块一次由一个线程执行时，对象或数组将被锁定。

### transient 

    transient 关键字可以应用于类的成员变量，以便指出该成员变量不应在包含它的类实例已序列化时被序列化。

    当一个对象被串行化的时候，transient型变量的值不包括在串行化的表示中，然而非transient型的变量是被包括进去的。

    Java的serialization提供了一种持久化对象实例的机制。当持久化对象时，可能有一个特殊的对象数据成员，我们不想用serialization机制来保存它。为了在一个特定对象的一个域上关闭serialization，可以在这个域前加上关键字transient。
     
    transient是Java语言的关键字，用来表示一个域不是该对象串行化的一部分。当一个对象被串行化的时候，transient型变量的值不包括在串行化的表示中，然而非transient型的变量是被包括进去的。

### volatile 

    volatile 关键字用于表示可以被多个线程异步修改的成员变量。 

    注意：volatile 关键字在许多 Java 虚拟机中都没有实现。 volatile 的目标用途是为了确保所有线程所看到的指定变量的值都是相同的。

    Java 语言中的 volatile 变量可以被看作是一种 “程度较轻的 synchronized”；与 synchronized 块相比，volatile 变量所需的编码较少，并且运行时开销也较少，但是它所能实现的功能也仅是 synchronized 的一部分。

## 程序控制语句

### break

    break 关键字用于提前退出 for、while 或 do 循环，或者在 switch 语句中用来结束 case 块。 

    break 总是退出最深层的 while、for、do 或 switch 语句。

### continue 

    continue 关键字用来跳转到 for、while 或 do 循环的下一个迭代。 

    continue 总是跳到最深层 while、for 或 do 语句的下一个迭代。

### return 

    return 关键字会导致方法返回到调用它的方法，从而传递与返回方法的返回类型匹配的值。 

    如果方法具有非 void 的返回类型，return 语句必须具有相同或兼容类型的参数。 

    返回值两侧的括号是可选的。

### do 

    do 关键字用于指定一个在每次迭代结束时检查其条件的循环。 

    do 循环体至少执行一次。 

    条件表达式后面必须有分号。

### while 

    while 关键字用于指定一个只要条件为真就会重复的循环。

### if 

    if 关键字指示有条件地执行代码块。条件的计算结果必须是布尔值。 

    if 语句可以有可选的 else 子句，该子句包含条件为 false 时将执行的代码。 

    包含 boolean 操作数的表达式只能包含 boolean 操作数。

### else

    else 关键字总是在 if-else 语句中与 if 关键字结合使用。else 子句是可选的，如果 if 条件为 false，则执行该子句。

### for 

    for 关键字用于指定一个在每次迭代结束前检查其条件的循环。 

    for 语句的形式为 for(initialize; condition; increment) 

    控件流进入 for 语句时，将执行一次 initialize 语句。 

    每次执行循环体之前将计算 condition 的结果。如果 condition 为 true，则执行循环体。 

    每次执行循环体之后，在计算下一个迭代的 condition 之前，将执行 increment 语句。

### instanceof 

    instanceof 关键字用来确定对象所属的类。

### switch 

    switch 语句用于基于某个表达式选择执行多个代码块中的某一个。 

    switch 条件的计算结果必须等于 byte、char、short 或 int。 

    case 块没有隐式结束点。break 语句通常在每个 case 块末尾使用，用于退出 switch 语句。 

    如果没有 break 语句，执行流将进入所有后面的 case 和/或 default 块。

### case 

    case 用来标记 switch 语句中的每个分支。 

    case 块没有隐式结束点。break 语句通常在每个 case 块末尾使用，用于退出 switch 语句。 

    如果没有 break 语句，执行流将进入所有后面的 case 和/或 default 块。

### default 

    default 关键字用来标记 switch 语句中的默认分支。 

    default 块没有隐式结束点。break 语句通常在每个 case 或 default 块的末尾使用，以便在完成块时退出 switch 语句。 

    如果没有 default 语句，其参数与任何 case 块都不匹配的 switch 语句将不执行任何操作。

##  错误处理

### try 

    try 关键字用于包含可能引发异常的语句块。 

    每个 try 块都必须至少有一个 catch 或 finally 子句。 

    如果某个特定异常类未被任何 catch 子句处理，该异常将沿着调用栈递归地传播到下一个封闭 try 块。如果任何封闭 try 块都未捕获到异常，Java 解释器将退出，并显示错误消息和堆栈跟踪信息。

### catch 

    catch 关键字用来在 try-catch 或 try-catch-finally 语句中定义异常处理块。 

    开始和结束标记 { 和 } 是 catch 子句语法的一部分，即使该子句只包含一个语句，也不能省略这两个标记。 

    每个 try 块都必须至少有一个 catch 或 finally 子句。 

    如果某个特定异常类未被任何 catch 子句处理，该异常将沿着调用栈递归地传播到下一个封闭 try 块。如果任何封闭 try 块都未捕获到异常，Java 解释器将退出，并显示错误消息和堆栈跟踪信息。

### throw  

    throw 关键字用于引发异常。 

    throw 语句将 java.lang.Throwable 作为参数。Throwable 在调用栈中向上传播，直到被适当的 catch 块捕获。 

    引发非 RuntimeException 异常的任何方法还必须在方法声明中使用 throws 修饰符来声明它引发的异常。

### throws

    throws 关键字可以应用于方法，以便指出方法引发了特定类型的异常。 

    throws 关键字将逗号分隔的 java.lang.Throwables 列表作为参数。 

    引发非 RuntimeException 异常的任何方法还必须在方法声明中使用 throws 修饰符来声明它引发的异常。 

    要在 try-catch 块中包含带 throws 子句的方法的调用，必须提供该方法的调用者。

## 包相关

### import 

    import 关键字使一个包中的一个或所有类在当前 Java 源文件中可见。可以不使用完全限定的类名来引用导入的类。 

当多个包包含同名的类时，许多 Java 程序员只使用特定的 import 语句（没有“*”）来避免不确定性。

### package 

    package 关键字指定在 Java 源文件中声明的类所驻留的 Java 包。 

    package 语句（如果出现）必须是 Java 源文件中的第一个非注释性文本。 

    例:java.lang.Object。 

    如果 Java 源文件不包含 package 语句，在该文件中定义的类将位于“默认包”中。请注意，不能从非默认包中的类引用默认包中的类。

## 基本类型

### boolean 

    boolean 是 Java 原始类型。boolean 变量的值可以是 true 或 false。 

    boolean 变量只能以 true 或 false 作为值。boolean 不能与数字类型相互转换。 

    包含 boolean 操作数的表达式只能包含 boolean 操作数。 

    Boolean 类是 boolean 原始类型的包装对象类。

### byte 

    byte 是 Java 原始类型。byte 可存储在 [-128, 127] 范围以内的整数值。 

    Byte 类是 byte 原始类型的包装对象类。它定义代表此类型的值的范围的 MIN_VALUE 和 MAX_VALUE 常量。 

    Java 中的所有整数值都是 32 位的 int 值，除非值后面有 l 或 L（如 235L），这表示该值应解释为 long。

### char

    char 是 Java 原始类型。char 变量可以存储一个 Unicode 字符。 

    可以使用下列 char 常量：\b - 空格, \f - 换页, \n - 换行, \r - 回车, \t - 水平制表符, \' - 单引号, \" - 双引号, \\ - 反斜杠, \xxx - 采用 xxx 编码的 Latin-1 字符。\x 和 \xx 均为合法形式，但可能引起混淆。 \uxxxx - 采用十六进制编码 xxxx 的 Unicode 字符。 

    Character 类包含一些可用来处理 char 变量的 static 方法，这些方法包括 isDigit()、isLetter()、isWhitespace() 和 toUpperCase()。 

    char 值没有符号。

### double

    double 是 Java 原始类型。double 变量可以存储双精度浮点值。 

    由于浮点数据类型是实际数值的近似值，因此，一般不要对浮点数值进行是否相等的比较。 

    Java 浮点数值可代表无穷大和 NaN（非数值）。
    
    Double 包装对象类用来定义常量 MIN_VALUE、MAX_VALUE、NEGATIVE_INFINITY、POSITIVE_INFINITY 和 NaN。

### float 

    float 是 Java 原始类型。float 变量可以存储单精度浮点值。 

    使用此关键字时应遵循下列规则： 

    Java 中的浮点文字始终默认为双精度。
    
    要指定单精度文字值，应在数值后加上 f 或 F，如 0.01f。 

    由于浮点数据类型是实际数值的近似值，因此，一般不要对浮点数值进行是否相等的比较。 

    Java 浮点数值可代表无穷大和 NaN（非数值）。
    
    Float 包装对象类用来定义常量 MIN_VALUE、MAX_VALUE、NEGATIVE_INFINITY、POSITIVE_INFINITY 和 NaN。

### int

    int 是 Java 原始类型。int 变量可以存储 32 位的整数值。 

    Integer 类是 int 原始类型的包装对象类。它定义代表此类型的值的范围的 MIN_VALUE 和 MAX_VALUE 常量。 

    Java 中的所有整数值都是 32 位的 int 值，除非值后面有 l 或 L（如 235L），这表示该值应解释为 long。

### long

    long 是 Java 原始类型。long 变量可以存储 64 位的带符号整数。 

    Long 类是 long 原始类型的包装对象类。它定义代表此类型的值的范围的 MIN_VALUE 和 MAX_VALUE 常量。 

    Java 中的所有整数值都是 32 位的 int 值，除非值后面有 l 或 L（如 235L），这表示该值应解释为 long。

### short

    short 是 Java 原始类型。short 变量可以存储 16 位带符号的整数。 

    Short 类是 short 原始类型的包装对象类。它定义代表此类型的值的范围的 MIN_VALUE 和 MAX_VALUE 常量。 

    Java 中的所有整数值都是 32 位的 int 值，除非值后面有 l 或 L（如 235L），这表示该值应解释为 long。

### null 

    null 是 Java 的保留字，表示无值。 

    将 null 赋给非原始变量相当于释放该变量先前所引用的对象。 

    不能将 null 赋给原始类型（byte、short、int、long、char、float、double、boolean）变量。

### true

    true 关键字表示 boolean 变量的两个合法值中的一个。

### false

    false 关键字代表 boolean 变量的两个合法值之一。

## 变量引用

### super 

    super 关键字用于引用使用该关键字的类的超类。 

    作为独立语句出现的 super 表示调用超类的构造方法。 

    super.<methodName>() 表示调用超类的方法。
    
    只有在如下情况中才需要采用这种用法：要调用在该类中被重写的方法，以便指定应当调用在超类中的该方法。

### this

    this 关键字用于引用当前实例。 

    当引用可能不明确时，可以使用 this 关键字来引用当前的实例。

### void

    void 关键字表示 null 类型。 

    void 可以用作方法的返回类型，以指示该方法不返回值。

##  保留字

### goto 

    goto 保留关键字，但无任何作用。结构化程序设计完全不需要 goto 语句即可完成各种流程，而 goto 语句的使用往往会使程序的可读性降低，所以 Java 不允许 goto 跳转。

### const 

    const 保留字，是一个类型修饰符，使用const声明的对象不能更新。与final某些类似。

### native 

    　Java不是完美的，Java的不足除了体现在运行速度上要比传统的C++慢许多之外，Java无法直接访问到操作系统底层（如系统硬件等)，为此Java使用native方法来扩展Java程序的功能。 

　　可以将native方法比作Java程序同Ｃ程序的接口，其实现步骤： 

　　１、在Java中声明native()方法，然后编译； 

　　２、用javah产生一个.h文件； 

　　３、写一个.cpp文件实现native导出方法，其中需要包含第二步产生的.h文件（注意其中又包含了JDK带的jni.h文件）； 

　　４、将第三步的.cpp文件编译成动态链接库文件； 

　　５、在Java中用System.loadLibrary()方法加载第四步产生的动态链接库文件，这个native()方法就可以在Java中被访问了。  

## 常见问题

### final、finally、finalize的区别

1、final修饰符（关键字）。被final修饰的类，就意味着不能再派生出新的子类，不能作为父类而被子类继承。因此一个类不能既被abstract声明，又被final声明。将变量或方法声明为final，可以保证他们在使用的过程中不被修改。被声明为final的变量必须在声明时给出变量的初始值，而在以后的引用中只能读取。被final声明的方法也同样只能使用，即不能方法重写。

2.finally是在异常处理时提供finally块来执行任何清除操作。不管有没有异常被抛出、捕获，finally块都会被执行。try块中的内容是在无异常时执行到结束。catch块中的内容，是在try块内容发生catch所声明的异常时，跳转到catch块中执行。finally块则是无论异常是否发生，都会执行finally块的内容，所以在代码逻辑中有需要无论发生什么都必须执行的代码，就可以放在finally块中。

3、finalize是方法名。java技术允许使用finalize（）方法在垃圾收集器将对象从内存中清除出去之前做必要的清理工作。这个方法是由垃圾收集器在确定这个对象没有被引用时对这个对象调用的。它是在object类中定义的，因此所有的类都继承了它。子类覆盖finalize（）方法以整理系统资源或者被执行其他清理工作。finalize（）方法是在垃圾收集器删除对象之前对这个对象调用的。 

### 若try中有return语句,finally会执行吗？在return之前还是之后呢？

    会执行，在方法return动作之前，return语句执行之后，若finally中再有return语句，则此方法以finally的return作为最终返回，若finally中无return语句，则此方法以try的return作为最终返回。

## 参考文档

[Java关键字及其作用](https://www.cnblogs.com/AloneZ/p/java1.html)

[浅析Java中的final关键字](http://www.cnblogs.com/dolphin0520/p/3736238.html)

[Java中的static关键字解析](https://www.cnblogs.com/dolphin0520/p/3799052.html)