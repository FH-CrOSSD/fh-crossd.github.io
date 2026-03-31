# Crawlers & Metrics

These pods retrieve the necessary information about repositories and calculate our [defined metrics](https://health.crossd.tech/doc) for assessing the health of OSS projects.

## Secrets used by all workers

- arango-worker-pwd
- redis-auth

## Interacting Components

- Redis
- ArangoDB

## c-drone

A Python [Celery](https://docs.celeryq.dev/en/stable/#) worker that queries GitHub mostly via GraphQL, but also via REST API and crawls the github.com repository pages.

Stores the results in the `repositories` and `commits` collections in ArangoDB and calls the subsequent task for calculating the metrics processed by m-drone. Depending on the configuration, it can also call the subsequent task for calculating the metrics processed by llm-drone.

### Secrets

- ghtoken

## m-drone

A Python [Celery](https://docs.celeryq.dev/en/stable/#) worker that receives the results from c-drone and calculates metrics.

Stores the results in the `metrics` collection in ArangoDB.

### Secrets

- ghtoken

## llm-drone

A Python [Celery](https://docs.celeryq.dev/en/stable/#) worker that receives the results from c-drone and calculates metrics using a large language model (LLM) via ollama API.

### Secrets

- llm-auth