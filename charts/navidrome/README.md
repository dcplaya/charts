<<<<<<< HEAD
# Navidrome

This is a helm chart for [Navidrome](https://github.com/deluan/navidrome).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/navidrome
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/navidrome
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
Read through the charts [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/navidrome/values.yaml)
file. It has several commented out suggested values.
Additionally you can take a look at the common library [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml) for more (advanced) configuration options.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install navidrome \
  --set env.TZ="America/New_York" \
    k8s-at-home/navidrome
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install navidrome k8s-at-home/navidrome --values values.yaml
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

A major chart version change (like 1.0.1 -> 2.0.0) indicates that there is an incompatible breaking change potentially needing manual actions.
=======
# navidrome

![Version: 3.0.1](https://img.shields.io/badge/Version-3.0.1-informational?style=flat-square) ![AppVersion: 0.39.0](https://img.shields.io/badge/AppVersion-0.39.0-informational?style=flat-square)

Navidrome is an open source web-based music collection server and streamer

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/deluan/navidrome>
* <https://hub.docker.com/r/deluan/navidrome>

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
helm install navidrome k8s-at-home/navidrome
```

## Installing the Chart

To install the chart with the release name `navidrome`

```console
helm install navidrome k8s-at-home/navidrome
```

## Uninstalling the Chart

To uninstall the `navidrome` deployment

```console
helm uninstall navidrome
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install navidrome \
  --set env.TZ="America/New York" \
    k8s-at-home/navidrome
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install navidrome k8s-at-home/navidrome -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env.ND_ENABLETRANSCODINGCONFIG | string | `"true"` |  |
| env.ND_LOGLEVEL | string | `"info"` |  |
| env.ND_MUSICFOLDER | string | `"/music"` |  |
| env.ND_SCANINTERVAL | string | `"15m"` |  |
| env.ND_SESSIONTIMEOUT | string | `"24h"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"deluan/navidrome"` |  |
| image.tag | string | `"0.39.0"` |  |
| ingress.enabled | bool | `false` |  |
| persistence.config.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.config.emptyDir | bool | `false` |  |
| persistence.config.enabled | bool | `false` |  |
| persistence.config.mountPath | string | `"/data"` |  |
| persistence.music.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.music.emptyDir | bool | `false` |  |
| persistence.music.enabled | bool | `false` |  |
| persistence.music.mountPath | string | `"/music"` |  |
| service.port.port | int | `4533` |  |
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
