---
date: 2022-06-01
category:
  - Java
  - 语法基础
tag:
  - Java
  - 基础
---
# 基础语法

### 基础语法

#### 特点
1. 面向对象：封装，继承，多态
2. 可移植(便携)：在不同系统上运行
3. 并发性：你可以在其中执行许多语句，而不必一次执行它
4. 一次编写多次执行：可在多个系统平台上（JVM虚拟机）运行
#### 标识符
命名规则：英文字母，数字，下划线，美元符号$，数字不能在首位。
> [!attention] 注意
> 
关键字不能做为变量名或包名作为标识符。

#### 常用标识符
- 包名：全部小写   `com.boot`
- 类或接口：每个单词首字母大写   `StudentName`
- 方法/变量：单词首字母小写   `studentAge`
- 常量：全部大写,每个并用下划线_隔开   `STUDENT_MAX_AGE`
- 文件名：全部小写
#### 修饰符
> [!todo]
> - [ ] 插入修饰符相关知识点

#### 变量
> [!abstract] 概念
> 内存中的一个存储空间，用于存储临时变量的数据

**作用域**：从变量定义的位置开始，到该变量所在的那对大括号结束

- 局部变量(方法变量)
  - ①随着方法和代码块的执行和结束变量随之创建和销毁
  - ②变量只在方法中生效。
  - ③访问修饰符不能用于局部变量
  - ④局部变量是在栈上分配的
  - ⑥局部变量没有默认值，局部变量被声明后，必须经过初始化，才可以使用。

- 静态变量(类变量)
  - ①常常被static修饰的变量成为静态变量，由于不属于任何实例对象，属于类的，在内存中只存在一份
  - ②在类的加载过程中，JVM只为静态变量分配一次内存空间
  - ③静态变量所属于类，静态变量存在于方法区中

- 实例变量(成员变量)
  - ①每次创建对象，都会为每个对象分配成员变量内存空间
  - ②实例变量是属于实例对象的，在内存中，每创建一个实例就会产生一个实例变量
  - ③成员变量随着对象创建而存在，成员变量存在于堆内存中。随着对象被回收而消失
####  常量
> [!abstract] 概念
> 被final修饰的变量，在程序执行的过程中值不能发生改变

```java
public final int a = 12 ;
```

- 字面值常量
  - 字符串常量：用双引号括起来的内容，举例："hello"，"world"
  - 整数常量：所有整数，举例：12，23
  - 小数常量：所有小数，举例：12.34，56.78
  - 字符常量：用单引号括起来的内容，举例：‘a’,’A’,’0’
  - 布尔常量，常用来表示是否，举例：true，false
  - 空常量，举例：null
- 自定义常量
  - 二进制，八进制，十进制，十六进制（逢X进一位）
#### 常用类型
**基本数据类型**
-  整数类型：byte, short, int, long
- 小数类型：Float,Double
- 字符型：char
- 布尔型：boolean
> [!hint] 备注
> Java基本数据类型没有String类型，所有整型都是有符号数，没有unsigned（无符号）类型。基本数据类型的大小是固定的，与平台是32位还是64位无关

**类型转换**
隐式类型转换（小转大）：byte，short，char—>int—>long—>float—>double
强制类型转换（大转小）：精度下降 
**引用数据类型**
- 类Class
- 接口Interface
- 数组Array
### 面向对象

#### 三大特性
**封装**
> [!tldr]
> 用户无需关心对象内部的细节，但可以通过对象对外提供的接口来访问该对象。使用时，通过声明私有变量通过set和get方法获取或给变量赋值

- 减少耦合
- 减轻维护的负担
- 提高软件的可重用性
- 降低了构建大型系统的风险
**继承**
继承应该遵循里氏替换原则，子类对象必须能够替换掉所有父类对象。
**多态**
> [!note]
> 多态分为编译时多态和运行时多态：编译时多态主要指方法的重载。运行时多态指程序中定义的对象引用所指向的具体类型在运行期间才确定
#### 接口
- 变量：常量：默认修饰 public static final   
- 方法：都是抽象的，默认修饰 public abstract   
- 关系
  - 类与类：只能单继承，可以多重继承。
  - 类与接口：实现关系。类可以多实现接口。
  - 接口与接口： 是继承关系。接口可以多继承接口。
**接口和抽象方法的区别**
- 一个类只能继承一个抽象类，而一个类却可以实现多个接口。
- 接口的设计目的，是对类的行为进行约束；而抽象类的设计目的，是为了代码复用。
- 抽象类只能被单继承 ，接口可以多实现,接口的出现避免了多继承的局限性。
- 抽象类中的数据特点
  - 成员变量：可以是变量，也可以是常量，可以有各种类型
  - 成员方法：可以是抽象方法，也可以有非抽象方法
  - 构造方法：有构造方法，本身不能实例化，供其子类实例化。
