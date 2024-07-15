# Setup

This project contains the setup script `setup.sh`, which performs the necessary steps:

- Enable MicroK8s plugins
- Setup permissions for secrets folder
- Install Kubernetes plugins `cert-manager` and `trust-manager`
- Apply Kubernetes resources for generating self-signed certificates (used for internal TLS)
- Set up Arango Kubernetes resources
- Build necessary container images
- Apply secrets
- Create all other Pods, Deployments, Services, etc.
  - Arango database
  - Redis
  - Workers
  - Frontend
  - Flower
