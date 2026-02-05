# Leave Form V2 Deployment

Kubernetes deployment manifests for the Leave Form API v2 application.

## Branch Strategy

| Branch | Environment |
|--------|-------------|
| `main` | Dev cluster |

## Project Structure

```
leave-form-v2-deployment/
└── leave-form-v2-api/
    ├── api-v2-deploy.yaml      # Deployment manifest
    ├── api-v2-pv-secret.yaml   # TLS certificate secrets
    └── api-v2-svc.yaml         # Service manifest
```

## Components

### Deployment (`api-v2-deploy.yaml`)
- Deploys the Leave Form API v2 container
- Namespace: `leave-form-v2-ns`
- Container port: 8080
- Mounts TLS certificates from secrets

### Service (`api-v2-svc.yaml`)
- Type: ClusterIP
- External port: 8000
- Target port: 8080

### Secrets (`api-v2-pv-secret.yaml`)
- Stores TLS certificate pair (public/private keys)

## Deployment

```bash
# Apply all manifests
kubectl apply -f leave-form-v2-api/
```

## Prerequisites

- Access to the Kubernetes cluster
- `kubectl` configured with appropriate context
- Image pull secret configured for the container registry
