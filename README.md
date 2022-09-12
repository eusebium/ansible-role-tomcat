tomcat
===================

Ansible role to install and configure Apache Tomcat on CentOS/RHEL.


Requirements
------------
* Tomcat supported versions by this role:
  * 7.0
  * 8.0
  * 8.5
  * 9.0 (9.0.1 or later)
* CentOS/RHEL 7,8,9
* SELinux disabled

Installation
------------
```
$ ansible-galaxy install eusebium.tomcat
```

Example Playbook
----------------
```yaml
- hosts: servers
  become: true
  vars:
    tomcat_version: 8.5.23

    tomcat_users:
      - username: "tomcat"
        password: "t3mpp@ssw0rd"
        roles: "tomcat,admin,manager,manager-gui"
      - username: "exampleuser"
        password: "us3rp@ssw0rd"
        roles: "tomcat"
  roles:
    - role: eusebium.tomcat

---

- hosts: all
  become: true
  vars:
    tomcat_instance_prefix: C30-backend
    tomcat_java_version: 11
    tomcat_version: 9.0.65
    tomcat_port_ajp: 8009
    tomcat_port_connector: 8080

  roles:
    - eusebium.tomcat

- hosts: all
  become: true
  vars:
    tomcat_instance_prefix: C30-frontend
    tomcat_java_version: 11
    tomcat_version: 9.0.65
    tomcat_port_ajp: 8010
    tomcat_port_connector: 8081

  roles:
    - eusebium.tomcat

```

Role Variables
--------------

see default/main.yml
