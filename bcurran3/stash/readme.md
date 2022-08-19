# Ansible-NAS plugin: Stash

Homepage: <Stash is a self-hosted webapp written in Go which organizes and serves your porn.>

[Stash](https://stashapp.cc/)

Stash is a self-hosted webapp written in Go which organizes and serves your porn.
* Stash gathers information about videos in your collection from the internet, and is extensible through the use of community-built plugins for a large number of content producers and sites.
* Stash supports a wide variety of both video and image formats.
* You can tag videos and find them later.
* Stash provides statistics about performers, tags, studios and more.

## Installation and Configuration

1. Clone the plugins repository.
`git clone https://github.com/bcurran3/ansible-nas-plugins.git`

2. Copy the contents of the `ansible-nas-plugins` to your `ansible-nas/plugins` directory. There may be more than one plugin by this developer, you don't need to use them all.

3. If you're installing your first plugin than copy `plugins/sample.yml` to `plugins/plugins.yml`. Edit `plugins.yml` and add:
```
  - import_tasks: plugins/bcurran3/stash/stash.yml
    when: (stash_enabled | default(False))
    tags: stash
```

4. Add the following to your `inventories/<your_inventory>/nas.yml` file and edit per your needs.
```
###
### Stash
###
stash_enabled: true
stash_available_externally: false
stash_data_directory: "{{ docker_home }}/stash"
stash_media_directory: "/media/porn"
stash_http_port: "9999"
stash_memory: "1g"
```

## Usage

Stash's web interface can be found at http://ansible_nas_host_or_ip:9999.
