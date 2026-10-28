# Requirements

Our project needs following requirements:

- Buildah
  - Build Docker images and push them to local registry
- MicroK8s (up to version 1.34 due to nginx ingress controller compatibility)
  - orchestrate the cluster

On Ubuntu you can install requirements as follows:

```bash
apt install buildah
snap install microk8s --classic --channel=1.34/stable
```

Microk8s needs the following plugins (enabled inside the setup script):

- registry
- dns
- hostpath-storage
- ingress (nginx)
- cert-manager
- rbac
