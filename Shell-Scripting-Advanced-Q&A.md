# DevOps Interview Notes (Shell Scripting – Advanced Q&A & Practical Guide) 🚀📜

### Core Shell Scripting Topics & Interview Questions 🔍

### Q1: How do you analyze the health of a server/node via shell scripting as a DevOps engineer? 🩺💻

**Answer:**
A DevOps engineer uses shell scripts to assess node health parameters:

* **Disk usage:** `df -h` 💾
* **Memory usage:** `free -m` or `free -g` 🧠
* **CPU count:** `nproc` ⚡
* **Process/resource monitoring:** `top` 📊

**Example:**
```bash
df -h
free -g
nproc
top
````

Interviewers often expect you to demonstrate such scripts or explain these commands. 🗣️

-----

### Q2: Why is it important to include metadata (author, date, purpose) in shell scripts? 📝

**Answer:**
Metadata clarifies the script's author, creation date, purpose, prerequisites, and version. This improves maintainability and collaboration, especially in larger teams. 🤝

-----

### Q3: What is the correct way to start a Bash script? Why specify the executable? ⬆️

**Answer:**
Start your scripts with a **shebang** specifying `/bin/bash`:

```bash
#!/bin/bash
```

Specifying Bash ensures script compatibility regardless of the default shell on the system (for example, `sh` might be linked to `dash` rather than `bash`). ✅

-----

### Q4: How do you improve the readability of your script's output? 👁️‍🗨️

  * Use `echo` statements to describe what each command does. 💬
  * For extensive scripts, use `set -x` at the start to enable debug mode, printing each command as it executes. 🐛

**Example:**

```bash
set -x
echo "Disk usage:"
df -h
```

-----

### Q5: What does `set -e` do in a shell script? Why combine with `set -o pipefail`? 🛡️

  * `set -e`: Exits the script if any command returns a non-zero (error) status. 🛑
  * `set -o pipefail`: Ensures the script fails if any command in a pipeline fails (not just the last). 💥

**Combined Example:**

```bash
set -e
set -o pipefail
```

These are best practices for robust, production-ready scripts. ✨

-----

### Q6: How do you find and filter running processes for a specific keyword? 🔍

```bash
ps -ef | grep <keyword>
```

**Example:**
To list all "amazon" processes:

```bash
ps -ef | grep amazon
```

To extract just the process IDs (PID), use `awk`:

```bash
ps -ef | grep amazon | awk '{print $2}'
```

-----

### Q7: What is the **pipe (`|`)** operator, and give a real example? 🔗

**Answer:**
The pipe sends output of one command as input to another. ➡️

**Example:**
Gets all running processes, filters those containing "amazon", and displays only their IDs:

```bash
ps -ef | grep amazon | awk '{print $2}'
```

**Interview trap:** Explain why `date | echo "Today is"` does NOT output the date.
**Reason:** `echo` does not accept piped input; it ignores stdin. 🚫📥

-----

### Q8: What is the use of `awk` in shell scripting? ✂️

`awk` is used for pattern scanning and reporting, such as extracting columns from output. 📊

**Example:**
Get the 2nd column (PID) from process list:

```bash
ps -ef | grep java | awk '{print $2}'
```

-----

### Q9: How do you reliably search for errors in remote log files as a DevOps engineer? 🕵️‍♂️📜

**Procedure:**

1.  **Retrieve the log file:**
      * Using `curl` (recommended) for fetching from web/S3:
        ```bash
        curl <url-to-logfile>
        ```
      * Or `wget` for download (natively saves the file):
        ```bash
        wget <url-to-logfile>
        ```
2.  **Pipe to `grep` for "ERROR" lines:**
    ```bash
    curl <url> | grep ERROR
    ```

**Curl vs. Wget:**

  * `curl`: Used for fetching data/streaming API responses. 🌐
  * `wget`: Used for file downloads; saves file to disk. 📥

-----

### Q10: How do you use `find` to search for files? 🌳🔎

```bash
find /path/to/search -type f -name "*.log"
```

This finds all `.log` files in the specified directory. ✅

-----

### Q11: What are `sudo` and `su` commands? 👑👤

  * `sudo`: Run commands as another user (default: root), requires *your* password. 🔑
  * `su`: Switch user, opens a login shell as another user. 🔄

-----

### Q12: How to use `if-else` and `for` loops in shell scripts? 🔁 조건

**If-Else Example:**

```bash
if [ -f file.txt ]; then
  echo "File exists"
else
  echo "File not found"
fi
```

**For Loop Example:**

```bash
for i in {1..5}; do
  echo "Number $i"
done
```

Loops and conditions are basic but vital for automation tasks. ✨

-----

### Best Practices & Interview Extras 👍

  * Always **document your code** and add comments. ✍️
  * Use robust error handling with `set -e` and `set -o pipefail`. 🚨
  * Use `echo` and debug mode (`set -x`) for clarity during troubleshooting. 🐛
  * Favor pipelines (using `|`) for chaining command outputs. ⛓️

-----

### Practical/Scenario Interview Questions 💬

**"How would you analyze a VM's health with a script?"**
Mention disk, memory, CPU, and top processes (see Q1 & Q4 above). 📊

**"How to extract only error lines from a log stored online?"**
Use: `curl <url> | grep ERROR` 🕵️‍♀️

**"How can you kill all processes started by 'tomcat'?"**
Use:

```bash
ps -ef | grep tomcat | awk '{print $2}' | xargs kill -9
```

This efficiently gets all Tomcat PIDs and forcefully terminates them. 💥

```
```
