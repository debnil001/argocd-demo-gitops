# Kubernetes GitOps with Argo CD & Helm

A production-style GitOps setup using Kubernetes, Helm and Argo CD.

The project demonstrates how application configuration can be managed entirely through Git, with Argo CD continuously reconciling Kubernetes to the desired state.

## Architecture

Developer
    |
    v
Application Repository
    |
    | Docker image + Helm chart
    v
GHCR / OCI Registry
    |
    v
GitOps Repository
    |
    | App-of-Apps
    v
Argo CD
    |
    +------------+
    |            |
    v            v
  Dev          Prod
Kubernetes   Kubernetes

## Components

- Kubernetes / Kind
- Argo CD
- Helm
- GitHub
- GitHub Container Registry (GHCR)
- Horizontal Pod Autoscaler
- Kubernetes Metrics Server

## Repository Structure

```text
gitops-repo/
├── bootstrap/
│   └── root-app.yaml
├── projects/
│   └── platform-project.yaml
├── applications/
│   ├── dev/
│   │   └── my-app.yaml
│   └── prod/
│       └── my-app.yaml
└── environments/
    └── my-app/
        ├── dev/
        │   └── values.yaml
        └── prod/
            └── values.yaml
