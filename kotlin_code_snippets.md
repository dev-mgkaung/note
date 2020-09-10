## Basic Type

```javascript

Every number type supports the following conversions:

toByte(): Byte
toShort(): Short
toInt(): Int
toLong(): Long
toFloat(): Float
toDouble(): Double
toChar(): Char

Built-in operations on booleans include

|| – lazy disjunction
&& – lazy conjunction
! - negation

Primitive type arrays

Kotlin also has specialized classes to represent arrays of primitive types without boxing overhead: ByteArray, ShortArray, IntArray and so on.

val x: IntArray = intArrayOf(1, 2, 3)
x[0] = x[1] + x[2]
// Array of int of size 5 with values [0, 0, 0, 0, 0]
val arr = IntArray(5)

// e.g. initialise the values in the array with a constant
// Array of int of size 5 with values [42, 42, 42, 42, 42]
val arr = IntArray(5) { 42 }

// e.g. initialise the values in the array using a lambda
// Array of int of size 5 with values [0, 1, 2, 3, 4] (values initialised to their index value)
var arr = IntArray(5) { it * 1 }

Break and Continue Labels

loop@ for (i in 1..100) {
    for (j in 1..100) {
        if (...) break@loop
    }
}

```


-----

## Properties and Fields

```python
Declaring Properties
Properties in Kotlin classes can be declared either as mutable using the var keyword, or as read-only using the val keyword.

class Address {
    var name: String = "Holmes, Sherlock"
    var street: String = "Baker"
    var city: String = "London"
    var state: String? = null
    var zip: String = "123456"
}

```
---

## Compile-Time Constants

```python
If the value of a read-only property is known at the compile time, mark it as a compile time constant using the const modifier. Such properties need to fulfil the following requirements:

Top-level, or member of an object declaration or a companion object.
Initialized with a value of type String or a primitive type
No custom getter
Such properties can be used in annotations:

const val SUBSYSTEM_DEPRECATED: String = "This subsystem is deprecated"
```
----

## Late-Initialized Properties and Variables
```python
Normally, properties declared as having a non-null type must be initialized in the constructor. However, fairly often this is not convenient. For example, properties can be initialized through dependency injection, or in the setup method of a unit test. In this case, you cannot supply a non-null initializer in the constructor, but you still want to avoid null checks when referencing the property inside the body of a class.

To handle this case, you can mark the property with the lateinit modifier:

public class MyTest {
    lateinit var subject: TestSubject
​
    @SetUp fun setup() {
        subject = TestSubject()
    }
​
    @Test fun test() {
        subject.method()  // dereference directly
    }
}

```

----

## Visibility Modifiers

```python
Classes, objects, interfaces, constructors, functions, properties and their setters can have visibility modifiers. (Getters always have the same visibility as the property.) There are four visibility modifiers in Kotlin: private, protected, internal and public. The default visibility, used if there is no explicit modifier, is public.

For members declared inside a class:

1. private _  means visible inside this class only (including all its members);
2. protected — same as private + visible in subclasses too;
3. internal — any client inside this module who sees the declaring class sees its internal members;
4. public — any client who sees the declaring class sees its public members.
```

---
 

# Control Flow: if, when, for, while

## When Expression

```javascript
val result = when( checkvalue)
{
0 -> println("0")
1,2 -> println("1,2")
in 3..5 -> println("3,4,5")
!in 6..8 -> println(" not contain 6,7,8 ")
parseInt(num) -> println(" num is int ")
in isValidateNum() -> println("validate")
is String -> checkvalue.startsWith("prefix")
else -> println("other wise default value")
}

```

```javascript
// The when expression replaces the switch statement in C-like languages. In the simplest form it looks like this
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> { // Note the block
        print("x is neither 1 nor 2")
    }
}
```

```javascript
//If many cases should be handled in the same way, the branch conditions may be combined with a comma:
when (x) {
    0, 1 -> print("x == 0 or x == 1")
    else -> print("otherwise")
}
```

```javascript
//We can use arbitrary expressions (not only constants) as branch conditions
when (x) {
    parseInt(s) -> print("s encodes x")
    else -> print("s does not encode x")
}
```

