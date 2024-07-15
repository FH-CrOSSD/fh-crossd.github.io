# API
Our web interface contains API endpoints to query the collected projects and metrics.
You can use them either on your own instance of our project or you can query the data of our public instance.

## `/api/projects`

Returns all queried projects from the database.

Properties:

|                      |                  |
| -------------------- | ---------------- |
| Allowed HTTP Methods | POST             |
| Content-Type         | application/json |

Parameters: None

Responses:

| Code | Description |
| ---- | ----------- |
| 200  | Success     |

Example:

```bash
curl https://health.crossd.tech/api/projects -X POST
```

---

## `/api/snapshots`

Returns the timestamps of the snapshots of a given project.

Properties:

|                      |                  |
| -------------------- | ---------------- |
| Allowed HTTP Methods | POST             |
| Content-Type         | application/json |

Parameters:

| Name | Description                          | Type   | Format                              | Required |
| ---- | ------------------------------------ | ------ | ----------------------------------- | -------- |
| term | project identifier (e.g. owner/name) | string | alphanumeric characters and `-\_./` | Yes      |

Responses:

| Code | Description                           |
| ---- | ------------------------------------- |
| 200  | Success                               |
| 400  | malformed JSON body                   |
| 422  | Parameters missing or in wrong format |

Example:

```bash
curl https://health.crossd.tech/api/snapshots -X POST -d "{\"term\":\"Peacexo/PAJAApp\"}" -H "Content-Type: application/json"
```

---

## `/api/metrics`

Returns the metrics of a snapshots of a given project.

Properties:

|                      |                  |
| -------------------- | ---------------- |
| Allowed HTTP Methods | POST             |
| Content-Type         | application/json |

Parameters:

| Name      | Description                          | Type   | Format                              | Required |
| --------- | ------------------------------------ | ------ | ----------------------------------- | -------- |
| term      | project identifier (e.g. owner/name) | string | alphanumeric characters and `-\_./` | Yes      |
| timestamp | timestamp of a snapshot              | number | epoch timestamp in seconds          | Yes      |

Responses:

| Code | Description                           |
| ---- | ------------------------------------- |
| 200  | Success                               |
| 400  | malformed JSON body                   |
| 422  | Parameters missing or in wrong format |

Example:

```bash
curl https://health.crossd.tech/api/metrics -X POST -d "{\"term\":\"Peacexo/PAJAApp\",\"timestamp\":1712087894.7108583}" -H "Content-Type: application/json"
```
