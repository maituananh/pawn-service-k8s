# Pawn Service - Kubernetes Manifests

Kubernetes manifests for Pawn Service, following GitOps best practices with Kustomize and ArgoCD.

## Prerequisites

- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [kustomize](https://kustomize.io/)
- [ArgoCD](https://argo-cd.readthedocs.io/) (for GitOps)

## GitOps

The repository follows GitOps best practices with ArgoCD.

### ArgoCD Application

The ArgoCD `Application` CR is located at `argocd/application.yaml`.

### Environment Overlays

The repository uses Kustomize overlays for different environments:
- [Development](overlays/dev/kustomization.yaml)
- [Production](overlays/prod/kustomization.yaml)

## Kustomize

The repository uses Kustomize to manage Kubernetes manifests.

### Base Directory

The base directory contains the core application manifests that are common to all environments.

### Overlays Directory

The overlays directory contains environment-specific configurations that extend the base manifests.

### Patches Directory

The patches directory contains patches that modify the base manifests for specific environments.

### Application Structure

## Project Structure

```
pawn-service-k8s/
├── argocd/                     # ArgoCD Application configuration
│   └── application.yaml
├── base/                       # Core application manifests (no environment-specific values)
│   ├── be/                     # Backend components
│   │   ├── configmap.yaml
│   │   ├── deployment.yaml
│   │   ├── ingress.yaml
│   │   └── service.yaml
│   ├── fe/                     # Frontend components
│   │   ├── configmap.yaml
│   │   ├── deployment.yaml
│   │   ├── ingress.yaml
│   │   └── service.yaml
│   └── kustomization.yaml      # Base Kustomize configuration
├── overlays/                   # Environment-specific configurations
│   ├── dev/                    # Development environment
│   │   ├── configmap.yaml
│   │   ├── kustomization.yaml
│   │   └── patch/              # Patches for base manifests
│   │       ├── deployment.yaml
│   │       └── ingress.yaml
│   └── prod/                   # Production environment
│       ├── configmap.yaml
│       ├── kustomization.yaml
│       └── patch/              # Patches for base manifests
│           ├── deployment.yaml
│           └── ingress.yaml
├── README.md
└── values.yaml                 # [Optional] Shared values for Kustomize (can be split by env)
```