```javascript
//We can also check a value for being in or !in a range or a collection:
when (x) {
    in 1..10 -> print("x is in the range")
    in validNumbers -> print("x is valid")
    !in 10..20 -> print("x is outside the range")
    else -> print("none of the above")
}
```


```javascript
//Another possibility is to check that a value is or !is of a particular type. Note that, due to smart casts, you can access the methods and properties of the type without any extra checks.
fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("prefix")
    else -> false
}
```



```javascript
//when can also be used as a replacement for an if-else if chain. If no argument is supplied, the branch conditions are simply boolean expressions, and a branch is executed when its condition is true:
when {
    x.isOdd() -> print("x is odd")
    y.isEven() -> print("y is even")
    else -> print("x+y is even.")
}
```


```javascript
//it is possible to capture when subject in a variable using following syntax:
fun Request.getBody() =
        when (val response = executeRequest()) {
            is Success -> response.body
            is HttpError -> throw HttpException(response.status)
        }
```
       
      
---
## For loop

```javascript
for (item in Collections) println(item)
for ( index in 1..3) println(i)
for ( index in 10 downTo 0 step 2) println(index)
for ( index in arrays.indices) println ( array[index])
for ( (index, value) in arrays.withIndex()) println( "element at $index is $vlaue")
```

---

## Classes and Inheritance

```javascript

Classes in Kotlin are declared using the keyword class:
class Invoice { /*...*/ }

Class members
Classes can contain:

1. Constructors and initializer blocks
2. Functions
3. Properties
4. Nested and Inner Classes
5. Object Declarations

------

Constructors
A class in Kotlin can have a primary constructor and one or more secondary constructors. The primary constructor is part of the class header: it goes after the class name (and optional type parameters).

class Person constructor(firstName: String) { /*...*/ }


* If the primary constructor does not have any annotations or visibility modifiers, the constructor keyword can be omitted:

class Person(firstName: String) { /*...*/ }

 * The primary constructor cannot contain any code. Initialization code can be placed in initializer blocks, which are prefixed with the init keyword.

class InitOrderDemo(name: String) {
    val firstProperty = "First property: $name".also(::println)
    
    init {
        println("First initializer block that prints ${name}")
    }
    
    val secondProperty = "Second property: ${name.length}".also(::println)
    
    init {
        println("Second initializer block that prints ${name.length}")
    }
}

----

class Person(val firstName: String, val lastName: String, var age: Int) { /*...*/ }


* Secondary constructors
The class can also declare secondary constructors, which are prefixed with constructor

class Person {
    var children: MutableList<Person> = mutableListOf<>()
    constructor(parent: Person) {
        parent.children.add(this)
    }
}

class Person(val name: String) {
    var children: MutableList<Person> = mutableListOf<>()
    constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
    }
}

class Constructors {
    init {
        println("Init block")
    }

    constructor(i: Int) {
        println("Constructor")
    }
}
```

---

## Inheritance

```javascript
All classes in Kotlin have a common superclass Any, that is the default superclass for a class with no supertypes declared:
class Example // Implicitly inherits from Any

Any has three methods: equals(), hashCode() and toString()
By default, Kotlin classes are final: they can’t be inherited. To make a class inheritable, mark it with the open keyword.
open class Base //Class is open for inheritance


open class Base(p: Int)
class Derived(p: Int) : Base(p)

class MyView : View {
    constructor(ctx: Context) : super(ctx)

    constructor(ctx: Context, attrs: AttributeSet) : super(ctx, attrs)
}

* Overriding methods
open class Shape {
    open fun draw() { /*...*/ }
    fun fill() { /*...*/ }
}

class Circle() : Shape() {
    override fun draw() { /*...*/ }
}


* Overriding properties
open class Shape {
    open val vertexCount: Int = 0
}

class Rectangle : Shape() {
    override val vertexCount = 4
}



interface Shape {
    val vertexCount: Int
}

class Rectangle(override val vertexCount: Int = 4) : Shape // Always has 4 vertices

class Polygon : Shape {
    override var vertexCount: Int = 0  // Can be set to any number later
}
```

---

