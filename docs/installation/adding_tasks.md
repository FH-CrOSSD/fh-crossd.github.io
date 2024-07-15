# Adding tasks

Adding tasks (repositories to scan) works currently via Kubernetes [Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/) or [CronJobs](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/).

`add_task_job.yaml` defines an example of such a Kubernetes job.
It uses to tool located in `tools/add_task` to interact with the task queue and the ArangoDB. As the secure connection requires the Kubernetes secrets and the self-signed TLS certificates, we build an image for a pod that can in turn be used by the Kubernetes Job.

`tools/add_task/add_task.py` can be used as follows:

``` { .txt .no-copy }
usage: add_task.py [-h] [--only {bak,metric}] [--user USER] [--password PASSWORD] [-t TAG] owner/name [owner/name ...]

Add a repository to the queue

positional arguments:
  owner/name           owner of the repository

options:
  -h, --help           show this help message and exit
  --only {bak,metric}  limit execution to a single task
  --user USER          arangodb username
  --password PASSWORD  arangodb password
  -t TAG, --tag TAG    Set a tag for the scan
```
