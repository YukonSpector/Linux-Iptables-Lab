# Linux-Iptables-Lab

Repo to store lab used to work with iptables.
The following is a list of the tasks to perform in the lab:
1. Add a route to the client to reach 100.100.100.2.
2. Add nat configuration to iptables to reach 100.100.100.1
	* use tcpdump to verify that natting is happening.

## Status

Coming soon.

## Design

![arch](/docs/imgs/Linux-Iptables-Lab_topology.jpg "Lab Topology")

## Requirements
1. Vagrant
2. Ansible

## Usage

### In terminal
1. To bring up the lab run the command
```bash
vagrant up
```
2. To access the instances run the command
```bash
vagrant ssh [instanceName]
```

## To-Do
* ~~Add playbook to set the nater instance kernel to forward by default.~~
