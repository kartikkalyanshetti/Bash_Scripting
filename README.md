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
                 🔗 Pipes & I/O
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
* [🔗 Pipes & Redirection](#-pipes--redirection)
* [🔍 Text Processing](#-text-processing)
* [🚦 Exit Status & Error Handling](#-exit-status--error-handling)
* [🛠️ Debugging](#️-debugging)
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

### ShellCheck

```bash
shellcheck script.sh
```

> 🧠 **Debugging is part of learning.**
>
> Breaking a script intentionally is often a better learning experience than simply reading working code.

---

# 🧠 Concepts I'm Building

| Concept             | Status |
| :------------------ | :----: |
| Shell & Terminal    |    ✅   |
| Linux Commands      |    ✅   |
| Files & Directories |    ✅   |
| Globbing            |   🟡   |
| Variables           |   🟡   |
| User Input          |   🟡   |
| Arguments           |   🟡   |
| Conditions          |   🟡   |
| Loops               |   🟡   |
| Functions           |    ⬜   |
| Arrays              |    ⬜   |
| Pipes               |   🟡   |
| Redirection         |   🟡   |
| Text Processing     |    ⬜   |
| Exit Status         |    ⬜   |
| Error Handling      |    ⬜   |
| Processes           |    ⬜   |
| Signals             |    ⬜   |
| Subshells           |    ⬜   |
| Advanced Bash       |    ⬜   |

**Legend:**
`✅ Completed` · `🟡 Learning` · `⬜ Not Started`

---



# 📈 Progress

### Course Progress

```text
[████░░░░░░░░░░░░░░░░] 20%
```

> 🎯 Progress will be updated as I complete the course.

### Learning Log

| Date          | What I Learned         |
| :------------ | :--------------------- |
| `11 Aug 2026` | Started Bash scripting |
|               |                        |
|               |                        |
|               |                        |

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
