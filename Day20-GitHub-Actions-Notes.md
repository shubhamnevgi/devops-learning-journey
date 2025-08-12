# 🚀 Day 20 Notes: GitHub Actions - Zero to Hero

## 🤖 What Is GitHub Actions?

GitHub Actions is a **CI/CD automation tool natively integrated into GitHub repositories**. It allows you to define workflows (as code) that automatically run jobs in response to repository events such as a code push, pull request, or issue creation.

-   ☁️ Completely cloud-hosted—no need to install or maintain a separate server.
-   📝 **Workflows** are YAML files in the `.github/workflows/` directory, describing all automation logic.

## Why and When Should You Use GitHub Actions?

-   **For GitHub-centric projects:** A seamless experience since everything (code, CI/CD, automation) is in one place.
-   **Automatic scaling, zero maintenance:** All infrastructure is managed by GitHub.
-   💸 **Cost-effective:** Free for public projects; metered billing for private repos.
-   🔌 **Easy integration:** Integrates with thousands of open-source "action" plugins without manual installation—just reference them in your YAML file.

> ⚠️ **Use if** your organization is committed to GitHub.
> ⚠️ **Be cautious if** you plan to move away from GitHub (to GitLab, Bitbucket, etc.), as migration would be costly.

---

## 🆚 GitHub Actions vs. Jenkins

Here's a quick comparison to help you understand the key differences.

| Feature | Jenkins | GitHub Actions |
| :--- | :--- | :--- |
| **Hosting/Setup** | Self-hosted (on VM/EC2); requires manual install and configuration. | Fully hosted (GitHub cloud); no setup needed. |
| **Plugins** | Manual install, version management. | Auto-managed, referenced directly in YAML. |
| **Maintenance** | Needs patching, updates, and troubleshooting. | No infrastructure to maintain. |
| **Cost** | Hosting cost + engineer time. | Free for public repos, metered for private. |
| **Pipeline as Code** | `Jenkinsfile` (Groovy/Declarative). | YAML workflow files. |
| **Platform Scope** | Any SCM, highly customizable. | Only tight integration with GitHub. |
| **Runner Options** | VM agents, Docker containers, self-hosted runners. | Hosted runners, with easy self-hosted options. |

### **Summary**
-   ✅ **Choose GitHub Actions** for GitHub-only projects that require a quick setup and low maintenance.
-   ✅ **Choose Jenkins** for complex, hybrid environments and multi-source code management.

---

## 💡 Project Examples Covered

1.  **Deploy to Kubernetes:** A pipeline that builds an application with Maven, performs a code quality check with Sonar, and then deploys it to a Kubernetes cluster.
2.  **Deploy/Build to Docker:** Automatically builds container images and pushes them to Docker Hub or a private registry.
3.  **Python Unit Testing:** Runs automated tests on every commit using a GitHub-hosted runner.

## 🛠️ Practical Steps to Use GitHub Actions

1.  **Create workflows:** Place YAML files in the `.github/workflows/` directory of your repository.
2.  **Define events:** Specify triggers like `on: push`, `on: pull_request`, or `on: issue`.
3.  **Jobs and steps:** Each job runs in its own container (e.g., `ubuntu-latest`). Steps define the commands to run, such as checking out code, setting up an environment, running tests, or deploying.
4.  **Plugins (Actions):** Use pre-made actions from the GitHub Marketplace (e.g., `actions/checkout@v3`, `actions/setup-python@v4`).
5.  **Secrets management:** Store sensitive information (tokens, passwords) securely in GitHub repo settings and reference them in your workflows as `${{ secrets.KEY_NAME }}`.

### **How to Configure Your Own GitHub Actions Runner**
If you need to run jobs on your own hardware for specialized computing or private network access, you can set up a self-hosted runner:

-   Go to your GitHub repository → **Settings** → **Actions** → **Runners**.
-   Click **New runner** and select your desired OS (Linux, Windows, macOS).
-   Download and configure the runner package by following the instructions.
-   Now, your workflows can target this self-hosted runner for specific jobs.

---

## 💻 Typical GitHub Actions Workflow (YAML Example)

```yaml
name: Run Python Tests

on: [push]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.8'
      - run: pip install -r requirements.txt
      - run: pytest
````

-----

## ❓ Interview Q\&A for Beginners

  - **Q: What is GitHub Actions?**

      - **A:** A CI/CD tool on GitHub that automates builds, tests, and deployments via workflow YAML files.

  - **Q: How do you trigger a workflow?**

      - **A:** By defining `on:` events in the YAML file (e.g., `push`, `pull_request`).

  - **Q: What is a job and a step?**

      - **A:** A **job** is an entire workflow unit that runs in a specific environment. A **step** is a command or action inside a job.

  - **Q: How do you use secrets in your workflows?**

      - **A:** You store them in the GitHub repo settings and reference them in the YAML as `${{ secrets.KEY_NAME }}`.

  - **Q: What is a self-hosted runner, and when would you use one?**

      - **A:** It's a machine you configure to execute workflow jobs, used for custom hardware, private network access, or specialized control.

  - **Q: Compare GitHub Actions with Jenkins. Why might you choose one over the other?**

      - **A:** GitHub Actions is a simpler, zero-maintenance choice for GitHub-based projects. Jenkins offers more flexibility and customization for complex, multi-source, hybrid environments.
