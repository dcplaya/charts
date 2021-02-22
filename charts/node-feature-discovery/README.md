<<<<<<< HEAD
# node-feature-discovery helm chart

This is a helm chart for [node-feature-discovery](https://github.com/kubernetes-sigs/node-feature-discovery) using the master/worker pattern.

## TL;DR

```shell
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm install k8s-at-home/node-feature-discovery
```

## Installing the Chart

To install the chart with the release name `my-release`:

```shell
helm install my-release k8s-at-home/node-feature-discovery
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```shell
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Sentry chart and their default values.
Read through the [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/node-feature-discovery/values.yaml) file. It has several commented out suggested values.

| Parameter                                   | Description                                                                                  | Default                                               |
| ------------------------------------------- | -------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| `image.repository`                          | Image repository                                                                             | `quay.io/kubernetes_incubator/node-feature-discovery` |
| `image.tag`                                 | Image tag. Possible values listed [here](https://github.com/kubernetes-sigs/node-feature-discovery/releases).     | `v0.6.0`                         |
| `image.pullPolicy`                          | Image pull policy                                                                            | `IfNotPresent`                                        |
| `strategyType`                              | Specifies the strategy used to replace old Pods by new ones                                  | `Recreate`                                            |
| `sources`                                   | List of sources to consider when labeling - see [documentation](https://github.com/kubernetes-sigs/node-feature-discovery#feature-sources) for info  | `[]`                                                  |
| `config`                                    | node-feature-discovery configuration - see [nfd-worker.conf.example](https://github.com/kubernetes-sigs/node-feature-discovery/blob/master/nfd-worker.conf.example) for example  | `{}` |
| `service.type`                              | Kubernetes service type for the GUI                                                          | `ClusterIP`                                           |
| `service.port`                              | Kubernetes port where the GUI is exposed                                                     | `8080`                                                |
| `service.annotations`                       | Service annotations for the GUI                                                              | `{}`                                                  |
| `service.labels`                            | Custom labels                                                                                | `{}`                                                  |
| `service.loadBalancerIP`                    | Loadbalancer IP for the GUI                                                                  | `{}`                                                  |
| `service.loadBalancerSourceRanges`          | List of IP CIDRs allowed access to load balancer (if supported)                              | `nil`                                                 |
| `podAnnotations`                            | Key-value pairs to add as pod annotations                                                    | `{}`                                                  |
| `master.replicaCount`                       | Number of replicas to scale the master component to                                          | `1`                                                   |
| `master.resources`                          | CPU/Memory resource requests/limits for master component                                     | `{}`                                                  |
| `master.nodeSelector`                       | Node labels for master component pod assignment                                              | `{}`                                                  |
| `master.tolerations`                        | Toleration labels for master component pod assignment                                        | See [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/node-feature-discovery/values.yaml)                                                  |
| `master.affinity`                           | Affinity settings for master component pod assignment                                        | See [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/node-feature-discovery/values.yaml)                                                  |
| `worker.resources`                          | CPU/Memory resource requests/limits for worker component                                     | `{}`                                                  |
| `worker.nodeSelector`                       | Node labels for worker component pod assignment                                              | `{}`                                                  |
| `worker.tolerations`                        | Toleration labels for worker component pod assignment                                        | `[]`                                                  |
| `worker.affinity`                           | Affinity settings for worker component pod assignment                                        | `{}`                                                  |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install my-release \
  --set image.pullPolicy="Always" \
    k8s-at-home/node-feature-discovery
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml k8s-at-home/node-feature-discovery
```
=======
# node-feature-discovery

![Version: 2.1.0](https://img.shields.io/badge/Version-2.1.0-informational?style=flat-square) ![AppVersion: 0.7.0](https://img.shields.io/badge/AppVersion-0.7.0-informational?style=flat-square)

Detect hardware features available on each node in a Kubernetes cluster, and advertises those features using node labels

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/node-feature-discovery>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| billimek | jeff@billimek.com |  |

## Source Code

* <https://github.com/kubernetes-sigs/node-feature-discovery>
* <https://github.com/k8s-at-home/charts>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| config | string | `"#sources:\n#  cpu:\n#    cpuid:\n##     NOTE: whitelist has priority over blacklist\n#      attributeBlacklist:\n#        - \"BMI1\"\n#        - \"BMI2\"\n#        - \"CLMUL\"\n#        - \"CMOV\"\n#        - \"CX16\"\n#        - \"ERMS\"\n#        - \"F16C\"\n#        - \"HTT\"\n#        - \"LZCNT\"\n#        - \"MMX\"\n#        - \"MMXEXT\"\n#        - \"NX\"\n#        - \"POPCNT\"\n#        - \"RDRAND\"\n#        - \"RDSEED\"\n#        - \"RDTSCP\"\n#        - \"SGX\"\n#        - \"SSE\"\n#        - \"SSE2\"\n#        - \"SSE3\"\n#        - \"SSE4.1\"\n#        - \"SSE4.2\"\n#        - \"SSSE3\"\n#      attributeWhitelist:\n#  kernel:\n#    kconfigFile: \"/path/to/kconfig\"\n#    configOpts:\n#      - \"NO_HZ\"\n#      - \"X86\"\n#      - \"DMI\"\n#  pci:\n#    deviceClassWhitelist:\n#      - \"0200\"\n#      - \"03\"\n#      - \"12\"\n#    deviceLabelFields:\n#      - \"class\"\n#      - \"vendor\"\n#      - \"device\"\n#      - \"subsystem_vendor\"\n#      - \"subsystem_device\"\n#  usb:\n#    deviceClassWhitelist:\n#      - \"0e\"\n#      - \"ef\"\n#      - \"fe\"\n#      - \"ff\"\n#    deviceLabelFields:\n#      - \"class\"\n#      - \"vendor\"\n#      - \"device\"\n#  custom:\n#    - name: \"my.kernel.feature\"\n#      matchOn:\n#        - loadedKMod: [\"example_kmod1\", \"example_kmod2\"]\n#    - name: \"my.pci.feature\"\n#      matchOn:\n#        - pciId:\n#            class: [\"0200\"]\n#            vendor: [\"15b3\"]\n#            device: [\"1014\", \"1017\"]\n#        - pciId :\n#            vendor: [\"8086\"]\n#            device: [\"1000\", \"1100\"]\n#    - name: \"my.usb.feature\"\n#      matchOn:\n#        - usbId:\n#          class: [\"ff\"]\n#          vendor: [\"03e7\"]\n#          device: [\"2485\"]\n#        - usbId:\n#          class: [\"fe\"]\n#          vendor: [\"1a6e\"]\n#          device: [\"089a\"]\n#    - name: \"my.combined.feature\"\n#      matchOn:\n#        - pciId:\n#            vendor: [\"15b3\"]\n#            device: [\"1014\", \"1017\"]\n#          loadedKMod : [\"vendor_kmod1\", \"vendor_kmod2\"]\n"` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"gcr.io/k8s-staging-nfd/node-feature-discovery"` |  |
| image.tag | string | `"v0.7.0"` |  |
| imagePullSecrets | list | `[]` |  |
| master.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].preference.matchExpressions[0].key | string | `"node-role.kubernetes.io/master"` |  |
| master.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].preference.matchExpressions[0].operator | string | `"In"` |  |
| master.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].preference.matchExpressions[0].values[0] | string | `""` |  |
| master.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[0].weight | int | `1` |  |
| master.nodeSelector | object | `{}` |  |
| master.replicaCount | int | `1` |  |
| master.resources | object | `{}` |  |
| master.securityContext | object | `{}` |  |
| master.tolerations[0].effect | string | `"NoSchedule"` |  |
| master.tolerations[0].key | string | `"node-role.kubernetes.io/master"` |  |
| master.tolerations[0].operator | string | `"Equal"` |  |
| master.tolerations[0].value | string | `""` |  |
| nameOverride | string | `""` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| rbac.create | bool | `true` |  |
| service.clusterIP | string | `""` |  |
| service.externalIPs | list | `[]` |  |
| service.externalTrafficPolicy | string | `nil` |  |
| service.loadBalancerIP | string | `""` |  |
| service.port | int | `8080` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| sources | list | `[]` |  |
| worker.affinity | object | `{}` |  |
| worker.nodeSelector | object | `{}` |  |
| worker.resources | object | `{}` |  |
| worker.securityContext | object | `{}` |  |
| worker.tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
