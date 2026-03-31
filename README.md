



# kubernetes_project
Here’s a **clean, professional README** you can directly paste into GitHub. I’m not going to overcomplicate it — but it will look serious enough for recruiters.

---

# 🚀 Kubernetes Capstone Project: WordPress + MySQL Deployment

## 📌 Overview

This project demonstrates a **production-style deployment of WordPress and MySQL on Kubernetes**, combining multiple core Kubernetes concepts into one working system.

The goal was simple:
👉 Build a **scalable, self-healing, and persistent application** using Kubernetes.

---

## 🏗️ Architecture

```
User → NodePort Service → WordPress Pods (Deployment)
                                ↓
                        MySQL Service (Headless)
                                ↓
                        MySQL Pod (StatefulSet)
                                ↓
                        Persistent Volume (PVC)
```

---

## 📸 Screenshots

### 🔹 WordPress Running

![WordPress Screenshot](images/wordpress.png)

### 🔹 Kubernetes Resources

![Kubectl Output](images/kubectl-output.png)

> ⚠️ Make sure you create an `images/` folder in your repo and upload screenshots with these names.

---

## ⚙️ Technologies Used

* Kubernetes (Minikube / Kind)
* Docker
* WordPress
* MySQL
* YAML (K8s Manifests)

---

## 🔧 Kubernetes Concepts Used

| Concept          | Description                        |
| ---------------- | ---------------------------------- |
| Namespace        | Isolated environment (`capstone`)  |
| Secret           | Stores MySQL credentials securely  |
| ConfigMap        | Stores WordPress configuration     |
| StatefulSet      | Manages MySQL with stable identity |
| Deployment       | Manages WordPress pods             |
| Service          | Exposes applications               |
| Headless Service | Stable DNS for MySQL               |
| PVC              | Persistent storage for database    |
| Resource Limits  | Controls CPU & Memory              |
| Probes           | Health checks for WordPress        |
| HPA              | Autoscaling based on CPU           |

---

## 🚀 Deployment Steps

### 1. Create Namespace

```bash
kubectl create namespace capstone
kubectl config set-context --current --namespace=capstone
```

---

### 2. Deploy MySQL

```bash
kubectl apply -f secret.yaml
kubectl apply -f statefull_service.yaml
kubectl apply -f mysql-statefulset.yaml
```

---

### 3. Deploy WordPress

```bash
kubectl apply -f config.yaml
kubectl apply -f wordpress_deployment.yaml
kubectl apply -f wordpress-service.yaml
```

---

### 4. Access WordPress

```bash
minikube service wordpress -n capstone
```

---

## 🔁 Self-Healing Test

* Deleted WordPress Pod → Automatically recreated ✅
* Deleted MySQL Pod → Recreated with data intact ✅

---

## 💾 Persistence Test

* Data stored in PVC
* After MySQL restart → **WordPress data remained intact** ✅

---

## 📈 Autoscaling

* HPA configured:

  * Min Pods: 2
  * Max Pods: 10
  * CPU Target: 50%

---

## 🔍 Key Learnings

* StatefulSets are critical for databases
* Headless Services enable stable networking
* Secrets + ConfigMaps separate config from code
* Kubernetes automatically handles failures (self-healing)
* HPA enables dynamic scaling

---

## ⚠️ Challenges Faced

* MySQL startup delays
* Correct DNS configuration for WordPress
* Initial probe failures
* PVC pending issues

---

## 📂 Project Structure

```
.
├── config.yaml
├── secret.yaml
├── statefull_service.yaml
├── wordpress_deployment.yaml
├── wordpress-service.yaml
├── README.md
└── images/
```

---

## 🧠 Final Thought

This project is not just about deploying WordPress —
it’s about understanding **how real-world applications run on Kubernetes**.

---

## 📌 Author

**Faiz Shaikh**
MBA Finance | Aspiring Equity Research Analyst | DevOps Learner

---

## 🔗 Connect With Me

(Add your LinkedIn link here)

---

### Brutal feedback (you need to hear this)

Most people just dump YAML files and call it a project.
This README already puts you ahead — **if** your repo actually works.

If someone clones your repo and it breaks → your credibility is gone.

So before pushing:

* Test everything from scratch
* Make sure screenshots are real (not fake or copied)
* Keep repo clean (no useless files)

---

If you want, I can:

* Review your GitHub repo like a recruiter
* Or upgrade this into a **top 1% DevOps portfolio project**
