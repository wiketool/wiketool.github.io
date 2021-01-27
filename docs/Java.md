# Java类

### 标准类

- 标准类由私有变量，无参构造，全参构造，私有变量的getter和setter，以及方法组成

```java
class standardClass{
    private name;
    
    public standardClass(){
    }
    
    public standardClass(String name){
        this.name = name;
    }
    
    public void setName(String name){
        this.name = name;
    }
    
    public String getName(){
        return this.name
    }
    
    public void mathod(){
        
    }
}
```

------

### 重载

> Overloading allows different methods to have the same name, but different signatures(方法) where the signature can differ by the number of input parameters(参数) or type of input parameters or both. Overloading is related to compile-time (or static) polymorphism(动态).

- 方法重载：参数列表的个数，参数列表的数据类型

  
 ```java
  public int sum(int x, int y)
  {
      return (x + y);
  }
  
//这是错误的，传入参数名称的不同不能用来进行方法的重载
//public int sum(int a,int c){
//    return (a + c);
//}

  public int sum(int x, int y, int z)
  {
      return (x + y + z);
  }
  
  public double sum(double x, double y)
  {
      return (x + y);
  }
  
 ```

- Java并不能单独的通过返回值类型的不同进行方法的重载，但当参数列表中个数或数据类型不同时，返回值类型可以不一样，变相的实现返回值数据类型不同时的方法重载

```java
public int method(int a){
    return a;
}

//这种是错误的，不能单单通过返回值的不同实现方法的重载
//public char method(int a){
//    return 'A';
//}

public char method(int a,char b){
    return b;
}
```

- Java可以对static方法进行重载 (但不可以**单独**通过有无static关键字进行方法重载)

```java
class Test{
	public static int method(int a){
        return a;
    }
    
    public static int method(int a,double c){
        return a;
    }
    
    //下面编译时会报错，不可以在参数列表个数及数据类型相同时仅仅通过有无static关键字进行方法的重载
    public int method (int a){
        return a;
    }
}
```

------

### 重构(Override)

> 重构是每一种OOP语言的特性之一，Java多态性的其中一种体现

- 重构的方法体编译时参考调用此方法的对象，即谁调用就用哪个方法

```java
class Parent{
    public void show(){
        System.out.println("Parents");
    }
}

class son extends Parent {
    @override
    public void show(){
        System.out.println("Son");
    }
}

public class Main{
    public static void main(){
        Parent obj1 = new Parent();
        Parent obj2 = new Child();
        Parent obj1 = new Parent(); // 调用父类中的方法
        obj2.show(); //调用子类中的方法
    }
}
```

- **Instance variable override（variable Hide）**
  
  [dozen]:https://dzone.com/articles/why-instance-variable-of-super-class-is-not-overri "参考"
  
  - 成员变量（member field）并不会像类方法一样被覆盖（override），**overriding**只作用于方法。当子类中的实例变量与父类中的实例变量拥有相同的名字时（即使数据类型不同），则这个实例变量就会从obj这个对象的引用类型中查找（当父类中没有时也不会前往子类查找）
  ```java
  //如下有这样一个java文件
  class superClass{
      int num = 10;
  }
  class subClass extends superClass{
      int num = 20;
  }
  public class demo{
      public static void main(){
          superClass obj = new subclass();
          System.out.println(obj.num) //  10
      }
  }
  ```
  - 当子类和父类中有两个相同名称的变量时，子类变量会隐藏父类变量，子类中的方法直接调用变量时会使用子类中的变量，如果想让方法中使用父类的变量必须加上```super```关键词；
  - 如果我们在父类和子类外面访问时，实例变量从引用类型中选择。但我们可以通过```((subclass)test).num```来访问子类中的实例变量
  ```java
    class superClass{
      int num = 10;
      public void print(){
          System.out.println(num) //  10
      }
    }
    class subClass extends superClass{
      int num = 20;
      @override
      public void print(){
          System.out.println(num) //  20
      }
    }
    public class demo{
      public static void main(){
          superClass obj = new subclass();
          obj.print(); // 20
          System.out.println(obj.num) //  10
          System.out.println(((subclass)obj).num) //  20
      }
    }
  ```
  
- 为什么这么设计？（不override实例变量）

  设想一下，在父类中有一个返回```int```值的```getX()```方法以及一个实例变量```int x```，现在有一个子类继承父类且定义了```object x```,若子类同时override父类的实例变量，会破坏方法的执行
  
