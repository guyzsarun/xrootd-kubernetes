# xrootd-kubernetes

[![pipeline](https://github.com/guyzsarun/xrootd-kubernetes/actions/workflows/main.yaml/badge.svg)](https://github.com/guyzsarun/xrootd-kubernetes/actions/workflows/main.yaml)

[XRootD](https://xrootd.slac.stanford.edu/) on Kubernetes, containing kubernetes manifests, example configurations and helmchart for deploying XRootD cluster ( manager and server )

## Building the image
```
docker build -f docker/Dockerfile .

or 

docker pull ghcr.io/guyzsarun/xrootd-kubernetes:5.6.1-1
```

## Installation

Update the number of xrootd-server in helm `values.yaml`

```
helm install xrootd-cluster -f values.yaml .
```

