<<<<<<< HEAD
# Traccar

This is a helm chart for [Traccar](https://github.com/traccar/traccar).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/traccar
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/traccar
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
Read through the charts [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/traccar/values.yaml)
file. It has several commented out suggested values.
Additionally you can take a look at the common library [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml) for more (advanced) configuration options.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install traccar \
  --set env.TZ="America/New_York" \
    k8s-at-home/traccar
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install traccar k8s-at-home/traccar --values values.yaml 
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
# traccar

![Version: 3.0.1](https://img.shields.io/badge/Version-3.0.1-informational?style=flat-square) ![AppVersion: v4.11](https://img.shields.io/badge/AppVersion-v4.11-informational?style=flat-square)

Traccar is an open source GPS tracking system.

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/traccar/traccar>
* <https://hub.docker.com/r/traccar/traccar>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | mariadb | 9.2.5 |
| https://k8s-at-home.com/charts/ | common | 3.0.1 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install traccar k8s-at-home/traccar
```

## Installing the Chart

To install the chart with the release name `traccar`

```console
helm install traccar k8s-at-home/traccar
```

## Uninstalling the Chart

To uninstall the `traccar` deployment

```console
helm uninstall traccar
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install traccar \
  --set env.TZ="America/New York" \
    k8s-at-home/traccar
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install traccar k8s-at-home/traccar -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env.CONFIG_USE_ENVIRONMENT_VARIABLES | bool | `true` |  |
| env.LOGGER_CONSOLE | bool | `true` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"traccar/traccar"` |  |
| image.tag | float | `4.11` |  |
| ingress.enabled | bool | `false` |  |
| mariadb.architecture | string | `"standalone"` |  |
| mariadb.auth.database | string | `"traccar"` |  |
| mariadb.auth.password | string | `"traccar"` |  |
| mariadb.auth.username | string | `"traccar"` |  |
| mariadb.enabled | bool | `false` |  |
| mariadb.primary.persistence.enabled | bool | `false` |  |
| persistence.data.emptyDir | bool | `false` |  |
| persistence.data.enabled | bool | `false` |  |
| persistence.data.mountPath | string | `"/opt/traccar/data"` |  |
| probes.startup.enabled | bool | `true` |  |
| service.port.port | int | `8082` |  |
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
