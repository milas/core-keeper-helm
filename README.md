# core-keeper-helm
Helm chart for running a dedicated Core Keeper server on Kubernetes

## Status
⚠️ Experimental

## Values
| Name                                      | Description                                        | Default                                            |
|-------------------------------------------|----------------------------------------------------|----------------------------------------------------|
| `image.repository`                        | Dedicated server image repo/name                   | tedtramonte/core-keeper-server                     |
| `image.tag`                               | Dedicated server image tag                         |                                                    |
| `coreKeeper.worldName`                    | **BROKEN** Server name                             | Core Keeper Server                                 |
| `coreKeeper.worldSeed`                    | **BROKEN** Random seed to use for world generation | 0                                                  |
| `coreKeeper.maxPlayers`                   | **BROKEN** Maximum number of players for server    | 100                                                |
| `coreKeeper.persistence.resources`        | Requests/limits for persistent data volume         | <pre lang="yaml">requests: { storage: 1GiB }</pre> |
| `coreKeeper.persistence.storageClassName` | Storage class for PVC (optional)                   |                                                    |
| `vpa.enabled`                             | Create VerticalPodAutoscaler recommender policy    | false                                              |

## Install
```shell
helm -n core-keeper \
  install \
    core-keeper \
    oci://ghcr.io/milas/charts/core-keeper \
    --create-namespace
```

## Upgrade
```shell
helm -n core-keeper \
  upgrade \
    core-keeper \
    oci://ghcr.io/milas/charts/core-keeper
```