- 对运行时多态性的一点点补充

  ```java
  superClass obj = new subclass();
  ```

  任何对象的声明和实例化都有两个部分：引用类型和创建的对象的类型

  - 引用类型确定的是可以用来调用的方法
  - 创建的对象的类型确定执行的方法

  > Each object reference can be used to invoke methods and the methods which can be invoked is decided based on the reference type. And this is decided during the compile time. But the implementation to be invoked is decided based on the type of the object created(https://dzone.com/articles/runtime-polymorphism-java)

# 关键字

- final

  - 修饰类

    当 ```final```修饰一个类时，该类不可以再有子类，同理无抽象方法

  - 修饰方法

    ```final```修饰一个方法时，该方法在子类中无法被覆盖重写

  - 修饰局部变量

    ```final```修饰一个局部变量时，此变量不能再进行更改，且至多接受一次赋值

  - 修饰成员变量

    ```final```修饰一个成员变量时，由于成员变量有默认值，要么使用直接赋值，如```final int num = 30;```，要么通过构造方法赋值（必须保证重载的构造方法都会对该成员变量赋值）





##### Swallow Copy 与 Deep Copy（浅深拷贝）

###### 浅拷贝

```java
class Student{
    private String name;
    private int id;
    private Score score;
    
    // standard constructors, getters and setters
}
class Score{
    private int mathScore;
    private int chineseScore;
    
    // standard constructors, getters and setters
}
public class demo{
    public static void main (void){
        Student stu01 = new Student("Li Hua",01,new Score(10,20));
        Student shallowCopy = new Student(stu01.getName(), stu01.getId(), stu01.getScore());
        System.out.println(shallowCopy == stu01);
    }
    
}
```

当我们使用浅拷贝时，```shallowCopy != stu01``` ，但修改任何一个对象的score.mathScore时，另一个对象的相应的值也会被改变。

###### 深拷贝

深拷贝正是为了解决上述的例子，是拷贝后的对象与原来的对象完全隔离，互不干扰

请看如下几种方法

1. 通过构造函数复制

   ```java
   public Student(Student that){
       this(that.getName(), that.getId(), that.getScore());
   }
   // ===============================
   public Score(int mathScore, int chineseScore) {
       this(that.getMathScore(), that.getChineseScore());
   }
   // ===============================
   Student shallowCopy = new Student(stu01);
   shallowCopy.getScore.setMathScore(100);
   System.out.println(stu01.getScore().getMathScore());
   ```

   通过额外的构造函数来进行深拷贝后，两个对象间不会互相干扰；

2. 通过```object.clone()```来完成

   如果在一个nonfinal类中重写了clone()方法，应该通过调用```super.clone()```来返回一个对象

   每一个类实现了```cloneable```接口的都应该提供一个合适的```public```的```clone()```方法

   - 假设现在有一个 PhoneNum 类，采取以下方法克隆一个对象

     ```java
     public PhoneNum(){
         String num;
     }
     ```
   
     ```java
     @Override
    public PhoneNum clone(){
         try{
          return (PhoneNum)super.clone();
         }catch(CloneNotSupportedException e)
     }
     ```
   
     如果要复制的对象中只有```final```对象或者原始的数据类型时，这样子复制是没有问题的
   
   - 若是以下这种情况时
  ```java
     public class User{
         String name;
         PhoneNum phoneNum;
     }
  ```

     ```java
     @Override
     public User clone(){
         try{
             return (User)super.clone
         }catch(CloneNotSupportedException e)
     } 
     ```
     
     此时对复制后的```obj.phoneNum.num```进行修改时，原始对象的对应值也会变化，这是因为，两个对象的 ```phoneNum``` 都指向了同一个地址，若想要复制后的对象互相不干扰，应该采用下列做法
     
     ```java
     public PhoneNum implements Cloneable{
         String num;
         @Override
         public object clone(){
             try{
                 return super.clone();
             }catch(CloneNotSupportedException e)
         }
     }
     ```
     
     ```java
     public User implements Cloneable{
         String name;
         PhoneNum phoneNum;
         @Override
         public User clone(){
             try{
                 User clone = (User) super.clone();
                 clone.phoneNum = (PhoneNum) super.clone();
                 return clone;
             }catch(CloneNotSupportedException e)
         }
     } 
     ```
     
     这样通过递归复制出来的两个对象就是完全独立的
     
     [Baeldung]:https://www.baeldung.com/java-deep-copy


​     

