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
Classes
Classes in Kotlin are declared using the keyword class:
class Invoice { /*...*/ }

Class members
Classes can contain:

Constructors and initializer blocks
Functions
Properties
Nested and Inner Classes
Object Declarations

Constructors
A class in Kotlin can have a primary constructor and one or more secondary constructors. The primary constructor is part of the class header: it goes after the class name (and optional type parameters).

class Person constructor(firstName: String) { /*...*/ }

If the primary constructor does not have any annotations or visibility modifiers, the constructor keyword can be omitted:

class Person(firstName: String) { /*...*/ }

The primary constructor cannot contain any code. Initialization code can be placed in initializer blocks, which are prefixed with the init keyword.

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


class Person(val firstName: String, val lastName: String, var age: Int) { /*...*/ }

Secondary constructors
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

Overriding methods
open class Shape {
    open fun draw() { /*...*/ }
    fun fill() { /*...*/ }
}

class Circle() : Shape() {
    override fun draw() { /*...*/ }
}

 Edit Page
Classes and Inheritance
Classes
Classes in Kotlin are declared using the keyword class:

class Invoice { /*...*/ }
class Invoice { /*...*/ }
The class declaration consists of the class name, the class header (specifying its type parameters, the primary constructor etc.) and the class body, surrounded by curly braces. Both the header and the body are optional; if the class has no body, curly braces can be omitted.

class Empty
Constructors
A class in Kotlin can have a primary constructor and one or more secondary constructors. The primary constructor is part of the class header: it goes after the class name (and optional type parameters).

class Person constructor(firstName: String) { /*...*/ }
class Person constructor(firstName: String) { /*...*/ }
If the primary constructor does not have any annotations or visibility modifiers, the constructor keyword can be omitted:

class Person(firstName: String) { /*...*/ }
class Person(firstName: String) { /*...*/ }
The primary constructor cannot contain any code. Initialization code can be placed in initializer blocks, which are prefixed with the init keyword.

During an instance initialization, the initializer blocks are executed in the same order as they appear in the class body, interleaved with the property initializers:

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
Target platform: JVMRunning on kotlin v. 1.4.0
Note that parameters of the primary constructor can be used in the initializer blocks. They can also be used in property initializers declared in the class body:

class Customer(name: String) {
    val customerKey = name.toUpperCase()
}
In fact, for declaring properties and initializing them from the primary constructor, Kotlin has a concise syntax:

class Person(val firstName: String, val lastName: String, var age: Int) { /*...*/ }
class Person(val firstName: String, val lastName: String, var age: Int) { /*...*/ }
Much the same way as regular properties, the properties declared in the primary constructor can be mutable (var) or read-only (val).

If the constructor has annotations or visibility modifiers, the constructor keyword is required, and the modifiers go before it:

class Customer public @Inject constructor(name: String) { /*...*/ }
For more details, see Visibility Modifiers.

Secondary constructors
The class can also declare secondary constructors, which are prefixed with constructor:

class Person {
    var children: MutableList<Person> = mutableListOf<>()
    constructor(parent: Person) {
        parent.children.add(this)
    }
}
class Person {
    var children: MutableList<Person> = mutableListOf<>()
    constructor(parent: Person) {
        parent.children.add(this)
    }
}
If the class has a primary constructor, each secondary constructor needs to delegate to the primary constructor, either directly or indirectly through another secondary constructor(s). Delegation to another constructor of the same class is done using the this keyword:

class Person(val name: String) {
    var children: MutableList<Person> = mutableListOf<>()
    constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
    }
}
class Person(val name: String) {
    var children: MutableList<Person> = mutableListOf<>()
    constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
    }
}
Note that code in initializer blocks effectively becomes part of the primary constructor. Delegation to the primary constructor happens as the first statement of a secondary constructor, so the code in all initializer blocks and property initializers is executed before the secondary constructor body. Even if the class has no primary constructor, the delegation still happens implicitly, and the initializer blocks are still executed:

