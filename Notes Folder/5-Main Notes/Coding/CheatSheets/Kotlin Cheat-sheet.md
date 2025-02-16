

2025-01-25 10:16

Tags:

# Kotlin Cheat Sheet

---

## **1. Basics**

### **Hello World**

```kotlin
fun main() {
    println("Hello, World!")
}
```

### **Comments**

- Single-line: `// This is a comment`
- Multi-line: `/* This is a
   multi-line comment */`

### **Variables**

```kotlin
val x: Int = 10  // Immutable variable
var y: String = "Kotlin"  // Mutable variable

val z = 42       // Type inference
```

### **Basic Types**

- `Int`: Integer
- `Double`: Double-precision floating-point
- `Float`: Single-precision floating-point
- `Char`: Single character
- `Boolean`: `true` or `false`
- `String`: Text values

---

## **2. Control Flow**

### **If-Else**

```kotlin
fun max(a: Int, b: Int): Int {
    return if (a > b) a else b
}
```

### **When Expression**

```kotlin
fun describe(x: Any): String = when (x) {
    1 -> "One"  // Matches if x is the integer 1
    "Hello" -> "Greeting"  // Matches if x is the string "Hello"
    is Long -> "Long number"  // Matches if x is of type Long
    !is String -> "Not a string"  // Matches if x is NOT of type String
    else -> "Unknown"  // Default case for all other values
}
```

---

## **3. Loops**

### **For Loop**

```kotlin
for (i in 1..5) {
    println(i)  // Prints 1 to 5
}

for (i in 1 until 5) {
    println(i)  // Prints 1 to 4
}

for (i in 5 downTo 1 step 2) {
    println(i)  // Prints 5, 3, 1
}
```

### **While Loop**

```kotlin
var i = 0
while (i < 5) {
    println(i)
    i++
}
```

### **Do-While Loop**

```kotlin
var i = 0
do {
    println(i)
    i++
} while (i < 5)
```

---

## **4. Functions**

### **Basic Function**

```kotlin
fun add(a: Int, b: Int): Int {
    return a + b
}
```

### **Single-Expression Function**

```kotlin
fun multiply(a: Int, b: Int) = a * b
```

### **Default and Named Arguments**

```kotlin
fun greet(name: String = "Guest") {
    println("Hello, $name!")
}

greet()  // Hello, Guest!
greet("Alice")  // Hello, Alice!
```

---

## **5. Collections**

### **List**

```kotlin
val nums = listOf(1, 2, 3)  // Immutable list
val mutableNums = mutableListOf(1, 2, 3)
mutableNums.add(4)
```

### **Map**

```kotlin
val map = mapOf(1 to "One", 2 to "Two")
val mutableMap = mutableMapOf(1 to "One")
mutableMap[2] = "Two"
```

### **Set**

```kotlin
val set = setOf(1, 2, 3)
val mutableSet = mutableSetOf(1, 2, 3)
mutableSet.add(4)
```

---

## **6. Classes and Objects**

### **Basic Class**

```kotlin
class Person(val name: String, var age: Int)

val person = Person("Alice", 25)
println(person.name)  // Alice
```

### **Data Class**

```kotlin
data class User(val name: String, val age: Int)

val user = User("Bob", 30)
println(user)  // User(name=Bob, age=30)
```

### **Inheritance**

```kotlin
open class Animal {
    open fun sound() {
        println("Animal makes a sound")
    }
}

class Dog : Animal() {
    override fun sound() {
        println("Bark")
    }
}

val dog = Dog()
dog.sound()  // Bark
```

---

## **7. Null Safety**

### **Nullable Types**

```kotlin
var name: String? = null
name = "Kotlin"

println(name?.length)  // Safe call operator
println(name?.length ?: 0)  // Elvis operator
```

---

## **8. Lambda Expressions**

### **Basic Lambda**

```kotlin
val add = { a: Int, b: Int -> a + b }
println(add(3, 4))  // 7
```

### **Higher-Order Function**

```kotlin
fun calculate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

val result = calculate(4, 5) { x, y -> x + y }
println(result)  // 9
```

---

## **9. Sample Program**

Here's a complete program demonstrating variables, loops, conditionals, and functions:

```kotlin
fun main() {
    println("Enter a number:")
    val num = readLine()?.toIntOrNull() ?: return

    if (num % 2 == 0) {
        println("Factorial of $num: ${factorial(num)}")
    } else {
        println("Sum of numbers up to $num: ${sumUpTo(num)}")
    }
}

fun factorial(n: Int): Int {
    return if (n == 0) 1 else n * factorial(n - 1)
}

fun sumUpTo(n: Int): Int {
    return (1..n).sum()
}
```

This cheat sheet provides a quick reference for Kotlin programming, covering essential syntax and concepts to help you write efficient code.



# References
---


	