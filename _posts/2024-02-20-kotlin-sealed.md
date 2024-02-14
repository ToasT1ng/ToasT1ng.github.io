---
layout: post
title: Kotlin Sealed vs Java Sealed   
date: 2024-02-20 00:01:01 +09:00
categories: [개발, Kotlin]
tags: [kotlin, java, sealed]                    
---

Kotlin 강의를 듣다가 sealed 에 관한 내용이 나왔다.

실무에서 Kotlin sealed를 사용할 때 JDK 17 이상을 사용해야만 한다고 생각하고 있었는데, 좀 찾아보니 아닌걸 알게됐다.

관련해 포스팅한다. (작성 진행중)

<br/>

---

## Kotlin부터 알아보자.
Kotlin은 JDK 6을 기반으로 만들어져 있다. Complie시 Byte Code들이 이에 맞춰 생성된다.

그래서 이후 JDK 버전과 호환이 안될 수도 있다고 한다.

하지만 JDK는 워낙 호환이 잘되도록 만들어져있어서, 관련해서 말썽을 일으킬 여지는 적어보인다.


## Kotlin Sealed
간단히 sealed에 대해 정리해본다.
```kotlin
sealed class Car (
    val name: String,
)

class HynudaiCar: Car("현대차")
class BMWCar: Car("BMW차")
```


```kotlin
fun main(car : Car) {
  when (car) {
    is HynudaiCar -> println("현대다")
    is BMWCar -> println("BMW다")
  }
}
```

### Java 디컴파일
JDK 9에서 컴파일된 Kotlin 코드를 Java로 디컴파일해서 확인해보니 다음과 같다.
```java
public final class HynudaiCar extends Car {
   public HynudaiCar() {
      super("현대차", (DefaultConstructorMarker)null);
   }
}

public final class BMWCar extends Car {
   public BMWCar() {
      super("BMW차", (DefaultConstructorMarker)null);
   }
}

public abstract class Car {
   @NotNull
   private final String name;

   @NotNull
   public final String getName() {
      return this.name;
   }
   
   private Car(String name) {
      this.name = name;
   }
   
   public Car(String name, DefaultConstructorMarker $constructor_marker) {
     this(name);
   }
}
```

Kotlin의 sealed class는 Java의 abstract class로 컴파일된다.


## Java Sealed


## JDK 15 이전 버전에서 Kotlin Sealed를 사용하면 어떻게 되는거지?
JDK 6 이상의 버전이라면 잘 컴파일 된다. (JDK 9에서 테스트해봤는데 문제 없이 잘 작동함)
