<<<<<<< HEAD
# Photoprism

This is a helm chart for [PhotoPrism](https://github.com/photoprism/photoprism).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

This chart requires heavy customization of the `env: {}` block within values.yaml to configure the service to operate properly. See the PhotoPrism [documentation](https://docs.photoprism.org/getting-started/config-options/) for available config options.

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/photoprism
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/photoprism
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
Read through the charts [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/photoprism/values.yaml)
file. It has several commented out suggested values.
Additionally you can take a look at the common library [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml) for more (advanced) configuration options.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install photoprism \
  --set env.TZ="America/New_York" \
    k8s-at-home/photoprism
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install photoprism k8s-at-home/photoprism --values values.yaml 
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
# photoprism

![Version: 3.0.1](https://img.shields.io/badge/Version-3.0.1-informational?style=flat-square) ![AppVersion: 20201122](https://img.shields.io/badge/AppVersion-20201122-informational?style=flat-square)

PhotoPrism® is a server-based application for browsing, organizing and sharing your personal photo collection

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/photoprism/photoprism>
* <https://hub.docker.com/r/photoprism/photoprism>

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
helm install photoprism k8s-at-home/photoprism
```

## Installing the Chart

To install the chart with the release name `photoprism`

```console
helm install photoprism k8s-at-home/photoprism
```

## Uninstalling the Chart

To uninstall the `photoprism` deployment

```console
helm uninstall photoprism
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install photoprism \
  --set env.TZ="America/New York" \
    k8s-at-home/photoprism
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install photoprism k8s-at-home/photoprism -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env.PHOTOPRISM_ORIGINALS_PATH | string | `"/photoprism/originals"` |  |
| env.PHOTOPRISM_STORAGE_PATH | string | `"/photoprism/storage"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"photoprism/photoprism"` |  |
| image.tag | string | `"20201122"` |  |
| ingress.enabled | bool | `false` |  |
| persistence.config.emptyDir | bool | `false` |  |
| persistence.config.enabled | bool | `false` |  |
| persistence.config.mountPath | string | `"/photoprism/storage"` |  |
| persistence.originals.emptyDir | bool | `false` |  |
| persistence.originals.enabled | bool | `false` |  |
| persistence.originals.mountPath | string | `"/photoprism/originals"` |  |
| service.port.port | int | `2342` |  |
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
