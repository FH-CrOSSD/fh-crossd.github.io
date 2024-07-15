# Arango Init Job

This [Job](https://kubernetes.io/docs/concepts/workloads/controllers/job/) waits for ArangoDB to be up and running and runs the script `arango-init/arango_init.js`, which creates the `crossd` database, all necessary collections and additional users for the frontend (readonly) and the workers (read/write).

The script `arango-init/arango_init.js` is mounted as a [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/).

## Secrets

- arango-root-pwd
- arango-worker-pwd
- arango-frontend-pwd

## Interacting Components

- ArangoDB
