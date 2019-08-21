# Why should you have minimum scope for variables?
提高可靠性,避免不经意的修改

# Why should you understand performance of String Concatenation?
这样我们可以在对字符串进行操作时,避免创建大量无用的临时对象.同时对性能有了解

# What are the best practices with Exception Handling?
1. 仅仅在需要的时候才是用异常
2. 对于可恢复的情况,使用检查型异常;对于程序错误(error),使用runtime异常
3. 避免没必要的检查型异常
4. 尽量使用标准异常
5. 抛出异常时,注意异常的抽象等级
6. 对于每个抛出异常的方法,都要在文档中记录
7. 在异常中包含错误细节
8. 保持失败的原子性.例如,如果初始化时一个对象的某些属性抛出了异常,那么这个对象就不应该被创建出来.
9. 不要忽略异常,即:不要留下空的catch块.即使不需要处理,也要在catch块中说明原因.

# When is it recommended to prefer Unchecked Exceptions?
当程序出现不可恢复的错误时,使用非检查异常

# When do you use a Marker Interface?
这样的接口,主要是体现其功能,但不限制用户的实现方式

# Why are ENUMS important for Readable Code?
可读性更强,并且更安全.

# Why should you minimize mutability?
不可变class的五项原则:
  1. 不提供任何修改对象状态的途径
  2. 确保class不可被继承
  3. 确保所有属性都是私有的
  4. 杜绝一切可变组件
java类的不可变对象包括:String 基本类型的包装类,BigInteger,BigDecimal
不可变对象的优点:
  1. 不可变对象本身就是线程安全的,无需同步
  2. 不可变对象可以随意共享,因此可以减少实例数量
  3. 不可变的类可以使用工厂方法来让用户获取实例对象,类对象本身持有一个对象,而无需每次都去创建新对象
  4. 如果一个对象是不可变的,那么我们无需因为担心其一致性而创建大量副本.正因如此,String对象么有copy方法
  5. 不仅不可变对象可以随意共享,他们的引用也可以随意共享
  6. 不可变对象可以作为一个Map或者set来用,而无需担心其被改变
  7. 唯一的缺点:对于每一种状态,需要创建独立的对象
  
# What is functional programming?
面向数据的编程方式,更注重数据的流向

# Why should you prefer Builder Pattern to build complex objects?
难题:
  1. new来创建实例,经常遇到不存在无参构造器的情况,使得创建对象困难重重,并且在编译期难以发现问题
  2. 面对一个拥有大量属性的类对象,静态工厂方法和构造器的通病:无法满足大量可选参数的情况,除非我们对其进行大规模重载
  3. 如果我们使用Javabean模式来逐项初始化这些属性,那么整个初始化过程就变成不连续的了.即,该对象在创建过程中,会呈现出多个不完整的状态
  4. javabean模式使得我们无法获得一个不肯变对象,因为setter不是私有的
  
builder优点:
  1. 中途只返回内部builder对象,只在调用build方法时,创建目标对象.
  2. 我们可以为一个类创建处于不同状态的多个不可变对象
  3. 我们可以完成一些复杂的/有关联的属性的初始化过程
# Why should you avoid floats for Calculations?
会导致丢失精度

# Why should you build the riskiest high priority features first?
高风险的模块越晚引入,系统复杂度越高.越早引入,越能针对风险进行控制
