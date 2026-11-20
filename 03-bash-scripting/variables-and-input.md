# Variables & Input

## 1. Variables

Variables store values that can be reused throughout a script.

```bash
name="Bayrem"
age=22

echo "$name"
echo "$age"
```

**Important:**
- No spaces around `=`.
- Use `$` to access a variable.
- Double quotes protect spaces and allow variable expansion.

## 2. User Input

Use `read` to receive input from the user.

```bash
#!/bin/bash

echo "Enter your name:"
read name

echo "Welcome, $name!"
```

A shorter version:

```bash
read -p "Enter your name: " name
```

## 3. Positional Arguments

Arguments are values passed when executing a script.

```bash
#!/bin/bash

echo "Script: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "Total arguments: $#"
```

Execute:

```bash
./script.sh Linux Bash
```

Output:

```text
Script: ./script.sh
First argument: Linux
Second argument: Bash
Total arguments: 2
```

## 4. Special Argument Variables

| Variable | Meaning |
|---|---|
| `$0` | Script name |
| `$1`, `$2` | Positional arguments |
| `$#` | Number of arguments |
| `$@` | All arguments, individually |
| `$*` | All arguments, treated as one word when quoted |

**Remember:** Prefer `"$@"` when passing arguments to another command because it preserves each argument separately.

## 5. Command Substitution

Command substitution stores the output of a command in a variable.

```bash
current_date=$(date)
current_user=$(whoami)

echo "$current_date"
echo "$current_user"
```

Modern syntax:

```bash
variable=$(command)
```

Older syntax:

```bash
variable=`command`
```

Prefer `$(...)` because it is easier to read and nest.

## 6. Environment Variables

Environment variables are available to processes started from the environment.

```bash
export APP_ENV="development"

echo "$APP_ENV"
```

Useful examples:

| Variable | Purpose |
|---|---|
| `$HOME` | User's home directory |
| `$USER` | Current username |
| `$PATH` | Directories searched for commands |
| `$PWD` | Current working directory |

## Remember

- Assign variables without spaces around `=`.
- Use `"$variable"` to safely expand values.
- `read` receives user input.
- `$1`, `$2`, and `$#` handle script arguments.
- `$(command)` captures command output.
- `export` makes a variable available to child processes.