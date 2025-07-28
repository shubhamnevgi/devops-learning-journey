# DevOps Interview Notes (Shell Scripting & Linux – Most Common Interview Q&A for Freshers) 🐧📜💬

### Q1: What are the most commonly used shell commands in your daily work? 👨‍💻

**Answer:**
Interviewers are checking for hands-on familiarity. Mention practical commands:

* `ls` – List files and directories 📂
* `cp` – Copy files 📄➡️📄
* `mv` – Move/rename files 🚚
* `mkdir` – Create directories 📁
* `touch` – Create an empty file ✨
* `vim`/`vi` – Open files for editing 📝
* `grep` – Filter output or search inside files 🔍
* `find` – Search for files 🔎
* `df`, `du` – Check disk usage 💾
* `top`, `ps` – Monitor processes 📊

(Don’t list advanced/networking tools unless you actually use them often; be honest and practical!) 👍

---

### Q2: Write a simple shell script to list all running processes. 📝 processes

**Answer:**
Use the `ps -ef` command:
```bash
#!/bin/bash
ps -ef
````

To print only the process IDs (PIDs), filter the output:

```bash
#!/bin/bash
ps -ef | awk '{print $2}'
```

Explain that `awk '{print $2}'` prints the second column, which is usually the PID. 💡

-----

### Q3: How do you extract only errors from a remote log file in a shell script? 🚨📄

**Answer:**
Combine `curl` (to fetch log), the pipe operator `|`, and `grep` for filtering:

```bash
curl <log_file_url> | grep ERROR
```

  * `curl` gets the file contents. 🌐
  * `grep ERROR` filters lines containing “ERROR”. 🔍
  * The pipe (`|`) passes data from one command to another. ➡️

-----

### Q4: Write a shell script to print numbers divisible by 3 and 5 but not by 15, for a range (e.g., 1 to 100). 🔢

**Sample Script:**

```bash
#!/bin/bash
for i in {1..100}; do
  if { [ $((i % 3)) -eq 0 ] || [ $((i % 5)) -eq 0 ]; } && [ $((i % 15)) -ne 0 ]; then
    echo $i
  fi
done
```

  * Use a `for` loop for the range. 🔁
  * Use modulo `%` for divisibility checks. ➗
  * Use `&&` and `||` for complex conditions. ➕➖
  * Clarify your reasoning for each step in the interview. 🗣️

-----

### Q5: How to count the occurrences of a specific character (e.g., ‘s’) in a string (“Mississippi”)? 🔠

**Answer:**

```bash
#!/bin/bash
echo "Mississippi" | grep -o "s" | wc -l
```

  * `grep -o "s"` outputs every ‘s’ on a new line. 🆕
  * `wc -l` counts the lines = count of ‘s’. 📏

-----

### Q6: How do you debug a shell script? 🐛

**Answer:**
Add `set -x` at the start. It will print each command before executing it, enabling easier troubleshooting. 🛠️

-----

### Q7: What is crontab and its use in Linux? ⏰

**Answer:**
**Crontab** schedules tasks to run at fixed times/dates (e.g., run a script every day at 6pm). 🗓️

**Example entry:**

```bash
0 18 * * * /path/to/script.sh
```

This will run `script.sh` every day at 6:00 PM. ⏱️

-----

### Q8: How do you open a file in read-only mode with `vim`? 🔒📄

**Answer:**
Use:

```bash
vim -R filename.txt
```

The `-R` flag is for read-only mode. 👓

-----

### Q9: What’s the difference between a hard link and a soft link (symbolic link) in Linux? 🔗

  * **Hard link:** Creates an exact copy (pointer) to the file's data on disk. If the original is deleted, the data stays as long as a hard link exists. 💪
  * **Soft link (symlink):** Is a shortcut pointing to the file path. If the original is deleted, the symlink breaks. 👻
  * Use `ln` to create a hard link, `ln -s` to create a symlink. ➡️

-----

### Q10: What’s the difference between `break` and `continue` in loops? 🔁

  * `break` exits the loop entirely. 🚪
  * `continue` skips the current iteration and continues with the next. ⏭️

-----

### Q11: Is Bash dynamically or statically typed? ✍️

**Answer:**
Bash is **dynamically typed** – variables can change type/value at runtime, no type declaration required. 🔄

-----

### Q12: What tools do you use for network troubleshooting in Linux? 🌐

**Answer:**

  * `traceroute` – To trace the path to a network host. 🗺️
  * `tracepath` – Similar to traceroute, doesn’t require root privileges. 🗺️ (no root)

-----

### Q13: How do you sort a list of names in a file? 🔤

**Answer:**
Use the `sort` command:

```bash
sort filename.txt
```

-----

### Q14: How would you manage huge log files generated every day in Linux? 🧹📄

**Answer:**
Use **`logrotate`** to automatically compress, rotate, and delete logs as per retention policy. ⚙️
**Example:** Rotate logs daily, compress, and remove logs older than 30 days. 📆

```
