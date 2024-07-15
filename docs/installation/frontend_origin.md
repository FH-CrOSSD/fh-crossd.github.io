# Frontend Origin

You need to modify the `ORIGIN` env variable inside `frontend.yaml`, since otherwise the [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) will prevent the web interface from functioning.

For instance replace

```yaml
- name: ORIGIN
  value: http://172.23.101.111:30380
```

with

```yaml
- name: ORIGIN
  value: https://<domain.for.frontend.tld>
```
