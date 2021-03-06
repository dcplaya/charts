<<<<<<< HEAD
# Neolink

This is a helm chart for [Neolink](https://github.com/thirtythreeforty/neolink).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose).**

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/neolink
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install my-release k8s-at-home/neolink
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```
The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
The chart's [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/neolink/values.yaml) file contains a set of suggested values for a minimal deployment. Further configuration options are found in the [common library](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml).

The configuration for the application itself is set as a configmap and mounted in the container as /etc/neolink.toml. Refer to the sample config [here.](https://github.com/thirtythreeforty/neolink/blob/master/sample_config.toml)


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install neolink \
  --set env.TZ="America/New_York" \
    k8s-at-home/neolink
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,
```console
helm install neolink k8s-at-home/neolink --values values.yaml
```
=======
# neolink

![Version: 2.0.1](https://img.shields.io/badge/Version-2.0.1-informational?style=flat-square) ![AppVersion: 0.3.0](https://img.shields.io/badge/AppVersion-0.3.0-informational?style=flat-square)

Neolink - RTSP bridge to Reolink IP cameras

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/thirtythreeforty/neolink>

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
helm install neolink k8s-at-home/neolink
```

## Installing the Chart

To install the chart with the release name `neolink`

```console
helm install neolink k8s-at-home/neolink
```

## Uninstalling the Chart

To uninstall the `neolink` deployment

```console
helm uninstall neolink
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install neolink \
  --set env.TZ="America/New York" \
    k8s-at-home/neolink
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install neolink k8s-at-home/neolink -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| config | string | `"bind = \"0.0.0.0\"\n[[cameras]]\nname = \"driveway\"\nusername = \"admin\"\npassword = \"12345678\"\naddress = \"192.168.1.187:9000\"\n"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"thirtythreeforty/neolink"` |  |
| image.tag | string | `"latest"` |  |
| ingress.enabled | bool | `false` |  |
| service.port.port | int | `8554` |  |
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
