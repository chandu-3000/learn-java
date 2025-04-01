# Learn JAVA

# Links
* [Learn Collection framework](https://github.com/AnirudhDas/AniruddhaDas.github.io/blob/master/Java/CollectionFrameworkInJava/CollectionFrameworkInJava.md)
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

