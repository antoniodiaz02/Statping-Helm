# Statping-Helm

## Overview
Statping-Helm is a Helm chart that simplifies the deployment of **Statping**, a self-hosted status monitoring solution, on Kubernetes. This chart is pre-configured to use SQLite for lightweight setups but can be modified to support MySQL or PostgreSQL.

## Features
- Easy deployment of Statping on Kubernetes.
- Default configuration with SQLite.
- Supports MySQL and PostgreSQL databases.
- Configurable Ingress, Service, and Persistent Storage.
- Readiness and Liveness probes included.

## Installation

### Prerequisites
- Helm installed (v3 recommended)
- Kubernetes cluster up and running
- Git installed

### Install helm
```sh
helm repo add statping-helm https://antoniodiaz02.github.io/Statping-Helm
helm repo update
helm install statping statping-helm/statping-helm
cd statping-helm
```

You can customize the installation by modifying values.yaml or passing parameters directly:
```sh
helm install statping --values values.yaml ./ \
  --set env.DB_CONN=mysql \
  --set image.tag=v0.90.78
```

## Configuration

The chart allows customization via the values.yaml file. Below are some key configurations:

| Parameter            | Description                                                    | Default               |
|----------------------|----------------------------------------------------------------|-----------------------|
| env.DB_CONN          | Database connection type (sqlite, mysql, postgres)            | sqlite                |
| image.repository     | Statping Docker image repository                               | adamboutcher/statping-ng |
| image.tag            | Statping image tag/version                                     | v0.90.78              |
| service.type         | Kubernetes service type (ClusterIP, NodePort, LoadBalancer)    | ClusterIP             |
| ingress.enabled      | Enable Ingress support                                         | true                  |
| persistence.size     | Persistent volume size for SQLite storage                      | 1Gi                   |

## Uninstall

To remove the deployment, use:

``` sh
helm uninstall statping
```

## License

This project is open-source created by Antonio Diaz, github account.

## Contributing

Feel free to open issues or submit pull requests to improve this Helm chart!

## Notes

- Modify the `values.yaml` file according to your needs before deployment.
- Ensure your cluster meets the necessary resource requirements.
- If using MySQL or PostgreSQL, update the database credentials accordingly in the `values.yaml` file.

### Happy Monitoring! 🚀
