# 代理模式


## 示例代码
Subject.java
```java
abstract class Subject{
	public abstract void request();
}
```

RealSubject.java
真实的执行者
```java
class RealSubject extends Subject{
	public void request(){
		System.out.println("");
	}
}
```

Proxy.java
代理类
```java
class Proxy extends Subject{
	RealSubject realSubject;
	public void request() {
		if (realSubject == null) {
			realSubject = new RealSubject();
		}

		realSubject.request();
	}
}
```
测试类
```java
public Test{
	public static void main(String[] args) {
		Proxy proxy = new Proxy();
		proxy.request();
	}
}
```





















