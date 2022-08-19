# Ansible-NAS plugin: Cleanup

Homepage: <https://github.com/bcurran3/ansible-nas-plugins/tree/main/bcurran3/cleanup>

Cleanup is a plugin I wrote to stop and remove any Docker containers that are still running after you've changed `<appname>_enabled: true` to `<appname>_enabled: false`. These app will have their Docker containers stopped and removed.

## Installation and Configuration

1. Clone the plugins repository.
`git clone https://github.com/bcurran3/ansible-nas-plugins.git`

2. Copy the contents of the `ansible-nas-plugins` to your `ansible-nas/plugins` directory. There may be more than one plugin by this developer, you don't need to use them all.

3. If you're installing your first plugin than copy `plugins/sample.yml` to `plugins/plugins.yml`. Edit `plugins.yml` and add:
```
  - import_tasks: plugins/bcurran3/cleanup/cleanup.yml
    when: (cleanup_enabled | default(False))
    tags: cleanup
```
NOTE: For Cleanup to work correctly, you want to make sure it's always the last entry in your `plugins/plugins.yml` file.

4. Add `cleanup_enabled: true` to your `inventories/<your_inventory>/nas.yml` file.

## Usage

Run your Ansible-NAS playbook as usual after installing or run with `--tags cleanup`
