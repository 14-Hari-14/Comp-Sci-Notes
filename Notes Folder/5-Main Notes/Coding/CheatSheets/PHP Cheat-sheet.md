
2025-01-25 10:21

Tags:

# PHP Cheat Sheet

---

## **1. Basics**

### **Hello World**

```php
<?php
  echo "Hello, World!";
?>
```

### **Comments**

- Single-line: `// This is a comment` or `# This is also a comment`
- Multi-line:

```php
/*
This is a
multi-line comment
*/
```

### **Variables**

```php
$name = "John";    // String
$age = 25;          // Integer
$is_admin = true;   // Boolean
$height = 5.9;      // Float
```

### **Basic Types**

- `String`
- `Integer`
- `Float`
- `Boolean`
- `Array`
- `Object`
- `NULL`

---

## **2. Control Structures**

### **If-Else**

```php
<?php
  $x = 10;

  if ($x > 5) {
    echo "x is greater than 5";
  } else {
    echo "x is 5 or less";
  }
?>
```

### **Ternary Operator**

```php
<?php
  $x = 10;
  echo ($x > 5) ? "Greater than 5" : "5 or less";
?>
```

### **Switch Statement**

```php
<?php
  $color = "red";

  switch ($color) {
    case "red":
      echo "The color is red";
      break;
    case "blue":
      echo "The color is blue";
      break;
    default:
      echo "Unknown color";
  }
?>
```

---

## **3. Loops**

### **While Loop**

```php
<?php
  $i = 0;
  while ($i < 5) {
    echo $i;
    $i++;
  }
?>
```

### **Do-While Loop**

```php
<?php
  $i = 0;
  do {
    echo $i;
    $i++;
  } while ($i < 5);
?>
```

### **For Loop**

```php
<?php
  for ($i = 0; $i < 5; $i++) {
    echo $i;
  }
?>
```

### **Foreach Loop**

```php
<?php
  $arr = [1, 2, 3, 4];

  foreach ($arr as $value) {
    echo $value;
  }
?>
```

---

## **4. Functions**

### **Basic Function**

```php
<?php
  function greet($name) {
    return "Hello, $name!";
  }

  echo greet("Alice");
?>
```

### **Default Arguments**

```php
<?php
  function greet($name = "Guest") {
    return "Hello, $name!";
  }

  echo greet();
  echo greet("Bob");
?>
```

### **Variable Arguments**

```php
<?php
  function sum(...$numbers) {
    return array_sum($numbers);
  }

  echo sum(1, 2, 3, 4);  // Output: 10
?>
```

---

## **5. Arrays**

### **Indexed Array**

```php
<?php
  $arr = [1, 2, 3, 4];
  echo $arr[0];  // Access the first element
?>
```

### **Associative Array**

```php
<?php
  $assoc = ["name" => "Alice", "age" => 25];
  echo $assoc["name"];
?>
```

### **Multidimensional Array**

```php
<?php
  $matrix = [
    [1, 2, 3],
    [4, 5, 6],
  ];
  echo $matrix[0][1];  // Access 2nd element of 1st array
?>
```

---

## **6. String Operations**

### **Concatenation**

```php
<?php
  $greeting = "Hello" . " " . "World";
  echo $greeting;
?>
```

### **String Interpolation**

```php
<?php
  $name = "Alice";
  echo "Hello, $name!";
?>
```

---

## **7. Classes and Objects**

### **Defining a Class**

```php
<?php
  class Person {
    public $name;
    public $age;

    public function __construct($name, $age) {
      $this->name = $name;
      $this->age = $age;
    }

    public function greet() {
      return "Hello, my name is $this->name.";
    }
  }

  $person = new Person("Alice", 25);
  echo $person->greet();
?>
```

---

## **8. File Operations**

### **Reading a File**

```php
<?php
  $content = file_get_contents("file.txt");
  echo $content;
?>
```

### **Writing to a File**

```php
<?php
  file_put_contents("file.txt", "Hello, File!");
?>
```

---

## **9. Sample Program**

Here is a sample program that combines variables, loops, and conditionals:

```php
<?php
  echo "Enter a number: ";
  $num = (int)fgets(STDIN);

  if ($num < 1 || $num > 10) {
    echo "Error: Number must be between 1 and 10.";
  } else {
    $factorial = 1;
    for ($i = 1; $i <= $num; $i++) {
      $factorial *= $i;
    }
    echo "The factorial of $num is $factorial.";
  }
?>
```



# References
---


	