<<<<<<< HEAD
# Duplicati Backup Client

This is a helm chart for [duplicati](https://github.com/duplicati/duplicati) leveraging the [Linuxserver.io image](https://hub.docker.com/r/linuxserver/duplicati/)

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/duplicati
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install my-release k8s-at-home/duplicati
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Sentry chart and their default values.

| Parameter                  | Description                         | Default                                                 |
|----------------------------|-------------------------------------|---------------------------------------------------------|
| `image.repository`         | Image repository | `linuxserver/duplicati` |
| `image.tag`                | Image tag. Possible values listed [here](https://hub.docker.com/r/linuxserver/duplicati/tags/).| `v2.0.5.1-2.0.5.1_beta_2020-01-18-ls58`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `strategyType`             | Specifies the strategy used to replace old Pods by new ones | `Recreate` |
| `timezone`                 | Timezone the duplicati instance should run as, e.g. 'America/New_York' | `UTC` |
| `puid`                     | process userID the duplicati instance should run as | `1001` |
| `pgid`                     | process groupID the duplicati instance should run as | `1001` |
| `cliArgs`                     | optionally specify any CLI variables you want to launch the app with | `nil` |
| `probes.liveness.initialDelaySeconds`  | Specify liveness `initialDelaySeconds` parameter for the deployment  | `60` |
| `probes.liveness.failureThreshold`     | Specify liveness `failureThreshold` parameter for the deployment     | `5`  |
| `probes.liveness.timeoutSeconds`       | Specify liveness `timeoutSeconds` parameter for the deployment       | `10` |
| `probes.readiness.initialDelaySeconds` | Specify readiness `initialDelaySeconds` parameter for the deployment | `60` |
| `probes.readiness.failureThreshold`    | Specify readiness `failureThreshold` parameter for the deployment    | `5`  |
| `probes.readiness.timeoutSeconds`      | Specify readiness `timeoutSeconds` parameter for the deployment      | `10` |
| `Service.type`          | Kubernetes service type for the duplicati GUI | `ClusterIP` |
| `Service.port`          | Kubernetes port where the duplicati GUI is exposed| `8200` |
| `Service.annotations`   | Service annotations for the duplicati GUI | `{}` |
| `Service.labels`        | Custom labels | `{}` |
| `Service.loadBalancerIP` | Loadbalance IP for the duplicati GUI | `{}` |
| `Service.loadBalancerSourceRanges` | List of IP CIDRs allowed access to load balancer (if supported)      | None
| `ingress.enabled`              | Enables Ingress | `false` |
| `ingress.annotations`          | Ingress annotations | `{}` |
| `ingress.labels`               | Custom labels                       | `{}`
| `ingress.path`                 | Ingress path | `/` |
| `ingress.hosts`                | Ingress accepted hostnames | `chart-example.local` |
| `ingress.tls`                  | Ingress TLS configuration | `[]` |
| `persistence.config.enabled`      | Use persistent volume to store configuration data | `true` |
| `persistence.config.size`         | Size of persistent volume claim | `1Gi` |
| `persistence.config.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.config.storageClass` | Type of persistent volume claim | `-` |
| `persistence.config.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.config.skipuninstall`  | Do not delete the pvc upon helm uninstall | `false` |
| `persistence.source.enabled`      | Use persistent volume to store source data | `true` |
| `persistence.source.size`         | Size of persistent volume claim | `10Gi` |
| `persistence.source.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.source.storageClass` | Type of persistent volume claim | `-` |
| `persistence.source.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.source.skipuninstall`  | Do not delete the pvc upon helm uninstall | `false` |
| `persistence.backups.enabled`      | Use persistent volume to store backups data | `true` |
| `persistence.backups.size`         | Size of persistent volume claim | `10Gi` |
| `persistence.backups.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.backups.storageClass` | Type of persistent volume claim | `-` |
| `persistence.backups.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.backups.skipuninstall`  | Do not delete the pvc upon helm uninstall | `false` |
| `persistence.extraExistingClaimMounts`  | Optionally add multiple existing claims | `[]` |
| `resources`                | CPU/Memory resource requests/limits | `{}` |
| `nodeSelector`             | Node labels for pod assignment | `{}` |
| `tolerations`              | Toleration labels for pod assignment | `[]` |
| `affinity`                 | Affinity settings for pod assignment | `{}` |
| `podAnnotations`           | Key-value pairs to add as pod annotations  | `{}` |
| `deploymentAnnotations`           | Key-value pairs to add as deployment annotations  | `{}` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install my-release \
  --set timezone="America/New York" \
    k8s-at-home/duplicati
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml k8s-at-home/duplicati
```

---
**NOTE**

If you get `Error: rendered manifests contain a resource that already exists. Unable to continue with install: existing resource conflict: ...` it may be because you uninstalled the chart with `skipuninstall` enabled, you need to manually delete the pvc or use `existingClaim`.

---

Read through the [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/duplicati/values.yaml) file. It has several commented out suggested values.
=======
# duplicati

![Version: 2.0.1](https://img.shields.io/badge/Version-2.0.1-informational?style=flat-square) ![AppVersion: v2.0.5.1](https://img.shields.io/badge/AppVersion-v2.0.5.1-informational?style=flat-square)

Store securely encrypted backups on cloud storage services!

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/duplicati>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| skaro13 | simon.caron@protonmail.com |  |

## Source Code

* <https://hub.docker.com/r/linuxserver/duplicati/>
* <https://github.com/duplicati/duplicati>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| cliArgs | string | `""` |  |
| deploymentAnnotations | object | `{}` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"linuxserver/duplicati"` |  |
| image.tag | string | `"v2.0.5.1-2.0.5.1_beta_2020-01-18-ls72"` |  |
| ingress.annotations | object | `{}` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0] | string | `"chart-example.local"` |  |
| ingress.labels | object | `{}` |  |
| ingress.path | string | `"/"` |  |
| ingress.tls | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| persistence.backups.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.backups.enabled | bool | `true` |  |
| persistence.backups.size | string | `"1Gi"` |  |
| persistence.backups.skipuninstall | bool | `false` |  |
| persistence.config.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.config.enabled | bool | `true` |  |
| persistence.config.size | string | `"1Gi"` |  |
| persistence.config.skipuninstall | bool | `false` |  |
| persistence.extraExistingClaimMounts | list | `[]` |  |
| persistence.source.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.source.enabled | bool | `true` |  |
| persistence.source.size | string | `"1Gi"` |  |
| persistence.source.skipuninstall | bool | `false` |  |
| pgid | int | `1001` |  |
| podAnnotations | object | `{}` |  |
| probes.liveness.failureThreshold | int | `5` |  |
| probes.liveness.initialDelaySeconds | int | `60` |  |
| probes.liveness.timeoutSeconds | int | `10` |  |
| probes.readiness.failureThreshold | int | `5` |  |
| probes.readiness.initialDelaySeconds | int | `60` |  |
| probes.readiness.timeoutSeconds | int | `10` |  |
| puid | int | `1001` |  |
| resources | object | `{}` |  |
| service.annotations | object | `{}` |  |
| service.labels | object | `{}` |  |
| service.loadBalancerIP | string | `nil` |  |
| service.port | int | `8200` |  |
| service.type | string | `"ClusterIP"` |  |
| strategyType | string | `"Recreate"` |  |
| timezone | string | `"UTC"` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
