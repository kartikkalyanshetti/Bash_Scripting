# 🐚 Bash Scripting

<p align="center">
  <img src="https://img.shields.io/badge/Shell-Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white" alt="Bash">
  <img src="https://img.shields.io/badge/OS-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/Editor-Neovim-57A143?style=for-the-badge&logo=neovim&logoColor=white" alt="Neovim">
  <img src="https://img.shields.io/badge/Git-GitHub-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">
</p>

<p align="center">
  <b>Learning Bash • Automating Linux • Building DevOps Foundations</b>
</p>

---

## 📖 About

This repository documents my journey of learning **Bash Scripting** — from basic Linux commands to writing scripts for automation and DevOps.

I'm following:

🎥 **[The Complete Bash Scripting Course — Dave Eddy](https://www.youtube.com/watch?v=Sx9zG7wa4FA)**

Along the way, I'm documenting:

* 📝 Notes
* 💻 Scripts
* 🧪 Experiments
* 🐛 Bugs & fixes
* 🚀 Mini projects
* 🧠 Important concepts

> **The goal isn't to memorize Bash.
> The goal is to understand it well enough to automate things.**

---

## 🗺️ Learning Path

```text
                    🐚 BASH
                       │
          ┌────────────┴────────────┐
          │                         │
      🐧 Linux                  📜 Scripting
          │                         │
     ┌────┴────┐              ┌─────┴─────┐
     │         │              │           │
  Commands  Files          Variables   Arguments
     │         │              │           │
     └────┬────┘              └─────┬─────┘
          │                         │
          └────────────┬────────────┘
                       │
                 🔀 Conditions
                       │
                    🔁 Loops
                       │
                   🧩 Functions
                       │
                 📦 Arrays
                       │
                 🔗 Pipes & I/O
                       │
              🧮 Arithmetic
                       │
             🔄 Command Substitution
                       │
              🔀 Process Substitution
                       │
                🔍 Text Processing
                       │
                 ⚠️ Error Handling
                       │
                    🚀 Projects
                       │
                    DEVOPS
```

---

## 📚 Contents

* [🐧 Linux Fundamentals](#-linux-fundamentals)
* [📜 Bash Basics](#-bash-basics)
* [🔀 Conditions](#-conditions)
* [🔁 Loops](#-loops)
* [🧩 Functions](#-functions)
* [📦 Arrays](#-arrays)
* [🔗 Pipes & Redirection](#-pipes--redirection)
* [🧮 Arithmetic Expressions](#-arithmetic-expressions)
* [🔄 Command Substitution](#-command-substitution)
* [🔀 Process Substitution](#-process-substitution)
* [🔍 Text Processing](#-text-processing)
* [🚦 Exit Status & Error Handling](#-exit-status--error-handling)
* [🛠️ Debugging](#️-debugging)
* [🔄 Bash Recap](#-bash-recap)
* [📂 Repository Structure](#-repository-structure)
* [🚀 Projects](#-projects)
* [📈 Progress](#-progress)
* [📚 Resources](#-resources)

---

# 🐧 Linux Fundamentals

Before diving deep into Bash, I'm getting comfortable with the Linux command line.

### 📁 Files & Directories

```bash
pwd
ls
cd
mkdir
touch
cp
mv
rm
find
```

### 🔐 Permissions

```bash
ls -l
chmod
chown
```

### 🔎 Useful Commands

```bash
man
help
type
which
history
file
stat
```

---

# 📜 Bash Basics

## Hello World

```bash
#!/usr/bin/env bash

echo "Hello, World!"
```

Make the script executable:

```bash
chmod +x script.sh
```

Run it:

```bash
./script.sh
```

---

## 📦 Variables

```bash
name="Kartik"

echo "$name"
```

### ⚠️ Remember

```bash
name="Kartik"     # ✅
name = "Kartik"   # ❌
```

Bash does **not** allow spaces around `=` during assignment.

---

## ⌨️ User Input

```bash
read -p "Enter your name: " name

echo "Hello, $name!"
```

---

## 🎯 Command-Line Arguments

```bash
./script.sh Kartik 24
```

Inside the script:

```bash
echo "$0"
echo "$1"
echo "$2"
echo "$#"
echo "$@"
```

| Parameter | Meaning             |
| :-------: | ------------------- |
|    `$0`   | Script name         |
|    `$1`   | First argument      |
|    `$2`   | Second argument     |
|    `$#`   | Number of arguments |
|    `$@`   | All arguments       |
|    `$?`   | Exit status         |
|    `$$`   | Current shell PID   |

---

# 🔀 Conditions

## `if`

```bash
if [[ condition ]]; then
    echo "True"
fi
```

### Example

```bash
if [[ -f "$file" ]]; then
    echo "File exists"
else
    echo "File does not exist"
fi
```

---

## 🧪 Common Tests

### Files

```bash
-f    # Regular file
-d    # Directory
-e    # Exists
-r    # Readable
-w    # Writable
-x    # Executable
```

### Strings

```bash
-z "$var"    # Empty
-n "$var"    # Not empty
```

### Numbers

```bash
-eq
-ne
-lt
-le
-gt
-ge
```

---

# 🔁 Loops

## `for`

```bash
for file in *.txt; do
    echo "$file"
done
```

## `while`

```bash
while [[ condition ]]; do
    echo "Running..."
done
```

## `until`

```bash
until [[ condition ]]; do
    echo "Waiting..."
done
```

### Loop Control

```bash
break
continue
```

---

# 🧩 Functions

Functions make scripts reusable.

```bash
greet() {
    local name="$1"

    echo "Hello, $name!"
}

greet "Kartik"
```

### Concepts

* Function arguments
* `local`
* Return status
* Scope
* Reusability

---

# 📦 Arrays

Bash supports two main types of arrays:

* **Indexed arrays**
* **Associative arrays**

---

## 🔢 Indexed Arrays

Indexed arrays use numbers as indexes.

```bash
fruits=("apple" "banana" "mango")
```

Access individual elements:

```bash
echo "${fruits[0]}"
echo "${fruits[1]}"
```

Output:

```text
apple
banana
```

### Get all elements

```bash
echo "${fruits[@]}"
```

### Get number of elements

```bash
echo "${#fruits[@]}"
```

### Loop through an array

```bash
for fruit in "${fruits[@]}"; do
    echo "$fruit"
done
```

### Add an element

```bash
fruits+=("orange")
```

---

## 🔑 Associative Arrays

Associative arrays use **keys instead of numeric indexes**.

```bash
declare -A person

person[name]="Kartik"
person[age]="24"
person[city]="Pune"
```

Access values using their keys:

```bash
echo "${person[name]}"
echo "${person[city]}"
```

### Useful for finding unique values

```bash
declare -A unique

for item in "${arguments[@]}"; do
    unique[$item]=1
done
```

If the same key appears again, it doesn't create another element.

```text
foo → 1
foo → 1
bar → 1
```

There are only **2 unique keys**:

```text
foo
bar
```

### Get number of unique keys

```bash
echo "${#unique[@]}"
```

---

## 🔢 Array Expansion

```bash
"${array[@]}"
```

Expands each element separately.

```bash
"${array[*]}"
```

Expands all elements as a single string.

Example:

```bash
items=("apple" "banana" "mango")

for item in "${items[@]}"; do
    echo "$item"
done
```

---

# 🔤 IFS — Internal Field Separator

`IFS` stands for **Internal Field Separator**.

Bash uses it when splitting words and when joining array elements with `[*]`.

The default value normally contains:

```text
space
tab
newline
```

### Example

```bash
items=("apple" "banana" "mango")

IFS=,

echo "${items[*]}"
```

Output:

```text
apple,banana,mango
```

Without changing `IFS`:

```bash
echo "${items[*]}"
```

Output:

```text
apple banana mango
```

### Remember

```text
"${array[@]}" → each element separately
"${array[*]}" → elements joined using IFS
```

`IFS` is especially useful when controlling how Bash splits or joins data.

---

# 🔗 Pipes & Redirection

One of the most important concepts in Linux.

### Standard Streams

```text
stdin   →  0
stdout  →  1
stderr  →  2
```

### Redirection

```bash
command > file.txt
command >> file.txt
command < file.txt
command 2> error.txt
command 2>&1
```

### Input Redirection

```bash
command < file.txt
```

The file is connected to the command's **standard input**.

### Pipes

```bash
command1 | command2
```

Example:

```bash
ps aux | grep bash
```

Think of it as:

```text
Command A
    │
    ▼
 stdout
    │
    ▼
Command B
    │
    ▼
 stdout
```

---

# 🧮 Arithmetic Expressions

Bash can perform arithmetic using:

```bash
$(( expression ))
```

Example:

```bash
a=10
b=5

echo $((a + b))
```

Output:

```text
15
```

### Common operators

```bash
+     # Addition
-     # Subtraction
*     # Multiplication
/     # Division
%     # Modulus
**    # Exponentiation
```

### Arithmetic commands

Bash also supports:

```bash
(( expression ))
```

Example:

```bash
(( a += 5 ))
(( b *= 2 ))
```

### Bitwise operators

```bash
&     # AND
|     # OR
^     # XOR
<<    # Left shift
>>    # Right shift
```

Example:

```bash
b=10

(( b >>= 1 ))

echo "$b"
```

Output:

```text
5
```

### Integer variables

`declare -i` tells Bash to treat a variable as an integer during assignments.

```bash
declare -i x

x=10+20

echo "$x"
```

Output:

```text
30
```

### Number bases

Bash arithmetic supports different bases.

A leading `0` can make Bash interpret a number as **octal (base 8)**:

```bash
d=010

echo "$d"
echo "$(( d ))"
```

Output:

```text
010
8
```

To force decimal (base 10):

```bash
echo "$(( 10#$d ))"
```

Output:

```text
10
```

---

# 🔄 Command Substitution

Command substitution allows you to **run a command and use its output as a value**.

The modern syntax is:

```bash
$(command)
```

Example:

```bash
current_dir=$(pwd)

echo "$current_dir"
```

Here:

```text
pwd
 ↓
output
 ↓
$(pwd)
 ↓
current_dir
```

Another example:

```bash
files=$(ls)

echo "$files"
```

### Why use it?

It is useful when the output of one command needs to be used somewhere else.

```bash
today=$(date)

echo "Today is: $today"
```

### Old syntax

You may also see:

```bash
`command`
```

Example:

```bash
current_dir=`pwd`
```

But `$(command)` is preferred because it is easier to read and can be nested.

---

# 🔀 Process Substitution

Process substitution lets you **use the output of a command as if it were a file**.

Syntax:

```bash
<(command)
```

Example:

```bash
diff <(sort file1.txt) <(sort file2.txt)
```

Here, Bash runs both `sort` commands and gives `diff` something it can read like files.

Conceptually:

```text
file1.txt → sort ──┐
                   ├──→ diff
file2.txt → sort ──┘
```

Another example:

```bash
while read -r line; do
    echo "$line"
done < <(ls)
```

The first `<` is **input redirection**.

The second `<(ls)` is **process substitution**.

```text
ls
 ↓
<(ls)
 ↓
input to while loop
```

### Command Substitution vs Process Substitution

```text
$(command)
     ↓
Get the command's OUTPUT as a value


<(command)
     ↓
Use the command's OUTPUT as a file-like input
```

---

# 🔍 Text Processing

Learning the Unix philosophy of combining small tools.

```bash
grep
sed
awk
cut
sort
uniq
tr
wc
head
tail
```

Example:

```bash
grep "ERROR" application.log
```

Count errors:

```bash
grep "ERROR" application.log | wc -l
```

---

# 🚦 Exit Status & Error Handling

Every command returns an exit status.

```bash
echo $?
```

```text
0      → Success
non-0  → Failure
```

### Example

```bash
if mkdir test; then
    echo "Directory created"
else
    echo "Failed"
fi
```

### Useful Options

```bash
set -e
set -u
set -o pipefail
```

Common combination:

```bash
set -euo pipefail
```

---

# 🛠️ Debugging

### Syntax Check

```bash
bash -n script.sh
```

### Debug Mode

```bash
bash -x script.sh
```

---

# 🔀 `case` Statement

The `case` statement is used to match a value against multiple patterns.

### Basic Syntax

```bash
case "$choice" in
    1)
        echo "Option 1"
        ;;
    2)
        echo "Option 2"
        ;;
    *)
        echo "Invalid option"
        ;;
esac
```

### 🔑 Case Terminators

Bash provides three important ways to end a `case` pattern:

| Terminator | Behavior                                                                     |
| :--------: | ---------------------------------------------------------------------------- |
|    `;;`    | Stop the `case` statement after the matching pattern                         |
|    `;&`    | Continue directly to the commands of the **next pattern** without testing it |
|    `;;&`   | Continue and **test the next pattern** as well                               |

### `;;` — Normal Behavior

Stops after the first matching pattern.

```bash
case "$value" in
    1)
        echo "One"
        ;;
    2)
        echo "Two"
        ;;
esac
```

### `;&` — Fall Through

Runs the commands of the **next pattern without checking whether it matches**.

```bash
case "$value" in
    1)
        echo "One"
        ;&
    2)
        echo "Two"
        ;;
esac
```

If `$value` is `1`:

```text
One
Two
```

### `;;&` — Continue Pattern Matching

After executing the current pattern, Bash continues to the **next pattern and checks it**.

```bash
case "$value" in
    1)
        echo "One"
        ;;&
    1|2)
        echo "One or Two"
        ;;
esac
```

If `$value` is `1`:

```text
One
One or Two
```

### 🧠 Quick Memory Trick

```text
;;   → STOP

;&   → NEXT pattern's commands
       (don't test)

;;&  → NEXT pattern
       (test again)
```

> **`;;` stops, `;&` falls through, `;;&` keeps matching.**

---

# 🔄 Bash Recap

This section is a quick review of the concepts I've learned so far.

### Variables

```bash
name="Kartik"

echo "$name"
```

### Arguments

```bash
"$@"
"$1"
"$2"
"$#"
```

### Indexed Arrays

```bash
items=("one" "two" "three")

echo "${items[0]}"
echo "${#items[@]}"
```

### Associative Arrays

```bash
declare -A unique

unique[apple]=1
unique[banana]=1
```

### IFS

```bash
IFS=,

echo "${items[*]}"
```

### Arithmetic

```bash
(( x += 10 ))

echo "$((x * 2))"
```

### Command Substitution

```bash
result=$(command)
```

### Process Substitution

```bash
diff <(command1) <(command2)
```

### Input / Output

```bash
command < input.txt
command > output.txt
command 2> error.txt
command | another-command
```

### Functions

```bash
function_name() {
    local value="$1"
    echo "$value"
}
```

### `case`

```bash
case "$value" in
    pattern)
        command
        ;;
esac
```

---

## 🧠 What I'm Practicing

Instead of only reading about a feature, I try to:

```text
Learn
  ↓
Write
  ↓
Run
  ↓
Experiment
  ↓
Break
  ↓
Understand the error
  ↓
Fix
  ↓
Document
```

---

# 📈 Progress

### Course Progress

```text
[████████░░░░░░░░░░░░] 40%
```

## 📈 Learning Log

| Date          | What I Learned                    |
| :------------ | :-------------------------------- |
| `11 Aug 2026` | Started Bash scripting            |
| `13 Aug 2026` | Learned `case` statements in Bash |
| `05 Sep 2026` | Learned indexed arrays            |
| `05 Sep 2026` | Learned associative arrays        |
| `05 Sep 2026` | Learned `IFS`                     |
| `05 Sep 2026` | Learned arithmetic expressions    |
| `05 Sep 2026` | Learned command substitution      |
| `05 Sep 2026` | Learned process substitution      |

---

## 🧠 Concepts I'm Building

| Concept                | Status |
| :--------------------- | :----: |
| Shell & Terminal       |    ✅   |
| Linux Commands         |    ✅   |
| Files & Directories    |    ✅   |
| Globbing               |   🟡   |
| Variables              |   🟡   |
| User Input             |   🟡   |
| Arguments              |   🟡   |
| Conditions             |   🟡   |
| `case` Statement       |    ✅   |
| Loops                  |   🟡   |
| Functions              |   🟡   |
| Indexed Arrays         |    ✅   |
| Associative Arrays     |    ✅   |
| `IFS`                  |    ✅   |
| Pipes                  |   🟡   |
| Redirection            |   🟡   |
| Arithmetic Expressions |    ✅   |
| Command Substitution   |    ✅   |
| Process Substitution   |    ✅   |
| Text Processing        |    ⬜   |
| Exit Status            |    ⬜   |
| Error Handling         |    ⬜   |
| Processes              |    ⬜   |
| Signals                |    ⬜   |
| Subshells              |    ⬜   |
| Advanced Bash          |    ⬜   |

---

**Legend:**
`✅ Completed` · `🟡 Learning` · `⬜ Not Started`

---

# 🧪 My Learning Method

I don't want this repository to become a collection of copied commands.

For every topic:

```text
        🎥 WATCH
           │
           ▼
        🧠 UNDERSTAND
           │
           ▼
        ⌨️ WRITE
           │
           ▼
        💥 BREAK
           │
           ▼
        🐛 DEBUG
           │
           ▼
        📝 DOCUMENT
           │
           ▼
        🚀 AUTOMATE
```

> **Watch less. Type more. Break things. Fix them.**

---

# 🎯 End Goal

```text
Bash
 │
 ├── 🐧 Linux
 │
 ├── ⚙️ Automation
 │
 ├── 🔧 System Administration
 │
 ├── 🌐 Networking
 │
 ├── 🐳 Docker
 │
 ├── 🔄 CI/CD
 │
 └── ☁️ DevOps
```

The ultimate goal is to become comfortable enough with Linux and Bash that when I encounter a repetitive task, my first thought is:

> **"Can I automate this?"**

---

# 📚 Resources

### 🎥 Primary Course

**The Complete Bash Scripting Course — Dave Eddy**

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=Sx9zG7wa4FA)

[🌐 Course Website](https://course.ysap.sh/)

### 📖 References

```bash
man bash
help <command>
info bash
```

### 🔍 Tools

* [ShellCheck](https://www.shellcheck.net/)
* Bash
* Git
* GitHub
* Linux

---

<p align="center">

### 🐚 Learn Bash. Break Bash. Automate Everything.

**Linux → Bash → Automation → DevOps**

</p>
