# Crawlers & Metrics

These pods retrieve the necessary information about repositories and calculate our [defined metrics](https://health.crossd.tech/doc) for assessing the health of OSS projects.

## Secrets

- arango-worker-pwd
- redis-auth
- ghtoken

## Interacting Components

- Redis
- ArangoDB

## c-drone

A Python [Celery](https://docs.celeryq.dev/en/stable/#) worker that queries GitHub mostly via GraphQL, but also via REST API and crawls the github.com repository pages.

Stores the results in the `repositories` collection in ArangoDB and calls the subsequent task for calculating the metrics processed by m-drone.

## m-drone

A Python [Celery](https://docs.celeryq.dev/en/stable/#) worker that receives the results from c-drone and calculates metrics.

Stores the results in the `metrics` collection in ArangoDB.

## bak-rest-drone

A Python [Celery](https://docs.celeryq.dev/en/stable/#) worker that queries GitHub mostly REST API, but also crawls the github.com repository pages.

Stores the data about the repositories in the `bak_repos` and the calculated metrics in the `bak_metrics` collection in ArangoDB.

We mostly use the [source code](https://github.com/JacquelineSchmatz/MDI_Thesis) developed by Jacqueline Schmatz for her master thesis (with some modifications). The metrics Jacqueline Schmatz chose are listed [here](https://health.crossd.tech/doc).
