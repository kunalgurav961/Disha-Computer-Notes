# Basics of R Programming

## Introduction to R

R is a free, open-source programming language and software environment for statistical computing and graphics. It is widely used among statisticians and data miners for developing statistical software and data analysis.

### Why R?
- **Statistical Analysis**: Comprehensive tools for statistical modeling
- **Data Visualization**: Excellent graphics capabilities
- **Open Source**: Free and community-driven
- **Extensible**: Over 18,000 packages available via CRAN
- **Cross-platform**: Runs on Windows, Mac, and Linux

---

## Installation and Setup

### Getting Started
1. Download R from [https://www.r-project.org](https://www.r-project.org)
2. Install R on your system
3. (Optional) Install RStudio for a better IDE experience
4. Launch R Console or RStudio

### First Command
```r
print("Hello, World!")
```

---

## Basic Data Types

### Numeric
```r
x <- 5
y <- 3.14
typeof(x)  # "double"
```

### Character (Strings)
```r
name <- "John"
message <- 'Hello World'
typeof(name)  # "character"
```

### Logical (Boolean)
```r
flag <- TRUE
check <- FALSE
typeof(flag)  # "logical"
```

### Complex Numbers
```r
z <- 3 + 4i
typeof(z)  # "complex"
```

---

## Variables and Assignment

### Variable Assignment
```r
# Using <-
x <- 10
y <- 20

# Using =
z = 30

# Using ->>
40 ->> w
```

### Naming Conventions
- Use meaningful names
- Use lowercase with underscores (snake_case): `my_variable`
- or camelCase: `myVariable`
- Cannot start with numbers or special characters

---

## Data Structures

### Vectors
A collection of elements of the same type.

```r
# Numeric vector
v1 <- c(1, 2, 3, 4, 5)

# Character vector
v2 <- c("apple", "banana", "orange")

# Logical vector
v3 <- c(TRUE, FALSE, TRUE)

# Using seq()
v4 <- seq(1, 10, by=2)  # 1, 3, 5, 7, 9

# Using rep()
v5 <- rep(1, 5)  # 1, 1, 1, 1, 1
```

### Lists
Ordered collection that can contain different data types.

```r
my_list <- list(
  name = "Alice",
  age = 25,
  scores = c(85, 90, 78)
)

# Accessing elements
my_list$name
my_list[[1]]
```

### Matrices
Two-dimensional data structure with same data type.

```r
m <- matrix(1:6, nrow=2, ncol=3)
#     [,1] [,2] [,3]
# [1,]    1    3    5
# [2,]    2    4    6
```

### Data Frames
Two-dimensional structure with columns of different types.

```r
df <- data.frame(
  name = c("Alice", "Bob", "Charlie"),
  age = c(25, 30, 35),
  salary = c(50000, 60000, 70000)
)
```

### Arrays
Multi-dimensional data structure.

```r
arr <- array(1:12, dim=c(2, 3, 2))
```

---

## Operators

### Arithmetic Operators
```r
5 + 3    # Addition: 8
5 - 3    # Subtraction: 2
5 * 3    # Multiplication: 15
5 / 3    # Division: 1.667
5 %% 3   # Modulus: 2
5 %/% 3  # Integer division: 1
5 ^ 3    # Exponentiation: 125
```

### Comparison Operators
```r
5 == 3   # Equal: FALSE
5 != 3   # Not equal: TRUE
5 > 3    # Greater than: TRUE
5 < 3    # Less than: FALSE
5 >= 3   # Greater or equal: TRUE
5 <= 3   # Less or equal: FALSE
```

### Logical Operators
```r
TRUE & FALSE   # AND: FALSE
TRUE | FALSE   # OR: TRUE
!TRUE          # NOT: FALSE
```

### Assignment Operators
```r
x <- 10        # Assign to x
10 -> x        # Assign to x (reverse)
x <<- 10       # Global assignment
```

---

## Control Flow

### if-else Statement
```r
x <- 10
if (x > 5) {
  print("x is greater than 5")
} else if (x == 5) {
  print("x equals 5")
} else {
  print("x is less than 5")
}
```

### for Loop
```r
for (i in 1:5) {
  print(i)
}

# Loop through vector
fruits <- c("apple", "banana", "orange")
for (fruit in fruits) {
  print(fruit)
}
```

### while Loop
```r
x <- 1
while (x <= 5) {
  print(x)
  x <- x + 1
}
```

### repeat Loop
```r
x <- 1
repeat {
  print(x)
  x <- x + 1
  if (x > 5) break
}
```

---

## Functions

### Creating Functions
```r
# Basic function
greet <- function(name) {
  message <- paste("Hello,", name)
  print(message)
}

greet("Alice")
```

### Functions with Multiple Arguments
```r
add <- function(a, b) {
  return(a + b)
}

result <- add(5, 3)  # 8
```

### Default Arguments
```r
power <- function(x, n = 2) {
  return(x ^ n)
}

power(3)      # 9 (default n=2)
power(3, 3)   # 27 (n=3)
```

### Variable Arguments
```r
sum_all <- function(...) {
  return(sum(...))
}

sum_all(1, 2, 3, 4, 5)  # 15
```

---

## Indexing and Subsetting

### Vector Indexing
```r
v <- c(10, 20, 30, 40, 50)

v[1]        # First element: 10
v[c(1, 3)]  # First and third: 10, 30
v[-1]       # All except first
v[v > 25]   # Elements greater than 25
```

### List Indexing
```r
my_list <- list(a = 1, b = 2, c = 3)

my_list$a       # Access by name: 1
my_list[["b"]]  # Access by double brackets: 2
my_list[[1]]    # Access by position: 1
```

### Data Frame Indexing
```r
df[1, ]         # First row
df[, 1]         # First column
df$name         # Access column by name
df[1, 2]        # Element at row 1, column 2
```

---

## Built-in Functions

### String Functions
```r
toupper("hello")           # "HELLO"
tolower("HELLO")           # "hello"
nchar("hello")             # 5
substr("hello", 1, 3)      # "hel"
paste("Hello", "World")    # "Hello World"
```

### Mathematical Functions
```r
abs(-5)         # 5
sqrt(16)        # 4
ceiling(3.2)    # 4
floor(3.9)      # 3
round(3.14159, 2)  # 3.14
```

### Statistical Functions
```r
mean(c(1, 2, 3, 4, 5))     # 3
median(c(1, 2, 3, 4, 5))   # 3
sd(c(1, 2, 3, 4, 5))       # 1.58
var(c(1, 2, 3, 4, 5))      # 2.5
```

---

## Useful Commands

### Getting Help
```r
?function_name       # Get help on function
help(function_name)  # Detailed help
example(function_name)  # Examples
```

### Workspace Management
```r
ls()            # List all variables
rm(x)           # Remove variable x
rm(list=ls())   # Clear workspace
getwd()         # Get working directory
setwd("/path")  # Set working directory
```

### Type Checking
```r
is.numeric(x)
is.character(x)
is.logical(x)
class(x)
typeof(x)
```

---

## Common Mistakes to Avoid

1. **Case Sensitivity**: R is case-sensitive; `x` and `X` are different
2. **Missing Parentheses**: Always close parentheses and brackets
3. **Incorrect Vector Indexing**: Remember R uses 1-based indexing (not 0-based)
4. **Type Mismatch**: Ensure data types match for operations
5. **Forgotten Assignment**: Use `<-` to store results

---

## Practice Exercises

1. Create a vector of numbers 1 to 10 and calculate the mean
2. Write a function that checks if a number is even or odd
3. Create a data frame with three columns and perform basic operations
4. Use a loop to print the multiplication table of 7
5. Create nested lists and practice accessing elements

---

## Summary

R is a powerful language for statistical computing. Key points:
- Vectors and data frames are fundamental structures
- Functions enable code reusability
- Control flow structures allow complex logic
- Extensive built-in functions simplify operations
- Practice is essential for mastery
