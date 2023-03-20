# ClearML Kubernetes Serving

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.2.0](https://img.shields.io/badge/AppVersion-1.2.0-informational?style=flat-square)

ClearML Serving Helm Chart

**Homepage:** <https://clear.ml>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| valeriano-manassero |  | <https://github.com/valeriano-manassero> |

## Introduction

The **clearml-serving** is the Kubernetes serving for for [ClearML](https://github.com/allegroai/clearml-serving).
It allows you to serve mopdels on a Kubernetes cluster.

# Upgrading Chart

## Upgrades/ Values upgrades

Updating to latest version of this chart can be done in two steps:

```
helm repo update
helm upgrade clearml-serving allegroai/clearml-serving
```

Changing values on existing installation can be done with:

```
helm upgrade clearml-serving allegroai/clearml-serving --version <CURRENT CHART VERSION> -f custom_values.yaml
```

## Source Code

* <https://github.com/allegroai/clearml-helm-charts>
* <https://github.com/allegroai/clearml>

## Requirements

Kubernetes: `>= 1.21.0-0 < 1.27.0-0`

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | kafka | 21.4.0 |
| https://grafana.github.io/helm-charts | grafana | 6.52.3 |
| https://prometheus-community.github.io/helm-charts | prometheus | 19.7.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| clearml | object | `{"apiAccessKey":"ClearML API Access Key","apiHost":"http://clearml-server-apiserver:8008","apiSecretKey":"ClearML API Secret Key","defaultBaseServeUrl":"http://127.0.0.1:8080/serve","filesHost":"http://clearml-server-fileserver:8081","servingTaskId":"ClearML Serving Task ID","webHost":"http://clearml-server-webserver:80"}` | ClearMl generic configurations |
| clearml_serving_inference | object | `{"affinity":{},"autoscaling":{"enabled":false,"maxReplicas":11,"minReplicas":1,"targetCPU":50,"targetMemory":50},"extraPythonPackages":[],"image":{"repository":"allegroai/clearml-serving-inference","tag":"1.2.0"},"ingress":{"annotations":{},"enabled":false,"hostName":"serving.clearml.127-0-0-1.nip.io","ingressClassName":"","path":"/","tlsSecretName":""},"nodeSelector":{},"resources":{},"tolerations":[]}` | ClearML serving inference configurations |
| clearml_serving_inference.affinity | object | `{}` | Affinity configuration |
| clearml_serving_inference.autoscaling | object | `{"enabled":false,"maxReplicas":11,"minReplicas":1,"targetCPU":50,"targetMemory":50}` | Autoscaling configuration |
| clearml_serving_inference.extraPythonPackages | list | `[]` | Extra Python Packages to be installed in running pods |
| clearml_serving_inference.image | object | `{"repository":"allegroai/clearml-serving-inference","tag":"1.2.0"}` | Container Image |
| clearml_serving_inference.ingress | object | `{"annotations":{},"enabled":false,"hostName":"serving.clearml.127-0-0-1.nip.io","ingressClassName":"","path":"/","tlsSecretName":""}` | Ingress exposing configurations |
| clearml_serving_inference.ingress.annotations | object | `{}` | Ingress annotations |
| clearml_serving_inference.ingress.enabled | bool | `false` | Enable/Disable ingress |
| clearml_serving_inference.ingress.hostName | string | `"serving.clearml.127-0-0-1.nip.io"` | Ingress hostname domain |
| clearml_serving_inference.ingress.ingressClassName | string | `""` | ClassName (must be defined if no default ingressClassName is available) |
| clearml_serving_inference.ingress.path | string | `"/"` | Ingress root path url |
| clearml_serving_inference.ingress.tlsSecretName | string | `""` | Reference to secret containing TLS certificate. If set, it enables HTTPS on ingress rule. |
| clearml_serving_inference.nodeSelector | object | `{}` | Node Selector configuration |
| clearml_serving_inference.resources | object | `{}` | Pod resources definition |
| clearml_serving_inference.tolerations | list | `[]` | Tolerations configuration |
| clearml_serving_statistics | object | `{"affinity":{},"extraPythonPackages":[],"image":{"repository":"allegroai/clearml-serving-statistics","tag":"1.2.0"},"nodeSelector":{},"resources":{},"tolerations":[]}` | ClearML serving statistics configurations |
| clearml_serving_statistics.affinity | object | `{}` | Affinity configuration |
| clearml_serving_statistics.extraPythonPackages | list | `[]` | Extra Python Packages to be installed in running pods |
| clearml_serving_statistics.image | object | `{"repository":"allegroai/clearml-serving-statistics","tag":"1.2.0"}` | Container Image |
| clearml_serving_statistics.nodeSelector | object | `{}` | Node Selector configuration |
| clearml_serving_statistics.resources | object | `{}` | Pod resources definition |
| clearml_serving_statistics.tolerations | list | `[]` | Tolerations configuration |
| clearml_serving_triton | object | `{"affinity":{},"autoscaling":{"enabled":false,"maxReplicas":11,"minReplicas":1,"targetCPU":50,"targetMemory":50},"enabled":true,"extraPythonPackages":[],"image":{"repository":"allegroai/clearml-serving-triton","tag":"1.2.0-22.07"},"ingress":{"annotations":{},"enabled":false,"hostName":"serving-grpc.clearml.127-0-0-1.nip.io","ingressClassName":"","path":"/","tlsSecretName":""},"nodeSelector":{},"resources":{},"tolerations":[]}` | ClearML serving Triton configurations |
| clearml_serving_triton.affinity | object | `{}` | Affinity configuration |
| clearml_serving_triton.autoscaling | object | `{"enabled":false,"maxReplicas":11,"minReplicas":1,"targetCPU":50,"targetMemory":50}` | Autoscaling configuration |
| clearml_serving_triton.enabled | bool | `true` | Triton pod creation enable/disable |
| clearml_serving_triton.extraPythonPackages | list | `[]` | Extra Python Packages to be installed in running pods |
| clearml_serving_triton.image | object | `{"repository":"allegroai/clearml-serving-triton","tag":"1.2.0-22.07"}` | Container Image |
| clearml_serving_triton.ingress | object | `{"annotations":{},"enabled":false,"hostName":"serving-grpc.clearml.127-0-0-1.nip.io","ingressClassName":"","path":"/","tlsSecretName":""}` | Ingress exposing configurations |
| clearml_serving_triton.ingress.annotations | object | `{}` | Ingress annotations |
| clearml_serving_triton.ingress.enabled | bool | `false` | Enable/Disable ingress |
| clearml_serving_triton.ingress.hostName | string | `"serving-grpc.clearml.127-0-0-1.nip.io"` | Ingress hostname domain |
| clearml_serving_triton.ingress.ingressClassName | string | `""` | ClassName (must be defined if no default ingressClassName is available) |
| clearml_serving_triton.ingress.path | string | `"/"` | Ingress root path url |
| clearml_serving_triton.ingress.tlsSecretName | string | `""` | Reference to secret containing TLS certificate. If set, it enables HTTPS on ingress rule. |
| clearml_serving_triton.nodeSelector | object | `{}` | Node Selector configuration |
| clearml_serving_triton.resources | object | `{}` | Pod resources definition |
| clearml_serving_triton.tolerations | list | `[]` | Tolerations configuration |
| grafana | object | `{"adminPassword":"clearml","adminUser":"admin","datasources":{"datasources.yaml":{"apiVersion":1,"datasources":[{"access":"proxy","isDefault":true,"name":"Prometheus","type":"prometheus","url":"http://{{ .Release.Name }}-prometheus-server"}]}},"enabled":true}` | Configuration from https://github.com/grafana/helm-charts/blob/main/charts/grafana/values.yaml |
| kafka | object | `{"enabled":true}` | Configuration from https://github.com/bitnami/charts/blob/main/bitnami/kafka/values.yaml |
| prometheus | object | `{"enabled":true,"extraScrapeConfigs":"- job_name: \"{{ .Release.Name }}-stats\"\n  static_configs:\n    - targets:\n      - \"{{ .Release.Name }}-statistics:9999\"\n","kube-state-metrics":{"enabled":false},"prometheus-node-exporter":{"enabled":false},"prometheus-pushgateway":{"enabled":false},"serverFiles":{"prometheus.yml":{"scrape_configs":[{"job_name":"prometheus","static_configs":[{"targets":["localhost:9090"]}]}]}}}` | Configuration from https://github.com/prometheus-community/helm-charts/blob/main/charts/prometheus/values.yaml |