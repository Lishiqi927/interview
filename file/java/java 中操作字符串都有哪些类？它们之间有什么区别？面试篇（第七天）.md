**初级回答：**

String、StringBuilder、Stringbuffer ，区别是String是不可变对象，每次都需要生成一个新的对象，StringBuilder、Stringbuffer是可变对象，每次都在同一个对象上进行操作。

**中级回答：**

String是不可变对象，假如String a = “1”; a=“2”; a=“3”; a=“4” ;这里我们给a不断的赋值，那么a肯定等于最后赋值的值4，这肯定是对的，但是前面赋值的1、2、3并没有销毁，他们还存在与堆内存中，堆空间中存放了值，在栈中存储了该数据的引用地址。如图。

![image](https://user-images.githubusercontent.com/35355940/113245108-da737600-92e8-11eb-86a6-2e2258e5c97d.png)
![image](https://user-images.githubusercontent.com/35355940/113245117-dd6e6680-92e8-11eb-8253-655ba8f94a86.png)
![image](https://user-images.githubusercontent.com/35355940/113245123-e0695700-92e8-11eb-96a6-e9e9bf85af67.png)


通过这里我们可以看到每一次赋值堆内存都会重新开辟一块新的内存空间用来存放新值，然后将新值的地址如“A00001”给栈内存，然后栈内存将引用地址改变就可以获得新值了，所以说如果对String类型的值重复进行很多次操作，会占用大量的堆内存空间。

**高级回答**

StringBuilder、Stringbuffer这两个类对字符串操作就没有以上那种情况，这两个类只在堆内存开辟一块空间，每次都只在这一块空间中修改，但是他们和String类型对值的操作方法有所不同，如图。

![image](https://user-images.githubusercontent.com/35355940/113245137-e52e0b00-92e8-11eb-9f36-484f6ffafb27.png)


我们同样对字符串先进行+“1”的操作，再进行+“2”的操作，String类型是直接用=号来进行赋值，+号来进行连接操作，而Stringbuilder和StringBuffer是使用append()方法来进行追加操作的，这是他们对值的操作方法有所不同，而Stringbuilder比StringBuffer的效率高，那么StringBuffer有什么过人之处呢，就是StringBuffer是线程安全的，也就是再多线程中可以使用Stringbuffer来对字符串进行操作。

**整理**

String：对字符串不进行重复操作时选择用String。
StringBuilder：在单线程中对字符串进行重复操作时选择用StringBuilder。
StringBuffer：在多线程中对字符串进行重复操作时选择用StringBuffer。

**总结**

如果大家想了解更多的有关JAVA方面的面试题与答案详解请搜索关注我的微信公众号《小奇JAVA面试》里面每天都会更新JAVA面试题，希望能够帮助到大家。

![image](https://user-images.githubusercontent.com/35355940/113245182-f545ea80-92e8-11eb-806a-faef260527b4.png)
