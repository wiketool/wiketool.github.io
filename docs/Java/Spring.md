# 🍃Spring

## IOC(控制反转)

### 读取Xml



#### BeanFactory模式

```java
Resource cr = new ClassPathResource("applicationContext.xml");

BeanFactory bf=new XmlBeanFactory(cr);

UserDao userDao = (UserDao)bf.getBean("userDao");
```

#### ApplicationContext模式

##### 相对路径

使用ClassPathXmlApplicationContext对象获取，必须把applicationContext.xml放置到类的加载路径中，也就是Src下面

```java
ApplicationContext factory=new ClassPathXmlApplicationContext("classpath:appcontext.xml");
UserDao userDao = (UserDao)context.getBean("userDao");
```

##### 绝对路径

必须把applicationContext.xml放置到工程目录下面，也就是项目路径的下面

```java
ApplicationContext factory=new FileSystemXmlApplicationContext("src/appcontext.xml");
```

使用了 classpath: 前缀,作为标志, 这样,FileSystemXmlApplicationContext 也能够读入classpath下的相对路径

```java
ApplicationContext factory=new FileSystemXmlApplicationContext("classpath:appcontext.xml"); 
```



## DI依赖注入

