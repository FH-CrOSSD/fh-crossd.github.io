# Add Task Job

[Kubernetes Job](https://kubernetes.io/docs/concepts/workloads/controllers/job/) for adding tasks to our Celery task queue as well as creating `scans` and `projects` entries in ArangoDB.

??? info "Design Decision"
    We decided to use jobs and therefore separate pods and container images for adding tasks, because we need the certificates for the TLS connections to Redis and ArangoDB (stored inside Kubernetes secrets) and also users and passwords (also stored in Kubernetes secrets).

    Additionally, we did not want to require NodePort services (opening the ports on the node) as this cannot be limited to localhost.

    Connecting to ClusterIP services (internal) would work, but the IPs are dynamic and we did not want to require changes to the DNS resolver on the host.

Our example `add_task_job.yaml` uses repositories owner/name arguments provided inside the yaml file, but they could also be provided e.g. via a Kubernetes [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/).

## Secrets

- arango-worker-pwd
- redis-auth

## Interacting Components

- ArangoDB
- Redis

