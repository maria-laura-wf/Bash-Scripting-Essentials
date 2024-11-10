
# Bash Scripting Essentials

This repository provides a comprehensive overview of essential Bash scripting concepts, organized into three levels of knowledge: **Basic**, **Intermediate**, and **Advanced**. This guide is ideal for both beginners and experienced users looking to expand their Bash skills.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Basic Level](#basic-level)
    - [Shebang Line](#shebang-line)
    - [Variables](#variables)
    - [User Input](#user-input)
    - [Simple Conditionals](#simple-conditionals)
    - [Basic Commands Table](#basic-commands-table)
- [Intermediate Level](#intermediate-level)
    - [Loops](#loops)
    - [Functions](#functions)
    - [File Operations](#file-operations)
    - [Command Line Arguments](#command-line-arguments)
    - [Exit Status Codes](#exit-status-codes)
    - [Indexed Arrays](#indexed-arrays)
- [Advanced Level](#advanced-level)
    - [Associative Arrays](#associative-arrays)
    - [Command Substitution](#command-substitution)
    - [Command Line Redirections](#command-line-redirections)
    - [Arithmetic Operations](#arithmetic-operations)
    - [Parameter Expansion](#parameter-expansion)
    - [Process Signal Handling](#process-signal-handling)
    - [Comments](#comments)

## Introduction

Bash scripting is an essential skill for automating tasks, managing files, and handling system operations in Unix-like operating systems. This documentation categorizes concepts by skill level, providing a clear learning path for mastering Bash.

## Prerequisites

- Basic familiarity with command-line interfaces
- A Unix-like operating system (Linux, macOS, etc.)
- Text editor for creating and editing scripts

## Basic Level

This level covers fundamental concepts that are essential for any Bash script.

### Shebang Line

```bash
#!/bin/bash
```
The shebang (#!) specifies the interpreter to run the script. For Bash scripts, this is typically /bin/bash.

### Variables

```bash
username="Jay"
filename=$3
```
Variables store data. Bash variables do not require a data type, and are referenced with $ (e.g., $username).

### User Input

```bash
read -p "Enter your username: " user
echo "Username: $user"
```
read collects user input, while the -p flag displays a prompt message.

### Simple Conditionals

```bash
if [ "$EUID" -ne 0 ]; then
  echo "Not running as root."
else
  echo "Running as root."
fi
```
if statements evaluate conditions using comparison operators like -eq, -ne, -lt, and -gt.

### Basic Commands Table

Below is a list of common Linux commands and their functionalities.

| Command | Functionality                           |
|---------|-----------------------------------------|
| ls      | Lists files and directories             |
| cd      | Changes the directory                   |
| pwd     | Prints the current directory path       |
| mkdir   | Creates a new directory                 |
| rm      | Removes files or directories            |
| cp      | Copies files or directories             |
| mv      | Moves or renames files/directories      |
| touch   | Creates a new, empty file               |
| echo    | Prints text to the terminal             |
| cat     | Concatenates and displays file content  |
| grep    | Searches text using patterns            |
| find    | Searches for files in a directory hierarchy |
| chmod   | Changes file permissions                |
| chown   | Changes file ownership                  |
| df      | Shows disk space usage                  |
| du      | Estimates file space usage              |
| top     | Displays running processes              |
| ps      | Shows current processes                 |
| kill    | Terminates processes by ID              |
| tar     | Archives files                          |
| gzip    | Compresses files                        |
| unzip   | Extracts compressed files               |
| ssh     | Connects to a remote machine securely   |
| wget    | Downloads files from the web            |
| curl    | Transfers data from or to a server      |

## Intermediate Level

This level introduces control structures, functions, and file operations, providing more control over script logic and file handling.

### Loops

```bash
for i in {1..5}; do
  echo "$i"
done
```
Loops (e.g., for, while) allow repetitive tasks. This example counts from 1 to 5.

### Functions

```bash
function greet() {
  echo "Hello, $1!"
}
greet "Alice"
```
Functions allow code reuse. greet takes an argument and outputs a greeting.

### File Operations

```bash
if [ -e "$filename" ] && [ -d "$filename" ]; then
  echo "File exists and is a directory."
else
  echo "File does not exist or is not a directory."
fi
```
File operations use flags (-e for existence, -d for directory) to check properties of files and directories.

### Command Line Arguments

```bash
echo "First argument: $1"
echo "Second argument: $2"
```
Command-line arguments allow passing data into scripts. $1, $2, etc., access each argument.

### Exit Status Codes

```bash
cat nonexistent-file.txt 2> /dev/null
echo "Exit status: $?"
```
Commands return exit codes (0 for success). $? holds the last command's exit code.

### Indexed Arrays

```bash
fruits=("Apple" "Orange" "Banana")
echo "First fruit: ${fruits[0]}"
```
Indexed arrays store ordered lists, accessed by index.

## Advanced Level

Advanced topics allow greater control over data manipulation, command outputs, and signal handling.

### Associative Arrays

```bash
declare -A capitals
capitals[USA]="Washington D.C."
capitals[France]="Paris"
echo "Capital of France: ${capitals[France]}"
```
Associative arrays use key-value pairs, ideal for mapping values.

### Command Substitution

```bash
current_date=$(date)
echo "Today's date: $current_date"
```
Command substitution runs a command and stores the output in a variable.

### Command Line Redirections

```bash
echo "This is a sample text." > example.txt
find / -name hello.txt &> /dev/null
```
Redirection operators control input/output (>, >>, and &>).

### Arithmetic Operations

```bash
result=$((5 * 2 - 2))
echo $result
```
Bash supports basic arithmetic within $(( )).

### Parameter Expansion

```bash
SRC="/path/to/foo.cpp"
BASEPATH=${SRC%%/*}
echo $BASEPATH
```
Parameter expansion manipulates variables by removing substrings or performing transformations.

### Process Signal Handling

```bash
trap "echo 'Received SIGTERM signal. Cleaning up...'; exit" SIGTERM
```
The trap command executes specified code upon receiving signals, like SIGTERM.

### Comments

```bash
# Single-line comment

: '
Multiline
comment
'
```
Comments improve readability. Single-line comments start with #; multiline comments use : '.