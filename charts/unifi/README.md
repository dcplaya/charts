<<<<<<< HEAD
# Ubiquiti Network's Unifi Controller

This is a helm chart for [Ubiquiti Network's][ubnt] [Unifi Controller][ubnt 2].

## TL;DR;

```shell
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm install k8s-at-home/unifi
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release stable/unifi
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Unifi chart and their default values.

| Parameter                                       | Default                      | Description                                                                                                            |
|-------------------------------------------------|------------------------------|------------------------------------------------------------------------------------------------------------------------|
| `image.repository`                              | `jacobalberty/unifi`         | Image repository                                                                                                       |
| `image.tag`                                     | `5.14.23`                    | Image tag. Possible values listed [here][docker].                                                                      |
| `image.pullPolicy`                              | `IfNotPresent`               | Image pull policy                                                                                                      |
| `strategyType`                                  | `Recreate`                   | Specifies the strategy used to replace old Pods by new ones                                                            |
| `guiService.type`                               | `ClusterIP`                  | Kubernetes service type for the Unifi GUI                                                                              |
| `guiService.port`                               | `8443`                       | Kubernetes port where the Unifi GUI is exposed                                                                         |
| `guiService.annotations`                        | `{}`                         | Service annotations for the Unifi GUI                                                                                  |
| `guiService.labels`                             | `{}`                         | Custom labels                                                                                                          |
| `guiService.loadBalancerIP`                     | `{}`                         | Loadbalance IP for the Unifi GUI                                                                                       |
| `guiService.loadBalancerSourceRanges`           | None                         | List of IP CIDRs allowed access to load balancer (if supported)                                                        |
| `guiService.externalTrafficPolicy`              | `Cluster`                    | Set the externalTrafficPolicy in the Service to either Cluster or Local                                                |
| `captivePortalService.enabled`                  | `false`                      | Install the captive portal service (needed if you want guest captive portal)                                           |
| `captivePortalService.type`                     | `ClusterIP`                  | Kubernetes service type for the captive portal                                                                         |
| `captivePortalService.http`                     | `8880`                       | Kubernetes port where the captive portal is exposed                                                                    |
| `captivePortalService.https`                    | `8843`                       | Kubernetes port where the captive portal is exposed (with SSL)                                                         |
| `captivePortalService.annotations`              | `{}`                         | Service annotations for the captive portal                                                                             |
| `captivePortalService.labels`                   | `{}`                         | Custom labels                                                                                                          |
| `captivePortalService.loadBalancerIP`           | `{}`                         | Loadbalance IP for the Unifi GUI                                                                                       |
| `captivePortalService.loadBalancerSourceRanges` | None                         | List of IP CIDRs allowed access to load balancer (if supported)                                                        |
| `captivePortalService.externalTrafficPolicy`    | `Cluster`                    | Set the externalTrafficPolicy in the Service to either Cluster or Local                                                |
| `captivePortalService.ingress.enabled`          | `false`                      | Enables Ingress (for the captive portal, the main ingress needs to be enabled for the controller to be accessible)     |
| `captivePortalService.ingress.annotations`      | `{}`                         | Ingress annotations for the captive portal                                                                             |
| `captivePortalService.ingress.labels`           | `{}`                         | Custom labels for the captive portal                                                                                   |
| `captivePortalService.ingress.path`             | `/`                          | Ingress path for the captive portal                                                                                    |
| `captivePortalService.ingress.hosts`            | `chart-example.local`        | Ingress accepted hostnames for the captive portal                                                                      |
| `captivePortalService.ingress.tls`              | `[]`                         | Ingress TLS configuration for the captive portal                                                                       |
| `controllerService.type`                        | `NodePort`                   | Kubernetes service type for the Unifi Controller communication                                                         |
| `controllerService.port`                        | `8080`                       | Kubernetes port where the Unifi Controller is exposed - this needs to be reachable by the unifi devices on the network |
| `controllerService.annotations`                 | `{}`                         | Service annotations for the Unifi Controller                                                                           |
| `controllerService.labels`                      | `{}`                         | Custom labels                                                                                                          |
| `controllerService.loadBalancerIP`              | `{}`                         | Loadbalance IP for the Unifi Controller                                                                                |
| `controllerService.loadBalancerSourceRanges`    | None                         | List of IP CIDRs allowed access to load balancer (if supported)                                                        |
| `controllerService.externalTrafficPolicy`       | `Cluster`                    | Set the externalTrafficPolicy in the Service to either Cluster or Local                                                |
| `controllerService.ingress.enabled`             | `false`                      | Enables Ingress for the controller                                                                                     |
| `controllerService.ingress.annotations`         | `{}`                         | Ingress annotations for the controller                                                                                 |
| `controllerService.ingress.labels`              | `{}`                         | Custom labels for the controller                                                                                       |
| `controllerService.ingress.path`                | `/`                          | Ingress path for the controller                                                                                        |
| `controllerService.ingress.hosts`               | `chart-example.local`        | Ingress accepted hostnames for the controller                                                                          |
| `controllerService.ingress.tls`                 | `[]`                         | Ingress TLS configuration for the controller                                                                           |
| `stunService.type`                              | `NodePort`                   | Kubernetes service type for the Unifi STUN                                                                             |
| `stunService.port`                              | `3478`                       | Kubernetes UDP port where the Unifi STUN is exposed                                                                    |
| `stunService.annotations`                       | `{}`                         | Service annotations for the Unifi STUN                                                                                 |
| `stunService.labels`                            | `{}`                         | Custom labels                                                                                                          |
| `stunService.loadBalancerIP`                    | `{}`                         | Loadbalance IP for the Unifi STUN                                                                                      |
| `stunService.loadBalancerSourceRanges`          | None                         | List of IP CIDRs allowed access to load balancer (if supported)                                                        |
| `stunService.externalTrafficPolicy`             | `Cluster`                    | Set the externalTrafficPolicy in the Service to either Cluster or Local                                                |
| `discoveryService.type`                         | `NodePort`                   | Kubernetes service type for AP discovery                                                                               |
| `discoveryService.port`                         | `10001`                      | Kubernetes UDP port for AP discovery                                                                                   |
| `discoveryService.annotations`                  | `{}`                         | Service annotations for AP discovery                                                                                   |
| `discoveryService.labels`                       | `{}`                         | Custom labels                                                                                                          |
| `discoveryService.loadBalancerIP`               | `{}`                         | Loadbalance IP for AP discovery                                                                                        |
| `discoveryService.loadBalancerSourceRanges`     | None                         | List of IP CIDRs allowed access to load balancer (if supported)                                                        |
| `discoveryService.externalTrafficPolicy`        | `Cluster`                    | Set the externalTrafficPolicy in the Service to either Cluster or Local                                                |
| `syslogService.type`                            | `NodePort`                   | Kubernetes service type for remote syslog capture                                                                      |
| `syslogService.port`                            | `5514`                       | Kubernetes UDP port for remote syslog capture                                                                          |
| `syslogService.annotations`                     | `{}`                         | Service annotations for remote syslog capture                                                                          |
| `syslogService.labels`                          | `{}`                         | Custom labels                                                                                                          |
| `syslogService.loadBalancerIP`                  | `{}`                         | Loadbalancer IP for remote syslog capture                                                                              |
| `syslogService.loadBalancerSourceRanges`        | None                         | List of IP CIDRs allowed access to load balancer (if supported)                                                        |
| `syslogService.externalTrafficPolicy`           | `Cluster`                    | Set the externalTrafficPolicy in the Service to either Cluster or Local                                                |
| `speedtestService.type`                         | `ClusterIP`                  | Kubernetes service type for mobile speedtest                                                                           |
| `speedtestService.port`                         | `6789`                       | Kubernetes UDP port for mobile speedtest                                                                               |
| `speedtestService.annotations`                  | `{}`                         | Service annotations for mobile speedtest                                                                               |
| `speedtestService.labels`                       | `{}`                         | Custom labels                                                                                                          |
| `speedtestService.loadBalancerIP`               | `{}`                         | Loadbalancer IP for mobile speedtest                                                                                   |
| `speedtestService.loadBalancerSourceRanges`     | None                         | List of IP CIDRs allowed access to load balancer (if supported)                                                        |
| `speedtestService.externalTrafficPolicy`        | `Cluster`                    | Set the externalTrafficPolicy in the Service to either Cluster or Local                                                |
| `unifiedService.enabled`                        | `false`                      | Use a single service for GUI, controller, STUN, discovery, syslog and speedtest                                        |
| `unifiedService.type`                           | `ClusterIP`                  | Kubernetes service type for the unified service                                                                        |
| `unifiedService.annotations`                    | `{}`                         | Annotations for the unified service                                                                                    |
| `unifiedService.labels`                         | `{}`                         | Custom labels for the unified service                                                                                  |
| `unifiedService.loadBalancerIP`                 | None                         | Load balancer IP for the unified service                                                                               |
| `unifiedService.loadBalancerSourceRanges`       | None                         | List of IP CIDRs allowed access to the load balancer (if supported)                                                    |
| `unifiedService.externalTrafficPolicy`          | `Cluster`                    | Set the externalTrafficPolicy in the service to either Cluster or Local                                                |
| `ingress.enabled`                               | `false`                      | Enables Ingress                                                                                                        |
| `ingress.annotations`                           | `{}`                         | Ingress annotations                                                                                                    |
| `ingress.labels`                                | `{}`                         | Custom labels                                                                                                          |
| `ingress.path`                                  | `/`                          | Ingress path                                                                                                           |
| `ingress.hosts`                                 | `chart-example.local`        | Ingress accepted hostnames                                                                                             |
| `ingress.tls`                                   | `[]`                         | Ingress TLS configuration                                                                                              |
| `timezone`                                      | `UTC`                        | Timezone the Unifi controller should run as, e.g. 'America/New York'                                                   |
| `runAsRoot`                                     | `false`                      | Run the controller as UID0 (root user); if set to false, will give container SETFCAP instead                           |
| `UID`                                           | `999`                        | Run the controller as user UID                                                                                         |
| `GID`                                           | `999`                        | Run the controller as group GID                                                                                        |
| `customCert.enabled`                            | `false`                      | Define whether you are using s custom certificate                                                                      |
| `customCert.isChain`                            | `false`                      | If you are using a Let's Encrypt certificate which already includes the full chain set this to `true`                  |
| `customCert.certName`                           | `tls.crt`                    | Name of the the certificate file in `<unifi-data>/cert`                                                                |
| `customCert.keyName`                            | `tls.key`                    | Name of the the private key file in `<unifi-data>/cert`                                                                |
| `customCert.certSecret`                         | `nil`                        | Name of the the k8s tls secret where the certificate and its key are stored.                                           |
| `logging.promtail.enabled`                      | `false`                      | Enable a Promtail sidecar to collect controller logs                                                                   |
| `logging.promtail.image.repository`             | `grafana/promtail`           | Promtail image repository                                                                                              |
| `logging.promtail.image.tag`                    | `1.6.0`                      | Promtail image tag                                                                                                     |
| `logging.promtail.image.pullPolicy`             | `IfNotPresent`               | Promtail image pull policy                                                                                             |
| `logging.promtail.loki.url`                     | `http://loki.logs.svc.cluster.local:3100/loki/api/v1/push` | URL of the Loki push API                                                                 |
| `mongodb.enabled`                               | `false`                      | Use external MongoDB for data storage                                                                                  |
| `mongodb.dbUri`                                 | `mongodb://mongo/unifi`      | external MongoDB URI                                                                                                   |
| `mongodb.statDbUri`                             | `mongodb://mongo/unifi_stat` | external MongoDB statdb URI                                                                                            |
| `mongodb.databaseName`                          | `unifi`                      | external MongoDB database name                                                                                         |
| `persistence.enabled`                           | `true`                       | Use persistent volume to store data                                                                                    |
| `persistence.size`                              | `5Gi`                        | Size of persistent volume claim                                                                                        |
| `persistence.existingClaim`                     | `nil`                        | Use an existing PVC to persist data                                                                                    |
| `persistence.subPath`                           | ``                           | Store data in a subdirectory of PV instead of at the root directory                                                    |
| `persistence.storageClass`                      | `-`                          | Type of persistent volume claim                                                                                        |
| `extraVolumes`                                  | `[]`                         | Additional volumes to be used by extraVolumeMounts                                                                     |
| `extraVolumeMounts`                             | `[]`                         | Additional volume mounts to be mounted in unifi container                                                              |
| `persistence.accessModes`                       | `[]`                         | Persistence access modes                                                                                               |
| `extraConfigFiles`                              | `{}`                         | Dictionary containing files mounted to `/configmap` inside the pod (See [values.yaml](values.yaml) for examples)       |
| `extraJvmOpts`                                  | `[]`                         | List of additional JVM options, e.g. `["-Dlog4j.configurationFile=file:/configmap/log4j2.xml"]`                        |
| `jvmInitHeapSize`                               | ``                           | Java Virtual Machine (JVM) initial, and minimum, heap size.                                                            |
| `jvmMaxHeapSize`                                | `1024M`                      | Java Virtual Machine (JVM) maximum heap size.                                                                          |
| `resources`                                     | `{}`                         | CPU/Memory resource requests/limits                                                                                    |
| `livenessProbe.enabled`                         | `true`                       | Turn on and off liveness probe                                                                                         |
| `livenessProbe.initialDelaySeconds`             | `30`                         | Delay before liveness probe is initiated                                                                               |
| `livenessProbe.periodSeconds`                   | `15`                         | How often to perform the probe                                                                                         |
| `livenessProbe.timeoutSeconds`                  | `5`                          | When the probe times out                                                                                               |
| `livenessProbe.failureThreshold`                | `3`                          | Minimum consecutive failures for the probe                                                                             |
| `livenessProbe.successThreshold`                | `1`                          | Minimum consecutive successes for the probe                                                                            |
| `readinessProbe.enabled`                        | `true`                       | Turn on and off readiness probe                                                                                        |
| `readinessProbe.initialDelaySeconds`            | `30`                         | Delay before readiness probe is initiated                                                                              |
| `readinessProbe.periodSeconds`                  | `15`                         | How often to perform the probe                                                                                         |
| `readinessProbe.timeoutSeconds`                 | `5`                          | When the probe times out                                                                                               |
| `readinessProbe.failureThreshold`               | `3`                          | Minimum consecutive failures for the probe                                                                             |
| `readinessProbe.successThreshold`               | `1`                          | Minimum consecutive successes for the probe                                                                            |
| `nodeSelector`                                  | `{}`                         | Node labels for pod assignment                                                                                         |
| `tolerations`                                   | `[]`                         | Toleration labels for pod assignment                                                                                   |
| `affinity`                                      | `{}`                         | Affinity settings for pod assignment                                                                                   |
| `podAnnotations`                                | `{}`                         | Key-value pairs to add as pod annotations                                                                              |
| `deploymentAnnotations`                         | `{}`                         | Key-value pairs to add as deployment annotations                                                                       |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install --name my-release \
  --set timezone="America/New York" \
    stable/unifi
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install --name my-release -f values.yaml stable/unifi
```

Read through the [values.yaml](values.yaml) file. It has several commented out suggested values.

## Regarding the services

- `guiService`: Represents the main web UI and is what one would normally point
  the ingress to.
- `captivePortalService`: This service is used to allow the captive portal webpage
  to be accessible. It needs to be reachable by the clients connecting to your guest
  network.
- `controllerService`: This is needed in order for the unifi devices to talk to
  the controller and must be otherwise exposed to the network where the unifi
  devices run. If you run this as a `NodePort` (the default setting), make sure
  that there is an external load balancer that is directing traffic from port
  8080 to the `NodePort` for this service.
- `discoveryService`: This needs to be reachable by the unifi devices on the
  network similar to the controller `Service` but only during the discovery
  phase. This is a UDP service.
- `stunService`: Also used periodically by the unifi devices to communicate
  with the controller using UDP. See [this article][ubnt 3] and [this other
  article][ubnt 4] for more information.
- `syslogService`: Used to capture syslog from Unifi devices if the feature is 
  enabled in the site configuration. This needs to be reachable by Unifi devices
  on port 5514/UDP.
- `speedtestService`: Used for mobile speedtest inside the UniFi Mobile app.
  This needs to be reachable by clients connecting to port 6789/TCP.

## Ingress and HTTPS

Unifi does [not support HTTP][unifi] so if you wish to use the guiService, you
need to ensure that you use a backend transport of HTTPS.

An example entry in `values.yaml` to achieve this is as follows:

```
ingress:
  enabled: true
  annotations:
    nginx.ingress.kubernetes.io/backend-protocol: "HTTPS"
```

[docker]: https://hub.docker.com/r/jacobalberty/unifi/tags/
[github]: https://github.com/jacobalberty/unifi-docker
[ubnt]: https://www.ubnt.com/
[ubnt 2]: https://unifi-sdn.ubnt.com/
[ubnt 3]: https://help.ubnt.com/hc/en-us/articles/204976094-UniFi-What-protocol-does-the-controller-use-to-communicate-with-the-UAP-
[ubnt 4]: https://help.ubnt.com/hc/en-us/articles/115015457668-UniFi-Troubleshooting-STUN-Communication-Errors
[unifi]: https://community.ui.com/questions/Controller-how-to-deactivate-http-to-https/c5e247d8-b5b9-4c84-a3bb-28a90fd65668
=======
# unifi

![Version: 1.5.1](https://img.shields.io/badge/Version-1.5.1-informational?style=flat-square) ![AppVersion: 5.14.23](https://img.shields.io/badge/AppVersion-5.14.23-informational?style=flat-square)

Ubiquiti Network's Unifi Controller

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/unifi>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| billimek | jeff@billimek.com |  |
| mcronce | mike@quadra-tec.net |  |

## Source Code

* <https://github.com/jacobalberty/unifi-docker>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| GID | int | `999` |  |
| UID | int | `999` |  |
| affinity | object | `{}` |  |
| captivePortalService.annotations | object | `{}` |  |
| captivePortalService.enabled | bool | `false` |  |
| captivePortalService.http | int | `8880` |  |
| captivePortalService.https | int | `8843` |  |
| captivePortalService.ingress.annotations | object | `{}` |  |
| captivePortalService.ingress.enabled | bool | `false` |  |
| captivePortalService.ingress.hosts[0] | string | `"chart-example.local"` |  |
| captivePortalService.ingress.path | string | `"/"` |  |
| captivePortalService.ingress.tls | list | `[]` |  |
| captivePortalService.labels | object | `{}` |  |
| captivePortalService.loadBalancerIP | string | `nil` |  |
| captivePortalService.type | string | `"ClusterIP"` |  |
| controllerService.annotations | object | `{}` |  |
| controllerService.ingress.annotations | object | `{}` |  |
| controllerService.ingress.enabled | bool | `false` |  |
| controllerService.ingress.hosts[0] | string | `"chart-example.local"` |  |
| controllerService.ingress.path | string | `"/"` |  |
| controllerService.ingress.tls | list | `[]` |  |
| controllerService.labels | object | `{}` |  |
| controllerService.loadBalancerIP | string | `nil` |  |
| controllerService.port | int | `8080` |  |
| controllerService.type | string | `"NodePort"` |  |
| customCert.certName | string | `"tls.crt"` |  |
| customCert.enabled | bool | `false` |  |
| customCert.isChain | bool | `false` |  |
| customCert.keyName | string | `"tls.key"` |  |
| deploymentAnnotations | object | `{}` |  |
| discoveryService.annotations | object | `{}` |  |
| discoveryService.labels | object | `{}` |  |
| discoveryService.loadBalancerIP | string | `nil` |  |
| discoveryService.port | int | `10001` |  |
| discoveryService.type | string | `"NodePort"` |  |
| extraConfigFiles | object | `{}` |  |
| extraJvmOpts | list | `[]` |  |
| extraVolumeMounts | list | `[]` |  |
| extraVolumes | list | `[]` |  |
| guiService.annotations | object | `{}` |  |
| guiService.labels | object | `{}` |  |
| guiService.loadBalancerIP | string | `nil` |  |
| guiService.port | int | `8443` |  |
| guiService.type | string | `"ClusterIP"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"jacobalberty/unifi"` |  |
| image.tag | string | `"5.14.23"` |  |
| ingress.annotations | object | `{}` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0] | string | `"chart-example.local"` |  |
| ingress.path | string | `"/"` |  |
| ingress.tls | list | `[]` |  |
| jvmInitHeapSize | string | `nil` |  |
| jvmMaxHeapSize | string | `"1024M"` |  |
| livenessProbe.enabled | bool | `true` |  |
| livenessProbe.failureThreshold | int | `3` |  |
| livenessProbe.initialDelaySeconds | int | `30` |  |
| livenessProbe.periodSeconds | int | `10` |  |
| livenessProbe.successThreshold | int | `1` |  |
| livenessProbe.timeoutSeconds | int | `1` |  |
| logging.promtail.enabled | bool | `false` |  |
| logging.promtail.image.pullPolicy | string | `"IfNotPresent"` |  |
| logging.promtail.image.repository | string | `"grafana/promtail"` |  |
| logging.promtail.image.tag | string | `"1.6.0"` |  |
| logging.promtail.loki.url | string | `"http://loki.logs.svc.cluster.local:3100/loki/api/v1/push"` |  |
| mongodb.databaseName | string | `"unifi"` |  |
| mongodb.dbUri | string | `"mongodb://mongo/unifi"` |  |
| mongodb.enabled | bool | `false` |  |
| mongodb.statDbUri | string | `"mongodb://mongo/unifi_stat"` |  |
| nodeSelector | object | `{}` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.enabled | bool | `true` |  |
| persistence.size | string | `"5Gi"` |  |
| podAnnotations | object | `{}` |  |
| readinessProbe.enabled | bool | `true` |  |
| readinessProbe.failureThreshold | int | `3` |  |
| readinessProbe.initialDelaySeconds | int | `15` |  |
| readinessProbe.periodSeconds | int | `10` |  |
| readinessProbe.successThreshold | int | `1` |  |
| readinessProbe.timeoutSeconds | int | `1` |  |
| resources | object | `{}` |  |
| runAsRoot | bool | `false` |  |
| speedtestService.annotations | object | `{}` |  |
| speedtestService.labels | object | `{}` |  |
| speedtestService.loadBalancerIP | string | `nil` |  |
| speedtestService.port | int | `6789` |  |
| speedtestService.type | string | `"ClusterIP"` |  |
| strategyType | string | `"Recreate"` |  |
| stunService.annotations | object | `{}` |  |
| stunService.labels | object | `{}` |  |
| stunService.loadBalancerIP | string | `nil` |  |
| stunService.port | int | `3478` |  |
| stunService.type | string | `"NodePort"` |  |
| syslogService.annotations | object | `{}` |  |
| syslogService.labels | object | `{}` |  |
| syslogService.loadBalancerIP | string | `nil` |  |
| syslogService.port | int | `5514` |  |
| syslogService.type | string | `"NodePort"` |  |
| timezone | string | `"UTC"` |  |
| tolerations | list | `[]` |  |
| unifiedService.annotations | object | `{}` |  |
| unifiedService.enabled | bool | `false` |  |
| unifiedService.labels | object | `{}` |  |
| unifiedService.loadBalancerIP | string | `nil` |  |
| unifiedService.type | string | `"ClusterIP"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
