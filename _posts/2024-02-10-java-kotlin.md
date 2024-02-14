---
layout: post
title: Kotlin 기본 문법 (1)   
date: 2024-02-10 10:01:01 +09:00
categories: [개발, Kotlin]
tags: [kotlin, java, kotlin java 비교]                    
---

<br/>
Kotlin의 기본 문법을 Java와 비교해 간단히 포스팅한다.

<br/>

---

# 변수 사용법
## 가변 / 불변 변수
Kotiln에서는 val(밸, 불변)과 var(발, 가변) 2가지 형태로 변수를 선언한다.   
(Default로 val을 사용해 변수를 선언하고 가변형일 경우에만 var을 사용하도록 한다.)
```java
final int a = 1;   
int b = 2;
```
```kotlin
val a: Int = 1
var b: Int = 2
```

## Null 처리
Kotlin에서는 Null에 민감하다. Java 코드를 마이그레이션 해야하는 경우, Null이 허용되는 변수인지 아닌지 잘 확인해야한다.
```java
Integer a = null;   
int b = 1;      
```
```kotlin
val a: Int? = null
val b: Int = 1
```

<br/>

---

# 비교 연산
Java에서의 동일성 판단 연산자가 Kotiln에서의 동등성 판단 연산자가 되기 때문에 유의해야한다.
## 동등성 (equality)
```java
if (a.equals(b))
```
```kotlin
if (a == b)
```

## 동일성 (identity)

```java
if (a == b)
```
```kotlin
if (a === b)
```

<br/>

---

# 제어문
## if-else문
Kotlin에서는 바로 Return이 가능하다. (if-else문 자체가 Expression이 된다.) 3항 연산자가 존재하지 않는다.
```java
public int compare(int a) {
    if (a > 1) return 1;
    else return 2;
}
```

```kotlin
fun compare(a: Int): Int {     
    return if (a > 1) 1 else 2
}
```


## switch문
마찬가지로 바로 Return이 가능하다. Kotlin은 Java와 달리 switch문이 굉장히 깔끔하게 표현된다.     
웬만한 if-else문을 when으로 바꾸면 코드 관리 편의성이 높아진다.
```java
public String main(int n) {
  switch (n) {
    case 1:
      return "1";
    case 2:
      return "2";
    case 3:
      return "3";
    default:
      return "4 or more";
  }
}
```

```kotlin
fun main(n: Int): String {
  return when (n) {
    1 -> "1"
    2 -> "2"
    3 -> "3"
    else -> "4 or more"
  }
}
```

<br/>

---

# 반복문
## for문
Kotlin에서는 더 이상 연산자를 사용하지 않는다.
```java
for (int i = 1; i <= 5; i += 2) {
    System.out.println(i);
}

for (int i = 5; i >= 1; i -= 2) {
    System.out.println(i);
}
```

```kotlin
for (i in 1 .. 5 step 2) {
    println(i)
}

for (i in 5 downTo 1 step 2) {
    println(i)
}
```

## for-each문
Kotlin에서는 변수를 따로 선언하지 하지 않는다. `:` 대신 `in` 을 사용한다.
```java
final List<Long> list = Arrays.asList(1L, 2L);
for (long number : list) {
    System.out.println(number);
}
```

```kotlin
val list = listOf(1L, 2L)
for (number in list) {
    println(number)
}
```

<br/>

---

# try-catch문
## 평범한 try-catch
Kotlin에서는 바로 Return이 가능하다. (try-catch문 자체가 Expression이 된다.)
```java
public double parseDouble(String a) {
    try {
        return Double.parseDouble(a);
    } catch (NumberFormatException e) {
        return 2.0d;
    }
}
```

```kotlin
fun parseDouble(a: String): Double {
    return try {
        a.toDouble()
    } catch (e: NumberFormatException) {
        2.0
    }
}
```

## try-with-resource
Kotlin에서는 try-with-resource 구문이 존재하지 않는다.
```java
try (BufferedReader bufferedReader = new BufferedReader(new FileReader("/path"))) {
    System.out.println(bufferedReader.readLine());
}
```

```kotlin
val bufferedReader = BufferedReader(FileReader("/path")).use { reader ->
    println(bufferedReader.readLine())
}
```

<br/>
