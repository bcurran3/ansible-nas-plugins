# Ansible-NAS plugin: Cleanup

Homepage: <https://github.com/bcurran3/ansible-nas-plugins/tree/main/bcurran3/cleanup>

Cleanup is a plugin to stop and remove any Docker containers that are running after you've disabled them via `<appname>_enabled: true`. Apps that you are no longer running will have their Docker containers stopped and removed.

## Configuration

1. From the same directory you cloned Ansible-NAS, clone the plugsins.
`git clone https://github.com/bcurran3/ansible-nas-plugins.git`

2. Copy the contents of the `ansible-nas-plugins` to your `ansible-nas/plugins` directory. This will copy all plugins in the repository but you don't need to enable or use them all.

3. If this is the first plugin you've installed than copy `plugins/sample.yml` to `plugins/plugins.yml`. Edit `samples.yml` and add **at the bottom**:
```
  - import_tasks: plugins/bcurran3/cleanup/cleanup.yml
    when: (cleanup_enabled | default(False))
    tags: cleanup
```

4. Add `cleanup_enabled: true` to your `inventories/<your_inventory>/nas.yml` file.

## Usage

Run your Ansible-NAS playbook as usual after installing or run with `--tags cleanup`
