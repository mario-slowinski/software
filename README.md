software
=========

Install software packages with default operating system package manager.

Requirements
------------

* [ansible.builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)
  * [dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)
  * [apt](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)
* [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/)
  * [pkg5](https://docs.ansible.com/ansible/latest/collections/community/general/pkg5_module.html)

Role Variables
--------------

* defaults

  ```yaml
  software_pkgs: []       # list of software to manage
  - name: []              # list of packages names to install or remove
    state: ""             # as in ansible modules
    autoremove: bool      # remove also obsolete packages
    update_cache: bool    # update package list from configured repo
    accept_licenses: bool # accept pkg5 package licenses
  ```

Dependencies
------------

This role has no dependencies. But it is frequently used as dependency in other roles.

Example Playbook
----------------

* `requirements.yml`

  ```yaml
  - name: software
    src: mario_slowinski.software
  ```

* playbook usage

  ```yaml
  - hosts: servers
    gather_facts: yes  # to determine ansible_os_family
    roles:
      - role: software
  ```

* role dependency usage

  ```yaml
  dependencies:
    - name: software
      src: mario_slowinski.software
      software_pkgs: "{{ <role>_pkgs }}"
  ```

License
-------

[GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.html)

Author Information
------------------

[mario.slowinski@gmail.com](mailto:mario.slowinski@gmail.com)