## Abstract classes
```javascript
A class and some of its members may be declared abstract. An abstract member does not have an implementation in its class. Note that we do not need to annotate an abstract class or function with open – it goes without saying.

We can override a non-abstract open member with an abstract one

open class Polygon {
    open fun draw() {}
}
​
abstract class Rectangle : Polygon() {
    abstract override fun draw()
}
```
---


##  Interfaces

```python

nterfaces in Kotlin can contain declarations of abstract methods, as well as method implementations. What makes them different from abstract classes is that interfaces cannot store state. They can have properties but these need to be abstract or to provide accessor implementations.

An interface is defined using the keyword interface

interface MyInterface {
    fun bar()
    fun foo() {
      // optional body
    }
}

* Implementing Interfaces
A class or object can implement one or more interfaces

class Child : MyInterface {
    override fun bar() {
        // body
    }
}


 * Properties in Interfaces
ou can declare properties in interfaces. A property declared in an interface can either be abstract, or it can provide implementations for accessors. Properties declared in interfaces can't have backing fields, and therefore accessors declared in interfaces can't reference them.

interface MyInterface {
    val prop: Int // abstract

    val propertyWithImplementation: String
        get() = "foo"

    fun foo() {
        print(prop)
    }
}

class Child : MyInterface {
    override val prop: Int = 29
}

 * Interfaces Inheritance
An interface can derive from other interfaces and thus both provide implementations for their members and declare new functions and properties. Quite naturally, classes implementing such an interface are only required to define the missing implementations:

interface Named {
    val name: String
}

interface Person : Named {
    val firstName: String
    val lastName: String
    
    override val name: String get() = "$firstName $lastName"
}

data class Employee(
    // implementing 'name' is not required
    override val firstName: String,
    override val lastName: String,
    val position: Position
) : Person



 * Resolving overriding conflicts
When we declare many types in our supertype list, it may appear that we inherit more than one implementation of the same method. For example

interface A {
    fun foo() { print("A") }
    fun bar()
}

interface B {
    fun foo() { print("B") }
    fun bar() { print("bar") }
}

class C : A {
    override fun bar() { print("bar") }
}

class D : A, B {
    override fun foo() {
        super<A>.foo()
        super<B>.foo()
    }

    override fun bar() {
        super<B>.bar()
    }
}
```
----


## Extensions

Kotlin provides the ability to extend a class with new functionality without having to inherit from the class or use design patterns such as Decorator. This is done via special declarations called extensions. 

```python
Extension functions
To declare an extension function, we need to prefix its name with a receiver type, i.e. the type being extended. The following adds a swap function to MutableList<Int>:

fun MutableList<Int>.swap(index1: Int, index2: Int) {
    val tmp = this[index1] // 'this' corresponds to the list
    this[index1] = this[index2]
    this[index2] = tmp
}
fun MutableList<Int>.swap(index1: Int, index2: Int) {
    val tmp = this[index1] // 'this' corresponds to the list
    this[index1] = this[index2]
    this[index2] = tmp
}

===

val list = mutableListOf(1, 2, 3)
list.swap(0, 2) // 'this' inside 'swap()' will hold the value of 'list'


* Companion object extensions
If a class has a companion object defined, you can also define extension functions and properties for the companion object. Just like regular members of the companion object, they can be called using only the class name as the qualifier:

class MyClass {
    companion object { }  // will be called "Companion"
}
​
fun MyClass.Companion.printCompanion() { println("companion") }
​
fun main() {
    MyClass.printCompanion()
}

* Scope of extensions
Most of the time we define extensions on the top level - directly under packages:

package org.example.declarations
 
fun List<String>.getLongestString() { /*...*/}
To use such an extension outside its declaring package, we need to import it at the call site:

package org.example.usage
​
import org.example.declarations.getLongestString
​
fun main() {
    val list = listOf("red", "green", "blue")
    list.getLongestString()
}

```

----

## Data Classes
We frequently create classes whose main purpose is to hold data. In such a class some standard functionality and utility functions are often mechanically derivable from the data. In Kotlin, this is called a data class and is marked as data:

