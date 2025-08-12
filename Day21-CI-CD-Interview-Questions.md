# 🚀 Day 21: CI/CD Interview Questions (GitHub, Jenkins, GitLab)

## 🔁 What is CI/CD and How Do You Explain It?

**CI/CD** stands for **Continuous Integration / Continuous Delivery (or Deployment)**.

-   **Continuous Integration (CI):** 🤝 Developers frequently merge their code to a shared repository. Each integration is validated by automated builds and tests to catch errors early.
-   **Continuous Delivery/Deployment (CD):** 🚚 Validated code is automatically released to pre-production or production environments, ensuring rapid and reliable delivery.

### **Example Explanation for Interviews**

> "In our organization, we use **Jenkins** as the CI orchestrator. Code is managed in **GitHub**. When a developer commits, Jenkins is triggered by a **webhook**, pulls the latest code, builds it using **Maven**, checks code quality with **SonarQube**, runs security scanning with **AppScan**, and then automatically deploys to our environments (like **Kubernetes via ArgoCD and Helm**, or **EC2 directly**)."

---

## ⚙️ Detailed CI/CD Pipeline Flow

1.  **Source Control**: Code is hosted on **GitHub/GitLab**.
2.  **Trigger**: ➡️ The pipeline is automatically triggered on a code commit. **Webhooks** are the most efficient trigger method.
3.  **Build**: 📦 Jenkins (or other CI tools) checks out the code and runs the build process (e.g., using Maven for Java).
4.  **Testing**: 🧪 Automated static code analysis, unit, and security tests are performed.
5.  **Deploy**: 🚀 Successful builds are promoted to different environments (Dev, QA, Prod), often using tools like **ArgoCD**.
6.  **GitOps**: 🔄 **ArgoCD** monitors the Git repository for changes to deployment manifests and automatically updates the Kubernetes clusters to match the desired state.

---

## 🔔 Key Ways to Trigger Jenkins Pipelines

-   **Webhooks**: 🌐 GitHub notifies Jenkins directly when code changes occur via a JSON payload. This is the most efficient method.
-   **Polling/Build Triggers**: ⏳ Jenkins periodically checks the repository for changes. This is less efficient and can cause delays.
-   **Manual or Scheduled Triggers**: 📅 You can also trigger pipelines manually or on a fixed schedule (using cron jobs).

---

## ❓ Jenkins CI/CD Interview Questions

### **Beginner-Level**

-   **Q: What is CI/CD? Why is it important?**
    -   **A:** It automates code integration, testing, and deployment to increase quality, reduce manual errors, and deliver faster.
-   **Q: How do you trigger Jenkins pipelines on source code changes?**
    -   **A:** By configuring **GitHub webhooks** to send a JSON payload to Jenkins on a `push` or `pull request` event.
-   **Q: How do you back up Jenkins?**
    -   **A:** Take a backup of the entire `.jenkins` folder. For larger organizations, you'd also back up external databases and plugins.

### **Intermediate-Level**

-   **Q: How do you handle secrets in Jenkins?**
    -   **A:** Use the **Jenkins Credentials plugin** to securely store secrets, or integrate with a tool like **HashiCorp Vault** to retrieve them at runtime.
-   **Q: What are shared modules/libraries in Jenkins?**
    -   **A:** They are reusable pipeline code snippets stored in a Git repository. This prevents code duplication and allows multiple teams to use common tasks.
-   **Q: Can Jenkins handle multi-language builds?**
    -   **A:** Yes. You can use different **Docker agents** for each pipeline stage (e.g., a `node` agent for frontend, a `java` agent for backend). This isolates dependencies and ensures a clean build environment.

### **Admin-Level**

-   **Q: How do you auto-scale Jenkins worker nodes?**
    -   **A:** Use **AWS EC2 Auto Scaling Groups** to dynamically create and destroy Jenkins agents based on workload. Jenkins can be configured to discover these nodes.
-   **Q: What is JNLP in Jenkins? Why is it used?**
    -   **A:** It's a protocol used to launch and connect agents to the Jenkins master node, enabling remote build execution securely.
-   **Q: How do you set up GitOps deployment with Jenkins?**
    -   **A:** After a successful build, Jenkins updates the deployment YAML file in a Git repository. A tool like **ArgoCD** then automatically syncs this change to the Kubernetes cluster.

### **Common Jenkins Plugins to Mention**
-   Git, GitHub, SSH Agent, Credentials, Pipeline, Docker, Maven, Blue Ocean, and SonarQube.

---

## 🌐 GitLab CI/CD and GitHub Actions – Basics

It's crucial to know the basics of these modern CI/CD tools for any DevOps interview.

### **GitLab CI/CD**
-   Uses a `.gitlab-ci.yml` file in the root of the repository to define pipeline jobs and stages.
-   Pipelines run automatically on code events, provided runners are configured.
-   **Typical Steps:**
    1.  Create a GitLab project.
    2.  Ensure runners are available (GitLab.com provides shared runners).
    3.  Write the `.gitlab-ci.yml` file.
    4.  Commit the changes; the pipeline will run.

### **GitHub Actions**
-   Uses workflow files in the `.github/workflows/` directory as YAML.
-   You define `on:` triggers (e.g., `push`, `pull_request`).
-   You specify jobs and steps; each job runs in a hosted runner container.
-   You can use the **Actions Marketplace** for reusable plugins.

---

## ✅ Actionable Tips for Interview Preparation

-   **Clearly explain a practical pipeline** from source code to production, mentioning each tool and its role.
-   **Practice scenario-based questions** and be able to adapt your answers to different technology stacks (Java, Python, Node.js, etc.).
-   **Be ready to discuss key concepts** like pipeline triggers, secrets management, backups, and shared pipeline code.
-   **Learn the basics of `.gitlab-ci.yml` and GitHub Actions** to show you're up-to-date with modern CI/CD practices.
