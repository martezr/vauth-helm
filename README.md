# vAuth Helm Chart

This repository contains the official vAuth Helm chart for installing
and configuring vAuth on Kubernetes. This chart supports multiple use
cases of vAuth on Kubernetes depending on the values provided.

## Prerequisites

To use the charts here, [Helm](https://helm.sh/) must be configured for your
Kubernetes cluster. Setting up Kubernetes and Helm and is outside the scope of
this README. Please refer to the Kubernetes and Helm documentation.

The versions required are:

  * **Helm 3.0+** - This is the earliest version of Helm tested. It is possible
    it works with earlier versions but this chart is untested for those versions.
  * **Kubernetes 1.9+** - This is the earliest version of Kubernetes tested.
    It is possible that this chart works with earlier versions but it is
    untested. Other versions verified are Kubernetes 1.10, 1.11.

## Usage
1) Edit `values.yaml` with configuration for the vAuth K8s cluster.
> NB! It's highly recommended to set your own secrets as file contains unsafe defaults like self-signed SSL certificates, SSH keys,

2) Pull 3rd party Helm dependencies:
```
helm dependency update
```

3) Install the chart
```
helm install .
```

4) Upgrade
Once you make any changes to values, upgrade the cluster:
```
helm upgrade <release-name> .
```

## Configuration

The default configuration values for this chart are described in `values.yaml`.

## Ingress

Ingress is worth considering if you want to expose multiple services under the same IP address, and
these services all use the same L7 protocol (typically HTTP). You only pay for one load balancer if
you are using native cloud integration, and because Ingress is "smart", you can get a lot of
features out of the box (like SSL, Auth, Routing, etc.). See the ingress section in `values.yaml`
for configuration details.

You will first need to deploy an ingress controller of your preference. See
https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/#additional-controllers
for more information.

## Components

### [vauth-backend]()

### [vauth-scheduler]()

### [vauth-syncer]()

### [vauth-ui]()

### [vauth-watcher]()

### [vauth-worker]()

### [cockroachdb]()

### [nats]()
