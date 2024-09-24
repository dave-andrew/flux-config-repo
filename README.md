# Flux Config Repo

This repository contains the configuration files for managing Kubernetes clusters using [Flux CD](https://fluxcd.io/), following the GitOps methodology.

## Repository Structure

- **apps/**: Kubernetes manifests and Helm charts for deployed applications.
- **clusters/**: Cluster-specific configurations.
  - **kube-playground/**: Configuration files for the `kube-playground` cluster.
- **infrastructure/**: Infrastructure components (e.g., ingress controllers, storage) managed in the cluster.

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/dave-andrew/flux-config-repo.git
   ```
2. Install Flux CD in your Kubernetes cluster following the [Flux Installation Guide](https://fluxcd.io/flux/installation/).
3. Bootstrap Flux to this repository:
   ```bash
    export GITHUB_TOKEN=<github-pat-token>
    export GITHUB_USER=<github-username>
    
    flux bootstrap github \
    	--token-auth \
      --owner=$GITHUB_USER \
      --repository=flux-config-repo \
      --branch=main \
      --path=./clusters/kube-playground \
      --personal \
      --components-extra='image-reflector-controller,image-automation-controller'
   ```
