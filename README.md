A role to install AIDE (Advanced Intrusion Detection Environment) via Ansible
=========


DON'T USE THIS YET IT'S WAY BROKEN
=========

I'll have it cleaned up soon :-)

Role Variables
--------------

```
email_to - In etc/aide where the email reports are to be sent.
checksums - In aide.conf you can choose how many checksums to run. If you want to sacrifice security for speed, just use 1.
aide_new_db - Used by the handler to determine where to put the new aide database
aide_db -  Used by the handler to know where the current aide database is
quiet_reports - set to yes if you don't want reports when nothing has changed
aide_ignore_list - this is a list of all the things your adding to the excludes list
```

In your vars you'll want to define a list of things/paths/files to ignore for the aide_ignore_list var like so:
```
    - { regex: 'what to match ', line: 'replace with this ' }
For example:
    - { regex: '^!/some/path', line: '!/some/path/.*' }
```

Example Playbook
----------------

```ansible-playbook -i [inventory] -u [user] -K ./aide.yml --limit=[server] --tags=install```

Author Information
------------------

Blake Carver
