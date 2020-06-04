Symfony chart
=============

This chart bootstraps a Symfony application deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.


## Prerequisites
  - Kubernetes 1.4+ with Beta APIs enabled


## Configuration

The following table lists the configurable parameters of the chart and their default values.

Parameter                  | Description                                                              | Default
-------------------------- | ------------------------------------------------------------------------ | -------
`image.repository`         | container image repository                                               | `nginx`
`image.tag`                | container image tag                                                      | `stable`
`image.pullPolicy`         | container image pull policy                                              | `IfNotPresent`
`image.pullSecrets`        | container image pull secrets                                             |
`service.name`             | name of the service                                                      | `nginx`
`service.type`             | type of the service                                                      | `ClusterIp`
`service.externalPort`     | external port of the service                                             | `80`
`service.internalPort`     | internal port of the service                                             | `80`
`resources`                | resource requests and limits (YAML)                                      | `{}`
`nodeSelector`             | node labels for pod assignment                                           |
`ingress.enabled`          | Either or not the ingress is enabled                                     | `false`
`ingress.hosts`            | Hosts to reach the application                                           | `false`
`ingress.annotations`      | Ingress annotation configuration                                         | `false`
`ingress.tls`              | TLS support                                                              | `false`
`nginx.sourcesPath`        | Path where the Symfony application is located                            | `/var/www/symfony`
`nginx.sourcesDir`         | Directory in sourcesPath where the Symfony application is located        | `public`
`nginx.mainControllerName` | Directory in sourcesPath where the Symfony application is located        | `index`
`nginx.accessLogPath`      | Path where Nginx access_log is located                                   | `/var/log/nginx/access.log`
`nginx.errorLogPath`       | Path where Nginx error_log is located                                    | `/var/log/nginx/error.log`
`nginx.locationParams`     | List of params added to location block in nginx config file              | `[]`
`env.container`            | Environment variables that are passed to the container and the webserver |
`env.initContainer`        | Environment variables that are passed to each initContainer              |
`extraEnv`                 | Add specific environment variable to the container                       | `[]`
`initContainers`           | Allow to configure initContainers for the deployment (YAML)              |
`secrets`                  | Allow to configure secrets (mounted only for now)                        |
`configMap.dollar.enabled` | Allow to pass variable with $ in value                                   | `false`

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,


## Installation

To install the chart with the release name `my-release` and the namespace `prod` using a `values.yaml` file:

```bash
helm install --name my-release --namespace prod suez/symfony -f ./values.yaml
```

```console
$ helm install --name my-release \
  --set image.repository=pathtodockerhub/name/whatever \
    suez/symfony
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
$ helm install --name my-release -f values.yaml suez/kube-lego
```

> **Tip**: You can use the default [values.yaml](values.yaml)


## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.