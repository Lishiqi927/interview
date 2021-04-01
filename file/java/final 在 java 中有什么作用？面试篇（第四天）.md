**初级回答：**
final修饰的值不能改变。

**中级回答：**
final可以修饰在变量上。
final可以修饰在方法上。
final可以修饰在类上。

**高级回答：**
final是修饰符，类似于public、private这种的修饰符号。
final是关键字，类似于static等关键字，关键字是不可以当做变量名称、方法名、类名的，如图。

![image](https://user-images.githubusercontent.com/35355940/113238441-6088c000-92db-11eb-8d04-632872ea7ff7.png)


final修饰在变量上分为基本数据类型和引用数据类型两种情况。
1、final修饰在基本数据类型例如String、int上，那么他们的值是不可以改变的。如图。

![image](https://user-images.githubusercontent.com/35355940/113238449-667ea100-92db-11eb-847c-4dd73e6f3b86.png)


2、final修饰在引用数据类型例如对象上，那么他的属性值可以变，但是对象值不能变，就是属性可以随意赋值，但是不可以将一个对象进行赋值。如图。

![image](https://user-images.githubusercontent.com/35355940/113238452-6aaabe80-92db-11eb-940a-1e45e59ab03a.png)


3、final修饰在方法上不可以被重写，例如父类有final修饰的方法，那么子类不可以重写这个方法，现在new一个父类Person写两个方法，一个被final修饰，一个不被final修饰，再写一个子类Student继承Person类，然后重写两个方法，如图。

![image](https://user-images.githubusercontent.com/35355940/113238466-6f6f7280-92db-11eb-864b-b813c066f9d5.png)
![image](https://user-images.githubusercontent.com/35355940/113238474-739b9000-92db-11eb-92a9-ac1d85fda322.png)


4、final修饰在类上不能被继承，现在我们把final修饰在父类Person上，然后使用子类Studnet继承它，如图。

![image](https://user-images.githubusercontent.com/35355940/113238482-77c7ad80-92db-11eb-8849-31c78b8345a9.png)
![image](https://user-images.githubusercontent.com/35355940/113238487-7a2a0780-92db-11eb-804d-6b964c9df3a2.png)


**隐藏知识点**
使用final修饰的变量、方法、类等使用的时候效率比较高，因为不需要去二次寻址了，调用的时候效率比较高，下面我们进行一个测试，我们使用两个for循环，循环10亿10亿次，循环中调用变量的长度，如图;
![image](https://user-images.githubusercontent.com/35355940/113238511-82824280-92db-11eb-9730-64b5758b9c2e.png)
![image](https://user-images.githubusercontent.com/35355940/113238520-857d3300-92db-11eb-8c87-83bd86bb7af3.png)


我们可以看到，在使用final修饰的变量，调用10亿10亿次，时间在1秒内，而调用不使用final修饰的变量的时候时间大约在两秒，这是大量测试过的不是偶然结果，为什么用两个for循环就是因为执行太快一个for循环看不出差距，两个for循环刚刚可以看出差距。

**总结**
如果大家想了解更多的有关JAVA方面的面试题与答案详解请搜索关注我的微信公众号《小奇JAVA面试》里面每天都会更新JAVA面试题，希望能够帮助到大家。
![Uploading image.png…]()
