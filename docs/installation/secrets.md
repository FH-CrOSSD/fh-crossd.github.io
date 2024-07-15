# Secrets

The project needs several secrets (passwords and users) in order to enable the services to interact securely.

The folder `secret_templates` contains all necessary templates.
Copy it with `cp -r secret_templates secrets` and replace all placeholders (`<username>`, `<password>`, `<github token>`) with the base64 encoded corresponding values.

You can encode your values with e.g.:

```bash
echo -n "replace-me" | base64 -w0
```

The project needs following secrets:

## arango-frontend-pwd

This user is utilised by the frontend web application and has only read permissions.

Properties:

- username
- password

## arango-root-pwd

The super user for the Arango database used to create other users and collections.

Properties:

- username
- password

## arango-worker-pwd

This user is utilised by the crawlers and has only read/write permissions.

Properties:

- username
- password

## flower-basic-auth

This secret contains the user and password (HTTP Basic Authentication) in the format `user:password` for the flower web interface for the task queue.

Properties:

- AUTH

## ghtoken

The GitHub token used by the workers to crawl the data about the repositories.

??? question "How to generate the token?"
     The token can be generated github.com via `Settings` - `Developer settings` - `Personal access tokens` - `Tokens (classic)` - `Generate new token` - `Generate new token (classic)`.

The token needs the scopes:

- read:org
- read:user
- repo

Properties:

- GH_TOKEN

## redis-auth

Used by containers that need to interact with the task queue broker (Redis).

Properties:

- RAUTH

!!! warning
    **All** secrets inside the yaml files need to be **base64** encoded.  
    **Ensure the file permissions are set accordingly** (although they are also set in the setup script.)  
    `setup.sh` sets following permissions:

```bash
chown root:root secrets -R
chmod o-r-w-x secrets -R
```

After being applied (either by `setup.sh` or manually), the secret files can be deleted as they are stored in microk8s.
