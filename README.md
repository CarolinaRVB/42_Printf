# printf Project - 42 School

## Overview

The objective of this project is to create a custom `printf` function capable of printing various formats of variables and returning the length of the printed output. The function must be variadic, meaning it can accept a variable number of arguments.

## Table of Contents

- [Functionality](#functionality)
  - [Basic Logic](#basic-logic)
  - [Main Function Workflow](#main-function-workflow)
  - [Format Handling](#format-handling)
- [File Structure](#file-structure)
- [Example Usage](#example-usage)
- [Compilation](#compilation)
- [Additional Notes](#additional-notes)
- [Conclusion](#conclusion)

## Functionality

### Basic Logic

1. **Check for Format String:**
   - The function first verifies if a format string is provided by the user. If not, it returns zero.
   
2. **Handling Variadic Arguments:**
   - Use `va_list` to manage the variable arguments.
   - `va_start` initializes the `args` variable with the first argument.
   - `va_arg` retrieves each argument as needed.

### Main Function Workflow

1. **Loop Through Format String:**
   - Iterate through the format string until the end is reached.
   - Use `ft_putchar` to print each character until a format specifier (`%`) is encountered, counting each printed character to keep track of the length.
   
2. **Format Specifier Handling:**
   - When a `%` is found, the next character indicates the format type.
   - Call the `ft_checkformat` function with this character, along with the `args` and `len` variables.
   
3. **Clean Up:**
   - Use the `va_end` macro to clean up the `args` variable.
   - Return the total length of the printed output.

### Format Handling

The `ft_checkformat` function classifies formats into three main types: integers, strings, and hexadecimal numbers.

#### Integer Formats

- Handle different integer types and ensure proper conversion and printing.

#### String Formats

- Manage string inputs, ensuring correct output and length calculation.

#### Hexadecimal Formats

- Print hexadecimal numbers. The function includes:
  - `ft_put_hex` for `unsigned int` type.
  - `ft_put_hex` for `unsigned long` type.
  
  Currently, these functions are somewhat redundant and could be optimized further.

## Example Usage

```c
#include "ft_printf.h"

int main(void) {
    int len;
    
    len = ft_printf("Hello, %s! The number is %d and in hex it is %x.\n", "world", 42, 42);
    ft_printf("Printed %d characters.\n", len);
    
    return 0;
}
````
## Compilation
Use the provided Makefile to compile the project:
```
make
```
