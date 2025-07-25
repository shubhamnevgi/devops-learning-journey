# DevOps Interview Notes: Connecting to EC2 Instances from Windows using MobaXterm

### Q1: What is MobaXterm, and why is it recommended for Windows users?

**Answer:**
MobaXterm is a free, user-friendly SSH client for Windows. It simplifies the process of connecting to Linux-based servers (like EC2 instances) by supporting `.pem` key files natively (unlike PuTTY, which requires `.ppk` conversion) and combining SSH, file transfer, and session management in one tool. It’s seen as easier and more reliable for beginners than alternatives.

---

### Q2: How do you connect to an AWS EC2 instance from a Windows laptop using MobaXterm?

**Step-by-step procedure:**

#### ✅ Launch EC2 Instance
- Go to AWS Console → Launch new EC2 instance (e.g., Ubuntu with `t2.micro`)
- Download the key pair as a `.pem` file and store it securely.

#### ✅ Prepare Network Settings
- Ensure your EC2 instance has a **public IP**.
- Confirm that the **security group** allows **SSH (port 22)** from your IP or 0.0.0.0/0 (for practice).

#### ✅ Install MobaXterm
- Download the **Community/Home Edition** from the official website.
- Install it (use the *installer* version for easier setup).

#### ✅ First-Time Setup
- Locate the `.pem` key in your Downloads folder.

#### ✅ Create SSH Session in MobaXterm
1. Open MobaXterm → Click `Session` → Choose `SSH`
2. **Hostname:** Enter the **public IP** of your EC2 instance
3. **Username:** Use `ubuntu` (for Ubuntu EC2)
4. Go to `Advanced SSH Settings` → Enable **Use private key** → Browse to your `.pem` file
5. Click **OK** to connect

#### ✅ Accept SSH Prompt & Verify
- Accept the SSH fingerprint prompt.
- You’ll land in the Linux terminal if successful.
- Run a test command like `sudo apt update` to confirm access.

---

### Q3: What are the key things to remember about SSH keys and secure connections?

- Always use the original `.pem` file with MobaXterm. No need to convert to `.ppk`.
- If you lose the private key, you **lose access** to the instance.
- Never share your SSH key publicly; keep it secure and backed up.

---

### Q4: How would you describe this process in an interview?

**Sample Answer:**
> "To connect to an EC2 instance from a Windows laptop, I’d use MobaXterm since it supports AWS `.pem` keys directly and makes SSH simple. After ensuring the instance has a public IP and SSH access, I input the IP, choose the `ubuntu` user, and connect using the key. Within seconds, I'm securely connected and can begin DevOps tasks."

---

### Q5: Why do recruiters value hands-on knowledge of MobaXterm and EC2 access?

- Shows you're ready to handle cloud server setup and troubleshooting.
- Indicates awareness of SSH security practices (key handling, port configuration).
- Demonstrates practical exposure to industry-standard DevOps tools.

---

### ✅ Practical Quick Checklist — EC2 via MobaXterm

| Step               | Key Action                                              |
|--------------------|---------------------------------------------------------|
| Launch EC2         | Download `.pem` key, note the public IP                |
| Network Settings   | Ensure port 22 (SSH) is open to your IP                |
| Install MobaXterm  | Use official installer on your Windows laptop          |
| New SSH Session    | Input public IP, set username as `ubuntu`, attach `.pem` |
| Connect & Verify   | Accept prompt, test with Linux commands                |
