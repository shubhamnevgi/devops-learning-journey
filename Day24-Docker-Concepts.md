# 🚀 Day 24 Notes: Docker - Basics & Best Practices

## 💡 Why Are Containers Lightweight?

Unlike virtual machines (VMs) which include a full guest operating system, containers are lightweight because they:

-   **Share the host OS kernel**, saving significant space and resources.
-   Include only the **application code**, dependencies, and minimal base OS components.
-   Provide logical isolation, ensuring security and preventing processes in one container from accessing another.

> **Example:** An official Ubuntu Docker image is only about **28 MB**, while a full Ubuntu VM image is around **2.3 GB**—almost **100 times larger**!

---

## 🏛️ Docker Architecture Overview



-   **Docker Client**: The command-line interface (CLI) where users issue commands like `docker build` or `docker run`.
-   **Docker Daemon (Docker D)**: The core engine running on the host. It manages the entire Docker lifecycle, from building images to running containers.
-   **Docker Images**: Immutable, read-only templates created from `Dockerfiles`. They contain all the necessary components to run an application.
-   **Docker Containers**: The live, runnable instances of Docker images. They are isolated and lightweight.
-   **Docker Registries**: Centralized repositories where images are stored and shared, such as **Docker Hub**. They can be public or private.

---

## 🔄 Docker Lifecycle Steps

1.  **Write a `Dockerfile`**: Define a set of instructions to build your image.
2.  **Build a Docker Image**: Use the `docker build` command to create the image based on your `Dockerfile`.
3.  **Run a Container**: Use `docker run` to instantiate the image as a container.
4.  **Push to Registry**: Upload your image to a registry for distribution and sharing.

---

## 🛠️ Installing Docker on Ubuntu EC2

1.  Update OS repositories: `sudo apt update`
2.  Install Docker: `sudo apt install docker.io -y`
3.  Add your user to the `docker` group to run commands without `sudo`.
4.  Restart your user session or log out and back in.
5.  Verify the installation: `docker run hello-world`

---

## 📄 Basic Dockerfile Example (Simple Python App)

```dockerfile
# Use an official lightweight Ubuntu image as the base
FROM ubuntu:latest

# Set the working directory inside the container
WORKDIR /app

# Copy the application code from the host into the container
COPY app.py .

# Install necessary dependencies (e.g., Python)
RUN apt-get update && apt-get install -y python3

# Define the command to run the application when the container starts
CMD ["python3", "app.py"]
````

-----

## 📦 Building, Running, and Pushing Images

  - **Building an image:** `docker build -t username/image_name:tag .`
  - **Running a container:** `docker run -it username/image_name:tag`
  - **Pushing to a registry:**
    1.  Log in to Docker Hub: `docker login`
    2.  Push your image: `docker push <repository>:<tag>`

-----

## ❓ Interview Questions & Answers

**Q1: What makes containers lightweight?**
**A:** Containers share the host OS kernel instead of running a full OS, which dramatically reduces their size and startup time.

**Q2: What is the role of the Docker daemon?**
**A:** The Docker daemon is the core engine that listens to client commands and manages the entire Docker lifecycle, including building images and running containers.

**Q3: How do you create and run a container?**
**A:** First, write a `Dockerfile`. Then, use `docker build` to create an image, and finally, use `docker run` to start a container from that image.

**Q4: What is a Docker registry?**
**A:** A Docker registry is a centralized service for storing and distributing Docker images. Docker Hub is the most popular public registry.

**Q5: How do you fix Docker permission errors on Ubuntu?**
**A:** Add your user to the Docker group with `sudo usermod -aG docker <username>` and restart your session to enable running commands without `sudo`.

**Q6: What distinguishes a Docker image from a container?**
**A:** An **image** is a static, read-only template, while a **container** is a live, running instance of an image.

**Q7: What are some Docker image best practices?**
**A:** Use minimal base images like Alpine, keep layers small, use multi-stage builds to reduce image size, and avoid running containers as the root user.
