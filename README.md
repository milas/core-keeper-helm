# core-keeper-helm
Helm chart for running a dedicated [Core Keeper][core-keeper] server on Kubernetes

## Status
⚠️ Experimental

## Values
| Name                                      | Description                                        | Default                                            |
|-------------------------------------------|----------------------------------------------------|----------------------------------------------------|
| `image.repository`                        | Dedicated server image repo/name                   | [tedtramonte/core-keeper-server][]                 |
| `image.tag`                               | Dedicated server image tag                         |                                                    |
| `coreKeeper.worldName`                    | **BROKEN** Server name                             | Core Keeper Server                                 |
| `coreKeeper.worldSeed`                    | **BROKEN** Random seed to use for world generation | 0                                                  |
| `coreKeeper.maxPlayers`                   | **BROKEN** Maximum number of players for server    | 100                                                |
| `coreKeeper.persistence.resources`        | Requests/limits for persistent data volume         | <pre lang="yaml">requests: { storage: 1GiB }</pre> |
| `coreKeeper.persistence.storageClassName` | Storage class for PVC (optional)                   |                                                    |
| `vpa.enabled`                             | Create VerticalPodAutoscaler recommender policy    | false                                              |

## Versioning
The Helm chart uses a fixed version of the Core Keeper dedicated server,
so it's necessary to use `helm upgrade` to update to a new version.

See [`appVersion` in Chart.yaml][chart-appVersion] for the current Core Keeper server version.
(This is a [Steam build ID][steam-builds], so does not align to the in-app version numbers for Core Keeper.)

If you want to try out a new version before the Helm chart is updated, see the Docker Hub listing for [tedramonte/core-keeper-server][tedtramonte/core-keeper-server-tags] for available tags.
Then, override the `image.tag` value with a `values.yaml` or `--set image.tag=...`.
Do this at your own risk, as there might be breaking changes in the image that require chart upgrades!

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

## Acknowledgments
* Docker Image: [tedtramonte/core-keeper-server][] 

[chart-appVersion]: https://github.com/milas/core-keeper-helm/blob/main/Chart.yaml
[core-keeper]: https://store.steampowered.com/app/1621690/Core_Keeper/
[steam-builds]: https://steamdb.info/app/1963720/depots/?branch=public
[tedtramonte/core-keeper-server]: https://gitlab.com/tedtramonte/core-keeper-server
[tedtramonte/core-keeper-server-tags]: https://hub.docker.com/r/tedtramonte/core-keeper-server/tags
