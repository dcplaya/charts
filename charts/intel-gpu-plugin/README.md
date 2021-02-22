<<<<<<< HEAD
# intel-gpu-plugin helm chart

This is a helm chart that will deploy [intel-gpu-plugin](https://github.com/intel/intel-device-plugins-for-kubernetes/blob/master/cmd/gpu_plugin) as a DaemonSet.

The GPU plugin facilitates offloading the processing of computation intensive workloads to GPU hardware.

## TL;DR

```shell
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm install k8s-at-home/intel-gpu-plugin
```

## Installing the Chart

To install the chart with the release name `my-release`:

```shell
helm install my-release k8s-at-home/intel-gpu-plugin
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```shell
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Sentry chart and their default values.
Read through the [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/intel-gpu-plugin/values.yaml) file. It has several commented out suggested values.

| Parameter                                   | Description                                                                                  | Default                                               |
| ------------------------------------------- | -------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| `image.repository`                          | Image repository                                                                             | `intel/intel-gpu-plugin` |
| `image.tag`                                 | Image tag. Possible values listed [here](https://hub.docker.com/r/intel/intel-gpu-plugin/tags).     | `0.18.1`                         |
| `image.pullPolicy`                          | Image pull policy                                                                            | `IfNotPresent`                                        |
| `strategyType`                              | Specifies the strategy used to replace old Pods by new ones                                  | `Recreate`                                            |
| `podAnnotations`                            | Key-value pairs to add as pod annotations                                                    | `{}`                                                  |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```shell
helm install my-release \
  --set image.pullPolicy="Always" \
    k8s-at-home/intel-gpu-plugin
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```shell
helm install my-release -f values.yaml k8s-at-home/intel-gpu-plugin
```

### Node Feature Discovery

If your cluster runs [Node Feature Discovery](https://github.com/k8s-at-home/charts/blob/master/charts/node-feature-discovery), you can deploy the device plugin only on nodes with Intel GPU by specifying the desired `nodeSelector` or `affinity` in your values. For example (make sure to update to your exact feature label):

```yaml
affinity:
  nodeAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
      nodeSelectorTerms:
        - matchExpressions:
            - key: feature.node.kubernetes.io/pci-0300_8086.present
              operator: In
              values:
                - "true"
```
=======
# intel-gpu-plugin

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![AppVersion: 0.18.1](https://img.shields.io/badge/AppVersion-0.18.1-informational?style=flat-square)

The Intel GPU plugin facilitates offloading the processing of computation intensive workloads to GPU hardware

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/intel-gpu-plugin>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| billimek | jeff@billimek.com |  |

## Source Code

* <https://github.com/intel/intel-device-plugins-for-kubernetes/blob/master/cmd/gpu_plugin>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"intel/intel-gpu-plugin"` |  |
| image.tag | string | `"0.18.1"` |  |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
