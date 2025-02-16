
2025-01-25 10:16

Tags:

# Ruby Cheat Sheet

---

## **1. Basics**

### **Hello World**

```ruby
puts "Hello, World!"
```

### **Comments**

- Single-line: `# This is a comment`
- Multi-line:

```ruby
=begin
This is a
multi-line comment
=end
```

### **Basic Data Types**

- `Integer`: Whole numbers, e.g., `42`
- `Float`: Decimal numbers, e.g., `3.14`
- `String`: Text, e.g., `'Hello'` or `"World"`
- `Boolean`: `true` or `false`
- `Array`: Ordered collection, e.g., `[1, 2, 3]`
- `Hash`: Key-value pairs, e.g., `{key: "value"}`

### **Declaring Variables**

```ruby
x = 10   # Integer
name = "Ruby"  # String
is_active = true  # Boolean
```

---

## **2. Control Structures**

### **Conditional Statements**

#### **If-Else**

```ruby
x = 10
if x > 5
  puts "x is greater than 5"
else
  puts "x is 5 or less"
end
```

#### **Unless**

```ruby
x = 10
unless x < 5
  puts "x is not less than 5"
end
```

#### **Ternary Operator**

```ruby
x = 10
puts x > 5 ? "Greater than 5" : "5 or less"
```

### **Case Statement**

```ruby
y = 3
case y
when 1
  puts "One"
when 2
  puts "Two"
else
  puts "Other"
end
```

---

## **3. Loops**

### **While Loop**

```ruby
x = 0
while x < 5
  puts x
  x += 1
end
```

### **Until Loop**

```ruby
x = 0
until x == 5
  puts x
  x += 1
end
```

### **For Loop**

```ruby
for i in 1..5
  puts i
end
```

### **Each Loop**

```ruby
[1, 2, 3].each do |num|
  puts num
end
```

---

## **4. Methods**

### **Defining Methods**

```ruby
def greet(name)
  "Hello, #{name}!"
end

puts greet("Alice")
```

### **Default Arguments**

```ruby
def greet(name = "Guest")
  "Hello, #{name}!"
end

puts greet
puts greet("Bob")
```

### **Blocks**

```ruby
3.times do
  puts "Hello"
end

[1, 2, 3].each { |num| puts num * 2 }
```

---

## **5. Collections**

### **Arrays**

```ruby
arr = [1, 2, 3, 4]
arr.push(5)  # Add an element
arr.pop      # Remove the last element
arr.each { |n| puts n }
```

### **Hashes**

```ruby
hash = {name: "Alice", age: 25}
hash[:name]  # Access value by key
hash[:city] = "New York"  # Add a new key-value pair
hash.each { |key, value| puts "#{key}: #{value}" }
```

---

## **6. Input and Output**

### **Getting Input**

```ruby
puts "Enter your name:"
name = gets.chomp
puts "Hello, #{name}!"
```

### **File I/O**

- **Reading a File**
    
    ```ruby
    File.open("file.txt", "r") do |file|
      file.each_line { |line| puts line }
    end
    ```
    
- **Writing to a File**
    
    ```ruby
    File.open("output.txt", "w") do |file|
      file.puts "Hello, File!"
    end
    ```
    

---

## **7. Classes and Objects**

### **Defining a Class**

```ruby
class Person
  attr_accessor :name, :age

  def initialize(name, age)
    @name = name
    @age = age
  end

  def greet
    "Hello, my name is #{@name} and I am #{@age} years old."
  end
end

person = Person.new("Alice", 25)
puts person.greet
```

---

## **8. Exception Handling**

```ruby
begin
  num = 10 / 0
rescue ZeroDivisionError => e
  puts "Error: #{e.message}"
end
```

---

## **9. Sample Program**

Here's a complete program that uses variables, loops, and conditional statements:

```ruby
puts "Enter a number (1 to 10):"
number = gets.chomp.to_i

if number < 1 || number > 10
  puts "Error: Please enter a number between 1 and 10."
else
  factorial = 1
  for i in 1..number
    factorial *= i
  end
  puts "The factorial of #{number} is #{factorial}."
end
```



# References
---


	