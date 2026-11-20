# Conditions & Loops

## 1. Conditional Statements

Conditions allow scripts to make decisions.

```bash
if [ "$age" -ge 18 ]; then
    echo "Adult"
else
    echo "Minor"
fi
```

### Comparison Operators

**Numbers**

| Operator | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |
| `-lt` | Less than |
| `-le` | Less than or equal |

**Strings**

| Operator | Meaning |
|---|---|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | Empty string |
| `-n` | Non-empty string |

## 2. File Conditions

Bash provides operators to check files and directories.

| Operator | Meaning |
|---|---|
| `-e` | Path exists |
| `-f` | Regular file exists |
| `-d` | Directory exists |
| `-r` | Readable |
| `-w` | Writable |
| `-x` | Executable |

Example:

```bash
if [ -f "config.txt" ]; then
    echo "File exists"
else
    echo "File not found"
fi
```

## 3. Logical Operators

Combine multiple conditions.

```bash
if [ "$age" -ge 18 ] && [ "$country" = "Tunisia" ]; then
    echo "Conditions matched"
fi
```

| Operator | Meaning |
|---|---|
| `&&` | AND |
| `||` | OR |
| `!` | NOT |

## 4. elif and case

Use `elif` to test multiple conditions.

```bash
if [ "$score" -ge 90 ]; then
    echo "Excellent"
elif [ "$score" -ge 50 ]; then
    echo "Passed"
else
    echo "Failed"
fi
```

Use `case` to match a value against multiple patterns.

```bash
case "$option" in
    start)
        echo "Starting..."
        ;;
    stop)
        echo "Stopping..."
        ;;
    *)
        echo "Invalid option"
        ;;
esac
```

## 5. For Loop

Repeats commands for each item in a list.

```bash
for name in Alice Bob Charlie; do
    echo "Hello $name"
done
```

Range example:

```bash
for i in {1..5}; do
    echo "$i"
done
```

## 6. While Loop

Repeats commands while a condition remains true.

```bash
counter=1

while [ "$counter" -le 5 ]; do
    echo "$counter"
    ((counter++))
done
```

## 7. Until Loop

Repeats commands until a condition becomes true.

```bash
counter=1

until [ "$counter" -gt 5 ]; do
    echo "$counter"
    ((counter++))
done
```

## 8. Loop Control

| Command | Purpose |
|---|---|
| `break` | Exit the loop |
| `continue` | Skip to the next iteration |

## Remember

- `if`, `elif`, and `else` control decisions.
- `case` is useful for matching multiple options.
- `for` iterates over a list or range.
- `while` continues while a condition is true.
- `until` continues until a condition becomes true.
- Always close loops with `done` and conditionals with `fi` or `esac`.