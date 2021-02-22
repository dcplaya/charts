<<<<<<< HEAD
# A tool to get statistics from Uptime Robot and log it into InfluxDB

![Screenshot](https://raw.githubusercontent.com/billimek/node-influx-uptimerobot/master/docs/dashboard.png)

This tool allows you to run periodic uptimerobot data usage checks and save the results to Influxdb

## TL;DR;

```console
$ helm repo add k8s-at-home https://k8s-at-home.com/charts/
$ helm install k8s-at-home/uptimerobot
```

## Introduction

This code is adopted from [this original repo](https://github.com/trojanc/node-influx-uptimerobot)

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release k8s-at-home/uptimerobot
```
## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The configuration is set as a block of text through a configmap and mounted as a file in /src/config.ini Any value in this text block should match the defined uptimerobot configuration. There are several values here that will have to match our kubernetes configuration.

## Configuration

The following tables lists the configurable parameters of the Sentry chart and their default values.

| Parameter                            | Description                                  | Default                                                    |
| -------------------------------      | -------------------------------              | ---------------------------------------------------------- |
| `image.repository`                   | uptimerobot image                            | `billimek/uptimerobotusage-for-influxdb`                   |
| `image.tag`                          | uptimerobot image tag                        | `latest`                                                   |
| `image.pullPolicy`                   | uptimerobot image pull policy                | `IfNotPresent`                                             |
| `delay`                              | number of seconds to wait between collections | `300`                                                     |
| `config.influxdb.host`               | InfluxDB hostname                            | `influxdb-influxdb`                                        |
| `config.influxdb.port`               | InfluxDB port                                | `8086`                                                     |
| `config.influxdb.database`           | InfluxDB database                            | `uptimerobot`                                              |
| `config.influxdb.protocol`           | InfluxDB protocol                            | `http`                                                     |
| `config.influxdb.username`           | InfluxDB username                            | ``                                                         |
| `config.influxdb.password`           | InfluxDB password                            | ``                                              |
| `config.uptimerobot.apikey`          | uptimerobot API key (REQUIRED)               | `someapikey`                                               |
| `podAnnotations`                     | Key-value pairs to add as pod annotations    | `{}` |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install --name my-release \
  --set config.uptimerobot.apikey=thisismyapikey \
    k8s-at-home/uptimerobot
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install --name my-release -f values.yaml k8s-at-home/uptimerobot
```

Read through the [values.yaml](https://github.com/k8s-at-home/charts/blob/master/charts/uptimerobot/values.yaml) file. It has several commented out suggested values.
=======
# uptimerobot

![Version: 3.0.0](https://img.shields.io/badge/Version-3.0.0-informational?style=flat-square) ![AppVersion: 1.1.0](https://img.shields.io/badge/AppVersion-1.1.0-informational?style=flat-square)

A tool to get statistics from Uptime Robot and log it into InfluxDB

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/uptimerobot>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| billimek | jeff@billimek.com |  |

## Source Code

* <https://github.com/trojanc/node-influx-uptimerobot>
* <https://github.com/k8s-at-home/charts>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| config.influxdb.database | string | `"uptimerobot"` |  |
| config.influxdb.host | string | `"influxdb-influxdb"` |  |
| config.influxdb.port | int | `8086` |  |
| config.influxdb.protocol | string | `"http"` |  |
| config.uptimerobot.apikey | string | `"someapikey"` |  |
| delay | int | `300` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"billimek/node-influx-uptimerobot"` |  |
| image.tag | string | `"latest"` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
>>>>>>> upstream/master
