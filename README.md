# Regret Helm Charts

Helm charts for deploying [Regret](https://github.com/regret-io/regret) to Kubernetes.

## Install

```bash
helm repo add regret https://regret-io.github.io/regret-charts
helm install regret regret/regret -n regret --create-namespace \
  --set image.repository=regretio/pilot \
  --set studio.image.repository=regretio/studio \
  --set authPassword=your-secret
```

## Components

- **Pilot** — StatefulSet with persistent storage (SQLite + RocksDB)
- **Studio** — Deployment for the web UI

## Values

| Key | Default | Description |
|-----|---------|-------------|
| `image.repository` | `regretio/pilot` | Pilot image |
| `image.tag` | `latest` | Pilot image tag |
| `studio.image.repository` | `regretio/studio` | Studio image |
| `authPassword` | `""` | Auth password (empty = disabled) |
| `storage.size` | `20Gi` | PVC size |
| `service.type` | `ClusterIP` | Service type |
