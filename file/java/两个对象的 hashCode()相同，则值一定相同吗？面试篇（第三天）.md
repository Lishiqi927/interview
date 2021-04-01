**初级回答**
不一定相同，因为hashCode是根据一定的规则计算出来的，不同值的hashCode有可能相同，如图。
![image](https://user-images.githubusercontent.com/35355940/113236179-fe2dc080-92d6-11eb-9936-cc6ea5e5cbc4.png)


在这里“Ma”和“NB”计算出来的hashCode值都为2484，但是他们的真实值是不相等的，所以两个对象的hashCode()相同，值则不一定相同。我们看一下hashCode()方法的源码如下图：
![image](https://user-images.githubusercontent.com/35355940/113236172-fa9a3980-92d6-11eb-8fd5-61cd4cf55230.png)


在源码中我们可以看到是对值进行了一系列的计算，所以有可能不同的值计算出来的hashCode()相同，但是同一个值的hashCode()是不会变的，所以可以根据字符串值推算出它的hashCode(),但是不能根据hashCode()的值推算出字符串的值。

高级回答
hashCode()存在的意义是什么？我们通过前面可以了解到hashCode()将一个字符串的值变为了一个整数，那么这样做的作用是什么呢？我们来看一段代码，如图。
![Uploading image.png…]()


我们平时经常用到map来存储对象，因为map是key，value形式的，它不像list形式的集合可以有顺序的从0开始往集合里放数据，而是随意的放，但是取值的话就很麻烦，因为它存放值的时候没有顺序，所以取值的时候根据key去里面一个一个对比，等找到key相等的值就取出，这样就会造成效率问题。
当我们用到hashCode()可以看到我们将name计算为3373707，age计算为98511，这样的话我们存值的时候就根据计算后的数值进行对应位置的存储，同样当我们get取值的时候再次将key计算为hashCode()值，因为同一个字符串hashCode()值相等，这个时候我们就可以直接根据hashCode()值将对应位置的数据取出，就不需要对key一个一个进行对比了，这样大大提高了效率，这就是为什么有hashCode()存在的原因了。

总结
如果大家想了解更多的有关JAVA方面的面试题与答案详解请搜索关注我的微信公众号《小奇JAVA面试》里面每天都会更新JAVA面试题，希望能够帮助到大家。
![Uploading image.png…]()
