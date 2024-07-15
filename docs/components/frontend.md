# Frontend

Our web interface uses [Svelte](https://svelte.dev/) and [Svelte Kit](https://kit.svelte.dev/) and provides access to the metrics of OSS projects. It also contains a list of the metrics.

Our public instance is available [here](https://health.crossd.tech).

## Secrets

- arango-frontend-pwd

## Services

- frontend-service:3000 (internal)
- frontend-service-exposed:30380 (optional, external, dev)

## Ingress

- frontend-ingress:443 (optional, external)

## Interacting Components

- ArangoDB