- 接口的数据特点
  - 成员变量：只有常量。默认修饰 public static final
  - 成员方法：都是且只有抽象方法。都有默认修饰 public abstract
  - 构造方法：没有构造方法
### 类
> [!important] 规范
> 以英文字母开头，后接字母，数字和下划线的组合
> 每个单词首字母大写
> 

#### 抽象类

使用：不能和哪些关键词共存？①private:私有内容子类继承不到，所以，不能重写。但是abstract修饰的方法，要求被重写。两者冲突。②final：final修饰的方法不能被重写。③static:假如一个抽象方法能通过static修饰，那么这个方法，就可以直接通过类名调用。而抽象方法是没有方法体的，这样的调用无意义。所以，不能用static修饰。

#### 枚举类

https://www.cnblogs.com/jingmoxukong/p/6098351.html

https://blog.csdn.net/hellojoy/article/details/79883671

#### 内部类

定义：将一个类的定义放在另外一个类的定义内部，这就是内部类。内部类本身就是类的一个属性，与其他属性定义方式一致。

内部类的分类：**成员内部类、局部内部类、匿名内部类和静态内部类**。

##### 静态内部类

定义在类内部的静态类，就是静态内部类。

```java
public class Outer {
    private static int radius = 1;
    static class StaticInner {
        public void visit() {
            System.out.println("visit outer static variable:" + radius);
        }
    }
}
```

静态内部类可以访问外部类所有的静态变量，而不可访问外部类的非静态变量；静态内部类的创建方式，new 外部类.静态内部类()

```java
Outer.StaticInner inner = new Outer.StaticInner();
inner.visit();
```

##### **成员内部类**

定义在类内部，成员位置上的非静态类，就是成员内部类。

```java
public class Outer {
    private static  int radius = 1;
    private int count =2;
    
     class Inner {
        public void visit() {
            System.out.println("visit outer static variable:" + radius);
            System.out.println("visit outer variable:" + count);
        }
    }
}
```

成员内部类可以访问外部类所有的变量和方法，包括静态和非静态，私有和公有。成员内部类依赖于外部类的实例，外部类实例.new 内部类()

非静态内部类不能有静态成员变量和静态代码块和静态方法，

```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
inner.visit();
```

##### **局部内部类**

定义在方法中的内部类，就是局部内部类。

```java
public class Outer {
    private  int out_a = 1;
    private static int STATIC_b = 2;
    public void testFunctionClass(){
        int inner_c =3;
        class Inner {
            private void fun(){
                System.out.println(out_a);
                System.out.println(STATIC_b);
                System.out.println(inner_c);
            }
        }
        Inner inner = new Inner();
        inner.fun();
    }
    public static void testStaticFunctionClass(){
        int d =3;
        class Inner {
            private void fun(){
                // System.out.println(out_a); 编译错误，定义在静态方法中的局部类不可以访问外部类的实例变量
                System.out.println(STATIC_b);
                System.out.println(d);
            }
        }
        Inner inner = new Inner();
        inner.fun();
    }
}
```

定义在实例方法中的局部类可以访问外部类的所有变量和方法，定义在静态方法中的局部类只能访问外部类的静态变量和方法（不能读取外部的非静态变量）。局部内部类的创建方式，在对应方法内，new 内部类()

```java
public static void testStaticFunctionClass(){
    class Inner {
    }
    Inner inner = new Inner();
}
```

##### **匿名内部类**

匿名内部类就是没有名字的内部类，常在对方法只调用一次时使用。

```java
public class Outer {
    private void test(final int i) {
        new Service() {
            public void method() {
                for (int j = 0; j < i; j++) {
                    System.out.println("匿名内部类" );
                }
            }
        }.method();
    }
 }
 //匿名内部类必须继承或实现一个已有的接口
 interface Service{
    void method();
}
```

除了没有名字，匿名内部类还有以下特点：

- 匿名内部类必须继承一个抽象类或者实现一个接口。
- 匿名内部类不能定义任何静态成员和静态方法。

- 当所在的方法的形参需要被匿名内部类使用时，必须声明为 final。
- 匿名内部类不能是抽象的，它必须要实现继承的类或者实现的接口的所有抽象方法。

**匿名内部类创建方式**

```java
new 类/接口{
  //匿名内部类实现部分
}
```

**内部类的优点**

- 一个内部类对象可以访问创建它的外部类对象的内容，包括私有数据！
- 内部类不为同一包的其他类所见，具有很好的封装性；

- 内部类有效实现了“多重继承”，优化 java 单继承的缺陷。
- 匿名内部类可以很方便的定义回调。

#### **内部类的应用场景**

- 一些多算法场合
- 解决一些非面向对象的语句块。

- 适当使用内部类，使得代码更加灵活和富有扩展性。
- 当某个类除了它的外部类，不再被其他的类使用时。

