一、对象创建与销毁

1. 静态工厂方法代替构造器

  ```
  使用场景：JDBC-Driver，class等
  ```
2. 参数多时使用Builder

  ```
  考虑这样的一个场景：用一个类表示包装食品外面显示的营养成分标签。这些标签中有几个域是必需的：每份的含量、每罐的含量以及每份的卡路里，还有超过20个可选域:总脂肪量、饱和脂肪量、转化脂肪、胆固醇、钠等等。
  NutritionFacts juice = new NutritionFacts.Builder(240, 8).calories(100).sodium(35).carbohydrate(27).build();
  ```
3. 单例

  ```
  使用私有构造器
  ```
4. 避免不必要的对象创建

  ```
  场景：java  string，基本类型
  ```
5. 消除过期引用
6. 避免使用finalizer

  ```
  重写后不显示调用supper.finalizer()将不会被调用
  ```

二、对于所有对象的通用方法

1. equals 和 hashCode的约定

  ```
  equal相等hashCode相等
  ```
2. 覆盖toString()

  ```
  打日志时不覆盖看到的是地址
  ```
3. 复制对象不要用自带的clone

  ```
  因为clone会调用supper.clone()，而我们并不能确定supper很好的实现了clone方法
  ```
4. 实现Comparable接口

  ```
  也可以不实现，在使用的时候写
  ```
  
三、类和接口
