Java内部类详解

-----------

## 概述

what why how?


    Java类中不仅可以定义变量和方法，还可以定义类，这样定义在类内部的类就被称为内部类。
   

## 内部类基础
    根据定义的方式不同，内部类分为静态内部类，成员内部类，局部内部类，匿名内部类四种。下面分别介绍着四种内部类

### 成员内部类

    　　成员内部类是最普通的内部类，它的定义为位于另一个类的内部，形如下面的形式：
···
class Circle {
class Circle {
    private double radius = 0;
 
    public Circle(double radius) {
        this.radius = radius;
        getDrawInstance().drawSahpe();   //必须先创建成员内部类的对象，再进行访问
    }
     
    private Draw getDrawInstance() {
        return new Draw();
    }
     
    class Draw {     //内部类
        public void drawSahpe() {
            System.out.println(radius);  //外部类的private成员
        }
    }
}
···

这样看起来，类Draw像是类Circle的一个成员，Circle称为外部类。

#### 特点

* 成员内部类可以无条件访问外部类的所有成员属性和成员方法（包括private成员和静态成员）。
* 在外部类中如果要访问成员内部类的成员，必须先创建一个成员内部类的对象，再通过指向这个对象的引用来访问
* 内部类可以拥有private访问权限、protected访问权限、public访问权限及包访问权限。
    
* 当成员内部类拥有和外部类同名的成员变量或者方法时，会发生隐藏现象，即默认情况下访问的是成员内部类的成员。如果要访问外部类的同名成员，需要以下面的形式进行访问：
    ···
    外部类.this.成员变量
    外部类.this.成员方法
    ···
* 成员内部类是依附外部类而存在的，也就是说，如果要创建成员内部类的对象，前提是必须存在一个外部类的对象。创建成员内部类对象的一般方式如下
···
public class Test {
    public static void main(String[] args)  {
        //第一种方式：
        Outter outter = new Outter();
        Outter.Inner inner = outter.new Inner();  //必须通过Outter对象来创建
         
        //第二种方式：
        Outter.Inner inner1 = outter.getInnerInstance();
    }
}

class Outter {
    private Inner inner = null;
    public Outter() {
         
    }
     
    public Inner getInnerInstance() {
        if(inner == null)
            inner = new Inner();
        return inner;
    }
      
    class Inner {
        public Inner() {
             
        }
    }
}
···

* 如上面的例子，如果成员内部类Inner用private修饰，则只能在外部类的内部访问，如果用public修饰，则任何地方都能访问；如果用protected修饰，则只能在同一个包下或者继承外部类的情况下访问；如果是默认访问权限，则只能在同一个包下访问。这一点和外部类有一点不一样，外部类只能被public和包访问两种权限修饰。由于成员内部类看起来像是外部类的一个成员，所以可以像类的成员一样拥有多种权限修饰。

### 局部内部类

    　　局部内部类是定义在一个方法或者一个作用域里面的类，它和成员内部类的区别在于局部内部类的访问仅限于方法内或者该作用域内。


···
class People{
    public People() {
         
    }
}
 
class Man{
    public Man(){
         
    }
     
    public People getWoman(){
        class Woman extends People{   //局部内部类
            int age =0;
        }
        return new Woman();
    }
}
···

#### 特点

* 局部内部类的访问仅限于方法内或者该作用域内。

* 局部内部类就像是方法里面的一个局部变量一样，是不能有public、protected、private以及static修饰符的。

* 只能访问块中或方法中的final变量

### 匿名内部类

    匿名内部类应该是平时我们编写代码时用得最多的，在编写事件监听的代码时使用匿名内部类不但方便，而且使代码更加容易维护。

下面这段代码为两个按钮设置监听器，这里面就使用了匿名内部类
···
scan_bt.setOnClickListener(new OnClickListener() {
             
            @Override
            public void onClick(View v) {
                // TODO Auto-generated method stub
                 
            }
        });
         
        history_bt.setOnClickListener(new OnClickListener() {
             
            @Override
            public void onClick(View v) {
                // TODO Auto-generated method stub
                 
            }
        });
···

使用匿名内部类能够在实现父类或者接口中的方法情况下同时产生一个相应的对象，但是前提是这个父类或者接口必须先存在才能这样使用。

下面这种写法也是可以的，跟上面使用匿名内部类达到效果相同。
···
private void setListener()
{
    scan_bt.setOnClickListener(new Listener1());       
    history_bt.setOnClickListener(new Listener2());
}
 
class Listener1 implements View.OnClickListener{
    @Override
    public void onClick(View v) {
    // TODO Auto-generated method stub
             
    }
}
 
class Listener2 implements View.OnClickListener{
    @Override
    public void onClick(View v) {
    // TODO Auto-generated method stub
             
    }
}
···

　这种写法虽然能达到一样的效果，但是既冗长又难以维护，所以一般使用匿名内部类的方法来编写事件监听代码。同样的，匿名内部类也是不能有访问修饰符和static修饰符的。

#### 特点
　　
* 匿名内部类是唯一一种没有构造器的类。
* 正因为其没有构造器，所以匿名内部类的使用范围非常有限，大部分匿名内部类用于接口回调。
* 匿名内部类在编译的时候由系统自动起名为Outter$1.class。
* 一般来说，匿名内部类用于继承其他类或是实现接口，并不需要增加额外的方法，只是对继承方法的实现或是重写。
* 类名没有意义，也就是不需要使用到。

### 静态内部类

