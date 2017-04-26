# Docker Swarm

Installations are based from a base install of the [netinst](https://www.debian.org/releases/stable/debian-installer/) of [Debian](https://www.debian.org/) 8.5 (Jessie)

----

* **[Index Page](README.md)**

* reference: [Swarm Tutorial](https://docs.docker.com/engine/swarm/swarm-tutorial/)


----

## Table of Contents

* [Swarm Member Requirements](#SwarmRequirements)
* [Install Docker](#InstallDocker)
* [Uninstall Docker](#UninstallDocker)

* [Fix the IP addresses](#FixtheIPaddresses)
* [Initiate a Swarm](#InitiateaSwarm)

----

## Swarm Requirements
* manager
* and a minimum of two workers

These machine were placed into their own network within VirtualBox with the following IP addresses


|  Host Name         |   IP Address   |
|-------------------:|----------------|
| docker-manager-vm  | - 192.168.22.2 |
| docker1-vm         | - 192.168.22.3 |
| docker2-vm         | - 192.168.22.4 |
|||

Note that I also added the [Development Machine](DevelopmentMachineInstall.md) to this network, for easy access to the Swarm (192.168.22.5)

### Install Docker

For all three machine

Install the dependances

  `sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common vim-nox`

Add the Docker GPG key

  `curl -fsSL https://apt.dockerproject.org/gpg | sudo apt-key add -`

Add the repository

  `sudo add-apt-repository "deb https://apt.dockerproject.org/repo debian-jessie main"`

  `sudo apt-get update`

and install Docker

  `sudo apt-get -y install docker-engine`


And add your user to the 'docker' group

  `sudo usermod -aG docker $USER`


And start on reboot

  `sudo systemctl enable docker`

----

### Uninstall Docker

Uninstall the Docker package:

  `sudo apt-get purge docker-engine`

Images, containers, volumes, or customized configuration files on your host are not automatically removed. To delete all images, containers, and volumes:

  `sudo rm -rf /var/lib/docker`

You must delete any edited configuration files manually.

----

### Fix the IP addresses

I created a 'Host-Only' network via the VirtualBox interface (192.168.22.0/24) and added the machines to the network by creating this file on each of te machines

  `sudo vi /etc/network/interfaces.d/host-only`

#### Manager


```
# Host-Only network for Docker
auto eth1
 iface eth1 inet static
    address 192.168.22.2
    netmask 255.255.255.0
```
----

#### Worker1

```
# Host-Only network for Docker
auto eth1
 iface eth1 inet static
    address 192.168.22.3
    netmask 255.255.255.0
```

----

#### Worker2


```
# Host-Only network for Docker
auto eth1
 iface eth1 inet static
    address 192.168.22.4
    netmask 255.255.255.0
```


### Initiate a Swarm
Using

docker swarm init --advertise-addr <MANAGER-IP>

in our case
```
keith@docker-manager-vm:~$ docker swarm init --advertise-addr 192.168.22.2
Swarm initialized: current node (y8y8vftmhfoltvja0t7mziokd) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join \
    --token SWMTKN-1-1yf0u2ulkboinf1wkjv7n0pe3nccolip82dz5vtr1p3y62hmyx-aleoyztv2qlc9n84wxdbcr6qu \
    192.168.22.2:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

I then followed the instructions given on each of the worker machines.

Both worker machines responded with

`This node joined a swarm as a worker.`

I confirmed this by running on the manager

`docker node ls`


```
keith@docker-manager-vm:~$ docker node ls
ID                           HOSTNAME           STATUS  AVAILABILITY  MANAGER STATUS
ijfbiz0g4otykoab8k8t6f77p    docker1-vm         Ready   Active
jffgtyggx2z6720vitwtq5bk6    docker2-vm         Ready   Active
y8y8vftmhfoltvja0t7mziokd *  docker-manager-vm  Ready   Active        Leader
```

----

* **[Index Page](README.md)**
