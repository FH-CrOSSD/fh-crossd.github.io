# Backing up database
??? info "Enterprise Edition"
    The `ArangoBackup` and `ArangoBackupPolicy` custom resources for Kubernetes are considered as [Hot Backup](https://docs.arangodb.com/3.11/operations/backup-and-restore/#hot-backups) (see [here](https://github.com/arangodb/kube-arangodb/issues/507)), which is only available for Enterprise Edition.

The recommended way for creating a backup using the Community Edition of ArangoDB is to use [`arangodump`](https://docs.arangodb.com/3.11/components/tools/arangodump/) and to restore the backup with [`arangorestore`](https://docs.arangodb.com/3.11/components/tools/arangorestore/). You can download the ArangoDB client tools directly from their [website](https://download.arangodb.com/arangodb311/index.html) (download the latest **3.11** package starting with `arangodb3-client`).

!!! warning "3.12 Incompatibility"
    Please use the latest client tools for ArangoDB **3.11**. ArangoDB client tools 3.12 and newer do **not** work with the ArangoDB 3.11 server.

!!! info
    You will either need a NodePort Service or an Ingress for the ArangoDB in order to connect to it or you could also create a Kubernetes Job for it.

The following is an example for a backup command:

```bash
arangodump --server.endpoint http+ssl://<ingress.domain>:443 --server.username <username> --server.database crossd --output-directory <path>/$(date -uI)-$(dd if=/dev/urandom bs=16 count=1 status=none | base32 | head -c 5)
```

It connects to the ArangoDB and backs up the entire crossd database and stores the compressed files in a directory in a path you specify. The subdirectory consists of the date in UTC ISO 8601 format and a 5 character long random string.

!!! warning "Limitations"
    You should also note the [arangodump limitations](https://docs.arangodb.com/3.11/components/tools/arangodump/limitations/).
