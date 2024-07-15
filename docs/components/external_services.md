# External Services

All external services (Kubernetes type [NodePort](https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport)) are optional and should only be used in development environment. They open up ports on the node, which can be used to connect to the service from outside the cluster.

We defined external service for:

- ArangoDB
  - arangodb-cluster-exposed:30529
- Frontend
  - frontend-service-exposed:30380
- Flower
  - flower-service-exposed:30555
