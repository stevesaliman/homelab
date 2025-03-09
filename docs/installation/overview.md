# Overview

This is a basic overview of the process.

## 1. From the bare metal
Running `make boot` does the following:

1. Run Ansible with `metal/boot.yml` to download an OS image, start up a PXE server (dnsmasq), send
  a wake signal to the hosts from `metal/inventories/prod.yml`, and wait for them to become
  available, as they install the OS, or simply boot.

