<<<<<<< HEAD
# statping | Status page for monitoring your websites and applications

## TL;DR
```console
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/statping
```

## Installing the Chart
To install the chart with the release name `statping`:
```console
helm install statping k8s-at-home/statping
```

## Uninstalling the Chart
To uninstall the `statping` deployment:
```console
helm uninstall statping
```
The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
Read through the [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/statping/values.yaml)
file. It has several commented out suggested values.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install statping \
  --set statping.env.TZ="America/New York" \
    k8s-at-home/statping
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install statping k8s-at-home/statping --values values.yaml 
```

=======
# statping

![Version: 1.5.1](https://img.shields.io/badge/Version-1.5.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v0.90.65](https://img.shields.io/badge/AppVersion-v0.90.65-informational?style=flat-square)

Status page for monitoring your websites and applications

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/statping>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| DirtyCajunRice | nick@cajun.pro |  |

## Source Code

* <https://github.com/statping/statping>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | postgresql | 10.2.6 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalVolumeMounts | list | `[]` |  |
| additionalVolumes | list | `[]` |  |
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `3` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| env | list | `[]` |  |
| externalSecret.enabled | bool | `false` |  |
| externalSecret.kubernetesExternalSecrets.data | list | `[]` |  |
| externalSecret.kubernetesExternalSecrets.spec | object | `{}` |  |
| externalSecret.type | string | `"kubernetes-external-secrets"` |  |
| fullnameOverride | string | `""` |  |
| global.postgresql.postgresqlDatabase | string | `"postgres"` |  |
| global.postgresql.postgresqlUsername | string | `"postgres"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"statping/statping"` |  |
| image.tag | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0] | string | `"/"` |  |
| ingress.labels | object | `{}` |  |
| ingress.tls | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.enabled | bool | `true` |  |
| persistence.size | string | `"1Gi"` |  |
| persistence.skipuninstall | bool | `false` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| postgres.kubedb.enabled | bool | `false` |  |
| postgres.kubedb.storage.accessModes[0] | string | `"ReadWriteOnce"` |  |
| postgres.kubedb.storage.resources.requests.storage | string | `"1Gi"` |  |
| postgres.kubedb.storageType | string | `"Durable"` |  |
| postgres.kubedb.version | float | `11.1` |  |
| postgres.posgresql.enabled | bool | `true` |  |
| postgres.type | string | `"postgresql"` |  |
| probes.liveness.failureThreshold | int | `5` |  |
| probes.liveness.initialDelaySeconds | int | `60` |  |
| probes.liveness.timeoutSeconds | int | `10` |  |
| probes.readiness.failureThreshold | int | `5` |  |
| probes.readiness.initialDelaySeconds | int | `60` |  |
| probes.readiness.timeoutSeconds | int | `10` |  |
| replication.enabled | bool | `false` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.additionalSpec | object | `{}` |  |
| service.annotations | object | `{}` |  |
| service.labels | object | `{}` |  |
| service.port | int | `8080` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| statping.admin.email | string | `""` |  |
| statping.admin.existingSecret.emailKey | string | `""` |  |
| statping.admin.existingSecret.enabled | bool | `false` |  |
| statping.admin.existingSecret.name | string | `""` |  |
| statping.admin.existingSecret.passwordKey | string | `""` |  |
| statping.admin.existingSecret.userKey | string | `""` |  |
| statping.admin.password | string | `""` |  |
| statping.admin.user | string | `""` |  |
| statping.description | string | `""` |  |
| statping.domain | string | `""` |  |
| statping.name | string | `""` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
