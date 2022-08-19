# Ansible-NAS plugin: Karaoke-Forever

Homepage     : https://www.karaoke-forever.com/  
Container    : https://github.com/david510c/Karaoke-Forever  
Documentation: https://www.karaoke-eternal.com/docs/  
Description  :  

Host awesome karaoke parties where everyone can easily find and queue songs from their phone's browser. The player is also fully browser-based with support for MP3+G, MP4 videos and WebGL visualizations. The server is self-hosted and runs on nearly everything.

# This will be replaced with the newer Karaoke Eternal

## Installation and Configuration

1. Clone the plugins repository.
`git clone https://github.com/bcurran3/ansible-nas-plugins.git`

2. Copy the contents of the `ansible-nas-plugins` to your `ansible-nas/plugins` directory. There may be more than one plugin by this developer, you don't need to use them all.

3. <ins>If</ins> you're installing your first plugin, then copy `plugins/sample.yml` to `plugins/plugins.yml`.

4. Edit `plugins/plugins.yml` and add:
```
  - import_tasks: plugins/bcurran3/karaoke-forever/karaoke-forever.yml
    when: (karaokeforever_enabled | default(False))
    tags: karaokeforever
```

5. Add the following to your `inventories/<your_inventory>/nas.yml` file and edit per your needs.
```
###
### Karaoke-Forever
###
karaokeforever_enabled: true
karaokeforever_available_externally: false
karaokeforever_memory: "512m"
karaokeforever_port_http: "8095"
karaokeforever_cdgfiles: "{{ music_root }}/karaoke"
```

## Usage

Karaoke-Forever's web interface can be found at http://ansible_nas_host_or_ip:8095.
