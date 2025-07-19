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
```java
// ========== PRIMITIVE TYPES & WRAPPER CLASSES ==========
/*
byte    → Byte       (-128 to 127)
short   → Short      (-32,768 to 32,767)
int     → Integer    (-2^31 to 2^31-1)
long    → Long       (-2^63 to 2^63-1)
float   → Float      (32-bit IEEE 754)
double  → Double     (64-bit IEEE 754)
char    → Character  (16-bit Unicode)
boolean → Boolean    (true/false)
*/

// ========== AUTOBOXING / UNBOXING ==========
int x = 5;
Integer y = x;        // Autoboxing: primitive → wrapper
int z = y;            // Unboxing: wrapper → primitive

// Integer cache: -128 to 127 are cached (same object reference)
Integer a = 127, b = 127;  // a == b → true (same object)
Integer c = 128, d = 128;  // c == d → false (different objects)

// ========== CHAR ↔ INT / ASCII CONVERSIONS ==========
char c = 'a';
int ascii = c;                    // 97 (ASCII value)
char d = (char) (ascii + 1);      // 'b'
char upper = (char) (c - 32);     // 'A' (manual case conversion)

// Common ASCII ranges
// 'A'-'Z' → 65-90, 'a'-'z' → 97-122, '0'-'9' → 48-57

// ========== CHARACTER UTILITIES ==========
Character.isDigit('5');           // true
Character.isLetter('a');          // true
Character.isAlphabetic('α');      // true (Unicode letters)
Character.isWhitespace(' ');      // true
Character.toUpperCase('b');       // 'B'
Character.toLowerCase('D');       // 'd'
Character.getNumericValue('7');   // 7 (digit to int)

// ========== CHAR ↔ STRING CONVERSIONS ==========
char ch = 'a';
String s = String.valueOf(ch);    // "a"
String s2 = Character.toString(ch); // "a" (alternative)
char c = "hello".charAt(0);       // 'h'

// String to char array
char[] chars = "abc".toCharArray();
String back = new String(chars);

// ========== INTEGER METHODS & UTILITIES ==========
// Parsing & Conversion
Integer.parseInt("123");          // 123
Integer.parseInt("FF", 16);       // 255 (hex)
Integer.parseInt("1010", 2);      // 10 (binary)
String.valueOf(123);              // "123"
Integer.toString(123, 16);        // "7b" (hex)

// Bit Operations
Integer.bitCount(5);              // 2 (number of 1-bits)
Integer.toBinaryString(5);        // "101"
Integer.toHexString(255);         // "ff"
Integer.highestOneBit(10);        // 8 (highest power of 2 ≤ n)
Integer.lowestOneBit(10);         // 2 (lowest set bit)
Integer.numberOfLeadingZeros(4);  // 29
Integer.reverse(0x12345678);      // Reverse bits

// Constants
Integer.MAX_VALUE;                // 2147483647
Integer.MIN_VALUE;                // -2147483648
Integer.SIZE;                     // 32 (bits)

// ========== EQUALITY & IDENTITY ==========
Integer x = 128, y = 128;
x == y;           // false (different objects, outside cache)
x.equals(y);      // true (value comparison)

int a = 128, b = 128;
a == b;           // true (primitive comparison)

// Safe comparison
Objects.equals(x, y);  // true (null-safe)

// ========== SORTING ARRAYS ==========
// Primitive arrays
int[] nums = {3, 1, 4};
Arrays.sort(nums);                // [1, 3, 4]

// Char arrays (lexicographical)
char[] chars = {'c', 'a', 'b'};
Arrays.sort(chars);               // ['a', 'b', 'c']

// Wrapper arrays (with custom comparators)
Integer[] arr = {3, 1, 4};
Arrays.sort(arr);                             // [1, 3, 4]
Arrays.sort(arr, Collections.reverseOrder()); // [4, 3, 1]
Arrays.sort(arr, (a, b) -> b - a);           // [4, 3, 1] (lambda)

// Partial sorting
Arrays.sort(arr, 0, 2);           // Sort only first 2 elements

// ========== FREQUENCY COUNTING ==========
// Character frequency (lowercase a-z)
int[] freq = new int[26];
String text = "hello";
for (char c : text.toCharArray()) {
    freq[c - 'a']++;
}

// All ASCII characters
int[] asciiFreq = new int[128];
for (char c : text.toCharArray()) {
    asciiFreq[c]++;
}

// Using HashMap for any character
Map<Character, Integer> charCount = new HashMap<>();
for (char c : text.toCharArray()) {
    charCount.put(c, charCount.getOrDefault(c, 0) + 1);
}

// ========== DIGIT ↔ CHAR CONVERSIONS ==========
// Digit to char
int digit = 5;
char c = (char) ('0' + digit);    // '5'

// Char to digit
char ch = '8';
int d = ch - '0';                 // 8

// Handle hex digits
char hexChar = 'A';
int hexValue = Character.digit(hexChar, 16);  // 10

// ========== NULL SAFETY ==========
Integer nullable = null;
if (nullable != null) {
    int value = nullable;         // Safe unboxing
}

// Using Optional for null safety
Optional.ofNullable(nullable)
    .ifPresent(val -> System.out.println(val));

// Default values
int safe = nullable != null ? nullable : 0;  // Ternary
int safer = Objects.requireNonNullElse(nullable, 0);  // Java 9+

// ========== ADVANCED TRICKS ==========
// Fast digit extraction
int num = 12345;
while (num > 0) {
    int digit = num % 10;         // Extract last digit
    num /= 10;                    // Remove last digit
}

// Fast power of 2 check
boolean isPowerOf2 = (n > 0) && ((n & (n - 1)) == 0);

// Swap without temp variable
int a = 5, b = 10;
a = a ^ b; b = a ^ b; a = a ^ b;  // Now a=10, b=5

// Fast multiplication/division by powers of 2
int doubled = n << 1;             // n * 2
int halved = n >> 1;              // n / 2
int times8 = n << 3;              // n * 8

// Count digits in number
int digitCount = String.valueOf(Math.abs(num)).length();
// Or: int digitCount = (int) Math.log10(Math.abs(num)) + 1;

// ========== SUMMARY TABLE ==========
/*
┌─────────────────┬──────────────────────────────────────┐
│ Operation       │ Code                                 │
├─────────────────┼──────────────────────────────────────┤
│ ASCII           │ (int) c, (char) (x + 'a')           │
│ Digit ↔ Char    │ '0' + d, c - '0'                     │
│ Int ↔ String    │ String.valueOf(i), parseInt(s)       │
│ Sort            │ Arrays.sort(arr)                     │
│ Reverse Sort    │ Arrays.sort(arr, Collections.rev())  │
│ Freq Count      │ freq[c - 'a']++                      │
│ Set Bits        │ Integer.bitCount(x)                  │
│ Binary          │ toBinaryString(x)                    │
│ Hex             │ toHexString(x)                       │
│ Power of 2      │ (n & (n-1)) == 0                     │
│ Safe Unbox      │ obj != null ? obj : default          │
└─────────────────┴──────────────────────────────────────┘
*/
```

