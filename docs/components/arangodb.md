# ArangoDB

[ArangoDB](https://arangodb.com/) is used as a persistent storage for data such as repository information and calculated metrics. We utilise the [ArangoDB Kubernetes Operator](https://arangodb.github.io/kube-arangodb/docs/using-the-operator) for deploying a database cluster.

## Collections
Collections inside the `crossd` database:

- task_results
  - Stores Celery task results, statuses, errors, ...
- scans
  - Stores information about the scans such as tasks for the repository, tags and connects other documents via the scan id
- projects
  - Contains owner/name of all scanned projects and the corresponding scan ids
- repositories
  - Stores information about repositories collected by c-drone
- metrics
  - Stores results of calculated metrics provided by m-drone
- bak_repos
  - Stores information about repositories collected by bak-rest-drone
- bak_metrics
  - Stores results of calculated metrics provided by bak-rest-drone

## Secrets

- arango-frontend-pwd
- arango-worker-pwd
- arango-root-pwd

## Services

- arango-cluster-internal:8529 (internal)
- arango-cluster-exposed:30529 (optional, external, dev)

## Ingress

- arangodb-ingress:443 (optional, external)

## Interacting Components

- Frontend
- Add Task Job
- m-drone
- c-drone
- bak-rest-drone
- Arango Init Job
