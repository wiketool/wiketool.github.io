# 🍃Spring

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

