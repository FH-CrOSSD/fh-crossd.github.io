# Flower

[Flower](https://flower.readthedocs.io/en/latest/) is used to monitor our Celery workers and tasks. It uses HTTP basic authentication.

## Secrets

- flower-basic-auth

## Services

- flower-service:5555 (internal)
- flower-service-exposed:30555 (optional, external, dev)

## Ingress

- flower-ingress:443 (optional, external)

## Interacting Components

- Redis
