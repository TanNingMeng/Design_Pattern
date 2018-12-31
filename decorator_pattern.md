# <span onclick="show()">装饰着模式</span>
> 动态地给一个对象添加一些额外的职责，就是增加功能来说，装饰者模式比生产子类更加灵活。

按照我对这个模式的感觉，装饰者模型着重点是灵活。例如项目上线第一期，我们写好了一个系统的核心算法成功上线了。过了一两个月了，项目的二期来了。项目经理让开发者给这个算法的结果增加一些功能处理：
1. 将**算法结果**进行单位换算，然后传递让前端显示
2. 将**算法结果**存储到数据库，以便以后统计

初学者一般会想着，直接去算法的代码后面加上两行代码：一行是单位换算，一行是存储数据库的 sql。但是这样做违反了``开闭原则``，在做修改的时候尽量不要修改原来的功能。如果后期需求。功能越来越多的话，我们就会不得不去增加这个算法类的负担，变得乱而不容易维护。     
既然我们要遵循这个原则，那么我们就需要在思考如何改造。首先，我们需要分清其职责，尽量算法的纯净。而至于这些**单位换算**，**存储数据库**这些与算法逻辑没有关联的额外操作，我们将它作为修饰内容独立出来。


## 例子

```java
public abstract class Component {
    public abstract void operation();
}
```

```java

public class ConcreteComponent extends Component {
    @Override
    public void operation() {
        System.out.println("ConcreteComponent");
    }
}
```

```java
public class ConcreteComponentA extends Decorator {
    @Override
    public void operation() {
        super.operation();
        aMehtod();
        System.out.println("ConcreteComponentA 方法");
    }

    private void aMehtod() {

    }
}
```


```java
public class ConcreteComponentB extends Decorator {
    @Override
    public void operation() {
        super.operation();
        bMehtod();
        System.out.println("ConcreteComponentB 方法");
    }

    private void bMehtod() {
    }
}
```

```java
public abstract class Decorator extends ConcreteComponent {

    private Component component;

    public void setComponent(Component component) {
        this.component = component;
    }

    @Override
    public void operation() {
        if (component != null) {
            component.operation();
        }
    }
}
```
测试类
```java
public class Test {
    public static void main(String[] args) {

        ConcreteComponent concreteComponent = new ConcreteComponent();

        ConcreteComponentA concreteComponentA = new ConcreteComponentA();

        ConcreteComponentB concreteComponentB = new ConcreteComponentB();

        concreteComponentA.setComponent(concreteComponent);

        concreteComponentB.setComponent(concreteComponentA);

        concreteComponentB.operation();

    }
}
```

## 使用场景与模式的总结
1. 当系统需要新功能的时候，是向旧的类中添加新的代码。当这些新加的代码增加了主类的复杂度时，就可以使用。
2. 装饰者模式的优点在于，对于已有的功能基础上，添加一些特殊的功能，
3. 类中的装饰功能从类中移除，这样可以简化原来的类。
4. 有效地将类的核心职责和修饰功能区分开。而且可以去除相关类中重复的装饰逻辑。
5. 可以根据自己想要的修饰顺序进行组装。











<!-- css/js -->
<script type="text/javascript">
	function show(argument) {
		// body...
		alert('彩蛋！')
	}
</script>


