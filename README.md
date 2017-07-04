Universal Tomcat
=========

[![Build Status](https://travis-ci.org/ChristopherDavenport/ansible-role-universal-tomcat.svg?branch=master)](https://travis-ci.org/ChristopherDavenport/ansible-role-universal-tomcat)

This is a system for installing and managing tomcat configurations.

Requirements
------------

Role Dependencies

Role Variables
--------------

```yaml
# defaults file for universal-tomcat

# Tomcat versions available
# 6.0.47
# 7.0.72
# 8.0.38
# 8.5.6
# 9.0.0.M11

tomcat_version: "8.5.6"

tomcat_mirrors:
  - http://archive.apache.org/dist/tomcat

# Temporary Storage Directory
tomcat_tmp_storage: /tmp/tomcat-ansible

tomcat_user_name: tomcat
tomcat_user_group: tomcat
tomcat_user_home: /home/{{ tomcat_user_name }}
tomcat_user_system: false

tomcat_port_shutdown: 8005
tomcat_port_connector: 8080
tomcat_port_redirect: 8443
tomcat_port_ajp: 8009

tomcat_java_opts: ""
tomcat_catalina_opts: ""

tomcat_base_dir: /opt
tomcat_catalina_home: "{{ tomcat_base_dir }}/tomcat"
tomcat_instance_path: "{{ tomcat_base_dir }}/tomcat"

tomcat_prefer_ipv4: true
tomcat_override_uri_encoding: ""
tomcat_prefer_urandom: true

tomcat_instance: tomcat

tomcat_roles:
  - manager
  - manager-gui
  - manager-script
  - manager-jmx
  - admin
  - admin-gui
  - admin-script

tomcat_users: []
  # - name: tomcat
  #   password: tomcat
  #   roles: "manager-gui,admin-gui"
  #

# This Edits And Allows Ansible To Configure These
# Otherwise it does a default install
tomcat_configure: true
tomcat_configure_configs: "{{ tomcat_configure }}"
tomcat_configure_libs: "{{ tomcat_configure }}"
tomcat_configure_webapps: "{{ tomcat_configure }}"

# These copy files across and will use basename
tomcat_extra_libs_path: ""
tomcat_webapps_path: []

# Strings That Allow you to modify your
# tomcat instance in a predictable fashion.
tomcat_extra_global_naming_resources: ""
tomcat_context_xml_header_extra: ""
tomcat_context_xml_extra: ""


# Disable or enable session persistence
tomcat_disable_persistence_across_restarts: false

# Custom Configuration Files
# Use these to use custom xml files
tomcat_use_custom_server_xml: false
# tomcat_custom_server_xml: Path
tomcat_use_custom_web_xml: false
# tomcat_custom_web_xml: Path
tomcat_use_custom_context_xml: false
# tomcat_custom_context_xml: Path
tomcat_use_custom_tomcat_users_xml: false
# tomcat_custom_tomcat_users_xml: Path
tomcat_use_custom_manager_context_xml: false
# tomcat_custom_manager_context_xml: Path
```


Dependencies
------------

[ChristopherDavenport.universal-java](https://github.com/ChristopherDavenport/ansible-role-universal-java)


Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - role: ChristopherDavenport.universal-tomcat
       become: yes
```

License
-------

MIT

Author Information
------------------

This role was created in 2016 by [ChristopherDavenport](https://github.com/ChristopherDavenport).
