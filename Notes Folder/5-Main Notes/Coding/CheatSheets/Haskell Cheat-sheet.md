
2025-01-22 12:34

Tags:

# Haskell Cheat-sheet

---

## **1. Basics**

### **Hello World**

```haskell
main :: IO ()
main = putStrLn "Hello, World!"
```

### **Comments**

- Single-line: `-- This is a comment`
- Multi-line: `{- This is a
  multi-line comment -}`

### **Basic Types**

- `Int`: Fixed-precision integer
- `Integer`: Arbitrary-precision integer
- `Float`: Single-precision floating-point
- `Double`: Double-precision floating-point
- `Char`: Single Unicode character
- `Bool`: `True` or `False`
- `String`: List of `Char`

### **Declaring Variables**

```haskell
x :: Int
x = 10

y :: String
y = "Haskell"
```

### **Lists**

```haskell
nums = [1, 2, 3, 4, 5]
chars = ['a', 'b', 'c']
```

- Access: `nums !! 0` (returns `1`)
- Concatenate: `[1, 2] ++ [3, 4]`
- Prepend: `1 : [2, 3, 4]` (returns `[1, 2, 3, 4]`)

---

## **2. Functions**

### **Basic Function Definition**

```haskell
add :: Int -> Int -> Int
add x y = x + y

-- Using accumulator for tail recursion
factorial :: Integer -> Integer
factorial n = factorialAcc n 1
  where
    factorialAcc 0 acc = acc
    factorialAcc n acc = factorialAcc (n - 1) (n * acc)
```

### **Anonymous Functions**

```haskell
\x -> x + 1  -- Adds 1 to x
```

### **Higher-Order Functions**

- **`map`**: Apply a function to all elements in a list.
  ```haskell
  map (*2) [1, 2, 3]  -- [2, 4, 6]
  ```
- **`filter`**: Filter elements in a list.
  ```haskell
  filter (>2) [1, 2, 3, 4]  -- [3, 4]
  ```
- **`foldl'`**: Strict left fold (more efficient than foldr for most cases)
  ```haskell
  import Data.List (foldl')
  foldl' (+) 0 [1, 2, 3]  -- 6
  ```

---

## **3. Conditional Statements**

### **If-Else**

```haskell
absolute :: Int -> Int
absolute x = if x >= 0 then x else -x

evenOrOdd :: Int -> String
evenOrOdd x = if x `mod` 2 == 0 then "Even" else "Odd"

maxValue :: Int -> Int -> Int
maxValue a b = if a > b then a else b
```


### **Guards**

Guards provide a clean way to write conditional logic based on multiple predicates. They are especially useful when you have several conditions to check. Each guard is marked with a `|` symbol and followed by a boolean expression. Guards are evaluated from top to bottom, and the first True condition is executed. 

```haskell
-- Example of guards for grade classification 
grade :: Int -> String grade score | score >= 90 = "A" -- Checks if score is 90 or above 

| score >= 80 = "B" -- If previous guard failed, checks if score is 80 or above
| score >= 70 = "C" -- Checks if score is 70 or above 
| score >= 60 = "D" -- Checks if score is 60 or above |
otherwise = "F" -- If all previous guards fail, returns "F"
-- Example with multiple parameters
compareToTen :: Int -> String 
compareToTen x 
| x < 10 = "Less than 10" 
| x > 10 = "Greater than 10" 
| otherwise = "Equal to 10" 

```

The `otherwise` guard is equivalent to `True` and catches all remaining cases. It's good practice to include it as the last guard to ensure all cases are handled.``

### **Case Expression** 

Case expressions provide pattern matching on values. They are particularly useful when you want to execute different code based on the specific value or structure of an expression. Unlike guards which test boolean conditions, case expressions match against patterns. 
```haskell
-- Basic case expression matching on values
describe :: Int -> String 
describe x = case x of 
1 -> "One" -- If x equals 1
2 -> "Two" -- If x equals 2 
_ -> "Other" -- Default case (matches anything) 

-- Pattern matching with lists
listDescription :: [a] -> String
case xs of 
[] -> "Empty list" -- Matches empty list 
[x] -> "Single element list" -- Matches list with exactly one element 
[x,y] -> "Two element list" -- Matches list with exactly two elements 
x:xs -> "List with many elements" -- Matches list with head 'x' and tail 'xs' 

-- Pattern matching with tuples 
describePair :: (Int, Int) -> String 
describePair pair = 
case pair of (0, 0) -> "Origin" -- Matches exact pair (0,0) 
(x, 0) -> "On X axis" -- Matches any pair with y=0 
(0, y) -> "On Y axis" -- Matches any pair with x=0 
(x, y) -> "Neither on axis" -- Matches any other pair 
```

Case expressions are exhaustive, meaning they must cover all possible values of the type being matched. The underscore `_` pattern acts as a catch-all, similar to `otherwise` in guards.`


## **4. Loops and Recursion**

### **For Loops**

Haskell doesn't have traditional `for` loops. Instead, we use recursion or list comprehensions. Here's how each approach works:

#### **Tail Recursive Example**

```haskell
-- This function sums all elements in a list using tail recursion
sumList :: Num a => [a] -> a
sumList xs = go xs 0
  where
    -- 'go' is a common name for helper functions in Haskell
    -- It takes two parameters:
    --   - The remaining list to process
    --   - An accumulator that holds our running sum
    go [] acc     = acc        -- Base case: empty list, return accumulated sum
    go (x:xs) acc = go xs (acc + x)  -- Recursive case: add head to accumulator and process tail