```python
data class User(val name: String, val age: Int)
data class User(val name: String = "", val age: Int = 0)

* Properties Declared in the Class Body
Note that the compiler only uses the properties defined inside the primary constructor for the automatically generated functions. To exclude a property from the generated implementations, declare it inside the class body:

data class Person(val name: String) {
    var age: Int = 0
}

val person1 = Person("John")
val person2 = Person("John")
person1.age = 10
person2.age = 20
```
---

## Sealed Classes
Sealed classes are used for representing restricted class hierarchies, when a value can have one of the types from a limited set, but cannot have any other type. They are, in a sense, an extension of enum classes: the set of values for an enum type is also restricted, but each enum constant exists only as a single instance, whereas a subclass of a sealed class can have multiple instances which can contain state.

```python
sealed class Expr
data class Const(val number: Double) : Expr()
data class Sum(val e1: Expr, val e2: Expr) : Expr()
object NotANumber : Expr()

```
---

# Nested and Inner Classes

```python
Classes can be nested in other classes:

class Outer {
    private val bar: Int = 1
    class Nested {
        fun foo() = 2
    }
}
​
val demo = Outer.Nested().foo() // == 2

```
---

## Inner classes
A nested class marked as inner can access the members of its outer class. Inner classes carry a reference to an object of an outer class:

```python
class Outer {
    private val bar: Int = 1
    inner class Inner {
        fun foo() = bar
    }
}

val demo = Outer().Inner().foo() // == 1
```

----

## Anonymous inner classes

```python
Anonymous inner class instances are created using an object expression:

window.addMouseListener(object : MouseAdapter() {
​
    override fun mouseClicked(e: MouseEvent) { ... }
​
    override fun mouseEntered(e: MouseEvent) { ... }
})


val listener = ActionListener { println("clicked") }
```
---


## Enum Classes

```python
The most basic usage of enum classes is implementing type-safe enums:

enum class Direction {
    NORTH, SOUTH, WEST, EAST
}
Each enum constant is an object. Enum constants are separated with commas.

* Initialization
Since each enum is an instance of the enum class, they can be initialized as:

enum class Color(val rgb: Int) {
        RED(0xFF0000),
        GREEN(0x00FF00),
        BLUE(0x0000FF)
}
enum class Color(val rgb: Int) {
        RED(0xFF0000),
        GREEN(0x00FF00),
        BLUE(0x0000FF)
}

```
----


## Object Expressions and Declarations
Sometimes we need to create an object of a slight modification of some class, without explicitly declaring a new subclass for it. Kotlin handles this case with object expressions and object declarations.

```python
Object declarations
Singleton may be useful in several cases, and Kotlin (after Scala) makes it easy to declare singletons:

object DataProviderManager {
    fun registerDataProvider(provider: DataProvider) {
        // ...
    }

    val allDataProviders: Collection<DataProvider>
        get() = // ...
}
```
---

## Companion Objects
An object declaration inside a class can be marked with the companion keyword:
```python

class MyClass {
    companion object Factory {
        fun create(): MyClass = MyClass()
    }
}



Members of the companion object can be called by using simply the class name as the qualifier:

val instance = MyClass.create()
The name of the companion object can be omitted, in which case the name Companion will be used:

class MyClass {
    companion object { }
}
​
val x = MyClass.Companion




* The name of a class used by itself (not as a qualifier to another name) acts as a reference to the companion object of the class (whether named or not):

class MyClass1 {
    companion object Named { }
}

val x = MyClass1

class MyClass2 {
    companion object { }
}

val y = MyClass2
class MyClass1 {
    companion object Named { }
}
​
val x = MyClass1
​
class MyClass2 {
    companion object { }
}
​
val y = MyClass2




* Note that, even though the members of companion objects look like static members in other languages, at runtime those are still instance members of real objects, and can, for 
example, implement interfaces:

interface Factory<T> {
    fun create(): T
}

class MyClass {
    companion object : Factory<MyClass> {
        override fun create(): MyClass = MyClass()
    }
}

val f: Factory<MyClass> = MyClass
interface Factory<T> {
    fun create(): T
}
​
class MyClass {
    companion object : Factory<MyClass> {
        override fun create(): MyClass = MyClass()
    }
}
​
val f: Factory<MyClass> = MyClass


Semantic difference between object expressions and declarations
There is one important semantic difference between object expressions and object declarations:

1. object expressions are executed (and initialized) immediately, where they are used;
2. object declarations are initialized lazily, when accessed for the first time;
3. a companion object is initialized when the corresponding class is loaded (resolved), matching the semantics of a Java static initializer.
```
---


