# ArgoCD Deployments

This repository contains Kubernetes deployment configurations managed via [ArgoCD](https://argo-cd.readthedocs.io/), using both **Helm** and **Kustomize** for different applications.

## 📦 Repository Structure

```plaintext
argocd-deployments/
├── helm/
│   ├── my-app/
│   │   └── values.yaml
│   └── another-app/
│       └── values.yaml
├── kustomize/
│   ├── my-app/
│   │   ├── base/
│   │   └── overlays/
│   │       ├── dev/
│   │       └── prod/
│   └── another-app/
│       └── ...
└── README.md
```

## 🚀 Purpose

This repo serves as the **source of truth** for GitOps-based deployment using ArgoCD. It organizes Kubernetes apps by tool (Helm or Kustomize) and keeps configurations version-controlled, reviewable, and reusable.
