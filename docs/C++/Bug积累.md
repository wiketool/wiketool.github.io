1. 引用类型不能绑定到临时类型上

```C++
Point& temp = Point{1, 2};  // ERROR
friend ostream& operator << (ostream& o, Point& p);
//形参列表传递也不行
```

