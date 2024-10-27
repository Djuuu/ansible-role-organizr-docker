Ansible Role: Organizr-docker
=============================

Install Organizr Docker Compose project.

- https://docs.organizr.app/
- https://github.com/causefx/Organizr/
- https://github.com/organizr/docker-organizr

Requirements
------------

Requires the following to be installed:
- docker
- docker compose

Role Variables
--------------

Common system variables:

```yaml
timezone: UTC
```

Common Docker projects variables:

```yaml
# Base directory for Docker projects
docker_projects_path: # /var/apps
```

Available role variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Docker project variables

organizr_project_name: organizr

# Main service additional docker-compose options (ex: cpu_shares, deploy, ...)
organizr_compose_service_additional_options: |
  #ports:
  #  - 80:80

organizr_traefik_middlewares:
  - "internal-access@file"


# Organizr project variables

# organizr/organizr image version
organizr_version: latest
```

Dependencies
------------

This role depends on :
- [djuuu.docker_project](https://github.com/Djuuu/ansible-role-docker-project)

Some variables allow integration with:
- [djuuu.traefik_docker](https://github.com/Djuuu/ansible-role-traefik-docker)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: all
  gather_facts: true
  gather_subset:
    - "!all"
    - "!min"
    - user_id

  roles:
    - djuuu.organizr_docker
```

License
-------

Beerware License
