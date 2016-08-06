Volumes
=======

An Ansible Role that mounts volumes and devices into GNU/Linux systems.

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    volumes_defaults:
      fstype: ext4
      opts: noatime,errors=remount-ro
      dump: 0
      passno: 2
      state: mounted
      fstab: /etc/fstab

This properties set the default values for the volumes of the list that does not override them explicitly.

    volumes:
      - dev: /dev/sda1
        mount_point: /data
        fstype: ext4
        opts: noatime,errors=remount-ro
        dump: 0
        passno: 2
        state: mounted
        fstab:/etc/fstab

List of volumes or devices that should be mounted. Each element must define at least `dev` and `mount_point` properties. The other properties would be set to the default value if they are not defined. They correspond to the options of the [`mount` module](https://docs.ansible.com/ansible/mount_module.html)

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: vps
      roles:
        - role: gcoop-libre.volumes
          volumes:
            - dev: /dev/vda
              mount_point: /data

License
-------

GPLv2

Author Information
------------------

This role was created in 2016 by [gcoop Cooperativa de Software Libre](http://gcoop.coop).
