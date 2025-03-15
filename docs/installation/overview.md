# Overview

This is a basic overview of the process.

## 1. Get the OS and k3s onto the bare metal
Running `make boot` does the following:

1. Run Ansible with `metal/boot.yml` to download an OS image, start up a PXE server (dnsmasq), send
  a wake signal to the hosts from `metal/inventories/prod.yml`, and wait for them to become
  available, as they install the OS, or simply boot.

2. Run Ansible with `metal/cluster.yml` to download and install k3s and Cilium.  This produces a
  `kubeconfig.yaml` that can be used in `~/.kube/config` to access the cluster.

## 2. Bootstrap the system layer

1. Run Ansible with `system/bootstral.yml` to install and configure Argo.  It runs on localhost
  because it runs the local helm to deploy to the cluster.