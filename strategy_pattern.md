# 策略模式


## 定义
它定义了算法家族，分别封装起来，让它们之间可以相互替换。此模式让算法的变化，不会影响到使用算法的客户。


## 用处
策略模式就是用来封装算法的，但在实践中，我们发现用它来封装几乎任何类型的规则。只要在分析过程中听到需要在不同时间应用不同的业务规则，就可以考虑使用策略模式处理这种变化的可能性。

## 示例代码
Strategy.java
策略的抽象类
```java
public abstract class Strategy{
	public abstract void algorithmImplements();
}
```

StrategyA.java
策略实现 A
```java
public class StrategyA extends Strategy{
	public void algorithmImplements(){
        System.out.println("算法A的实现");
	}
}
```

StrategyB.java
策略实现 B
```java
public class StrategyB extends Strategy{
	public void algorithmImplements(){
        System.out.println("算法B的实现");
	}
}
```

StrategyC.java
策略实现 C
```java
public class StrategyC extends Strategy{
	public void algorithmImplements(){
        System.out.println("算法C的实现");
	}
}
```
 
Context.java
```java
public class Context{
	Strategy strategy;

	public Context(Strategy strategy){
		this.strategy = strategy;
	}

	public void ContextInvoke(){
		strategy.algorithmImplements();
	}
}
```

## 代码讲解
一般来说，策略模式是为了分隔算法和前端之间的耦合。








