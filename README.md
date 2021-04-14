software
=========

Install software packages with default operating system package manager.

Requirements
------------

* [ansible.builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)
  * [dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)
  * [apt](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)

Role Variables
--------------

* defaults

  ```yaml
  software_pkgs: []     # list of software to manage
  - name: []            # list of packages names to install or remove
    state:              # as in ansible modules
    autoremove: bool    # remove also obsolete packages
    update_cache: bool  # update package list from configured repo
  ```

Dependencies
------------

This role has no dependencies. But it is frequently used as dependency in other roles.

Example Playbook
----------------

* playbook usage

  ```yaml
  - hosts: servers
    gather_facts: yes  # to determine ansible_os_family
    roles:
    - role: software
  ```

* role dependency usage

  ```yaml
  - dependencies:
    roles:
    - role: software
      software_pkgs: "{{ role_pkgs }}"
  ```

License
-------

BSD

Author Information
------------------

[mario.slowinski@gmail.com](mailto:mario.slowinski@gmail.com)
