<<<<<<< HEAD
# LazyLibrarian helm chart

This is a helm chart for [LazyLibrarian](https://gitlab.com/LazyLibrarian/LazyLibrarian.git) based on the [container image provided by LinuxServer.io](https://hub.docker.com/r/linuxserver/lazylibrarian/).

## TL;DR

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/lazylibrarian
```

## Installing the Chart

To install the chart with the release name `my-release`:

```shell
helm install my-release k8s-at-home/lazylibrarian
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```shell
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the LazyLibrarian chart and their default values.

| Parameter                                   | Description                                                                                         | Default                                        |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| `image.repository`                          | Image repository                                                                                    | `linuxserver/lazylibrarian`                    |
| `image.tag`                                 | Image tag. Possible values listed [here](https://hub.docker.com/r/linuxserver/lazylibrarian/tags/). | `581cdfb3-ls23`                                |
| `image.pullPolicy`                          | Image pull policy                                                                                   | `IfNotPresent`                                 |
| `strategyType`                              | Specifies the strategy used to replace old Pods by new ones                                         | `Recreate`                                     |
| `timezone`                                  | Timezone the instance should run as, e.g. 'America/New_York'                                        | `UTC`                                          |
| `puid`                                      | process userID the instance should run as                                                           | `1001`                                         |
| `pgid`                                      | process groupID the instance should run as                                                          | `1001`                                         |
| `dockerMods.calibre.enabled`                | Enable optional calibre conversion feature. refer [here](https://github.com/linuxserver/docker-lazylibrarian#application-setup) | `false`            |
| `dockerMods.calibre.image.repository`       | DockerMod image repository                                                                          | `linuxserver/calibre-web`                      |
| `dockerMods.calibre.image.tag`              | DockerMod image tag. Can be found [here](https://hub.docker.com/r/linuxserver/calibre-web/tags/)    | `calibre`                                      |
| `dockerMods.ffmpeg.enabled`                 | Enable optional ffmpeg conversion feature. refer [here](https://github.com/linuxserver/docker-lazylibrarian#application-setup) | `false`             |
| `dockerMods.ffmpeg.image.repository`        | DockerMod image repository                                                                          | `linuxserver/mods`                             |
| `dockerMods.ffmpeg.image.tag`               | DockerMod image tag.                                                                                | `lazylibrarian-ffmpeg`                         |
| `probes.liveness.enabled`                   | Enables liveness probe for the main container                                                       | `true`                                         |
| `probes.liveness.initialDelaySeconds`       | Specify liveness `initialDelaySeconds` parameter for the main container                             | `60`                                           |
| `probes.liveness.failureThreshold`          | Specify liveness `failureThreshold` parameter for the main container                                | `5`                                            |
| `probes.liveness.timeoutSeconds`            | Specify liveness `timeoutSeconds` parameter for the main container                                  | `10`                                           |
| `probes.readiness.enabled`                  | Enables readiness probe for the main container                                                      | `true`                                         |
| `probes.readiness.initialDelaySeconds`      | Specify readiness `initialDelaySeconds` parameter for the main container                            | `60`                                           |
| `probes.readiness.failureThreshold`         | Specify readiness `failureThreshold` parameter for the main container                               | `5`                                            |
| `probes.readiness.timeoutSeconds`           | Specify readiness `timeoutSeconds` parameter for the main container                                 | `10`                                           |
| `probes.startup.enabled`                    | Enables startup probe for the main container                                                        | `false`                                        |
| `probes.startup.failureThreshold`           | Specify startup `failureThreshold` parameter for the main container                                 | `30`                                           |
| `probes.startup.timeoutSeconds`             | Specify startup `periodSeconds` parameter for the main container                                    | `10`                                           |
| `service.type`                              | Kubernetes service type for the GUI                                                                 | `ClusterIP`                                    |
| `service.port`                              | Kubernetes port where the GUI is exposed                                                            | `5299`                                         |
| `service.annotations`                       | Service annotations for the GUI                                                                     | `{}`                                           |
| `service.labels`                            | Custom labels                                                                                       | `{}`                                           |
| `service.loadBalancerIP`                    | Loadbalancer IP for the GUI                                                                         | `{}`                                           |
| `service.loadBalancerSourceRanges`          | List of IP CIDRs allowed access to load balancer (if supported)                                     | None                                           |
| `ingress.enabled`                           | Enables Ingress                                                                                     | `false`                                        |
| `ingress.annotations`                       | Ingress annotations                                                                                 | `{}`                                           |
| `ingress.labels`                            | Custom labels                                                                                       | `{}`                                           |
| `ingress.path`                              | Ingress path                                                                                        | `/`                                            |
| `ingress.hosts`                             | Ingress accepted hostnames                                                                          | `chart-example.local`                          |
| `ingress.tls`                               | Ingress TLS configuration                                                                           | `[]`                                           |
| `persistence.enabled`                       | Use persistent volume to store configuration data                                                   | `true`                                         |
| `persistence.size`                          | Size of persistent volume claim                                                                     | `1Gi`                                          |
| `persistence.existingClaim`                 | Use an existing PVC to persist data                                                                 | `nil`                                          |
| `persistence.storageClass`                  | Type of persistent volume claim                                                                     | `-`                                            |
| `persistence.subPath`                       | Mount a sub directory if set                                                                        | `nil          `                                |
| `persistence.accessMode`                    | Persistence access mode                                                                             | `ReadWriteOnce`                                |
| `persistence.extraVolumes`                  | Optionally add multiple additional volumes                                                          | `[]`                                           |
| `resources`                                 | CPU/Memory resource requests/limits                                                                 | `{}`                                           |
| `nodeSelector`                              | Node labels for pod assignment                                                                      | `{}`                                           |
| `tolerations`                               | Toleration labels for pod assignment                                                                | `[]`                                           |
| `affinity`                                  | Affinity settings for pod assignment                                                                | `{}`                                           |
| `podAnnotations`                            | Key-value pairs to add as pod annotations                                                           | `{}`                                           |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install my-release \
  --set timezone="Europe/Amsterdam" \
    k8s-at-home/lazylibrarian
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml k8s-at-home/lazylibrarian
```

---

Read through the [values.yaml](https://github.com/k8s-at-home/charts/lazylibrarian/values.yaml) file. It has several commented out suggested values.
=======
# lazylibrarian

![Version: 4.0.1](https://img.shields.io/badge/Version-4.0.1-informational?style=flat-square) ![AppVersion: 1.7.2](https://img.shields.io/badge/AppVersion-1.7.2-informational?style=flat-square)

A Helm chart for deploying LazyLibrarian

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://gitlab.com/LazyLibrarian/LazyLibrarian.git>
* <https://lazylibrarian.gitlab.io>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://k8s-at-home.com/charts/ | common | 3.0.1 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install lazylibrarian k8s-at-home/lazylibrarian
```

## Installing the Chart

To install the chart with the release name `lazylibrarian`

```console
helm install lazylibrarian k8s-at-home/lazylibrarian
```

## Uninstalling the Chart

To uninstall the `lazylibrarian` deployment

```console
helm uninstall lazylibrarian
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install lazylibrarian \
  --set env.TZ="America/New York" \
    k8s-at-home/lazylibrarian
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install lazylibrarian k8s-at-home/lazylibrarian -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | `{}` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"linuxserver/lazylibrarian"` |  |
| image.tag | string | `"version-047f91af"` |  |
| ingress.enabled | bool | `false` |  |
| persistence.config.emptyDir | bool | `false` |  |
| persistence.config.enabled | bool | `false` |  |
| persistence.media.emptyDir | bool | `false` |  |
| persistence.media.enabled | bool | `false` |  |
| persistence.media.mountPath | string | `"/media"` |  |
| service.port.port | int | `5299` |  |
| strategy.type | string | `"Recreate"` |  |

## Changelog

All notable changes to this application Helm chart will be documented in this file but does not include changes from our common library. To read those click [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/README.md#Changelog).

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

### [1.0.0]

#### Added

- N/A

#### Changed

- N/A

#### Removed

- N/A

[1.0.0]: #1.0.0

## Support

- See the [Wiki](https://github.com/k8s-at-home/charts/wiki)
- Open a [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/charts/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
