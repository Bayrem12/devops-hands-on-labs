# Functions & Arguments

## 1. Functions

Functions group commands into reusable blocks of code.

```bash
greet() {
    echo "Hello, World!"
}

greet
```

## 2. Functions with Parameters

Functions can receive arguments.

```bash
greet() {
    echo "Hello, $1!"
}

greet "Bayrem"
```

Output:

```text
Hello, Bayrem!
```

Inside a function, `$1`, `$2`, and other positional parameters refer to the function's arguments.

## 3. Returning Values

Bash functions use `return` to provide an exit status (0–255), not to return ordinary text.

```bash
check_status() {
    return 0
}

check_status

echo $?
```

To capture text output, use command substitution:

```bash
get_username() {
    echo "$USER"
}

username=$(get_username)

echo "$username"
```

## 4. Local Variables

Use `local` to limit a variable's scope to its function.

```bash
show_message() {
    local message="Hello"
    echo "$message"
}

show_message
```

## 5. Script Arguments vs Function Arguments

| Feature | Script | Function |
|---|---|---|
| First argument | `$1` | `$1` |
| Second argument | `$2` | `$2` |
| Argument count | `$#` | `$#` |
| All arguments | `"$@"` | `"$@"` |

Inside a function, positional parameters refer to the function arguments, temporarily replacing the script's positional parameters.

## 6. Practical Example

```bash
#!/bin/bash

add_numbers() {
    local result=$(( $1 + $2 ))
    echo "$result"
}

sum=$(add_numbers 10 20)

echo "Result: $sum"
```

Output:

```text
Result: 30
```

## Remember

- Functions improve code reuse and organization.
- Pass values through positional parameters.
- Use `local` for function-specific variables.
- `return` provides an exit status.
- Use `echo` with command substitution to capture text output.