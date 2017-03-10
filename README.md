jira-config
===========

Additional jira customization on-top of a base jira install.

Requirements
------------

You are on your own to configure your webserver, database, and any
other needed base server config. This is not an all-encompassing role to
stand-up a jira instance. Just particulars related to post-jira install.
The example playbook tests integration with two popular community roles
to cover nginx and a postgresql install for testing. Check the python
requirements in the `requirements.txt`.

Role Variables
--------------

```yaml
jira_home: /var/lib/jira
jira_user: jira
jira_group: "{{ jira_user }}"

jira_config_db_host: localhost
jira_config_db_port: 5432
jira_config_db_name: jira
jira_config_db_user: jira_user
jira_config_db_pass: "{{ jira_config_db_user }}"
jira_config_db_type: postgres


jira_config_db_params:
  postgres:
    type: postgres72
    driver: "org.postgresql.Driver"
    url: postgresql
```

Dependencies
------------

* `pantarei.jira`
* `ansiblebit.oracle-java`

Example Playbook
----------------

    - hosts: jira
      roles:
         - role: freedomofpress.jira-config
           jira_config_db_name: prod-jira-dbname
           jira_config_db_user: jira_db_user
           jira_config_db_pass: jira_db_pass
           jira_config_db_type: postgres

License
-------

MIT
