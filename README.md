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


### Garbage Collection (GC)
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

  - ##### Garbage collector types
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
  #### Conclusion
  Choosing the right GC for your application can significantly impact performance, especially in large-scale or latency-sensitive systems.
