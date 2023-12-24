# Ansible role [gitlab_runner](https://galaxy.ansible.com/ui/standalone/roles/buluma/gitlab_runner/documentation)

Install and configure gitlab-runner on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-gitlab_runner/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-gitlab_runner/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-gitlab_runner.svg)](https://github.com/buluma/ansible-role-gitlab_runner/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-gitlab_runner.svg)](https://github.com/buluma/ansible-role-gitlab_runner/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-gitlab_runner.svg)](https://github.com/buluma/ansible-role-gitlab_runner/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/gitlab_runner)](https://galaxy.ansible.com/ui/standalone/roles/buluma/gitlab_runner/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-gitlab_runner/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.gitlab_runner
      gitlab_runner_tags:
        - docker
        - my_runner
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-gitlab_runner/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-gitlab_runner/blob/master/defaults/main.yml):

```yaml
---
# defaults file for gitlab_runner

# These are the setting you need to register a runner.
# gitlab_runner_registration_token: "123ABC"

# The name as shown in the GitLab webinterface.
gitlab_runner_name: "{{ ansible_fqdn }}"

# The URL to register the runner to.
gitlab_runner_url: "https://gitlab.com/"

# The list of tags.
gitlab_runner_tags: []

# The type of executor. Choose from: "ssh", "shell", "parallels", "virtualbox",
# "docker", "docker_machine", "kubernetes" or "custom"
gitlab_runner_executor: docker

# The docker image to run.
gitlab_runner_docker_image: "alpine:latest"

# The version of the GitLab runner to install.
gitlab_runner_version: "16.3.1"

# Set the amount of concurrent jobs.
gitlab_runner_concurrency: "{{ ansible_processor_vcpus }}"

# Activate or deactivate privileged runner
gitlab_runner_privileged: true
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-gitlab_runner/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-gitlab_runner/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|8, 9|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|bionic, focal|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-gitlab_runner/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-gitlab_runner/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-gitlab_runner/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)


Template inspired by [Robert de Bock](https://github.com/robertdebock)
