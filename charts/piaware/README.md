<<<<<<< HEAD
# piaware

This is a helm chart for [piaware](https://github.com/flightaware/piaware).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/piaware
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/piaware
```

**IMPORTANT NOTE:** a piaware device must be accessible on the node where this pod runs, in order for this chart to function properly.

First, you will need to mount your piaware device into the pod, you can do so by adding the following to your values:

```yaml
additionalVolumeMounts:
  - name: usb
    mountPath: /path/to/device

additionalVolumes:
  - name: usb
    hostPath:
      path: /path/to/device
```

Second you will need to set a nodeAffinity rule, for example:

```yaml
affinity:
  nodeAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
      nodeSelectorTerms:
      - matchExpressions:
        - key: app
          operator: In
          values:
          - piaware
```

... where a node with an attached piaware USB device is labeled with `app: piaware`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

Read through the charts [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/piaware/values.yaml)
file. It has several commented out suggested values.
Additionally you can take a look at the common library [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml) for more (advanced) configuration options.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install my-release \
  --set env.TZ="America/New_York" \
    k8s-at-home/piaware
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install my-release k8s-at-home/piaware --values values.yaml 
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

### Upgrading from 2.x.x to 3.x.x

As of 3.0.0 this chart was migrated to a centralized [common](https://github.com/k8s-at-home/charts/tree/master/charts/common) library, some values in `values.yaml` have changed.

Examples:

* `service.port` has been moved to `service.port.port`.
* `persistence.type` has been moved to `controllerType`.

Refer to the [common](https://github.com/k8s-at-home/charts/tree/master/charts/common) library for more configuration options.
=======
# piaware

![Version: 5.0.1](https://img.shields.io/badge/Version-5.0.1-informational?style=flat-square) ![AppVersion: v4.0](https://img.shields.io/badge/AppVersion-v4.0-informational?style=flat-square)

Program for forwarding ADS-B data to FlightAware

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/flightaware/piaware>

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
helm install piaware k8s-at-home/piaware
```

## Installing the Chart

To install the chart with the release name `piaware`

```console
helm install piaware k8s-at-home/piaware
```

## Uninstalling the Chart

To uninstall the `piaware` deployment

```console
helm uninstall piaware
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install piaware \
  --set env.TZ="America/New York" \
    k8s-at-home/piaware
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install piaware k8s-at-home/piaware -f values.yaml
```

## Custom configuration

**IMPORTANT NOTE:** a piaware device must be accessible on the node where this pod runs, in order for this chart to function properly.

First, you will need to mount your piaware device into the pod, you can do so by adding the following to your values:

```yaml
additionalVolumeMounts:
  - name: usb
    mountPath: /path/to/device

additionalVolumes:
  - name: usb
    hostPath:
      path: /path/to/device
```

Second you will need to set a nodeAffinity rule, for example:

```yaml
affinity:
  nodeAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
      nodeSelectorTerms:
      - matchExpressions:
        - key: app
          operator: In
          values:
          - piaware
```

... where a node with an attached piaware USB device is labeled with `app: piaware`

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalVolumeMounts[0].mountPath | string | `"/dev/bus/usb/001/004"` |  |
| additionalVolumeMounts[0].name | string | `"usb"` |  |
| additionalVolumes[0].hostPath.path | string | `"/dev/bus/usb/001/004"` |  |
| additionalVolumes[0].name | string | `"usb"` |  |
| env | object | `{}` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"mikenye/piaware"` |  |
| image.tag | string | `"v4.0"` |  |
| ingress.enabled | bool | `false` |  |
| securityContext.privileged | bool | `true` |  |
| service.port.port | int | `8080` |  |
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
