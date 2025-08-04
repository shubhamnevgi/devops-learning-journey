# 🛠️ DevOps Interview Notes (Day 15): Ansible “Begginer guide” 🦸

### **1. How Do You Get Started Practically With Ansible?**

**Step 1 – Install Ansible:**
Use your OS package manager (recommended):
* **Ubuntu:** `sudo apt update && sudo apt install ansible`
* **MacOS:** `brew install ansible`
* **Windows:** Use Chocolatey or WSL (Windows Subsystem for Linux).

Verify installation:
```bash
ansible --version
````

**Step 2 – Set Up Passwordless SSH Authentication:**
Generate key:

```bash
ssh-keygen # Creates public/private key pair in ~/.ssh/
```

Copy the public key (`id_rsa.pub`) to the `authorized_keys` file of your target machine(s). This allows the Ansible server to connect seamlessly to target servers. 🔑

**Step 3 – Prepare Your Inventory File:**
The inventory file (default: `/etc/ansible/hosts`, but often kept locally) lists the IP addresses or hostnames of target machines.
You can group machines for role-based deployments (e.g., `[webservers]`, `[dbservers]`). 📄

-----

### **2. What Is an Ansible Ad-Hoc Command? When Should You Use It?**

**Ad-hoc command:** Run direct, one-off tasks without writing a Playbook (e.g., restart a service, copy a file). 🎯

**Example:**

```bash
ansible -i inventory all -m shell -a "touch /tmp/devops-class"
```

  * `-i inventory`: points to your inventory file.
  * `all`: run on all hosts in the inventory.
  * `-m shell`: use the “shell” module.
  * `-a`: arguments to the module.

**When to use:**

  * For simple, quick tasks affecting one or a few servers.
  * For bulk actions across all or a group of servers (without needing Playbooks).

-----

### **3. What Is an Ansible Playbook and How Do You Write One?**

**Ansible Playbook:**
A YAML file containing one or more “plays”—a set of tasks to execute on a group of hosts. Playbooks are used for complex, multi-step configurations. 📜

**Sample Playbook to Install & Start Nginx:**

```yaml
---
- name: install and start nginx
  hosts: all
  become: yes
  tasks:
    - name: install nginx
      apt:
        name: nginx
        state: present
    - name: start nginx
      service:
        name: nginx
        state: started
```

Save as `first-playbook.yaml`.
Run with:

```bash
ansible-playbook -i inventory first-playbook.yaml
```

-----

### **4. How Can You Target Specific Groups of Hosts?**

In the inventory file, group machines:

```ini
[webservers]
192.168.1.10
192.168.1.20

[dbservers]
192.168.1.30
```

Run commands or playbooks on a specific group:

```bash
ansible -i inventory webservers -m ping
```

-----

### **5. Debugging and Verbosity**

Add `-v`, `-vv`, or `-vvv` for more detailed output when running playbooks:

```bash
ansible-playbook -i inventory first-playbook.yaml -vvv
```

Use output to trace errors, understand how tasks run step-by-step. 🐛

-----

### **6. What Are Ansible Roles?**

**Roles** are a way to organize complex playbooks into reusable, modular units.
Useful for large projects (e.g., setting up Kubernetes clusters with dozens of tasks). 📦

Create a role:

```bash
ansible-galaxy role init kubernetes
```

This creates a standard folder structure:

```
kubernetes/
  tasks/
  handlers/
  files/
  templates/
  vars/
  defaults/
  meta/
```

-----

### **7. Essential Ansible Interview Questions**

**Q: How does Ansible connect to target machines?**
**A:** Via SSH (Linux) or WinRM (Windows) with passwordless authentication preferred. 🔐

**Q: What is the difference between ad-hoc commands and playbooks?**
**A:**

  * **Ad-hoc:** Quick, single time operations.
  * **Playbooks:** Complex, multi-step procedures/configurations. ↔️

**Q: How do you group servers and run tasks on just one group?**
**A:** Group in the inventory file, refer by group name. 🏷️

**Q: How do you escalate privileges in a playbook?**
**A:** Use `become: yes` for root access (sudo). 👑

**Q: What language are Ansible playbooks written in?**
**A:** YAML. 📝

**Q: Why are roles important in Ansible?**
**A:** Modularization, reusability, maintainability—especially for large setups (e.g., Kubernetes, multi-tier apps). 🧩

-----

### **8. Real-World Project Scenarios**

  * Use **ad-hoc commands** for mass reboots, quick file changes, or to check disk space across 100s of servers. 📊
  * Use **playbooks** for standardized OS patching, middleware installs, or setting up new environments (e.g., QA, staging, prod) effortlessly. 🔄
  * Use **roles** for deploying entire application stacks, complex clusters, or to comply with DRY (Don’t Repeat Yourself) best practices. 🏗️

<!-- end list -->

```
```
