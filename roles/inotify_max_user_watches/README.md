inotify_max_user_watches
========================

This ansible role will permanently set the number of inotify watches to a definable value.

This may be needed for [Syncthing](https://syncthing.net) or [Nextcloud](https://nextcloud.com) clients. See the [Syncthing FAQ](https://docs.syncthing.net/users/faq.html#inotify-limits) for reference.

Requirements
------------

Any system allowing sysctl values to be defined in /etc/sysctl.d/ should be supported.

Role Variables
--------------

`fs_inotify_max_user_watches` is set to 204800 by default. The system default on many Linux distributions is 8192.

Dependencies
------------

n/a

Example Playbook
----------------

    - hosts: workstations
      roles:
        - { role: rompe.inotify_max_user_watches }
      vars:
        - fs_inotify_max_user_watches: 16384

License
-------

MIT

Author Information
------------------

Created in 2019 by Ulf Rompe

