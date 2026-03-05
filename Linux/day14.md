
## Introduction to Search and Filter Utilities
Linux provides powerful utilities to search and filter data efficiently, streamlining tasks like file management, data parsing, and text processing.

### Importance of Searching and Filtering Data in Linux
- Saves time by automating data retrieval and organization.
- Essential for managing large datasets and directory structures.
- Integral to scripting and system administration.

## Key Utilities Overview: grep, cat, sort, uniq

### grep: Global Regular Expression Print
- **Purpose**: Searches for specific patterns in files or input streams.
- **Syntax**: `grep [OPTIONS] PATTERN [FILE]`

#### Common Options:
- `-i`: Case-insensitive search.
- `-v`: Invert match to show lines that do not match the pattern.
- `-n`: Show line numbers with matches.
- `-r`: Recursively search directories.

#### Example:
```bash
# Find lines containing "error" in a log file:
grep 'error' system.log
```

### cat: Concatenate and Display Files
- **Purpose**: Reads file content and displays it in the terminal.
- **Syntax**: `cat [OPTIONS] [FILE]`

#### Example:
```bash
# Display content of a file:
cat example.txt
```

### sort: Sort Lines in Files
- **Purpose**: Sorts lines in text files or input streams.
- **Syntax**: `sort [OPTIONS] [FILE]`

#### Common Options:
- `-r`: Reverse the sort order.
- `-n`: Sort numerically.
- `-k`: Specify a key for sorting.

#### Example:
```bash
# Sort a list of numbers:
cat numbers.txt | sort -n
```

### uniq: Filter Unique Lines
- **Purpose**: Removes duplicate lines from sorted input.
- **Syntax**: `uniq [OPTIONS] [FILE]`

#### Common Options:
- `-c`: Count occurrences of each line.
- `-d`: Show only duplicate lines.

#### Example:
```bash
# Find unique lines in a sorted file:
sort input.txt | uniq
```

## Introduction to the find Utility
`find` is a robust tool for locating files and directories based on various criteria.

### Basic Syntax of `find`
```bash
find [PATH] [OPTIONS] [EXPRESSION]
```

### Common Options:
- `-name`: Search by file name (case-sensitive).
- `-iname`: Search by file name (case-insensitive).
- `-type`: Specify file type (e.g., `f` for files, `d` for directories).
- `-size`: Search by file size (e.g., `+100k` for files larger than 100KB).
- `-mtime`: Search by modification time (e.g., `-1` for files modified in the last day).

#### Example:
```bash
# Find all .txt files in the current directory:
find . -name "*.txt"

# Find files larger than 1MB:
find /home -size +1M

# Find files modified in the last 7 days:
find /var/log -mtime -7
```

### Advanced Usage and Filtering Options
- Combine multiple expressions using `-and`, `-or`, and `!` (not).
- Execute commands on found files using `-exec`.

#### Example:
```bash
# Find and delete empty files:
find /tmp -type f -empty -exec rm {} \;
```

## Practical Exercises
1. **Search for all error logs in `/var/log`**:
   ```bash
   grep -r 'error' /var/log
   ```
2. **Find and list all `.log` files modified in the last 2 days**:
   ```bash
   find /var/log -name "*.log" -mtime -2
   ```
3. **Sort a file of names alphabetically and remove duplicates**:
   ```bash
   sort names.txt | uniq
   ```
