


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


