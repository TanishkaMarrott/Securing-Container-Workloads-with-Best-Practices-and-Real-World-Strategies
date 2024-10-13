# **Securing Container Workloads: Best Practices for Container Security**

## **Description**
Some actionable, secure configurations for containerized environments. From Dockerfiles to Kubernetes, we’ve got you covered with battle-tested security techniques. Whether you're automating security scans or setting up AppArmor and SELinux policies, this guide will help you secure container workloads—without compromising performance.

### **Key Features**:
- **Minimal Base Images**: Start small, reduce attack surface by using the lightest base images like Alpine. Why have more when you need less?
- **Non-Root Containers**: By default, containers often run as root—exposing unnecessary privileges. We enforce non-root containers across Docker, Kubernetes, and more.
- **AppArmor & SELinux**: Leverage mandatory access controls to define granular security policies. Use profiles that restrict file access, network traffic, and more.
- **Security Context in Kubernetes**: Kubernetes provides tools to sandbox containers. We show you how to use `securityContext` and network policies to isolate workloads.
- **CI/CD Integration**: Automate security checks using tools like **Trivy**—scan your container images and catch vulnerabilities before they hit production.

---

### **Project Structure**:
```bash
.
├── AppArmor/
│   └── apparmor-profile          # Define restrictive AppArmor profiles for your containers
├── CI_CD/
│   └── trivy-scan.yml            # CI/CD Pipeline: Automate image scanning for vulnerabilities using Trivy
├── Dockerfiles/
│   ├── Dockerfile.minimal        # Lightweight Dockerfile based on Alpine for secure, small footprint containers
│   └── Dockerfile.nonroot        # Dockerfile enforcing non-root users for enhanced security
├── Kubernetes/
│   ├── network-policy.yaml       # Kubernetes Network Policy for isolating containers
│   └── security-context.yaml     # Security context configurations: runAsUser, allowPrivilegeEscalation, etc.
├── SELinux/
│   └── selinux-policy            # SELinux policy restricting containers from accessing sensitive directories
└── LICENSE
```

---

## **Usage**

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/securing-container-workloads.git
   cd securing-container-workloads
   ```

2. **Docker Security**:
   - Check the `Dockerfiles/` directory for examples of secure Docker builds.
   - Use `Dockerfile.nonroot` to run your containers as a non-root user.
   - Build the image:
     ```bash
     docker build -t secure-app -f Dockerfile.nonroot .
     ```

3. **Kubernetes Security**:
   - Apply the `network-policy.yaml` to limit pod-to-pod communication:
     ```bash
     kubectl apply -f Kubernetes/network-policy.yaml
     ```
   - Secure your pods with `security-context.yaml`:
     ```bash
     kubectl apply -f Kubernetes/security-context.yaml
     ```

4. **CI/CD Pipeline**:
   - Automate security scans with **Trivy** by integrating `trivy-scan.yml` into your pipeline. This step ensures your images are free from known vulnerabilities before being pushed to production.

5. **Enforce AppArmor and SELinux**:
   - Use `apparmor-profile` to control the capabilities of your containers. Prevent unnecessary network access and filesystem modifications.
   - Apply **SELinux** policies from the `SELinux/` directory to further harden your environment.

---

## **Best Practices**:
- **Isolate workloads**: Leverage **Network Policies** and **Security Contexts** to ensure that one container doesn’t impact another.
- **Enforce Policies**: Use AppArmor or SELinux to define strict security policies that restrict what containers can access.
- **Run Containers as Non-Root**: Always enforce non-root containers to reduce the risk of privilege escalation.
- **Automate Scans**: Integrate security tools like **Trivy** into your CI/CD pipeline for continuous vulnerability scanning.
- **Update Regularly**: Make sure your images are kept up-to-date with security patches and hardening techniques.

---

## **Contributing**
We welcome contributions! Please open an issue or submit a pull request for any enhancements or bug fixes.

---

## **License**
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

Let’s make sure every container is secure, from build to production!
