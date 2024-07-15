# Ingress

[Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) acts a reverse proxy and load balancer and provides access to service from the outside. It is also able to terminate TLS connections and request Let's Encrypt certificates. As we use MicroK8s `ingress` plugin, `nginx` acts as our [Ingress Controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/).

The ClusterIssuer `lets-encrypt` retrieves the Let's Encrypt certificates for our cluster. It is optional and the template is located at `ingress_templates/cluster-issuer.yaml`.

We defined templates for ingress endpoints for:

- ArangoDB
  - `ingress_templates/arangodb-ingress.yaml`
- Frontend
  - `ingress_templates/frontend-ingress.yaml`
- Flower
  - `ingress_templates/flower-ingress.yaml`

!!! info
    All ingress endpoints use TCP port 443 for providing HTTPS connections.
