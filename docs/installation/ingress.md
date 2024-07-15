# Ingress

Per default all Kubernetes services can only be used inside the cluster. To access the web interfaces from the Internet, we have to make them available via Ingress.
Our Ingress resources redirect incoming HTTPS traffic to the corresponding pods (determined by domain main) and automatically retrieve the [Let's Encrypt](https://letsencrypt.org/de/) certificates for the TLS connection.

The folder `ingress_templates` contains all necessary templates.
Copy it with `cp -r ingress_templates ingress` and replace all placeholders (`<domain>`, `<email>`) with the according values.

!!! info "Subdomains"
    The configuration of the templates uses different domain names for each service. Therefore, you should register different subdomains.
