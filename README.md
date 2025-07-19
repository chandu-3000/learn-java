# Learn JAVA
* [A Good resources for learning java things](https://gyansetu-core-java-for-java.gitbook.io/project)
# Links
* [Learn Collection framework](https://github.com/AnirudhDas/AniruddhaDas.github.io/blob/master/Java/CollectionFrameworkInJava/CollectionFrameworkInJava.md)
* Use ArrayDequeue for both Queue and Stack, just you need to remember 6 functions. (queue/stack push -> addLast, addFirst, queue/stack pop -> removeFirst/removeLast, queue/stack top -> getFirst, getLast.
  
## How Java Works.
* Java is a object-oriented, high-level programming language
* Java is a WORA (Write Once Run Anywhere).
* JDK -> JRE -> JVM (For Development) (Write once here).
* JRE -> JVM (For Production). (Run AnyWhere).
## String
* String class is immutable, it doesn't change the existing string, it will create new object. so even if you add a single character, it will create a new string object. (Not recommended).
* StringBuilder was introduced to solve this problem, but it is not thread-safe.
* StringBuffer is thread-safe, both StringBuffer & StringBuilder has apis.


## OOP
* Java doesn't support multiple inheritance, instead it supports multi level inheritance.
* To call Super class constructors, we should call "super()" function, if you want to call parameterized constructor of Super Class then pass the same args to the super() function call.
* If you want to call Same Class constructor then this() call has to be made.
* There is no header files funda in Java, everything will be in a .class files.
* If you want to include a class from different directory, then we should use **import** and in that .java file we use **package <class_name>** statement.
* final is nothing but constant.
* If you make your class as final, then you are stopping inheritance on that class.
* If you make method in a class as final, then inherited classes can not override that method.
* notation Class<?> in Java is a way to represent a class object of an unknown type ( Unknown type).
* Class<T>: Represents a class object of type T (type parameter used in generic programming(like c++ template).

  
### Object class
The Object class in Java is the root of the class hierarchy. Every class in Java is a descendant, directly or indirectly, of the Object class. This means that all classes inherit the methods of the Object class. Here are some key methods provided by the Object class:
* equals(Object obj): Determines whether another object is equal to this one.
* hashCode(): Returns a hash code value for the object.
* toString(): Returns a string representation of the object.
* clone(): Creates and returns a copy of this object.
* finalize(): Called by the garbage collector on an object when garbage collection determines that there are no more references to the object.
* getClass(): Returns the runtime class of this object.
* notify(): Wakes up a single thread that is waiting on this object's monitor.
* notifyAll(): Wakes up all threads that are waiting on this object's monitor.
* wait(): Causes the current thread to wait until another thread invokes the notify() method or the notifyAll() method for this object.

## Primitive types & their wrapper classes.

Each primitive has a wrapper class which has some extra functionalities.

### 🔁 Autoboxing / Unboxing
```java
int x = 5; Integer y = x; int z = y;
```

### 🔢 Char ↔ Int / ASCII
```java
char c = 'a'; int ascii = c; char d = (char) (ascii + 1);
```

### 🔠 Character Utilities
```java
Character.isDigit('5'); Character.isLetter('a');
Character.toUpperCase('b'); Character.toLowerCase('D');
```

### 🔁 Char ↔ String
```java
char ch = 'a'; String s = String.valueOf(ch);
char c = "hi".charAt(0);
```

### 🧮 Integer Methods
```java
Integer.parseInt("123"); String.valueOf(123);
Integer.bitCount(5); Integer.toBinaryString(5);
Integer.highestOneBit(10); Integer.MAX_VALUE;
```

### ⚖️ Equality & Identity
```java
Integer a = 128, b = 128; a == b -> false, a.equals(b) -> true;
int x = 128, y = 128; x == y -> true;
```

### 🔃 Sorting Arrays
```java
char[] cs = {'b','a'}; Arrays.sort(cs);
Integer[] a = {3,1}; Arrays.sort(a, Collections.reverseOrder());
```

### 📊 Frequency Count
```java
int[] freq = new int[26];
for (char c : "abc".toCharArray()) freq[c - 'a']++;
```

### 🔁 Digit ↔ Char
```java
int d = 5; char c = (char) ('0' + d);
char c = '8'; int d = c - '0';
```

### 🚨 Null Safety
```java
Integer a = null; if (a != null) int b = a;
```

### 📌 Summary Table
| Case         | Trick                      |
|--------------|----------------------------|
| ASCII        | `(int) c`, `(char) (x + 'a')` |
| Digit ↔ Char | `'0' + d`, `c - '0'`       |
| Int ↔ String | `String.valueOf(i)`, `parseInt(s)` |
| Sort         | `Arrays.sort()`            |
| Reverse Sort | `Arrays.sort(arr, rev)`    |
| Freq Count   | `freq[c - 'a']++`          |
| Set Bits     | `Integer.bitCount(x)`      |
| Binary       | `toBinaryString(x)`        |

---

## Comparable & Comparator.

# Java Comparable vs Comparator Cheatsheet

## 🔍 When to Use Comparable vs Comparator

| Feature | `Comparable` | `Comparator` |
|---------|-------------|-------------|
| Interface | `Comparable<T>` | `Comparator<T>` |
| Package | `java.lang` | `java.util` |
| Sort logic location | Inside the class (natural order) | Outside the class (custom order) |
| Method to implement | `compareTo(T o)` | `compare(T o1, T o2)` |
| Use case | One default sort | Multiple or dynamic sorts |
| Modifiable class? | Yes | No |

## ✅ `Comparable` Example

```java
class Person implements Comparable<Person> {
    String name;
    int age;
    
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    @Override
    public int compareTo(Person other) {
        return Integer.compare(this.age, other.age);
    }
}
```

## ✅ Sorting a List using `Comparable`:

```java
Collections.sort(list); // Uses compareTo()
```

## ✅ `Comparator` Cheatsheet

### 🔸 Basic Comparator

```java
Comparator<Person> ageComparator = new Comparator<Person>() {
    public int compare(Person p1, Person p2) {
        return p1.age - p2.age;
    }
};
```

### 🔸 Lambda (Java 8+)

```java
list.sort((a, b) -> a.age - b.age);
list.sort(Comparator.comparingInt(p -> p.age));
```

### 🔸 Reversed Order

```java
list.sort((a, b) -> b.age - a.age); // Manual
list.sort(Comparator.comparingInt(p -> p.age).reversed()); // Built-in
```

### 🔸 Multiple Fields Comparison

```java
list.sort(Comparator.comparing((Person p) -> p.age)
                   .thenComparing(p -> p.name));
```

### 🔸 Null Handling

```java
list.sort(Comparator.nullsFirst(Comparator.comparing(p -> p.age)));
list.sort(Comparator.nullsLast(Comparator.comparing(p -> p.age)));
```

### 🔸 Comparing Strings (Lexicographical)

```java
list.sort(Comparator.comparing(p -> p.name));
list.sort(Comparator.comparing(String::toLowerCase)); // Case-insensitive
```

### 🔸 Using Method References

```java
list.sort(Comparator.comparingInt(Person::getAge));
list.sort(Comparator.comparing(Person::getName));
```

## 🧠 Built-in Comparator Methods Summary

| Method | Purpose |
|--------|---------|
| `comparing(T::getX)` | Sort by field X |
| `comparingInt/Long/Double(...)` | Primitive sorting |
| `reversed()` | Reverse the order |
| `thenComparing(...)` | Tie-breaker sort |
| `nullsFirst(nullsLast(...))` | Handle nulls in sort |

## 🎯 Quick Rules

* Use `Comparable` when:
  * There's a **natural/default** way to sort objects.
  * You **own or can modify** the class.

* Use `Comparator` when:
  * You want **custom/multiple** sort strategies.
  * You **can't modify** the class or need dynamic sorting.
## Garbage Collection (GC)
* Java runs on the JVM, which uses Garbage Collection to automatically free up memory used by objects that are no longer needed.
```kotlin
              Java Heap
   ┌─────────────────────────────────────┐
   │                                     │
   │      🔹 Young Generation            │
   │       ┌────────┬────────┬────────┐  │
   │       │  Eden  │  S0    │   S1   │  │
   │       └────────┴────────┴────────┘  │
   │                                     │
   │      🔸 Old Generation              │
   │       ┌──────────────────────────┐  │
   │       │     Long-living Objects  │  │
   │       └──────────────────────────┘  │
   │                                     │
   └─────────────────────────────────────┘
```
* Eden: Where new objects are created. It fills up fast.
* Survivor Spaces (S0 and S1): After surviving a few collections, objects are moved here temporarily.
* Old Generation: Where long-living objects go (objects that survived multiple cycles).
- #### GC Types
  | Type      | What It Cleans      | Frequency        | Cost    | Pause  |
  |-----------|---------------------|------------------|---------|--------|
  | **Minor GC** | Young Gen only      | Happens often    | Fast    | Short  |
  | **Major GC** | Old Gen (and full heap) | Less frequent    | Slower  | Long   |

- **Minor GC**: 
    - Focuses on cleaning up the **Young Generation** (new objects).
    - **Happens frequently**, but is generally **fast** and has a **short pause**.
    - Occurs When Eden is full.
  
- **Major GC**: 
    - Involves cleaning up the **Old Generation** (long-lived objects) and sometimes the full heap.
    - **Occurs less frequently** but is **slower**, causing **longer pause times**.
    - When Old Generation is full OR explicitly triggered (System.gc()).

* During GC, JVM stops your application (all threads are paused). This is called a pause, and it varies:
   - Minor GC pause: short (milliseconds)
   - Major GC pause: can be longer (hundreds of ms or more)
* This is why GC tuning matters in low-latency apps.

* Garbage collector types
  | GC Type        | Best For                             | JVM Option                |
  |----------------|--------------------------------------|---------------------------|
  | **Serial GC**  | Small apps, single-threaded         | `-XX:+UseSerialGC`         |
  | **Parallel GC**| High throughput apps                | `-XX:+UseParallelGC`       |
  | **G1 GC**      | Balanced needs (default since Java 9) | `-XX:+UseG1GC`            |
  | **ZGC**        | Very low pause time, large heaps    | `-XX:+UseZGC`              |
  | **Shenandoah** | Low pause, concurrent                | `-XX:+UseShenandoahGC`     |

  - **Serial GC**: Ideal for **small applications** or **single-threaded environments**.
  - **Parallel GC**: Suitable for **high-throughput applications**, using multiple threads for garbage collection.
  - **G1 GC**: The default GC since **Java 9**, designed to provide **balanced performance** for **low-latency applications**.
  - **ZGC**: A **low-latency GC** suitable for **large heaps**, aiming for **very short pause times**.
  - **Shenandoah**: A GC focused on **low pause times** with a **concurrent** collection strategy.

* Garbage Collection Phases:
  - Mark Phase: The garbage collector identifies which objects are still reachable and which can be discarded.
  - Sweep Phase: Unused objects are removed from memory.
  - Compact Phase: The remaining objects are compacted to make space and reduce fragmentation.


* To use specific GC, we can use such below command
  ```
  java -Xms512m -Xmx1024m -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -Xlog:gc* -jar app.jar
  ```
  #### Conclusion
  Choosing the right GC for your application can significantly impact performance, especially in large-scale or latency-sensitive systems.
