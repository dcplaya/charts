<<<<<<< HEAD
# deCONZ helm chart

This is a helm chart for [deCONZ](https://www.dresden-elektronik.de/funk/software/deconz.html) based on the [container image provided by marthoc](https://hub.docker.com/r/marthoc/deconz/).

## TL;DR

```shell
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm install k8s-at-home/deconz
```

## Installing the Chart

To install the chart with the release name `my-release`:

```shell
helm install my-release k8s-at-home/deconz
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```shell
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Sentry chart and their default values.
Read through the [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/deconz/values.yaml) file. It has several commented out suggested values.

| Parameter                                   | Description                                                                                  | Default                                        |
| ------------------------------------------- | -------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| `replicaCount`                              | Number of replicas to scale to                                                               | `1`                                            |
| `autoscaling.enabled`                       | Enables Pod auto-scaling                                                                     | `false`                                        |
| `autoscaling.minReplicas`                   | Minimum number of replicas to auto-scale to                                                  | `1`                                            |
| `autoscaling.maxReplicas`                   | Maximum number of replicas to auto-scale to                                                  | `1`                                            |
| `image.repository`                          | Image repository                                                                             | `marthoc/deconz`                               |
| `image.tag`                                 | Image tag. Possible values listed [here](https://hub.docker.com/r/marthoc/deconz/tags/).     | `amd64-2.05.79`                                |
| `image.pullPolicy`                          | Image pull policy                                                                            | `IfNotPresent`                                 |
| `strategyType`                              | Specifies the strategy used to replace old Pods by new ones                                  | `Recreate`                                     |
| `timezone`                                  | Timezone the instance should run as, e.g. 'America/New_York'                                 | `UTC`                                          |
| `zigbeeDevice.enabled`                      | Enables passing through a Zigbee device                                                      | `false`                                        |
| `zigbeeDevice.hostPath`                     | HostPath of the Zigbee device that should be passed through                                  | `/dev/ttyUSB1`                                 |
| `vnc.enabled`                               | Enabled the built-in VNC server to access the application                                    | `true`                                         |
| `vnc.password`                              | VNC server password                                                                          | `changeme`                                     |
| `vnc.existingSecret`                        | Existing Kubernetes secret containing the VNC password                                       | `nil`                                          |
| `probes.liveness.enabled`                   | Enables liveness probe for the Pod                                                           | `true`                                         |
| `probes.liveness.failureThreshold`          | Specify liveness `failureThreshold` parameter for the Pod                                    | `5`                                            |
| `probes.liveness.initialDelaySeconds`       | Specify liveness `initialDelaySeconds` parameter for the Pod                                 | `60`                                           |
| `probes.liveness.timeoutSeconds`            | Specify liveness `timeoutSeconds` parameter for the Pod                                      | `10`                                           |
| `probes.readiness.enabled`                  | Enables readiness probe for the Pod                                                          | `true`                                         |
| `probes.readiness.initialDelaySeconds`      | Specify readiness `initialDelaySeconds` parameter for the Pod                                | `60`                                           |
| `probes.readiness.failureThreshold`         | Specify readiness `failureThreshold` parameter for the Pod                                   | `5`                                            |
| `probes.readiness.timeoutSeconds`           | Specify readiness `timeoutSeconds` parameter for the Pod                                     | `10`                                           |
| `probes.startup.enabled`                    | Enables startup probe for the Pod                                                            | `false`                                        |
| `probes.startup.failureThreshold`           | Specify startup `failureThreshold` parameter for the Pod                                     | `30`                                           |
| `probes.startup.timeoutSeconds`             | Specify startup `periodSeconds` parameter for the Pod                                        | `10`                                           |
| `service.type`                              | Kubernetes service type for the GUI                                                          | `ClusterIP`                                    |
| `service.httpPort`                          | Kubernetes port where the GUI is exposed                                                     | `80`                                           |
| `service.websocketPort`                     | Kubernetes port where the Websocket is exposed                                               | `443`                                          |
| `service.vncPort`                           | Kubernetes port where the VNC server is exposed                                              | `5900`                                         |
| `service.annotations`                       | Service annotations for the GUI                                                              | `{}`                                           |
| `service.labels`                            | Custom labels                                                                                | `{}`                                           |
| `service.loadBalancerIP`                    | Loadbalancer IP for the GUI                                                                  | `{}`                                           |
| `service.loadBalancerSourceRanges`          | List of IP CIDRs allowed access to load balancer (if supported)                              | `nil`                                          |
| `ingress.enabled`                           | Enables Ingress                                                                              | `false`                                        |
| `ingress.annotations`                       | Ingress annotations                                                                          | `{}`                                           |
| `ingress.labels`                            | Custom labels                                                                                | `{}`                                           |
| `ingress.path`                              | Ingress path                                                                                 | `/`                                            |
| `ingress.hosts`                             | Ingress accepted hostnames                                                                   | `chart-example.local`                          |
| `ingress.tls`                               | Ingress TLS configuration                                                                    | `[]`                                           |
| `persistence.enabled`                       | Use persistent volume to store configuration data                                            | `true`                                         |
| `persistence.annotations`                   | Key-value pairs to add as persistent volume claim annotations                                | `{}`                                           |
| `persistence.storageClass`                  | Type of persistent volume claim                                                              | `-`                                            |
| `persistence.existingClaim`                 | Use an existing PVC to persist data                                                          | `nil`                                          |
| `persistence.accessMode`                    | Persistence access mode                                                                      | `ReadWriteOnce`                                |
| `persistence.size`                          | Size of persistent volume claim                                                              | `1Gi`                                          |
| `persistence.subPath`                       | Mount a sub dir of the persistent volume                                                     | `nil`                                          |
| `extraVolumes`                              | Optionally add additional Volumes                                                            | `[]`                                           |
| `resources`                                 | CPU/Memory resource requests/limits                                                          | `{}`                                           |
| `nodeSelector`                              | Node labels for pod assignment                                                               | `{}`                                           |
| `tolerations`                               | Toleration labels for pod assignment                                                         | `[]`                                           |
| `affinity`                                  | Affinity settings for pod assignment                                                         | `{}`                                           |
| `podAnnotations`                            | Key-value pairs to add as pod annotations                                                    | `{}`                                           |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install my-release \
  --set timezone="Europe/Amsterdam" \
    k8s-at-home/deconz
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml k8s-at-home/deconz
```
=======
# deconz

![Version: 2.0.1](https://img.shields.io/badge/Version-2.0.1-informational?style=flat-square) ![AppVersion: 2.05.80](https://img.shields.io/badge/AppVersion-2.05.80-informational?style=flat-square)

A Helm chart for deploying deCONZ

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/deconz>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| billimek | jeff@billimek.com |  |

## Source Code

* <https://github.com/dresden-elektronik/deconz-rest-plugin>
* <https://github.com/marthoc/docker-deconz>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `1` |  |
| autoscaling.minReplicas | int | `1` |  |
| extraVolumes | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"marthoc/deconz"` |  |
| image.tag | string | `"amd64-2.05.80"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"deconz.local"` |  |
| ingress.path | string | `"/"` |  |
| ingress.tls | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.annotations | object | `{}` |  |
| persistence.enabled | bool | `false` |  |
| persistence.size | string | `"1Gi"` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| probes.liveness.enabled | bool | `true` |  |
| probes.liveness.failureThreshold | int | `5` |  |
| probes.liveness.initialDelaySeconds | int | `30` |  |
| probes.liveness.timeoutSeconds | int | `10` |  |
| probes.readiness.enabled | bool | `true` |  |
| probes.readiness.failureThreshold | int | `5` |  |
| probes.readiness.initialDelaySeconds | int | `30` |  |
| probes.readiness.timeoutSeconds | int | `10` |  |
| probes.startup.enabled | bool | `false` |  |
| probes.startup.failureThreshold | int | `30` |  |
| probes.startup.periodSeconds | int | `10` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext.privileged | bool | `true` |  |
| service.clusterIP | string | `""` |  |
| service.externalIPs | list | `[]` |  |
| service.externalTrafficPolicy | string | `"Local"` |  |
| service.httpPort | int | `80` |  |
| service.loadBalancerIP | string | `""` |  |
| service.type | string | `"ClusterIP"` |  |
| service.vncPort | int | `5900` |  |
| service.websocketPort | int | `443` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| strategyType | string | `"Recreate"` |  |
| timezone | string | `"UTC"` |  |
| tolerations | list | `[]` |  |
| vnc.enabled | bool | `true` |  |
| vnc.existingSecret | string | `""` |  |
| vnc.password | string | `"changeme"` |  |
| zigbeeDevice.enabled | bool | `false` |  |
| zigbeeDevice.hostPath | string | `"/dev/ttyUSB1"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
