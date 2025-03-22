.POSIX:

env ?= prod
export KUBECONFIG = $(shell pwd)/kubeconfig.yaml

default: boot cluster

# Only uncomment this if we need to generate new keys for the cluster.
# ~/.ssh/id_rsa:
# 	ssh-keygen -t rsa -P '' -f "$@"

# Wake up the cluster, but don't do anything else
wake: ~/.ssh/id_rsa
	ansible-playbook \
		--inventory inventories/${env}.yml \
		wake.yml

# Start teh PXE server, then wake the cluster to install the OS.
boot: ~/.ssh/id_rsa
	ansible-playbook \
		--inventory inventories/${env}.yml \
		boot.yml

cluster:
	ansible-playbook \
		--inventory inventories/${env}.yml \
		cluster.yml

console:
	ansible-console \
		--inventory inventories/${env}.yml

# Convenience target to shutdown the cluster
shutdown: ~/.ssh/id_rsa
	ansible-playbook \
		--inventory inventories/${env}.yml \
		shutdown.yml
