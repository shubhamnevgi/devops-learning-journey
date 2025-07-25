# DevOps Interview Notes (Day 6: Linux & Shell Scripting Fundamentals) 🐧📜

### 1. What is an Operating System (OS) and how does it work? 🖥️

**Answer:**
An **operating system** acts as a bridge between hardware and software, enabling applications to interact with computer hardware (CPU, RAM, storage, etc.). It manages resources, provides an interface for user interactions, and coordinates the execution of application programs. ⚙️

**Interview tip:**
In real-world terms, the OS lets users run applications (like Jenkins, Python, or Java) on their hardware. Users interact with applications, applications talk to the OS, and the OS manages hardware resources. 🤝

---

### 2. Why is Linux widely used in DevOps and cloud environments? ☁️🚀

**Answer:**

* **Open Source:** Free to use and modify. 🆓
* **Security:** Built-in security features; less prone to malware and viruses compared to Windows. 🛡️
* **Speed:** Lightweight, fast, and reliable for server and cloud use. ⚡
* **Stability:** Rarely crashes; trusted for production workloads. 💪
* **Multiple distributions:** Ubuntu, CentOS, Red Hat, Debian, etc.; choose per use case. choices.
* **Industry Standard:** Most servers, cloud platforms, and production workloads use Linux. 🥇

---

### 3. What is the architecture of Linux OS? 🏗️

**Core Components:**

| Component          | Description                                                                 |
| :----------------- | :-------------------------------------------------------------------------- |
| **Kernel** | The "heart" of the OS. Manages communication between hardware and software. Handles process, memory, device management, and system calls. ❤️ |
| **System Libraries** | Tools/functions for user programs to interact with the kernel. Example: `glibc`. 📚 |
| **System Software** | Tools for system setup/maintenance (e.g., shell, command-line tools). 🔧      |
| **User Processes** | Applications and services launched by users or system software. 🏃‍♂️           |

**Kernel responsibilities:**
* Device Management 💾
* Memory Management 🧠
* Process Management 🔄
* Handling System Calls 📞

---

### 4. What is Shell and why is Shell Scripting important in DevOps? ✍️ automation

**Answer:**
The **shell** is a command-line interpreter that lets users interact with the OS. ⌨️

**Shell scripting** automates tedious tasks (file manipulation, deployments, monitoring). 🤖
Bash is the most common shell for Linux (preferred for DevOps). 🚀

---

### 5. What are some fundamental Linux commands every DevOps fresher should know? 🔑

| Command     | Purpose                                     | Example/Usage                   |
| :---------- | :------------------------------------------ | :------------------------------ |
| `pwd`       | Print working directory                     | `pwd` (Shows current folder)    |
| `ls`        | List files and directories                  | `ls -ltr` (shows details/date)  |
| `cd`        | Change directory                            | `cd /home/ubuntu`               |
| `touch`     | Create a new empty file                     | `touch hello.txt`               |
| `vi`/`nano` | Text editors to create/edit files           | `vi myscript.sh`                |
| `cat`       | View contents of a file                     | `cat hello.txt`                 |
| `mkdir`     | Create a directory                          | `mkdir newfolder`               |
| `rm`        | Remove a file                               | `rm file.txt`                   |
| `rm -r`     | Remove a directory and its contents         | `rm -r foldername`              |
| `ls -ltr`   | Detailed file listing (permissions, owner, timestamp) | (Already covered with `ls`) 👀 |

---

### 6. How do you view and manage system resources from the command line? 📊

* **Memory usage:** `free -g` (shows in GB) 🧠
* **CPU information:** `nproc` (shows number of CPU cores) ⚙️
* **Disk usage:** `df -h` (human-readable disk free space) 💾
* **Real-time monitoring:** `top` (shows CPU, memory, processes) 📈

---

### 7. Practical: How do you create and edit files in Linux? 🛠️

* Use `touch filename` to create a file. ✨
* Use `vi filename` to open and edit (press `i` for insert mode, write content, press `Esc`, then type `:wq` to save & exit). 📝
* Use `cat filename` to view file content. 👀
* To create a directory: `mkdir dir_name` 📁
* To remove a file: `rm filename` ❌
* To remove a directory: `rm -r dir_name` 🗑️

---

### 8. What is the typical process flow to connect to a Linux server for DevOps tasks? ➡️

**Step-by-step:**

1.  **Provision instance/server** (e.g., on AWS, Azure). ☁️
2.  **Connect via SSH** from your terminal (using appropriate user and key). 🔑
3.  **Navigate directories and manage files** using shell commands. 📂
4.  **Monitor system health** (`free`, `top`, etc.) and automate with shell scripts. 🩺🤖

---

### 9. Why is it important for a DevOps engineer to master Linux and shell scripting? 🏆

* Most real-world servers use Linux. 🌐
* Automating deployment, configuration, and monitoring saves time and prevents errors. ⏰🚫
* Command line is essential; GUIs are rarely installed on production systems. 🚫🖥️
* Common commands and scripts are reusable across most distributions. ♻️

---

### 10. Example Interview Q&A 🗣️

**Q:** What command would you use to list all files in a directory with their permissions and timestamps?
**A:** `ls -ltr` ✅

**Q:** How do you check disk space usage in Linux?
**A:** `df -h` ✅

**Q:** You want to know the total RAM available on your server. What command would you use?
**A:** `free -g` ✅

**Q:** Describe a practical scenario where you’d use a shell script in DevOps.
**A:** Automating the deployment of an application, regular log cleanup, or monitoring system health. 🚀🧹🩺
