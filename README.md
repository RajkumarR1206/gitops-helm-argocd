

---

# GitOps Deployment using Helm & ArgoCD on Kubernetes (K3s)

This project demonstrates a **production-style GitOps workflow** using **Helm and ArgoCD** on a lightweight **Kubernetes (K3s) cluster**. It shows how Kubernetes applications can be **deployed, managed, and auto-scaled declaratively** using Git as the single source of truth.

---

## Project Overview

* GitHub acts as the **single source of truth**
* ArgoCD continuously monitors the Git repository
* Any change committed to Git is **automatically reconciled** in the cluster
* Helm is used for templating Kubernetes resources
* Application scaling is handled through **Git-managed Horizontal Pod Autoscaler (HPA)**

This setup reflects how real-world teams implement **continuous deployment, self-healing, and auto-scaling** using GitOps principles.

---

## Project Demo:

* ArgoCD nginx Application:
  
<img width="1326" height="576" alt="argocd" src="https://github.com/user-attachments/assets/6b0efae3-9d27-4687-b6ac-e78016489db0" />

* Current Pod list:

<img width="740" height="158" alt="arcd3" src="https://github.com/user-attachments/assets/e3a70483-2fd7-441a-af17-890c670daea3" />

* Scaling Nginx replicas via GitOps:
  
<img width="987" height="435" alt="gitops1" src="https://github.com/user-attachments/assets/ad195b3a-ca88-429f-b978-7a9ed7907ad1" />

* Pods after scaling:
  
<img width="703" height="352" alt="gitops2" src="https://github.com/user-attachments/assets/2eec5d60-79b0-4d38-b61c-80c43e50fb75" />

* ArgoCD Scaling sync:

<img width="1366" height="310" alt="arcd4" src="https://github.com/user-attachments/assets/d02b37d9-f45f-4f5b-946e-06fd4dd70995" />

* Application exposed using NodePort service:

<img width="823" height="100" alt="gitops3" src="https://github.com/user-attachments/assets/cb82a53d-fe88-4900-ad1d-5b1dfb63e4cb" />

* Nginx application access:

<img width="1046" height="400" alt="nginxargo" src="https://github.com/user-attachments/assets/05fcc8e4-3c19-4a44-b985-32f9c34f0fd9" />
  
---


## Tech Stack

* **Kubernetes**: K3s
* **GitOps Tool**: ArgoCD
* **Package Manager**: Helm
* **Application**: Nginx
* **Auto Scaling**: Kubernetes HPA (CPU-based)
* **Platform**: Linux VM (Azure VM)
* **Version Control**: GitHub

---

## Repository Structure

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

1. Application configuration is defined using Helm charts
2. Changes are committed and pushed to GitHub
3. ArgoCD automatically detects repository changes
4. Kubernetes resources are created or updated automatically
5. The cluster continuously reconciles itself to match Git state

No manual `kubectl apply` is required after initial setup.

---

## Auto Scaling via GitOps (HPA)

This project implements **Horizontal Pod Autoscaling fully managed through GitOps**.

* HPA configuration is defined declaratively in `hpa.yaml`
* ArgoCD deploys and continuously enforces the HPA resource
* Pod replicas scale automatically based on CPU utilization
* Manual changes in the cluster are reverted to match Git state

### Scaling Behavior

* Minimum replicas: 1
* Maximum replicas: 5
* Scaling metric: CPU utilization

When application load increases, Kubernetes scales pods automatically, while ArgoCD ensures the scaling configuration always matches what is defined in Git.

---

## Key Features

* GitOps-based continuous deployment
* Helm-driven Kubernetes manifests
* Automated sync and self-healing with ArgoCD
* Git-managed Horizontal Pod Autoscaling
* Namespace-isolated application deployment
* External access using NodePort service
* Cloud-agnostic and cost-efficient setup

---

## Application Access

The application is exposed using a **NodePort service**.

```
http://<VM_PUBLIC_IP>:30500
```

NodePort is used to keep the setup simple, portable, and independent of cloud load balancers.

---

## What Was Implemented

* Declarative GitOps workflow using ArgoCD
* Helm chart–based Kubernetes deployment
* Continuous reconciliation and self-healing
* CPU-based Horizontal Pod Autoscaling via HPA
* Namespace isolation for application resources
* External service exposure using NodePort

---


## Future Enhancements

* Ingress controller with TLS
* Monitoring using Prometheus and Grafana
* Multi-environment GitOps (dev / staging / prod)
* Secrets management and RBAC hardening

---

## Conclusion

This project demonstrates hands-on implementation of **GitOps**, **Helm-based Kubernetes deployments**, and **auto-scaling through declarative configuration**, reflecting modern Kubernetes operational practices.

---
