# DevOps Interview Notes (Day 4: Creating Virtual Machines on AWS & Azure)

### Q1: What are the ways to create a Virtual Machine (VM) as a DevOps Engineer?

**Answer:**  
You can create a VM via:

- **Cloud Provider UI:** Using AWS Console or Azure Portal’s web interface for manual setup.  
- **Automation:** Utilizing command-line tools (CLI), APIs, or Infrastructure as Code (IaC) tools (e.g., AWS CLI, AWS SDKs, CloudFormation Templates, Terraform).

---

### Q2: What is the process for creating a VM using AWS Console?

**Step-by-step:**

1. **Login to AWS Console:** Access with your credentials (create a new AWS account if needed).  
2. **Navigate to EC2 Service:** Search for ‘EC2’ in the services menu.  
3. **Launch Instance:**  
   - Click "Launch Instance".  
   - Fill in details: Name, OS (common choices: Ubuntu, Amazon Linux), and instance type.  
   - **Tip:** Select “Free Tier eligible” to avoid charges while learning.  
4. **Create Key Pair:** Download and save; it’s required to SSH into your instance.  
5. **Launch:** Click on "Launch Instance".  
6. **Access:** Wait for the instance to initialize; use the provided public IP and the downloaded key file to connect via SSH.

---

### Q3: How to create a VM in Microsoft Azure Portal?

**Step-by-step:**

1. **Sign in to Azure Portal:** Create a free trial account or log in with GitHub.  
2. **Create Resource/Virtual Machine:**  
   - Click “Create Resource” then “Virtual Machine”.  
   - Fill basic details: subscription, region, OS, VM size.  
   - **Tip:** Use the “Start Free” option if eligible; note Azure’s free trial is of shorter duration.  
3. **Set Authentication:** Choose SSH public key or password.  
4. **Review & Create:** Confirm the config, then click “Create”.

---

### Q4: Why is automation preferable over manual VM creation in DevOps?

**Answer:**

- **Efficiency:** Automates repetitive tasks (e.g., creating multiple VMs on demand).  
- **Error Reduction:** Eliminates manual mistakes.  
- **Scalability:** Supports large-scale infrastructure management.  
- **Consistency:** Ensures every VM is created with identical settings.  
- **Core to DevOps:** Automation is a foundational DevOps principle.

---

### Q5: What types of automation can you use to create VMs on AWS (and similar for other clouds)?

| Automation Type | Description                           | Example Tools/Approaches                     |
|------------------|----------------------------------------|-----------------------------------------------|
| CLI (Command Line) | Scripts to run commands on your machine | AWS CLI, Azure CLI                            |
| API/SDK           | Programmatic calls through code        | boto3 (Python/AWS), Azure SDK                 |
| IaC Templates     | Templates for resource provisioning    | AWS CloudFormation, Azure ARM, Terraform     |
| Provider UI       | Manual point-and-click (not preferred) | AWS Console, Azure Portal                    |

---

### Q6: Example interview Q&A for hands-on knowledge

**Q: Suppose you need to create 10 VMs at once. How do you proceed in a DevOps way?**  
**A:**  
“I would use automation—such as AWS CLI scripts, boto3 (Python), CloudFormation templates, or Terraform—to provision multiple instances at once instead of creating them manually through the UI. This approach increases efficiency and consistency.”

**Q: What considerations must you keep in mind when creating a VM via script/API?**  
**A:**

- Ensure the API call is valid, user is authenticated and authorized.  
- Use correct resource specifications (e.g., instance size, region).  
- Manage key pairs securely for VM access.

---

### Q7: What is the significance of tools like Terraform and AWS Cloud Development Kit (CDK)?

**Answer:**

- **Terraform:**  
  - Tool for automating infrastructure across multiple cloud providers (AWS, Azure, GCP).  
  - Ideal for hybrid/multi-cloud environments.

- **AWS CDK:**  
  - Native AWS toolkit; tightly integrated and updated with AWS.  
  - Best for AWS-focused organizations.

**Choosing Tools:**

- Use AWS-specific tools (CLI, CDK) when focused on AWS.  
- Prefer Terraform for hybrid/multi-cloud or when needing cloud neutrality.

---

### Q8: Practical tip for freshers—How to create an AWS account and stay within the free tier?

- Register for a new account and verify with a credit/debit card.  
- Use Free Tier eligible resources (EC2 t2.micro, limited storage and bandwidth).  
- Monitor billing dashboard to avoid accidental costs.  
- Always terminate unused instances.

---

### Q9: What is a key pair and why is it important?

**Answer:**  
A key pair (public/private key) is used to securely SSH into your VM. Losing the private key means you cannot access your instance.

---

### Q10: How does learning VM creation help in DevOps interviews?

- Shows hands-on familiarity with cloud concepts.  
- Demonstrates understanding of both manual setup and automation (a key DevOps skill).  
- Prepares you for real-world scenarios and collaboration within teams.

---
