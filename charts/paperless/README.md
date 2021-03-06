<<<<<<< HEAD
# Paperless

This is a helm chart for [Paperless](https://github.com/the-paperless-project/paperless). The documentation can be found [here](https://paperless.readthedocs.io/en/latest/index.html).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose).**

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/paperless
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/paperless
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```
The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
The chart's [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/paperless/values.yaml) file contains a set of suggested values for a minimal deployment. Further configuration options are found in the [common library](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml). All configuration for the Paperless application itself is through environment variables. Please refer to the links provided in chart's [values](https://github.com/k8s-at-home/charts/blob/master/charts/paperless/values.yaml) file.


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install paperless \
  --set env.TZ="America/New_York" \
    k8s-at-home/paperless
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,
```console
helm install paperless k8s-at-home/paperless --values values.yaml
```

## Backup & Restore
Documents can be exported and re-imported by running the following commands directly on the pod. [More info](https://paperless.readthedocs.io/en/latest/migrating.html).

Backup: `/usr/src/paperless/src/manage.py document_exporter /path/to/somewhere/`
Restore: `/usr/src/paperless/src/manage.py document_importer /path/to/somewhere/`
=======
# paperless

![Version: 4.0.1](https://img.shields.io/badge/Version-4.0.1-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

Paperless - Index and archive all of your scanned paper documents

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/jonaswinkler/paperless-ng>

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
helm install paperless k8s-at-home/paperless
```

## Installing the Chart

To install the chart with the release name `paperless`

```console
helm install paperless k8s-at-home/paperless
```

## Uninstalling the Chart

To uninstall the `paperless` deployment

```console
helm uninstall paperless
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install paperless \
  --set env.TZ="America/New York" \
    k8s-at-home/paperless
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install paperless k8s-at-home/paperless -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalContainers[0].image | string | `"redis:6.0"` |  |
| additionalContainers[0].imagePullPolicy | string | `"IfNotPresent"` |  |
| additionalContainers[0].name | string | `"broker"` |  |
| env.COMPOSE_PROJECT_NAME | string | `"paperless"` |  |
| env.PAPERLESS_OCR_LANGUAGE | string | `"eng"` |  |
| env.PAPERLESS_REDIS | string | `"redis://localhost:6379"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"jonaswinkler/paperless-ng"` |  |
| image.tag | string | `"latest"` |  |
| ingress.enabled | bool | `false` |  |
| persistence.consume.emptyDir | bool | `false` |  |
| persistence.consume.enabled | bool | `false` |  |
| persistence.consume.mountPath | string | `"/usr/src/paperless/consume"` |  |
| persistence.data.emptyDir | bool | `false` |  |
| persistence.data.enabled | bool | `false` |  |
| persistence.data.mountPath | string | `"/usr/src/paperless/data"` |  |
| persistence.export.emptyDir | bool | `false` |  |
| persistence.export.enabled | bool | `false` |  |
| persistence.export.mountPath | string | `"/usr/src/paperless/export"` |  |
| persistence.media.emptyDir | bool | `false` |  |
| persistence.media.enabled | bool | `false` |  |
| persistence.media.mountPath | string | `"/usr/src/paperless/media"` |  |
| service.port.port | int | `8000` |  |
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
