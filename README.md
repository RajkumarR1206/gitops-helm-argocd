#  GitOps Deployment using Helm & ArgoCD on Kubernetes (K3s)

This project demonstrates a **real-world GitOps workflow** using **Helm and ArgoCD** on a lightweight **Kubernetes (K3s) cluster**. It showcases how modern DevOps/SRE teams manage Kubernetes applications using **declarative configuration**, **version control**, and **automated continuous deployment**.

---

##  Project Overview

* GitHub acts as the **single source of truth**
* ArgoCD continuously monitors the Git repository
* Any change committed to Git is **automatically deployed** to Kubernetes
* Helm is used for templating and managing Kubernetes manifests

This project demonstrates a practical implementation of GitOps principles by combining declarative configuration, version-controlled deployments, and automated synchronization in a Kubernetes environment.

---

## Tech Stack

* **Kubernetes**: K3s (lightweight Kubernetes)
* **GitOps Tool**: ArgoCD
* **Package Manager**: Helm
* **Application**: Nginx (Helm-based deployment)
* **Platform**: Linux VM (Azure VM)
* **Version Control**: GitHub

---

##  Repository Structure

```
.
├── helm/
│   └── nginx/
│       ├── Chart.yaml
│       ├── values.yaml
│       ├── templates/
│       │   ├── deployment.yaml
│       │   ├── service.yaml
│       │   ├── ingress.yaml
│       │   ├── hpa.yaml
│       │   └── serviceaccount.yaml
```

---

## GitOps Workflow

1. Developer updates Helm chart or values in GitHub
2. Commit & push changes to repository
3. ArgoCD detects changes automatically
4. Kubernetes resources are updated without manual `kubectl apply`
5. Application stays **synced, versioned, and self-healing**

---

##  Key Features

* GitOps-based continuous deployment
* Helm chart management
* Automatic sync and self-healing using ArgoCD
* Kubernetes namespace isolation
* External access using NodePort service
* Beginner-friendly yet production-aligned

---

##  Application Access

The application is exposed using a **NodePort service**.

```
http://<VM_PUBLIC_IP>:30500
```

> Note: NodePort is used instead of LoadBalancer to keep the setup cloud-agnostic and cost-free.

---

## Screenshots (Optional)

You can add screenshots such as:

* ArgoCD UI showing application `Synced` and `Healthy`
* Kubernetes pods running
* Nginx application accessed via browser

---

## What Was Implemented

* Git-based declarative application management using ArgoCD
* Helm chart–driven Kubernetes deployments
* Automated synchronization and self-healing of cluster state
* Namespace-isolated application deployment
* External service exposure using NodePort

---

## Future Enhancements

* Add Ingress + TLS
* Integrate monitoring (Prometheus / Grafana)
* Add multi-environment GitOps (dev / prod)
* Implement RBAC & secrets management

---

##  Conclusion

This project proves hands-on experience with **GitOps principles**, **Helm-based deployments**, and **Kubernetes automation** — exactly what modern DevOps and SRE roles demand.

