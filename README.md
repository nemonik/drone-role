# Drone CI Server Ansible role

![Basic role syntax check](https://github.com/nemonik/drone-role/workflows/Basic%20role%20syntax%20check/badge.svg)

An Ansible role for ensuring the configuration of [Drone CI](https://drone.io/).

## Requirements

Requires Docker, private Docker Registry, Docker Compose and GitLab installed.

## Role Variables

| Variable                | Required | Default     | Choices       | Comments                                         |
|-------------------------|----------|-------------|---------------|--------------------------------------------------|
| docker_timeout          | yes      | 300         | Integer value | Number of seconds before docker pull timeout     |
| docker_retries          | yes      | 60          | Integer value | Number of tries for docker pull                  |
| docker_delay            | yes      | 10          | Integer value | Delay in seconds between pull retries            |
| default_retries         | yes      | 60          | Integer value | Default number of retries                        |
| default_delay           | yes      | 60          | Integer value | Default delay in seconds between retries         |
| drone_port              | yes      | 80          | Integer value | Port to listen on                                |
| registry_host           | yes      | not defined | String value  | IP address of private Docker registry            |
| registry_port           | yes      | not defined | Integer value | Port the private Docker registry listens on      |
| images_cache_path       | no       | not defined | Path          | Path to folder used to cache saved Docker images |
| cache_container_timeout | no       | 300 seconds | Integer value | Number of seconds before Ansible times out       |

## Example Playbook

An example can be found used in my Hands-on DevOps course's [ansible/master-playbook.yml](https://github.com/nemonik/hands-on-DevOps/blob/master/ansible/master-playbook.yml).

```
- hosts: masters
  remote_user: vagrant
  roles:
    - common
    - docker
    - docker-compose
    - docker-registry
    - k3s-server
    - metallb
    - gitlab
    - drone
```

The above Ansible playbook uses my 

- [Common role](https://github.com/nemonik/common-role) to configure the instance past the base CentOS 7, Alpine 3.10 or Ubuntu Bionic image
- [Docker role](https://github.com/nemonik/docker-role) to install and configure Docker
- [Docker-compose role](https://github.com/nemonik/docker-compose-role) to install Docker-compose
- [Docker Registry role](https://github.com/nemonik/docker-registry-role) to install a private Docker registry
- [K3s-server role](https://github.com/nemonik/k3s-server-role) to install Lightweight Kubernetes (K3s)
- [metallb role](https://github.com/nemonik/metallb-role) to install MetalLB 
- [GitLab role](https://github.com/nemonik/gitlab-role) to install GitLab
- [This role](https://github.com/nemonik/drone-role) to install Drone CI

For more information and to see this role put into action checkout my [Hands-on DevOps class](https://github.com/nemonik/hands-on-DevOps) project.

## License

3-Clause BSD License

## Author Information

Michael Joseph Walsh <mjwalsh@nemonik.com>


