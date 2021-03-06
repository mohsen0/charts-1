# KubeView

[KubeView](https://github.com/benc-uk/kubeview) is a Kubernetes cluster visualiser and graphical explorer.

## TL;DR;

```bash
$ helm repo add cowboysysop https://cowboysysop.github.io/charts/
$ helm install cowboysysop/kubeview
```

## Introduction

This chart bootstraps a KubeView deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.12+
- Helm 2.11+

## Installing

Install the chart using:

```bash
$ helm repo add cowboysysop https://cowboysysop.github.io/charts/
$ helm install --name my-release cowboysysop/kubeview
```

These commands deploy KubeView on the Kubernetes cluster in the default configuration and with the release name `my-release`. The deployment configuration can be customized by specifying the customization parameters with the `helm install` command using the `--values` or `--set` arguments. Find more information in the [configuration section](#configuration) of this document.

## Upgrading

Upgrade the chart deployment using:

```bash
$ helm upgrade my-release cowboysysop/kubeview
```

The command upgrades the existing `my-release` deployment with the most latest release of the chart.

**TIP**: Use `helm repo update` to update information on available charts in the chart repositories.

## Uninstalling

Uninstall the `my-release` deployment using:

```bash
$ helm delete my-release
```

The command deletes the release named `my-release` and frees all the kubernetes resources associated with the release.

**TIP**: Specify the `--purge` argument to the above command to remove the release from the store and make its name free for later use.

## Configuration

The following table lists all the configurable parameters expose by the KubeView chart and their default values.

| Name                                 | Description                                                                                           | Default                                          |
|--------------------------------------|-------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| `replicaCount`                       | Number of replicas                                                                                    | `1`                                              |
| `image.repository`                   | KubeView image name                                                                                   | `bencuk/kubeview`                                |
| `image.tag`                          | KubeView image tag                                                                                    | `0.1.11`                                         |
| `image.pullPolicy`                   | Image pull policy                                                                                     | `IfNotPresent`                                   |
| `imagePullSecrets`                   | Docker registry secret names as an array                                                              | `[]`                                             |
| `nameOverride`                       | Partially override `kubeview.fullname` template with a string (will prepend the release name)         | `nil`                                            |
| `fullnameOverride`                   | Fully override `kubeview.fullname` template with a string                                             | `nil`                                            |
| `serviceAccount.create`              | Specify whether to create a ServiceAccount                                                            | `true`                                           |
| `serviceAccount.annotations`         | ServiceAccount annotations                                                                            | `{}`                                             |
| `serviceAccount.name`                | The name of the ServiceAccount to create                                                              | Generated using the `kubeview.fullname` template |
| `podAnnotations`                     | Additional pod annotations                                                                            | `{}`                                             |
| `podLabels`                          | Additional pod labels                                                                                 | `{}`                                             |
| `podSecurityContext`                 | Pod security context                                                                                  | `{}`                                             |
| `securityContext`                    | Container security context                                                                            | `{}`                                             |
| `livenessProbe.enabled`              | Enable liveness probe                                                                                 | `true`                                           |
| `livenessProbe.initialDelaySeconds`  | Delay before the liveness probe is initiated                                                          | `0`                                              |
| `livenessProbe.periodSeconds`        | How often to perform the liveness probe                                                               | `10`                                             |
| `livenessProbe.timeoutSeconds`       | When the liveness probe times out                                                                     | `1`                                              |
| `livenessProbe.failureThreshold`     | Minimum consecutive failures for the liveness probe to be considered failed after having succeeded    | `3`                                              |
| `livenessProbe.successThreshold`     | Minimum consecutive successes for the liveness probe to be considered successful after having failed  | `1`                                              |
| `readinessProbe.enabled`             | Enable readiness probe                                                                                | `true`                                           |
| `readinessProbe.initialDelaySeconds` | Delay before the readiness probe is initiated                                                         | `0`                                              |
| `readinessProbe.periodSeconds`       | How often to perform the readiness probe                                                              | `10`                                             |
| `readinessProbe.timeoutSeconds`      | When the readiness probe times out                                                                    | `1`                                              |
| `readinessProbe.failureThreshold`    | Minimum consecutive failures for the readiness probe to be considered failed after having succeeded   | `3`                                              |
| `readinessProbe.successThreshold`    | Minimum consecutive successes for the readiness probe to be considered successful after having failed | `1`                                              |
| `service.type`                       | Kubernetes Service type                                                                               | `ClusterIP`                                      |
| `service.port`                       | KubeView service port                                                                                 | `8000`                                           |
| `ingress.enabled`                    | Enable ingress controller resource                                                                    | `false`                                          |
| `ingress.annotations`                | Ingress annotations                                                                                   | `{}`                                             |
| `ingress.hosts[0].name`              | Hostname to your KubeView installation                                                                | `kubeview.local`                                 |
| `ingress.hosts[0].paths`             | Paths within the url structure                                                                        | `[]`                                             |
| `ingress.tls[0].secretName`          | TLS Secret (certificates)                                                                             | `nil`                                            |
| `ingress.tls[0].hosts[0]`            | TLS hosts                                                                                             | `nil`                                            |
| `resources`                          | CPU/Memory resource requests/limits                                                                   | `{}`                                             |
| `nodeSelector`                       | Node labels for pod assignment                                                                        | `{}`                                             |
| `tolerations`                        | Tolerations for pod assignment                                                                        | `[]`                                             |
| `affinity`                           | Map of node/pod affinities                                                                            | `{}`                                             |

Specify the parameters you which to customize using the `--set` argument to the `helm install` command. For instance,

```bash
$ helm install --name my-release \
    --set replicaCount=3 cowboysysop/kubeview
```

The above command sets the `replicaCount` to `3`.

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```bash
$ helm install --name my-release \
    --values values.yaml cowboysysop/kubeview
```

**Tip**: You can use the default [values.yaml](values.yaml).
