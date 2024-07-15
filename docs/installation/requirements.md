# Requirements

Our project needs following requirements:

- Buildah
  - Build Docker images and push them to local registry
- MicroK8s
  - orchestrate the cluster

On Ubuntu you can install requirements as follows:

```bash
apt install buildah
snap install microk8s --classic
```

Microk8s needs the following plugins (enabled inside the setup script):

- registry
- dns
- hostpath-storage
- ingress
- cert-manager
- rbac
