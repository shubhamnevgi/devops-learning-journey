# DevOps Interview Notes (Shell Scripting Zero to Hero – Key Q&A & Practical Guide) 📜🚀

### Q1: What is Shell Scripting and Why Use It in DevOps? 🤖

**Answer:**
**Shell scripting** is the process of writing scripts to automate routine tasks on a Linux system. In DevOps, it is crucial for automating repetitive tasks such as provisioning servers, deploying code, or maintaining environments. Automation via shell scripts saves time, reduces human error, and is fundamental in CI/CD automation and system administration. ⏰🛡️

---

### Q2: How do you create a file and list files/folders in Linux? 📂

**To create a file:**
```bash
touch filename.sh
````

**To list files/folders:**

```bash
ls
ls -ltr # shows details like timestamps and permissions
```

-----

### Q3: What is the `man` command and when would you use it? 🤔

**Answer:**
The `man` command shows the manual (help documentation) for any Linux command. For example, `man touch` gives documentation for the `touch` command—useful when you forget command options or syntax. 📖

-----

### Q4: How do you open and write to a file in Linux? ✍️

**Edit a file:**

```bash
vi filename.sh
# or
vim filename.sh
```

`vi` is available by default; `vim` might need installation.

**Write to the file:**
After opening, press `i` to enter insert mode, type your content, press `Esc`, then type `:wq!` to save and exit. 💾

-----

### Q5: What is the difference between `touch` and `vim`/`vi` for file creation? ↔️

| Feature   | `touch`                       | `vim`/`vi`                        |
| :-------- | :---------------------------- | :-------------------------------- |
| **Purpose** | Create empty file             | Create and edit file             |
| **Usage** | Used in scripts/automations   | Used for manual editing          |
| **Example** | `touch myfile.sh`             | `vi myfile.sh`                    |

-----

### Q6: What is the purpose of the shebang (`#!`) line like `#!/bin/bash` at the start of scripts?  interpreters

**Answer:**
The **shebang (`#!`)** defines which shell/interpreter should execute the script (e.g., bash, sh, ksh). For DevOps, it's recommended to use `#!/bin/bash` as bash is the most common and compatible shell. 🚀

-----

### Q7: What is the difference between `/bin/sh`, `/bin/bash`, and `/bin/dash`? 🔄

**Answer:**
Previously, `/bin/sh` would redirect (link) to `/bin/bash`, but modern Linux distributions (like Ubuntu) may link it to `/bin/dash`. Bash supports more features and is the standard for scripting, so always use `#!/bin/bash` for portability and consistency in scripts. ✅

-----

### Q8: How do you print output in a shell script? 💬

Use the `echo` command:

```bash
echo "Hello World"
```

-----

### Q9: How to run/execute a shell script on Linux? ▶️

**Direct execution:**

```bash
./filename.sh
```

(might need execute permission via `chmod +x filename.sh`)

**Using the shell:**

```bash
sh filename.sh
# or
bash filename.sh
```

-----

### Q10: What is `chmod` used for? 🔒

**Answer:**
`chmod` changes file permissions. For execution, use `chmod 777 filename.sh` (grants all permissions to everyone, **not secure for production**). Numbers map to:

  * `4` = read 📖
  * `2` = write ✍️
  * `1` = execute ▶️

So, `7` = `4+2+1` (all permissions).
**Example:** `chmod 777 script.sh` grants full permissions to user, group, and others. **Always grant the least privileges needed\!** ⛔

-----

### Q11: How do you view command history in Linux? 🕰️

**Show recent commands:**

```bash
history
```

-----

### Q12: What are some essential Linux commands for shell scripting? 🛠️

| Command     | Purpose                       |
| :---------- | :---------------------------- |
| `ls`        | Lists files & folders         |
| `touch`     | Creates files                 |
| `vi`/`vim`  | Edits files (text editor)     |
| `cat`       | Displays file contents        |
| `chmod`     | Changes file/folder permissions |
| `pwd`       | Prints working directory      |
| `mkdir`     | Makes a new directory/folder  |
| `cd`        | Changes directories           |
| `man`       | Opens the manual for a command |

-----

### Q13: How do you check CPU, RAM, and running processes from the command line? 📊

  * **CPU and RAM:**
    ```bash
    free -m
    ```
  * **Running processes:**
    ```bash
    top
    ```
  * **Number of CPU cores:**
    ```bash
    nproc
    ```
  * **Disk usage:**
    ```bash
    df -h
    ```

-----

### Q14: What makes shell scripting important in DevOps? ⭐

  * Automates regular system/admin/dev tasks. 🔄
  * Ensures repeatability and consistency. ✨
  * Enables hands-free CI/CD and troubleshooting. 🚀
  * Is foundational knowledge for managing Linux servers in cloud or on-prem environments. ☁️🏡

-----

### Example Practical Flow: Writing and Running a Simple Shell Script 👨‍💻

**Create a new script:**

```bash
touch hello.sh
```

**Edit and add content:**

```bash
vi hello.sh
```

# Add the lines:

```bash
#!/bin/bash
echo "Hello, DevOps World!"
```

**Change permissions to make it executable:**

```bash
chmod +x hello.sh
```

**Run the script:**

```bash
./hello.sh
```

Output: `Hello, DevOps World!` 👋

-----

### Sample Interview Q\&A for Freshers 🗣️

**Q:** What steps are needed to automate daily DevOps activities with shell scripting?

**A:** Identify repetitive tasks, write scripts with commands like `touch`, `ls`, `chmod`, and schedule them using tools (e.g., cron), ensuring proper permissions and reliable execution. ✅

**Q:** Why not always give `chmod 777` to all files?

**A:** It gives full permissions to everyone, which is a **security risk**. Grant the least privileges needed for the script to run. 🚨🔒

