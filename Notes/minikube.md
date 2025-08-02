# 🐳 Minikube - My Detailed DevOps Notes

> 🧠 For learning, testing, and developing Kubernetes locally without using cloud services.

---

## 📌 What is Minikube?

**Minikube** is a lightweight tool that lets me run a **local single-node Kubernetes cluster** on my **laptop/desktop**.

* It helps me practice Kubernetes commands without using AWS EKS, GKE, or other cloud services.
* Ideal for **learning**, **experiments**, and **local app testing**.

### 🔍 Think of Minikube like:

“A local Kubernetes playground where I’m the boss — no billing, no cloud login, no restrictions!”

---

## ❓ Why Minikube? (My Use Cases)

| 🎯 Use Case          | ✅ Why It's Useful                                          |
| -------------------- | ---------------------------------------------------------- |
| Learn Kubernetes     | Practice YAMLs, Pods, Services, Deployments                |
| Run apps locally     | Deploy apps like Nginx, NodeJS, Java, etc.                 |
| Debug problems       | Troubleshoot pods/services before production               |
| Practice GitOps/CD   | Run Argo CD or Helm locally                                |
| Test CI/CD pipelines | Run GitHub Actions or Jenkins pipelines that deploy to K8s |

---

## 🖥️ Prerequisites

Before installing Minikube:

* **kubectl** (Kubernetes command-line tool)
* A container runtime or VM driver (like **Docker**, **VirtualBox**, or **Hyper-V**)

---

## 🛠️ Installation Steps

### 1️⃣ Install `kubectl`

Refer:  https://kubernetes.io/docs/tasks/tools/

---

### 2️⃣ Install Minikube

Refer: https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download

---

## 🚀 How to Use Minikube

---

### ✅ 1. Start Minikube

```bash
minikube start
```

🔹 By default, it uses Docker as the driver if available.
🔹 To specify a driver:

```bash
minikube start --driver=docker
```

✅ This spins up a local VM or container that runs Kubernetes.

---

### ✅ 2. Verify Everything is Running

```bash
minikube status
kubectl get nodes
kubectl get pods -A
```

> 🔍 Good habit: Always check if your cluster is healthy before deploying.

---

### ✅ 3. Launch Kubernetes Dashboard (GUI)

```bash
minikube dashboard
```

🔹 This opens a visual interface in your browser.
🔹 Super helpful for inspecting Pods, Deployments, and Services.

---

### ✅ 4. Deploy a Sample App

Let’s deploy a simple web server:

```bash
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```

Now open the service in a browser:

```bash
minikube service hello-minikube
```

✅ Minikube opens the app in your default browser!

---

### ✅ 5. Check Logs, Describe, Debug

```bash
kubectl get pods
kubectl logs <pod-name>
kubectl describe pod <pod-name>
```

---

### ✅ 6. Stop or Delete the Cluster

```bash
minikube stop      # Stop the running cluster
minikube delete    # Remove the entire cluster and clean up resources
```

---

## 💡 Useful Minikube Commands

| Command                      | What It Does                         |
| ---------------------------- | ------------------------------------ |
| `minikube start`             | Starts a local Kubernetes cluster    |
| `minikube stop`              | Stops the cluster                    |
| `minikube delete`            | Deletes the cluster                  |
| `minikube dashboard`         | Opens Kubernetes Dashboard GUI       |
| `minikube service <service>` | Opens the app URL in browser         |
| `minikube ip`                | Shows Minikube cluster IP            |
| `kubectl`                    | Use it to interact with your cluster |

---

## ⚠️ Common Issues & Fixes

| Problem                        | Fix                                     |
| ------------------------------ | --------------------------------------- |
| Docker not found               | Install Docker Desktop or Docker Engine |
| “No VM driver found”           | Install VirtualBox or use Docker driver |
| Pods stuck in `Pending`        | Check storage and resources             |
| `minikube service` not opening | Try `minikube tunnel` or check firewall |

---

## 📁 Pro Tip – Create Aliases for Speed

```bash
alias k='kubectl'
alias mk='minikube'
```

So I can run `k get pods` or `mk dashboard` faster 😎


