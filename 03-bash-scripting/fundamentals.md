# Bash Scripting Fundamentals

## 1. What is Bash?

Bash (Bourne Again Shell) is a command-line interpreter that executes commands and scripts to automate tasks in Linux.

## 2. Shell Script Structure

A shell script is a file containing commands executed in sequence.

```bash
#!/bin/bash

echo "Hello, World!"
```

| Element | Purpose |
|---|---|
| `#!/bin/bash` | Shebang: specifies the interpreter |
| `echo` | Prints text to the terminal |
| `#` | Starts a comment |

## 3. Creating and Executing Scripts

```bash
# Create a script
nano script.sh

# Make it executable
chmod +x script.sh

# Execute it
./script.sh

# Execute using Bash
bash script.sh
```

**Difference:**
- `./script.sh` requires execution permission.
- `bash script.sh` runs the file through Bash directly.

## 4. Exit Status

Every command returns an exit status.

| Status | Meaning |
|---|---|
| `0` | Success |
| Non-zero | Failure or another condition |

```bash
mkdir test

echo $?
```

`$?` stores the exit status of the most recently executed command.

## 5. Important Special Variables

| Variable | Meaning |
|---|---|
| `$0` | Script name |
| `$1`, `$2` | First and second arguments |
| `$#` | Number of arguments |
| `$@` | All arguments as separate values |
| `$?` | Last command's exit status |
| `$$` | Current shell process ID |

## 6. Debugging

```bash
bash -x script.sh
```

Displays commands as Bash executes them, helping identify errors.

## Remember

- Bash scripts automate repetitive Linux tasks.
- The shebang identifies the interpreter.
- `chmod +x` adds execution permission.
- Exit status `0` indicates success.
- `$?` helps check whether a command succeeded.

