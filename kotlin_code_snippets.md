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


Overriding properties
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
