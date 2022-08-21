# Ansible-NAS plugin: Osclass

Homepage     : https://osclass-classifieds.com/  
Container    : https://hub.docker.com/r/bitnami/osclass / https://github.com/bitnami/bitnami-docker-osclass  
Documentation: https://docs.bitnami.com/installer/apps/osclass/  
Description  :  

Osclass is your one-stop shop to building your own classifieds website. Create a site with car classifieds, rentals, real estate ads, job listings or just create a general classifieds for free with our open-source CMS. With many themes and plugins, Osclass is easy to customize. Start your business now with Osclass, it's so simple!

## Installation and Configuration

1. Clone the plugins repository.
`git clone https://github.com/bcurran3/ansible-nas-plugins.git`

2. Copy the contents of the `ansible-nas-plugins` to your `ansible-nas/plugins` directory. There may be more than one plugin by this developer, you don't need to use them all.

3. <ins>If</ins> you're installing your first plugin, then copy `plugins/sample.yml` to `plugins/plugins.yml`.

4. Edit `plugins/plugins.yml` and add:
```
  - import_tasks: plugins/bcurran3/osclass/osclass.yml
    when: (osclass_enabled | default(False))
    tags: osclass
```

5. Add the following to your `inventories/<your_inventory>/group_vars/nas.yml` file and edit per your needs.
```
###
### osclass
###
osclass_enabled: true
osclass_available_externally: false
osclass_data_directory: "{{ docker_home }}/osclass"
osclass_memory: "1g"
osclass_port: "8091"
osclass_hostname: "classifieds"
osclass_admin_password: "topsecret"
osclass_web_title: "{{ ansible_nas_domain }} Classifieds"
```

## Usage

Osclass's web interface can be found at http://ansible_nas_host_or_ip:8091.
