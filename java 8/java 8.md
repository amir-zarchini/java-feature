#java 8
<p dir="rtl">
ویژگی های جاوا 8 عبارتند از :
</p>

- [Lambda Expressions](#lambda-expressions)
- Method references,
- Functional interfaces,
- Stream API,
- Default methods,
- Base64 Encode Decode,
- Static methods in interface,
- Optional class,
- Collectors class,
- ForEach() method,
- Nashorn JavaScript Engine,
- Parallel Array Sorting,
- Type and Repating Annotations,
- IO Enhancements,
- Concurrency Enhancements,
- JDBC Enhancements etc.


<div align="center">

# Lambda Expressions
</div>

---

<div dir="rtl">

<li>
 Lambda Expression ها یک بلاک کد یا به تعبیری فانکش بدون نام هستند که شامل لیستی از   
  ورودی ها و یک بدنه میباشد
</li>
<li>
علامت فلش (<-) برای جدا کردن بخش تعریف پارامتر ها و بدنه استفاده میشود
</li>
<li>
مثال:
</li>
</div>

``` java
(int x) -> x + 1
(int x , int y) -> x + y
(int x , int y) -> {int max = x > y ? x : y; return max;}
```

<div dir="rtl">
هر عبارت لامبدا باید به نوعی پیاده سازی از هر  Functional Interface باشد. Interface ای که حداکثر یک متود
abstract داشته باشد
</div>

<details>
<summary>Without Lambda Expression</summary>

```java
interface Drawable{  
    public void draw();  
}  
public class LambdaExpressionExample {  
    public static void main(String[] args) {  
        int width=10;  
  
        //without lambda, Drawable implementation using anonymous class  
        Drawable d=new Drawable(){  
            public void draw(){System.out.println("Drawing "+width);}  
        };  
        d.draw();  
    }  
} 
```
</details>

<details>
<summary>Java Lambda Expression Example</summary>

```java
@FunctionalInterface  //It is optional  
interface Drawable{  
public void draw();  
}

public class LambdaExpressionExample2 {  
public static void main(String[] args) {  
int width=10;

        //with lambda  
        Drawable d2=()->{  
            System.out.println("Drawing "+width);  
        };  
        d2.draw();  
    }  
} 
```
</details>