class Constructors {
    init {
        println("Init block")
    }

    constructor(i: Int) {
        println("Constructor")
    }
}
class Constructors {
    init {
        println("Init block")
    }
​
    constructor(i: Int) {
        println("Constructor")
    }
}
Target platform: JVMRunning on kotlin v. 1.4.0
If a non-abstract class does not declare any constructors (primary or secondary), it will have a generated primary constructor with no arguments. The visibility of the constructor will be public. If you do not want your class to have a public constructor, you need to declare an empty primary constructor with non-default visibility:

class DontCreateMe private constructor () { /*...*/ }
NOTE: On the JVM, if all of the parameters of the primary constructor have default values, the compiler will generate an additional parameterless constructor which will use the default values. This makes it easier to use Kotlin with libraries such as Jackson or JPA that create class instances through parameterless constructors.

class Customer(val customerName: String = "")
Creating instances of classes
To create an instance of a class, we call the constructor as if it were a regular function:

val invoice = Invoice()
​
val customer = Customer("Joe Smith")
Note that Kotlin does not have a new keyword.

Creating instances of nested, inner and anonymous inner classes is described in Nested classes.

Class members
Classes can contain:

Constructors and initializer blocks
Functions
Properties
Nested and Inner Classes
Object Declarations
Inheritance
All classes in Kotlin have a common superclass Any, that is the default superclass for a class with no supertypes declared:

class Example // Implicitly inherits from Any
class Example // Implicitly inherits from Any
Any has three methods: equals(), hashCode() and toString(). Thus, they are defined for all Kotlin classes.

By default, Kotlin classes are final: they can’t be inherited. To make a class inheritable, mark it with the open keyword.

open class Base //Class is open for inheritance
open class Base //Class is open for inheritance
To declare an explicit supertype, place the type after a colon in the class header:

open class Base(p: Int)

class Derived(p: Int) : Base(p)
open class Base(p: Int)
​
class Derived(p: Int) : Base(p)
If the derived class has a primary constructor, the base class can (and must) be initialized right there, using the parameters of the primary constructor.

If the derived class has no primary constructor, then each secondary constructor has to initialize the base type using the super keyword, or to delegate to another constructor which does that. Note that in this case different secondary constructors can call different constructors of the base type:

class MyView : View {
    constructor(ctx: Context) : super(ctx)

    constructor(ctx: Context, attrs: AttributeSet) : super(ctx, attrs)
}
class MyView : View {
    constructor(ctx: Context) : super(ctx)
​
    constructor(ctx: Context, attrs: AttributeSet) : super(ctx, attrs)
}
Overriding methods
As we mentioned before, we stick to making things explicit in Kotlin. So, Kotlin requires explicit modifiers for overridable members (we call them open) and for overrides:

open class Shape {
    open fun draw() { /*...*/ }
    fun fill() { /*...*/ }
}

class Circle() : Shape() {
    override fun draw() { /*...*/ }
}
open class Shape {
    open fun draw() { /*...*/ }
    fun fill() { /*...*/ }
}
​
class Circle() : Shape() {
    override fun draw() { /*...*/ }
}
The override modifier is required for Circle.draw(). If it were missing, the compiler would complain. If there is no open modifier on a function, like Shape.fill(), declaring a method with the same signature in a subclass is illegal, either with override or without it. The open modifier has no effect when added on members of a final class (i.e.. a class with no open modifier).

A member marked override is itself open, i.e. it may be overridden in subclasses. If you want to prohibit re-overriding, use final:

open class Rectangle() : Shape() {
    final override fun draw() { /*...*/ }
}
Overriding properties
open class Shape {
    open val vertexCount: Int = 0
}

class Rectangle : Shape() {
    override val vertexCount = 4
}

Note that you can use the override keyword as part of the property declaration in a primary constructor.

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