## Comparable & Comparator.
```java
// ========== COMPARABLE ==========
// Use when: Natural ordering, can modify class, single sort strategy
class Person implements Comparable<Person> {
    String name;
    int age;
    
    @Override
    public int compareTo(Person other) {
        return Integer.compare(this.age, other.age); // Natural order by age
    }
}

// Usage: Collections.sort(list); // Uses compareTo()

// ========== COMPARATOR ==========
// Use when: Custom ordering, can't modify class, multiple sort strategies

// 1. Anonymous Class
Comparator<Person> ageComp = new Comparator<Person>() {
    public int compare(Person p1, Person p2) { return p1.age - p2.age; }
};

// 2. Lambda Expressions (Java 8+)
list.sort((a, b) -> a.age - b.age);                    // Manual comparison
list.sort(Comparator.comparingInt(p -> p.age));        // Built-in method

// 3. Method References
list.sort(Comparator.comparingInt(Person::getAge));    // Cleaner syntax

// 4. Reversed Order
list.sort(Comparator.comparingInt(p -> p.age).reversed());

// 5. Multiple Fields (Chaining)
list.sort(Comparator.comparing((Person p) -> p.age)
                   .thenComparing(p -> p.name));

// 6. Null Handling
list.sort(Comparator.nullsFirst(Comparator.comparing(p -> p.age)));
list.sort(Comparator.nullsLast(Comparator.comparing(p -> p.age)));

// 7. String Comparison
list.sort(Comparator.comparing(p -> p.name));              // Case-sensitive
list.sort(Comparator.comparing(p -> p.name.toLowerCase())); // Case-insensitive

// ========== QUICK REFERENCE ==========
/*
COMPARABLE:
- Interface: Comparable<T> (java.lang)
- Method: compareTo(T o)
- Returns: negative, 0, positive
- Usage: One natural ordering per class

COMPARATOR:
- Interface: Comparator<T> (java.util)
- Method: compare(T o1, T o2)
- Returns: negative, 0, positive
- Usage: Multiple custom orderings

KEY METHODS:
- comparing(Function)        - Sort by field
- comparingInt/Long/Double() - Primitive types
- reversed()                 - Reverse order
- thenComparing()           - Secondary sort
- nullsFirst/Last()         - Handle nulls
*/
```



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
