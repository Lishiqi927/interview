**初级回答：**
== 判断的是地址是否相同，equals判断的是值是否相同。

**中级回答：**
== 在基本类型中， == 比较的是值是否相同，例如：int a = 1； int b = 2； a==b比较的是1和2的值。
== 在引用类型中（引用类型是类类型、接口类型、数组类型）， == 比较的是地址是否相同，例如String c = new String(“李四”); 和 String d = new String(“李四”); 他们的比较c == d比较的是c和d的地址引用是否相同，这里很明显c和d的地址引用是不相同的，因为是两个不同的对象。

**高级回答**
首先来看equals的源码，源码中的注释是我添加的，我觉得通过注释就可以很简单的明白equals方法中的逻辑了吧，背景图片是我idea的背景图，有想要的可以私信我，嘿嘿。。。
![image](https://user-images.githubusercontent.com/35355940/113235890-6af48b00-92d6-11eb-8cf3-950c40b56fdc.png)


public boolean equals(Object anObject) {
        //判断地址是否相同，如果地址相同则直接返回true，如果地址不相同再去判断值是否相同
        if (this == anObject) {
            return true;
        }
        //首先判断传进来的类是否是String类的子类，不懂instanceof函数可以百度
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            //判断两个数据长度是否相同，如果长度相同则判断每一位字符是否相同，长度不同则直接返回false
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    //判断每一位字符是否相同，如果有一位字符不相同则返回false
                    if (v1[i] != v2[i])
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }


通过源码可以看到equals方法中首先判断的是地址是否相同，如果地址相同则直接返回为true，如果地址不相同则再判断值是否相同。这里首先说明一下这段equals源码是在String类中的，如下图。
![image](https://user-images.githubusercontent.com/35355940/113235999-9c6d5680-92d6-11eb-936d-b5e9bffe602d.png)


就是说只有String类型的使用equals方法才能先比较地址是否相同，如果地址不同则再比较值是否相同，那么equals在对象类型或者数组类型中有没有这种比较逻辑呢，我们看图。
![image](https://user-images.githubusercontent.com/35355940/113236009-a4c59180-92d6-11eb-9bbb-4b951dd227cb.png)


        class Student {
            public Student(String name) {
                this.name = name;
            }

            private String name;

            public String getName() {
                return name;
            }

            public void setName(String name) {
                this.name = name;
            }
        }

        Student s1 = new Student("张三");
        Student s2 = new Student("张三");
        System.out.println(s1.equals(s2)); // false


        char [] q = {1,2,3};
        char [] w = {1,2,3};
        System.out.println(q.equals(w)); //false

我们实例了两个学生对象，然后对象name都赋值为“张三”，而我们也创建了两个数组对象，里面都是1、2、3，这样看来如果用equals方法的话，应该都为true才对，但是我们的结果都为false，这是为什么呢，让我们点击对象或者数组调用的equals方法中去看看，如图。
![image](https://user-images.githubusercontent.com/35355940/113236027-af802680-92d6-11eb-90df-b516f6751c5f.png)


我们可以看到对象和数组调用的equals方法都是Object类中的方法，而且Object类中的方法只有一个对比地址的逻辑，没有对比值的逻辑，所以如果我们没有重写equals方法的话，对象和数组都是用的Object类中的方法都是比较的地址，如果我们重写equalse的话才可以在equals方法中写比较值的逻辑，而String类型的equals方法本身就有比较值的逻辑，所以我们平时基本类型比较值的时候使用 == ，String类型比较值的时候使用equalse，如果要比较两个对象是否相等直接使用equalse的话比较的是两个对象的地址是否相等。

**总结**
如果大家想了解更多的有关JAVA方面的面试题与答案详解请搜索关注我的微信公众号《小奇JAVA面试》里面每天都会更新JAVA面试题，希望能够帮助到大家。
![image](https://user-images.githubusercontent.com/35355940/113236046-b73fcb00-92d6-11eb-8daa-b241fd8b386c.png)
