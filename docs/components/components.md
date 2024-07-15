# Components

![cluster](https://github.com/FH-CrOSSD/crossd/assets/20456596/3b1e8458-9dc6-465e-a7bb-8be67de3dfcd)

Our project uses [MicroK8s](https://microk8s.io/) and in turn various components which are realised as Kubernetes Pods, Deployments, etc.

Pod can interact with each other only via defined interfaces (so-called Services) and use TLS to encrypt the traffic. Specifically, connections to ArangoDB and Redis are encrypted via TLS using self-signed certificates created with [cert-manager](https://cert-manager.io/).

??? info "Self-signed Certificates"
    ArangoDB creates self-signed certificates for the agents, coordinators and db-servers. ArangoDB handles issuing the certificates itself and is therefore provided with the CA certificate and key from cert-manager.

The containers establishing a connection to ArangoDB or Redis are provided with the CA certificate using trust bundles of [trust-manager](https://cert-manager.io/docs/trust/trust-manager/).
