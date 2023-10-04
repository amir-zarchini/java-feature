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

<div dir="rtl">
برخلاف متود ها عبارات لامبدا این 3 بخش را ندارند :

1) این عبارات نام ندارند.
2) Return Type ندارند. جنس خروجی یک لامبدا توسط کامپایلر از جایی که استفاده میشود تشخیص
   داده میشود. 
3) نمیتوانند  Type Parameter تعریف کنند ؛ بنابراین lambda expression ها نمیتوانند Generic باشند.
</div>

| With Lambda                                                           | Without Lambda                                                    |
|-----------------------------------------------------------------------|-------------------------------------------------------------------|
| (x , y) -> {return x + y;} <br/> (final int x ,final int y) -> x + y; | int sum(int x , int y) <br/> {return x + y; }                     |
| str -> str.length()                                                   | int map(String str) <br/> {return str.length(); }                 |
| () -> { <br/> out.print(LocalDate.now()); <br/> }                     | void printCurrentDate(){<br/> out.print(LocalDate.now()); <br/> } |
| () -> {}                                                              | void doNothing(){ <br/> // No Code goes here<br/>  }              |

<div dir="rtl">
چند مثال از lambda expression : 
</div>

<details>
<summary>No Parameter</summary>

```java
interface Sayable{  
    public String say();  
}  

public class LambdaExpressionExample3{
    public static void main(String[] args) {  
        Sayable s=()->{  
            return "I have nothing to say.";  
        };  
        System.out.println(s.say());  
    }  
}  
```
</details>
<details>
<summary>Single Parameter</summary>

```java
interface Sayable{
    public String say(String name);
}

public class LambdaExpressionExample4{
    public static void main(String[] args) {
        
        // Lambda expression with single parameter.  
        Sayable s1=(name)->{
            return "Hello, "+name;
        };
        System.out.println(s1.say("Sonoo"));

        // You can omit function parentheses    
        Sayable s2= name ->{
            return "Hello, "+name;
        };
        System.out.println(s2.say("Sonoo"));
    }
}  
```
</details>

<details>
<summary>Multiple Parameter</summary>

```java
interface Addable{  
    int add(int a,int b);  
}

public class LambdaExpressionExample5{  
    public static void main(String[] args) {
        
        // Multiple parameters in lambda expression  
        Addable ad1=(a,b)->(a+b);  
        System.out.println(ad1.add(10,20));  
          
        // Multiple parameters with data type in lambda expression  
        Addable ad2=(int a,int b)->(a+b);  
        System.out.println(ad2.add(100,200));  
    }  
} 
```
</details>
<details>
<summary>Foreach Loop</summary>

```java
public class LambdaExpressionExample7{  
    public static void main(String[] args) {  
          
        List<String> list=new ArrayList<String>();  
        list.add("ankit");  
        list.add("mayank");  
        list.add("irfan");  
        list.add("jai");  
          
        list.forEach(  
            (n)->System.out.println(n)  
        );  
    }  
}  
```
</details>
<details>
<summary>Filter Collection Data</summary>

```java
class Product{
   int id;
   String name;
   float price;
   public Product(int id, String name, float price) {
      super();
      this.id = id;
      this.name = name;
      this.price = price;
   }
}
public class LambdaExpressionExample11{
   public static void main(String[] args) {
      List<Product> list=new ArrayList<Product>();
      list.add(new Product(1,"Samsung A5",17000f));
      list.add(new Product(3,"Iphone 6S",65000f));
      list.add(new Product(2,"Sony Xperia",25000f));
      list.add(new Product(4,"Nokia Lumia",15000f));
      list.add(new Product(5,"Redmi4 ",26000f));
      list.add(new Product(6,"Lenevo Vibe",19000f));

      // using lambda to filter data  
      Stream<Product> filtered_data = list.stream().filter(p -> p.price > 20000);

      // using lambda to iterate through collection  
      filtered_data.forEach(
              product -> System.out.println(product.name+": "+product.price)
      );
   }
}    
```
</details>
