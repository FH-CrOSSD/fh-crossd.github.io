# Redis

[Redis](https://redis.io/) acts as the broker for our [Celery Task Queue](https://docs.celeryq.dev/en/stable/#). It stores and distributes the tasks for our workers.

## Secrets

- redis-auth

## Services

- redis-service:6379 (internal)

## Interacting Components

- Flower
- Add Task Job
- m-drone
- c-drone
- bak-rest-drone
    
!!! info "Redis Access"
    We did not provide a (development) external service for Redis, as we deemed it not necessary. If you need to inspect the Redis database, get into the pod, establish a TLS connection and authenticate to Redis.
    ```bash
    # connect into pod
    microk8s kubectl exec -it <pod name> -- sh
    # connect to redis
    redis-cli --tls --cacert /tls/ca.crt
    # authenticate inside redis
    127.0.0.1:6379> auth <password in redis-auth>
    ```