**局部内部类和匿名内部类访问局部变量的时候，为什么变量必须要加上final？**

```java
public class Outer {
    void outMethod(){
        final int a =10;
        class Inner {
            void innerMethod(){
                System.out.println(a);
            }
        }
    }
}
```

是因为生命周期不一致， 局部变量直接存储在栈中，当方法执行结束后，非final的局部变量就被销毁。而局部内部类对局部变量的引用依然存在，如果局部内部类要调用局部变量时，就会出错。加了final，可以确保局部内部类使用的变量与外层的局部变量区分开，解决了这个问题。

```java
public class Outer {
    private int age = 12;
    class Inner {
        private int age = 13;
        public void print() {
            int age = 14;
            System.out.println("局部变量：" + age);
            System.out.println("内部类变量：" + this.age);
            System.out.println("外部类变量：" + Outer.this.age);
        }
    }
    public static void main(String[] args) {
        Outer.Inner in = new Outer().new Inner();
        in.print();
    }
}
```

运行结果：

```plain
局部变量：14
内部类变量：13
外部类变量：12
```

### 方法

> 作用：提高使用复用性，有时称为函数。

```java
修饰符 返回值类型 方法名(参数类型 参数名1，参数类型 参数名2…) {
     函数体;
     return 返回值;
 }
```

- ①方法不调用不执行。
- ②方法与方法是平级关系，不能嵌套定义。
- ③方法定义的时候参数之间用逗号隔开。
- ④方法调用的时候不用再传递数据类型。
- ⑤如果方法有明确的返回值，一定要有return带回一个值。

**方法重载**

> 多个相同方法名，但参数列表不同(参数类型和参数个数不同)称为方法重载。返回值和参数顺序无关。

**方法重写**

> 子类继承自父类的相同方法，在子类中重写该方法——相同参数，不同实现。

重写规则

1. 参数列表必须完全与被重写的方法相同。
2. 返回的类型必须与被重写的方法的返回类型相同

3. 访问修饰符的限制一定要大于被重写方法的访问修饰符（public>protected>default>private）
4. 重写方法一定不能抛出新的检查异常或者比被重写方法申明更加宽泛的检查型异常

#### 抽象方法

#### 静态方法

在外部调用静态方法时，可以使用"类名.方法名"的方式，也可以使用"对象名.方法名"的方式。而实例方法只有后面这种方式。调用静态方法可以无需创建对象。静态方法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态方法），而不允许访问实例成员变量和实例方法。

### 泛型

引入泛型的意义：

- 1）适用于多种数据类型执行相同的代码（代码复用）

```java
private static int add(int a, int b) {
    System.out.println(a + "+" + b + "=" + (a + b));
    return a + b;
}
private static float add(float a, float b) {
    System.out.println(a + "+" + b + "=" + (a + b));
    return a + b;
}
//改进：使用泛型
private static <T extends Number> double add(T a, T b) {
    System.out.println(a + "+" + b + "=" + (a.doubleValue() + b.doubleValue()));
    return a.doubleValue() + b.doubleValue();
}
```

- 2）泛型中的类型在使用时指定，不需要强制类型转换（类型安全，编译器会检查类型）

```java
List<String> list = new ArrayList<String>();
// list中只能放String, 不能放其它类型的元素
```

泛型的基本使用

- 泛型类、泛型接口、泛型方法

泛型上下限

```java
<?> 无限制通配符
<? extends E> extends 关键字声明了类型的上界，表示参数化的类型可能是所指定的类型，或者是此类型的子类
class Info<T extends Number>{    // 此处泛型只能是数字类型
<? super E> super 关键字声明了类型的下界，表示参数化的类型可能是指定的类型，或者是此类型的父类
fun(Info<? super String> temp){    // 只能接收String或Object类型的泛型，String类的父类只有Object类

// 使用原则《Effictive Java》
// 为了获得最大限度的灵活性，要在表示 生产者或者消费者 的输入参数上使用通配符，使用的规则就是：生产者有上限、消费者有下限
1. 如果参数化类型表示一个 T 的生产者，使用 < ? extends T>;
2. 如果它表示一个 T 的消费者，就使用 < ? super T>；
3. 如果既是生产又是消费，那使用通配符就没什么意义了，因为你需要的是精确的参数类型。
```

泛型数组

```java
List<String>[] list11 = new ArrayList<String>[10]; //编译错误，非法创建 
List<String>[] list12 = new ArrayList<?>[10]; //编译错误，需要强转类型 
List<String>[] list13 = (List<String>[]) new ArrayList<?>[10]; //OK，但是会有警告 
List<?>[] list14 = new ArrayList<String>[10]; //编译错误，非法创建 
List<?>[] list15 = new ArrayList<?>[10]; //OK 
List<String>[] list6 = new ArrayList[10]; //OK，但是会有警告
```