## Delegation
Property Delegation
Delegated properties are described on a separate page: Delegated Properties.

```python

Implementation by Delegation
The Delegation pattern has proven to be a good alternative to implementation inheritance, and Kotlin supports it natively requiring zero boilerplate code. A class Derived can implement an interface Base by delegating all of its public members to a specified object:

interface Base {
    fun print()
}
​
class BaseImpl(val x: Int) : Base {
    override fun print() { print(x) }
}
​
class Derived(b: Base) : Base by b
​
fun main() {
    val b = BaseImpl(10)
    Derived(b).print()
}


The by-clause in the supertype list for Derived indicates that b will be stored internally in objects of Derived and the compiler will generate all the methods of Base that forward to b.

Overriding a member of an interface implemented by delegation
Overrides work as you might expect: the compiler will use your override implementations instead of those in the delegate object. If we were to add override fun printMessage() { print("abc") } to Derived, the program would print "abc" instead of "10" when printMessage is called:

interface Base {
    fun printMessage()
    fun printMessageLine()
}
​
class BaseImpl(val x: Int) : Base {
    override fun printMessage() { print(x) }
    override fun printMessageLine() { println(x) }
}
​
class Derived(b: Base) : Base by b {
    override fun printMessage() { print("abc") }
}
​
fun main() {
    val b = BaseImpl(10)
    Derived(b).printMessage()
    Derived(b).printMessageLine()



Note, however, that members overridden in this way do not get called from the members of the delegate object, which can only access its own implementations of the interface members:

interface Base {
    val message: String
    fun print()
}
​
class BaseImpl(val x: Int) : Base {
    override val message = "BaseImpl: x = $x"
    override fun print() { println(message) }
}
​
class Derived(b: Base) : Base by b {
    // This property is not accessed from b's implementation of `print`
    override val message = "Message of Derived"
}
​
fun main() {
    val b = BaseImpl(10)
    val derived = Derived(b)
    derived.print()
    println(derived.message)
}
```
---

## Delegated Properties
There are certain common kinds of properties, that, though we can implement them manually every time we need them, would be very nice to implement once and for all, and put into a library. Examples include:

lazy properties: the value gets computed only upon first access;
observable properties: listeners get notified about changes to this property;
storing properties in a map, instead of a separate field for each property.
To cover these (and other) cases, Kotlin supports delegated properties:

```python
class Example {
    var p: String by Delegate()
}
```

Standard delegates
The Kotlin standard library provides factory methods for several useful kinds of delegates.

### Lazy
lazy() is a function that takes a lambda and returns an instance of Lazy<T> which can serve as a delegate for implementing a lazy property: the first call to get() executes the lambda passed to lazy() and remembers the result, subsequent calls to get() simply return the remembered result.
    
 ```python
    
    val lazyValue: String by lazy {
    println("computed!")
    "Hello"
    }

fun main() {
    println(lazyValue)
    println(lazyValue)
}

```
---

## Functions
Function declarations
Functions in Kotlin are declared using the fun keyword:

```python
fun double(x: Int): Int {
    return 2 * x
}
fun powerOf(number: Int, exponent: Int) { /*...*/ }

Default arguments
fun read(b: Array<Byte>, off: Int = 0, len: Int = b.size) { /*...*/ }

```
Named arguments
```python
fun reformat(
    str: String,
    normalizeCase: Boolean = true,
    upperCaseFirstLetter: Boolean = true,
    divideByCamelHumps: Boolean = false,
    wordSeparator: Char = ' ') {
/*...*/
}


When calling this function, you don’t have to name all its arguments:

reformat(
    'String!',
    false,
    upperCaseFirstLetter = false,
    divideByCamelHumps = true,
    '_'
)

You can skip all arguments with default values:

reformat('This is a long String!')

You can skip some arguments with default values. However, after the first skipped argument, you must name all subsequent arguments:

reformat('This is a short String!', upperCaseFirstLetter = false, wordSeparator = '_')
```


