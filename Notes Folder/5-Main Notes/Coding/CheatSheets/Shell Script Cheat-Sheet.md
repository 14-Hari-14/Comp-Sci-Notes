
# Shell Scripting Cheat Sheet

## Basics of Shell Scripting

### Script Structure
```bash
#!/bin/bash  # Always start with this shebang
```

### Input Handling
- Use `read` to accept user input
- For multiple inputs:
  ```bash
  read n         # Single value input
  read -a array  # Array input
  ```

### Array Operations
- Declare arrays:
  ```bash
  array=()              # Empty array
  array=(1 2 3 4)       # Pre-populated array
  ```
- Access array elements:
  ```bash
  ${array[0]}           # First element
  "${array[@]}"         # All elements
  ${#array[@]}          # Array length
  ```

### Associative Arrays
- Use declare to create:
  ```bash
  declare -A hashmap    # Associative array declaration
  hashmap[key]=value    # Adding elements
  ```

### Loops
#### For Loop
```bash
# Iterate through array
for item in "${array[@]}"; do
    # Your code here
done

# Range-based loop
for ((i=0; i<length; i++)); do
    # Your code here
done
```

### Conditional Checks
```bash
# Basic if-else structure
if [[ condition ]]; then
    # Code if condition is true
else
    # Code if condition is false
fi

# Numeric if-else with arithmetic expansion
if ((a > b)); then
    # Greater than logic
else
    # Less than or equal logic
fi

# Multiple conditions
if [[ condition1 ]]; then
    # First condition logic
elif [[ condition2 ]]; then
    # Second condition logic
else
    # Default logic
fi
```

### Nested Conditionals
```bash
# Nested if-else example
if [[ outer_condition ]]; then
    if [[ inner_condition ]]; then
        # Nested true condition
    else
        # Nested false condition
    fi
else
    # Outer condition false
fi
```
### String Manipulation
```bash
word="example"
length=${#word}         # String length
substring=${word:0:3}   # Substring extraction
```

### Variable Assignment Best Practices

```bash
# Correct spacing 

variable=value # No spaces around '=' 
name="John Doe" # Quotes for strings with spaces 

# INCORRECT - These will cause errors 

	variable = value # ❌ Spaces on both sides 
name = "John Doe" # ❌ Spaces around '='
```

## Advanced Numeric Manipulation
### Divisibility Checks
```bash
# Multiple condition divisibility
if ((number % 3 == 0 || number % 5 == 0)); then
    # Number is divisible by 3 or 5
fi

# Modulo operator (%) for remainder
# Useful for checking divisibility
```

### Cumulative Sum Calculation
```bash
# Initialize sum
sum=0

# Accumulate values with conditional checks
for ((i = 1; i <= n; i++)); do
    if ((condition)); then
        sum=$((sum + i))
    fi
done
```

## Common Pitfalls to Avoid
1. **Spacing Matters!**
   - `if[[ $var ]]` ❌ 
   - `if [[ $var ]]` ✅
   - Always space around `[[` and `]]`

2. **Array Indexing**
   - Start from 0
   - Use `"${array[@]}"` to handle elements with spaces

3. **Integer Comparisons**
   - Use `(( ))` for numeric checks
   - Don't use `[ ]` for numeric comparisons

4. **Variable Expansion**
   - `"$variable"` (with quotes) prevents word splitting
   - `${variable}` helps in complex expansions

## Efficiency Tips
- Use `exit 0` to stop script immediately after finding result
- Minimize unnecessary iterations
- Use built-in bash arithmetic and string operations

## Debugging Techniques
- Add `-x` to shebang for verbose execution
  ```bash
  #!/bin/bash -x
  ```
- Print debug information strategically

## Performance Optimization
- Prefer built-in bash operations over external commands
- Use arithmetic expansion `(( ))` for calculations
- Minimize function calls and subshells

## Sample Problem: Word Frequency Counter

### Problem Description
Write a shell script that:
- Reads a sentence
- Counts the frequency of each word
- Prints words that appear more than twice

### Sample Solution
```bash
#!/bin/bash

# Read the input sentence
read -p "Enter a sentence: " sentence

# Create an associative array for word count
declare -A word_count

# Convert to lowercase and split into words
for word in $sentence; do
    # Increment word count
    ((word_count[$word]++))
done

# Print words with frequency > 2
echo "Words appearing more than twice:"
for word in "${!word_count[@]}"; do
    if ((word_count[$word] > 2)); then
        echo "$word: ${word_count[$word]} times"
    fi
done
```



### Divisibility Check Tips
- Use `||` for multiple conditions
- `%` operator gives remainder
- Early exit strategies can optimize

### Performance Considerations
- Minimize iterations
- Use built-in arithmetic
- Avoid unnecessary computations




### STRING INDEXING TECHNIQUES
#### Basic Syntax:
- **${word:start:length}**
- Positive indices from start
- Negative indices from end

**Examples:**
```bash
word="hello"
first_char=${word:0:1}     # "h"
last_char=${word: -1:1}    # "o"
middle=${word:1:2}         # "el"
last_two=${word: -2}       # "lo"
```

**Key Patterns:**
- First character: ${word:0:1}
- Last character: ${word: -1:1}
- Substring: ${word:start:length}

- Negative indices count from end
# References
---


	