    　静态内部类也是定义在另一个类里面的类，只不过在类的前面多了一个关键字static。

```
public class Test {
    public static void main(String[] args)  {
        Outter.Inner inner = new Outter.Inner();
    }
}
 
class Outter {
    public Outter() {
         
    }
     
    static class Inner {
        public Inner() {
             
        }
    }
}
```

#### 特点

* 静态内部类是不需要依赖于外部类的，这点和类的静态成员属性有点类似，并且它不能使用外部类的非static成员变量或者方法

* 静态内部类中可以定义静态或者非静态的成员

* 不再包含外部类的this指针，并且在外部类装载时初始化

* 静态内部类只能访问外部类static成员. 

* 外部类访问静态内部类的成员：static成员：类名.成员；非static成员：对象.成员



## 深入理解内部类

### 为什么成员内部类可以无条件访问外部类的成员？

编译器在进行编译的时候，会将成员内部类单独编译成一个字节码文件，编译器会默认为成员内部类添加了一个指向外部类对象的引用.
虽然我们在定义的内部类的构造器是无参构造器，编译器还是会默认添加一个参数，该参数的类型为指向外部类对象的一个引用，所以成员内部类中的Outter this&0 指针便指向了外部类对象，因此可以在成员内部类中随意访问外部类的成员。
从这里也间接说明了成员内部类是依赖于外部类的，如果没有创建外部类的对象，则无法对Outter this&0引用进行初始化赋值，也就无法创建成员内部类的对象了。

### 为什么局部内部类和匿名内部类只能访问局部final变量？

如果局部变量的值在编译期间就可以确定，则直接在匿名内部里面创建一个拷贝。如果局部变量的值无法在编译期间确定，则通过构造器传参的方式来对拷贝进行初始化赋值。

### 静态内部类有特殊的地方吗？

从前面可以知道，静态内部类是不依赖于外部类的，也就说可以在不创建外部类对象的情况下创建内部类的对象。另外，静态内部类是不持有指向外部类对象的引用的，这个读者可以自己尝试反编译class文件看一下就知道了，是没有Outter this&0引用的。

## 内部类的使用场景和好处



Java为什么要引入内部类这个概念呢？

* 每个内部类都能独立的继承一个接口的实现，所以无论外部类是否已经继承了某个(接口的)实现，对于内部类都没有影响。内部类使得多继承的解决方案变得完整，

* 方便将存在一定逻辑关系的类组织在一起，又可以对外界隐藏。

* 方便编写事件驱动程序

* 方便编写线程代码


## 常见的与内部类相关的笔试面试题

### 创建内部类对象

　　创建静态内部类对象的一般形式为：  外部类类名.内部类类名 xxx = new 外部类类名.内部类类名()

　　创建成员内部类对象的一般形式为：  外部类类名.内部类类名 xxx = 外部类对象名.new 内部类类名()

```
public class Test{
    public static void main(String[] args){
           // 初始化Bean1
           (1)
           bean1.I++;
           // 初始化Bean2
           (2)
           bean2.J++;
           //初始化Bean3
           (3)
           bean3.k++;
    }
    class Bean1{
           public int I = 0;
    }
 
    static class Bean2{
           public int J = 0;
    }
}
 
class Bean{
    class Bean3{
           public int k = 0;
    }
}

1. 
Test test = new Test();    
Test.Bean1 bean1 = test.new Bean1();   
 
2. 
Test.Bean2 b2 = new Test.Bean2();    
 
3. 
Bean bean = new Bean();     

Bean.Bean3 bean3 =  bean.new Bean3();  
```

### 作用域

```
public class Test {
    public static void main(String[] args)  {
        Outter outter = new Outter();
        outter.new Inner().print();
    }
}
 
 
class Outter
{
    private int a = 1;
    class Inner {
        private int a = 2;
        public void print() {
            int a = 3;
            System.out.println("局部变量：" + a);
            System.out.println("内部类变量：" + this.a);
            System.out.println("外部类变量：" + Outter.this.a);
        }
    }
}

3
2
1

```

###成员内部类的继承问题

　　1）成员内部类的引用方式必须为 Outter.Inner.

　　2）构造器中必须有指向外部类对象的引用，并通过这个引用调用super()。

```
class WithInner {
    class Inner{
         
    }
}
class InheritInner extends WithInner.Inner {
      
    // InheritInner() 是不能通过编译的，一定要加上形参
    InheritInner(WithInner wi) {
        wi.super(); //必须有这句调用
    }
  
    public static void main(String[] args) {
        WithInner wi = new WithInner();
        InheritInner obj = new InheritInner(wi);
    }
}
```

## 总结

* 内部类作为外部类的一个特殊的成员来看待，因此它有类成员的封闭等级：private ,protected,默认(friendly),public 它有类成员的修饰符:   static,final,abstract

* 非静态内部类nested inner class,内部类隐含有一个外部类的指针this,因此，它可以访问外部类的一切资源（当然包括private）外部类访问内部类的成员，先要取得内部类的对象,并且取决于内部类成员的封装等级。非静态内部类不能包含任何static成员.

* 静态内部类：static inner class,不再包含外部类的this指针，并且在外部类装载时初始化. 静态内部类只能访问外部类static成员. 外部类访问静态内部类的成员：static成员：类名.成员；非static成员：对象.成员

* 对于方法中的内部类或块中内部类只能访问块中或方法中的final变量。

## 参考文档

[Java内部类的定义和使用](https://www.cnblogs.com/xiao-chuan/p/6014752.html)

[Java内部类详解](http://www.cnblogs.com/dolphin0520/p/3811445.html)