## Unit-returning functions
If a function does not return any useful value, its return type is Unit. Unit is a type with only one value - Unit. This value does not have to be returned explicitly:

```python
fun printHello(name: String?): Unit {
    if (name != null)
        println("Hello $name")
    else
        println("Hi there!")
    // `return Unit` or `return` is optional
}

The Unit return type declaration is also optional. The above code is equivalent to:

fun printHello(name: String?) { ... }
fun printHello(name: String?) { ... }

````
Single-expression functions

```python
When a function returns a single expression, the curly braces can be omitted and the body is specified after a = symbol:

fun double(x: Int): Int = x * 2
Explicitly declaring the return type is optional when this can be inferred by the compiler:

fun double(x: Int) = x * 2

```

Generic functions
Functions can have generic parameters which are specified using angle brackets before the function name:

```python
fun <T> singletonList(item: T): List<T> { /*...*/ }
```
---

## Lambda expression syntax
The full syntactic form of lambda expressions is as follows:

```python
val sum: (Int, Int) -> Int = { x: Int, y: Int -> x + y }



Instantiating a function type
There are several ways to obtain an instance of a function type:

Using a code block within a function literal, in one of the forms:
a lambda expression: { a, b -> a + b },
an anonymous function: fun(s: String): Int { return s.toIntOrNull() ?: 0 }
Function literals with receiver can be used as values of function types with receiver.

Using a callable reference to an existing declaration:
a top-level, local, member, or extension function: ::isOdd, String::toInt,
a top-level, member, or extension property: List<Int>::size,
a constructor: ::Regex
```

---

## Kotlin Collections Overview

1. List is an ordered collection with access to elements by indices – integer numbers that reflect their position. Elements can occur more than once in a list. An example of a list is a sentence: it's a group of words, their order is important, and they can repeat.

2. Set is a collection of unique elements. It reflects the mathematical abstraction of set: a group of objects without repetitions. Generally, the order of set elements has no significance. For example, an alphabet is a set of letters.

3. Map (or dictionary) is a set of key-value pairs. Keys are unique, and each of them maps to exactly one value. The values can be duplicates. Maps are useful for storing logical connections between objects, for example, an employee's ID and their position.

# List

```python
val numbers = listOf("one", "two", "three", "four")
println("Number of elements: ${numbers.size}")
println("Third element: ${numbers.get(2)}")
println("Fourth element: ${numbers[3]}")


MutableList

val numbers = mutableListOf(1, 2, 3, 4)
numbers.add(5)
numbers.removeAt(1)
numbers[0] = 0
numbers.shuffle()
println(numbers)
```

# Set

```python
val numbers = setOf(1, 2, 3, 4)
println("Number of elements: ${numbers.size}")
if (numbers.contains(1)) println("1 is in the set")

val numbersBackwards = setOf(4, 3, 2, 1)
println("The sets are equal: ${numbers == numbersBackwards}")

MutableSet
val numbers = setOf(1, 2, 3, 4)  // LinkedHashSet is the default implementation
val numbersBackwards = setOf(4, 3, 2, 1)

println(numbers.first() == numbersBackwards.first())
println(numbers.first() == numbersBackwards.last())
```

# Map

```python

val numbersMap = mapOf("key1" to 1, "key2" to 2, "key3" to 3, "key4" to 1)

println("All keys: ${numbersMap.keys}")
println("All values: ${numbersMap.values}")
if ("key2" in numbersMap) println("Value by key \"key2\": ${numbersMap["key2"]}")    
if (1 in numbersMap.values) println("The value 1 is in the map")
if (numbersMap.containsValue(1)) println("The value 1 is in the map") // same as previous


MutableMap

val numbersMap = mutableMapOf("one" to 1, "two" to 2)
numbersMap.put("three", 3)
numbersMap["one"] = 11

println(numbersMap)
```
---
