# 🍃Spring

## 常用注解

### IOC相关

#### Bean对象

##### 数据注入相关

`@Component(value = "fuckPeople")`

> 作用：用于把当前类对象存入spring容器中 
>
> 属性： 
>
> ​	value：用于指定bean的id。当我们不写时，它的默认值是当前类名，且首字母改小写。

- xml中配置

  ```java
  <context:component-scan base-package="xxx.xxx.xxx"/>
  ```

  

- `controller`：一般用在表现层 

- `Service`：一般用在业务层 

- `Repository`：一般用在持久层 

- 以上三个注解他们的作用和属性与`component`是一模一样。 他们三个是spring框架为我们提供明确的三层使用的注解，使我们的三层对象更加清晰

`@Autowired`

先按照类型自动寻找Bean容器中对应的，如果有多个匹配，再按照变量名与匹配项的Bean id进行匹配

`@Qualifier(value = "fuckDao")`

- 给类成员注入时，单独使用注入不成功，需要搭配`@Autowired`
- 给成员方法注入时，可以单独使用

`Resource(name = "beanName")`

- 可以单独使用，直接根据bean的id注入

`Value("xxx")`

- 用于基本数据类型和String的注入
- 可以使用Spring的el表达式，即SpEL

**集合类型的数据只能通过XML注入**

##### 作用范围

`@Scope("singleton")`

**singleton** **prototype** **request** **session** **global-session**

##### 生命周期

```java
@PostConstruct

@PreDestroy
```

## IOC(控制反转)

### XML

#### XML配置

##### Bean Scope

1. **singleton**

   范围设置为单例，IOC容器将为该Bean所定义的对象创建唯一的实例，并存入高速缓存中，以后调用都不会再次创建新的对象实例

2. **prototype**

   每次调用该Bean对象时，IOC容器都会创建该对象的新实例

3. **request**

4. **session**

5. **global-session**

##### Bean 对象生命周期

###### 单例对象

与容器共存亡

###### 多例对象

1. 被调用时创建
2. 长时间未使用，被 Java 垃圾回收销毁

#### 读取Xml

##### BeanFactory模式

```java
Resource cr = new ClassPathResource("applicationContext.xml");

BeanFactory bf=new XmlBeanFactory(cr);

UserDao userDao = (UserDao)bf.getBean("userDao");
```

##### ApplicationContext模式

###### 相对路径

使用ClassPathXmlApplicationContext对象获取，必须把applicationContext.xml放置到类的加载路径中，也就是Src下面

```java
ApplicationContext factory=new ClassPathXmlApplicationContext("classpath:appcontext.xml");
UserDao userDao = (UserDao)context.getBean("userDao");
```

###### 绝对路径

必须把applicationContext.xml放置到工程目录下面，也就是项目路径的下面

```java
ApplicationContext factory=new FileSystemXmlApplicationContext("src/appcontext.xml");
```

使用了 classpath: 前缀,作为标志, 这样,FileSystemXmlApplicationContext 也能够读入classpath下的相对路径

```java
ApplicationContext factory=new FileSystemXmlApplicationContext("classpath:appcontext.xml"); 
```



## DI依赖注入

### 注入方式

#### 构造函数注入 `constructor-arg`

1. `type`用于指定要注入的数据的数据类型，该数据类型也是构造函数中某个或某些参数的类型
2. `index`用于指定要注入的数据给构造函数中指定索引位置的参数赋值。索引的位置是从0开始 
3. `name`用于指定给构造函数中指定名称的参数赋值
4. `value` 用于提供基本类型和string类型的数据
5. `ref`用于指定其他的bean类型数据。它指的就是在spring的Ioc核心容器中出现过的bean对象

#### `set`方法注入 `property`

1. `name` 指定 set 方法
2. `value` 提供基本类型和string类型的数据
3. `ref` 用于指定其他的bean类型数据。它指的就是在spring的Ioc核心容器中出现过的bean对象

##### 复杂集合的注入

1. 用于给List结构集合注入的标签： `list` `array` `set` 
2. 用于Map结构集合注入的标签：`map` `props` 
3. 结构相同，标签可以互换 

```java
	<bean id="people" class="people">
        <property name="age" value="10"/>
        <property name="name" value="Success"/>
        <property name="nameSet">
            <array>
                <value>111</value>
                <value>222</value>
            </array>
        </property>
        <property name="nameMap">
            <map>
                <entry key="Fuck" value="fuck"/>
                
            </map>
        </property>
    </bean>
```

