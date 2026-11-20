# Practical Bash Scripting

## 1. Redirection

Redirection controls where command input and output go.

| Operator | Purpose |
|---|---|
| `>` | Redirect output, overwrite file |
| `>>` | Append output |
| `<` | Read input from a file |
| `2>` | Redirect errors |
| `&>` | Redirect standard output and errors |

Examples:

```bash
echo "Hello" > output.txt
echo "New line" >> output.txt

cat < output.txt

ls missing-file 2> errors.txt
```

## 2. Pipes

A pipe (`|`) sends the output of one command as input to another.

```bash
ls -l | grep ".txt"
```

Another example:

```bash
cat access.log | grep "ERROR"
```

## 3. Arithmetic Operations

Bash supports integer arithmetic.

```bash
a=10
b=5

echo $((a + b))
echo $((a - b))
echo $((a * b))
echo $((a / b))
echo $((a % b))
```

For decimal calculations, use `bc`.

```bash
echo "10 / 3" | bc -l
```

## 4. File and Directory Operations

```bash
mkdir -p backups

cp file.txt backups/
mv old.txt new.txt

if [ -f "file.txt" ]; then
    echo "File found"
fi
```

## 5. Reading Files Line by Line

```bash
while IFS= read -r line; do
    echo "$line"
done < input.txt
```

`IFS=` preserves leading and trailing whitespace, while `-r` prevents backslash interpretation.

## 6. Error Handling

Use `exit` to stop a script with a specific status.

```bash
#!/bin/bash

if [ -f "config.txt" ]; then
    echo "Configuration found"
else
    echo "Configuration missing"
    exit 1
fi
```

Check command success:

```bash
mkdir test

if [ $? -eq 0 ]; then
    echo "Directory created"
else
    echo "Operation failed"
fi
```

A clearer alternative:

```bash
if mkdir test; then
    echo "Directory created"
else
    echo "Operation failed"
fi
```

## 7. Useful Bash Commands

| Command | Purpose |
|---|---|
| `echo` | Print text |
| `read` | Read user input |
| `test` | Evaluate conditions |
| `source` | Execute a file in the current shell |
| `export` | Export environment variables |
| `set -x` | Enable execution tracing |
| `set +x` | Disable execution tracing |
| `trap` | Handle signals and shell events |

## 8. Script Safety

Common options:

```bash
set -e
set -u
set -o pipefail
```

| Option | Purpose |
|---|---|
| `-e` | Exit when an unhandled command fails (with exceptions) |
| `-u` | Treat unset variables as errors |
| `pipefail` | Make a pipeline fail if a command in it fails |

These options are useful, but they have edge cases. Test scripts carefully rather than assuming they replace proper error handling.

## Remember

- `>` overwrites; `>>` appends.
- `2>` redirects standard error.
- `|` connects commands.
- `$(( ))` handles integer arithmetic.
- `bc` supports decimal calculations.
- Check command results and handle failures intentionally.
- Use `set -euo pipefail` thoughtfully, not blindly.