<<<<<<< HEAD
# Resilio Sync

This is a helm chart for [resilio-sync](https://resilio-sync.org/).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/resilio-sync
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/resilio-sync
```

The default login details (change ASAP) are:

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

Read through the charts [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/resilio-sync/values.yaml)
file. It has several commented out suggested values.
Additionally you can take a look at the common library [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml) for more (advanced) configuration options.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install my-release \
  --set env.TZ="America/New_York" \
    k8s-at-home/resilio-sync
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install my-release k8s-at-home/resilio-sync --values values.yaml 
```

```yaml
image:
  tag: ...
```

---
**NOTE**

If you get
```console
Error: rendered manifests contain a resource that already exists. Unable to continue with install: existing resource conflict: ...`
```
it may be because you uninstalled the chart with `skipuninstall` enabled, you need to manually delete the pvc or use `existingClaim`.

---

## Upgrading an existing Release to a new major version

A major chart version change (like 4.0.1 -> 5.0.0) indicates that there is an incompatible breaking change potentially needing manual actions.
=======
# resilio-sync

![Version: 2.0.1](https://img.shields.io/badge/Version-2.0.1-informational?style=flat-square) ![AppVersion: 2.7.2](https://img.shields.io/badge/AppVersion-2.7.2-informational?style=flat-square)

Resilio Sync is a fast, reliable, and simple file sync and share solution, powered by P2P technology

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/orgs/linuxserver/packages/container/package/resilio-sync>

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
helm install resilio-sync k8s-at-home/resilio-sync
```

## Installing the Chart

To install the chart with the release name `resilio-sync`

```console
helm install resilio-sync k8s-at-home/resilio-sync
```

## Uninstalling the Chart

To uninstall the `resilio-sync` deployment

```console
helm uninstall resilio-sync
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install resilio-sync \
  --set env.TZ="America/New York" \
    k8s-at-home/resilio-sync
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install resilio-sync k8s-at-home/resilio-sync -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | `{}` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/linuxserver/resilio-sync"` |  |
| image.tag | string | `"version-2.7.2.1375"` |  |
| ingress.enabled | bool | `false` |  |
| persistence.config.emptyDir | bool | `false` |  |
| persistence.config.enabled | bool | `false` |  |
| persistence.config.mountPath | string | `"/config"` |  |
| persistence.downloads.emptyDir | bool | `false` |  |
| persistence.downloads.enabled | bool | `false` |  |
| persistence.downloads.mountPath | string | `"/downloads"` |  |
| persistence.media.emptyDir | bool | `false` |  |
| persistence.media.enabled | bool | `false` |  |
| persistence.media.mountPath | string | `"/media"` |  |
| persistence.sync.emptyDir | bool | `false` |  |
| persistence.sync.enabled | bool | `false` |  |
| persistence.sync.mountPath | string | `"/sync"` |  |
| service.additionalServices[0].enabled | bool | `true` |  |
| service.additionalServices[0].nameSuffix | string | `"bt"` |  |
| service.additionalServices[0].port.name | string | `"bt"` |  |
| service.additionalServices[0].port.port | int | `55555` |  |
| service.additionalServices[0].port.protocol | string | `"TCP"` |  |
| service.additionalServices[0].port.targetPort | int | `55555` |  |
| service.additionalServices[0].type | string | `"ClusterIP"` |  |
| service.additionalServices[1].enabled | bool | `true` |  |
| service.additionalServices[1].nameSuffix | string | `"utp"` |  |
| service.additionalServices[1].port.name | string | `"utp"` |  |
| service.additionalServices[1].port.port | int | `55555` |  |
| service.additionalServices[1].port.protocol | string | `"UDP"` |  |
| service.additionalServices[1].port.targetPort | int | `55555` |  |
| service.additionalServices[1].type | string | `"ClusterIP"` |  |
| service.port.port | int | `8888` |  |
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
