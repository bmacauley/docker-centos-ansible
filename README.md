CentOS 7.x Ansible Test Image
=============================
![Build Status](https://img.shields.io/docker/automated/jrottenberg/ffmpeg.svg)

CentOS 7.x Docker container for Ansible playbook and role testing

How to Build
------------
This image is built on Docker Hub automatically any time the upstream base OS container is rebuilt, and any time a commit is made or merged to the master branch. But if you need to build the image on your own locally, do the following:

1. [Install Docker](https://docs.docker.com/engine/installation/)
2. `cd` into this directory.
3. Run `docker build -t centos7-ansible`

How to use
----------
1. [Install Docker](https://docs.docker.com/engine/installation/)
2. Pull this image from Docker Hub: `docker pull bmacauley/docker-centos7-ansible:latest` (or use the tag you built earlier, e.g. centos7-ansible).
3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro bmacauley/docker-centos7-ansible:latest /usr/lib/systemd/systemd` (to test my Ansible roles, I add in a volume mounted from the current working directory with --volume=`pwd`:/etc/ansible/roles/role_under_test:ro).
4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

Author
-------
Brian Macauley

Heavily based on  [geerlingguy/docker-centos7-ansible](https://github.com/geerlingguy/docker-centos7-ansible)