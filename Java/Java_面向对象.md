## 抽象类

### 抽象类怎么用：
1. 创建抽象类
```
abstract class Animal {
    abstract void move();  // 抽象方法
}
```
2. 子类继承并实现抽象方法
```
class Dog extends Animal {
    @Override
    void move() {
        System.out.println("狗在跑");
    }
}
```
3. 通过多态使用
```
Animal a = new Dog();
a.move();
```
- a 的编译类型（静态类型）是 Animal
- new Dog( ) 创建出来的对象是真正的 Dog。
- 所以 a 在运行时其实是 Dog 对象。
- 编译器只允许你用 Animal 里定义的方法
- 所以如果 Dog 里有方法 bark()，你不能写：
```
Animal a = new Dog();
a.move();      // ✔ OK
a.bark();      // ❌ 编译错误（即使 Dog 有 bark）

((Dog)a).bark(); // ✔ 可以调用 Dog 的方法

```
### 为什么要用抽象类？
 原因：
#### 1. 子类必须实现某些方法，但父类没法给出默认实现
```
abstract class Animal {
    abstract void move();
}
```
这样能保证：

Dog 一定实现 move()

Cat 一定实现 move()

Bird 一定实现 move()

强制统一标准（必须实现某些方法）。

#### 2. 抽象类可以提供共同的属性与方法（接口不行）
```
abstract class Animal {
    String name;

    // 公共方法
    void eat() {
        System.out.println(name + " is eating");
    }

    // 子类必须实现的方法
    abstract void move();
}
```
子类继承后无需重复写 eat( )。

#### 3. 用于“模板方法模式”（高级用法，非常常见）
```
abstract class Game {
    final void start() { // 模板固定流程
        init();
        play();
        end();
    }

    abstract void init();
    abstract void play();
    abstract void end();
}
```
子类只写关键步骤，流程由父类控制。

####  4. 避免创建“概念上不存在的对象”
```
Animal a = new Dog(); // OK
new Animal();  // ❌ 不允许
```
比如你不会创建一个“动物（Animal）”，动物只是一个抽象概念。

你只会创建狗、猫、鸟：

### 例子：
定义抽象类
```
abstract class Vehicle {
    
    // 公共方法：所有交通工具都一样
    void checkSystem() {
        System.out.println("正在检查系统...");
    }

    // 抽象方法：不同交通工具的启动方式不同
    abstract void startEngine();

    // 模板方法：固定流程
    void start() {
        checkSystem();     // 1. 所有交通工具都要检查系统
        startEngine();     // 2. 让子类自己写发动机启动逻辑
        System.out.println("启动完成！");  // 3. 完成提示
    }
}
```
子类继承抽象类
```
class Car extends Vehicle {
    @Override
    void startEngine() {
        System.out.println("汽车发动机启动：点火...");
    }
}
class Ebike extends Vehicle {
    @Override
    void startEngine() {
        System.out.println("电动车启动：电机供电...");
    }
}
class Motorcycle extends Vehicle {
    @Override
    void startEngine() {
        System.out.println("摩托车发动机启动：拉动引擎...");
    }
}
```

实际使用
```
public class Main {
    public static void main(String[] args) {
        Vehicle v1 = new Car();
        Vehicle v2 = new Ebike();
        Vehicle v3 = new Motorcycle();

        v1.start();
        v2.start();
        v3.start();
    }
}
```

## 为什么这么写？
代码可复用、可扩展、可替换性强

参数为父类的 方法 ，子类对象可以代入
```
void startVehicle(Vehicle v) {
    v.start();
}

startVehicle(new Car());
startVehicle(new Ebike());
startVehicle(new Motorcycle());
```
可以一次性批量管理不同类型对象

可以把 子类 保存到 父类 list
```
Vehicle[] list = {
    new Car(),
    new Ebike(),
    new Motorcycle()
};

for (Vehicle v : list) {
    v.start(); // 每个对象执行自己的逻辑
}
```
