# Ansible-NAS plugin: Ghost

Homepage     : https://github.com/TryGhost/Ghost  
Container    : https://hub.docker.com/_/ghost  
Documentation: https://forum.ghost.org/  
Description  :  

Ghost is a free and open source blogging platform written in JavaScript and distributed under the MIT License, designed to simplify the process of online publishing for individual bloggers as well as online publications.

## Installation and Configuration

1. Clone the plugins repository.
`git clone https://github.com/bcurran3/ansible-nas-plugins.git`

2. Copy the contents of the `ansible-nas-plugins` to your `ansible-nas/plugins` directory. There may be more than one plugin by this developer, you don't need to use them all.

3. <ins>If</ins> you're installing your first plugin, then copy `plugins/sample.yml` to `plugins/plugins.yml`.

4. Edit `plugins/plugins.yml` and add:
```
  - role: plugins/bcurran3/ghost
    tags:
      - ghost
    when: (ghost_enabled | default(False))
```

5. Add the following to your `inventories/<your_inventory>/nas.yml` file to enable Ghost.
```
ghost_enabled: true
```

## Usage

Ghost's web interface can be found at http://ansible_nas_host_or_ip:2368.
