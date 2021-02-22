<<<<<<< HEAD
# zigbee2mqtt

This is a helm chart for [zigbee2mqtt](https://www.zigbee2mqtt.io).

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## TL;DR;

```shell
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/zigbee2mqtt
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release k8s-at-home/zigbee2mqtt
```

**IMPORTANT NOTE:** a zigbee controller device must be accessible on the node where this pod runs, in order for this chart to function properly.

First, you will need to mount your zigbee device into the pod, you can do so by adding the following to your values:

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
          - zigbee-controller
```

... where a node with an attached zigbee controller USB device is labeled with `app: zigbee-controller`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

Read through the charts [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/zigbee2mqtt/values.yaml)
file. It has several commented out suggested values.
Additionally you can take a look at the common library [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/common/values.yaml) for more (advanced) configuration options.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,
```console
helm install my-release \
  --set env.TZ="America/New_York" \
    k8s-at-home/zigbee2mqtt
```
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the
chart. For example,
```console
helm install my-release k8s-at-home/zigbee2mqtt --values values.yaml 
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

**Note:** _It may be wise to back up your existing data incase something unexpected happens_

As of 3.0.0 this chart was migrated to a centralized [common](https://github.com/k8s-at-home/charts/tree/master/charts/common) library, some values in `values.yaml` have changed.

Examples:

* `service.port` has been moved to `service.port.port`.
* `persistence.type` has been moved to `controllerType`.

Refer to the [common](https://github.com/k8s-at-home/charts/tree/master/charts/common) library for more configuration options.

### Upgrading from 1.x.x to 2.x.x

Zigbee2MQTT has gained a native full-feature WebUI. Because of this, Zigbee2MQTTAssistant was dropped from the chart

You should delete the assistant config from your values.yaml. If you wish to use the new UI, make sure you have
```
frontend:
  port: 8080
experimental:
  new_api: true
```
in the config section, and enable the ingress in values.yaml. Because of the way this chart works, you'll need to add this section to your configuration.yaml in zigbee2mqtt manually if you want to upgrade in-place
=======
# zigbee2mqtt

![Version: 6.0.1](https://img.shields.io/badge/Version-6.0.1-informational?style=flat-square) ![AppVersion: 1.17.1](https://img.shields.io/badge/AppVersion-1.17.1-informational?style=flat-square)

Bridges events and allows you to control your Zigbee devices via MQTT

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/Koenkk/zigbee2mqtt>

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
helm install zigbee2mqtt k8s-at-home/zigbee2mqtt
```

## Installing the Chart

To install the chart with the release name `zigbee2mqtt`

```console
helm install zigbee2mqtt k8s-at-home/zigbee2mqtt
```

## Uninstalling the Chart

To uninstall the `zigbee2mqtt` deployment

```console
helm uninstall zigbee2mqtt
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](../common/values.yaml) from the [common library](../common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install zigbee2mqtt \
  --set env.TZ="America/New York" \
    k8s-at-home/zigbee2mqtt
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install zigbee2mqtt k8s-at-home/zigbee2mqtt -f values.yaml
```

## Custom configuration

**IMPORTANT NOTE:** a zigbee controller device must be accessible on the node where this pod runs, in order for this chart to function properly.

First, you will need to mount your zigbee device into the pod, you can do so by adding the following to your values:

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
          - zigbee-controller
```

... where a node with an attached zigbee controller USB device is labeled with `app: zigbee-controller`

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/charts/tree/master/charts/common/)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalVolumeMounts | list | `[]` |  |
| additionalVolumes | list | `[]` |  |
| config.advanced.homeassistant_discovery_topic | string | `"homeassistant"` |  |
| config.advanced.homeassistant_status_topic | string | `"homeassistant/status"` |  |
| config.advanced.last_seen | string | `"ISO_8601"` |  |
| config.advanced.log_level | string | `"info"` |  |
| config.advanced.log_output[0] | string | `"console"` |  |
| config.advanced.network_key | string | `"GENERATE"` |  |
| config.experimental.new_api | bool | `true` |  |
| config.frontend.port | int | `8080` |  |
| config.homeassistant | bool | `false` |  |
| config.mqtt.base_topic | string | `"zigbee2mqtt"` |  |
| config.mqtt.include_device_information | bool | `true` |  |
| config.mqtt.server | string | `"mqtt://localhost"` |  |
| config.permit_join | bool | `true` |  |
| config.serial | string | `nil` |  |
| env.ZIGBEE2MQTT_DATA | string | `"/data"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"koenkk/zigbee2mqtt"` |  |
| image.tag | string | `"1.17.1"` |  |
| ingress.enabled | bool | `false` |  |
| persistence.data.emptyDir | bool | `false` |  |
| persistence.data.enabled | bool | `false` |  |
| persistence.data.mountPath | string | `"/data"` |  |
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