-- Here's another example that squares each number in a list
squareList :: Num a => [a] -> [a]
squareList xs = go xs []
  where
    -- Parameters:
    --   - Input list remaining to be processed
    --   - Accumulator list containing processed squares
    go [] acc     = reverse acc    -- Base case: reverse final list (since we prepended)
    go (x:xs) acc = go xs (x*x : acc)  -- Square current number and prepend to accumulator

-- Example processing a range with a condition
-- Sums only even numbers from 1 to n
sumEvens :: Integer -> Integer
sumEvens n = go n 0
  where
    -- Parameters:
    --   - Current number being checked
    --   - Running sum of even numbers
    go 0 acc = acc                      -- Base case: reached zero, return sum
    go n acc | even n    = go (n-1) (acc + n)  -- If n is even, add to sum
            | otherwise  = go (n-1) acc         -- If n is odd, skip it
```

#### **List Comprehension Examples**

```haskell
-- Basic list comprehension: squares numbers from 1 to 10
squares = [x * x | x <- [1..10]]
-- Components:
--   x * x       : the output expression
--   x <- [1..10]: the generator (creates values for x)

-- List comprehension with a condition (filter)
evenSquares = [x * x | x <- [1..10], even x]
-- Components:
--   x * x       : the output expression
--   x <- [1..10]: the generator
--   even x      : the predicate (filter condition)

-- List comprehension with multiple generators
coordinates = [(x, y) | x <- [1..3], y <- [1..3]]
-- Creates all possible coordinate pairs:
-- [(1,1), (1,2), (1,3), (2,1), (2,2), (2,3), (3,1), (3,2), (3,3)]

-- Complex example: Generate Pythagorean triples
pythTriples n = [(x, y, z) | 
    x <- [1..n],          -- First number
    y <- [x..n],          -- Second number (start from x to avoid duplicates)
    z <- [y..n],          -- Third number (start from y)
    x*x + y*y == z*z]     -- Pythagorean condition
```

### **While Loops**

Haskell doesn't have traditional while loops. Here are idiomatic alternatives:

```haskell
-- Using takeWhile: takes elements while condition is True
-- Example: Take numbers until we exceed 10
takeWhile (<= 10) [1..]  -- Returns [1,2,3,4,5,6,7,8,9,10]

-- Recursive version of while loop
-- Example: Calculate sum until exceeding limit
sumUntil :: (Num a, Ord a) => a -> a -> a
sumUntil limit = go 0
  where
    -- Parameters:
    --   - acc: accumulated sum so far
    --   - x: current number to process
    go acc x
      | acc > limit = acc         -- Stop condition: sum exceeds limit
      | otherwise   = go (acc + x) (x + 1)  -- Add current number and continue
```



---

## **5. Input and Output (I/O)**

### **Getting Input**

```haskell
main = do
  putStrLn "Enter your name:"
  name <- getLine
  putStrLn ("Hello, " ++ name)
```

### **File I/O**

```haskell
import System.IO

-- Reading a file
main = do
  handle <- openFile "file.txt" ReadMode
  contents <- hGetContents handle
  putStr contents
  hClose handle

-- Writing to a file (using strict I/O)
main = do
  writeFile "output.txt" "Hello, Haskell!"
```

---

## **6. Modules and Imports**

### **Importing Modules**

```haskell
import Data.List (sort, nub)  -- Import specific functions
import qualified Data.Map as Map  -- Alias a module
```

### **Using Functions from Modules**

```haskell
maximum [1, 2, 3]  -- 3 (from Prelude)
Map.empty          -- Create an empty map
```

---

## **7. Key Libraries**

### **Data.List**

```haskell
import Data.List

sort [3,1,2]    -- [1,2,3]
nub [1,1,2,2]   -- [1,2]
elem 1 [1,2,3]  -- True
```

### **Data.Map**

```haskell
import qualified Data.Map.Strict as Map  -- Note: Using strict Map

let m = Map.fromList [(1, "One"), (2, "Two")]
Map.lookup 1 m  -- Just "One"
```

---

## **8. Miscellaneous**

### **Lazy Evaluation**

```haskell
take 5 [1..]  -- [1,2,3,4,5]
```

### **Strict Evaluation**

```haskell
import Control.DeepSeq

-- Force strict evaluation
value `deepseq` someOperation
```

---

## **9. Sample Program (Optimized)**

```haskell
-- Program to calculate the factorial of a number if it is even, otherwise return the sum of numbers up to that number.

main :: IO ()
main = do
  putStrLn "Enter a number (0 to 20):"
  input <- getLine
  let number = read input :: Int
  if number < 0 || number > 20
    then putStrLn "Error: Please enter a number between 0 and 20."
    else putStrLn ("Result: " ++ show (processNumber number))

-- Function to process the number
processNumber :: Int -> Int
processNumber x = if even x then factorial x else sumUpTo x

-- Function to calculate factorial recursively
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n - 1)

-- Function to calculate the sum of numbers up to x
sumUpTo :: Int -> Int
sumUpTo 0 = 0
sumUpTo n = n + sumUpTo (n - 1)
```


# References
---


	