# CentOS 8.x Ansible Test Image

[![Docker Automated build](https://img.shields.io/docker/automated/v0rts/docker-centos8-ansible.svg?maxAge=2592000)](https://hub.docker.com/r/v0rts/docker-centos8-ansible/)
[![Docker Automated build](https://img.shields.io/docker/pulls/v0rts/docker-centos8-ansible.svg?maxAge=2592000)](https://hub.docker.com/r/v0rts/docker-centos8-ansible/)
[![Docker Automated build](https://img.shields.io/docker/stars/v0rts/docker-centos8-ansible.svg?maxAge=2592000)](https://hub.docker.com/r/v0rts/docker-centos8-ansible/)

CentOS 8.x Docker container for Ansible playbook and role testing.

## How to Build

This image is built on Docker Hub automatically any time the upstream OS container is rebuilt, and any time a commit is made or merged to the `master` branch. But if you need to build the image on your own locally, do the following:

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. `cd` into this directory.
  3. Run `docker build -t centos8-ansible .`

## How to Use

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. Pull this image from Docker Hub: `docker pull v0rts/docker-centos8-ansible:latest` (or use the tag you built earlier, e.g. `centos8-ansible`).
  3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro v0rts/docker-centos8-ansible:latest /usr/lib/systemd/systemd` (to test my Ansible roles, I add in a volume mounted from the current working directory with ``--volume=`pwd`:/etc/ansible/roles/role_under_test:ro``).
  4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

## Notes



## Author

Modified and maintained by v0rts
Created in 2016 by [Jeff Geerling](http://jeffgeerling.com/) 
