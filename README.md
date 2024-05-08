# LogScale Vector Demo

This is a quick LAB to install vector agent daemonset, and configure it to ship Kubernetes logs to LogScale

## Installing Local Kubernetes Cluster
Use [Kind](https://kind.sigs.k8s.io/) to install and run local kind cluster
* Download and install kind
* Install the cluster with the default configuration `kind create cluster`

## Installing Vector Agent

* Add Vector Helm repository
```
helm repo add vector https://helm.vector.dev
helm repo update
```

* Install Vector
```
helm install vector vector/vector \
  --namespace vector \
  --create-namespace \
  --values vector-values.yaml
  --set humio.token=<HUMIO_SANDBOX_TOKEN>
```

**Note**
Replace the `HUMIO_SANDBOX_TOKEN` in the above command with the token you get from [LogScale](https://cloud.humio.com/) under sandbox (your personal storage)

## Uninstalling Vector Agent
```
helm uninstall vector --namespace vector
```

