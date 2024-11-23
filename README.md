Ansible role: needrestart
=========================

Installs needrestart and allows configuration of
/etc/needrestart/conf.d/*.conf, /etc/needrestart/notify.d/ and /etc/needrestart/restart.d/.

Role Variables
--------------

```
ENTRY POINT: *main* - Install and configure needrestart

          Installs needrestart and allows configuration of
          /etc/needrestart/conf.d/*.conf, /etc/needrestart/notify.d/
          and /etc/needrestart/restart.d/.

Options (= indicates it is required):

- needrestart_conf_d  List of conf.d configuration files to create
          default: []
          elements: dict
          type: list
          options:

          = config            Contents of the conf.d configuration file
            type: str

          = name            Name of the conf.d configuration file
            type: str

- needrestart_notify_d  List of notify.d configuration files to create
          default: []
          elements: dict
          type: list
          options:

          = config            Contents of the notify.d configuration file
            type: str

          = name            Name of the notify.d configuration file
            type: str

- needrestart_restart_d  List of restart.d configuration files to create
          default: []
          elements: dict
          type: list
          options:

          = config            Contents of the restart.d configuration file
            type: str

          = name            Name of the restart.d configuration file
            type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/needrestart,main,wandansible.needrestart
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.needrestart
      src: https://github.com/wandansible/needrestart

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: all
      roles:
         - role: wandansible.needrestart
           become: true
           vars:
             needrestart_conf_d:
               - name: restart
                 config: |
                   $nrconf{restart} = 'a'
