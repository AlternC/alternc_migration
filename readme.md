# Ansible script to migrate website to Alternc server


This script provide a huge ansible script to move any website (hosted on alternc, ubuntu, debian) to a standard alternc server.

## Migrate between two alternc servers

Betfote to launch a migration you must set a *variables.yml* file

**ansible-playbook migrate_site.yml**

A simple *variable.yml* file could be set as :

    ---
    source:
        domain: www.domain.tld
        cms: wordpress
        host: old.alternc.tld
        user: ssh_acccount
        key: /home/my/.ssh/id_rsa
        alternc: alternc_account
        database:
            host: 127.0.0.1
            user: "database_user"
            pass: "database_pass"
            name: "database_name"
    target:
        host: new.alternc.tld
        user: ssh_account
        key: /home/my/.ssh/id_rsa
        database:
            user: "new_database_user"
            pass: "new_database_pass"
            name: "new_database_name"

In this sample, we want migrate a worpdress with a new database to same altenrc account.


## Migrate full option variables

    ---
    source:
        domain: www.domain.tld
        alias: [ cdn.domain.tld ]
        ssl: true
        cms: wordpress
        cms_path: htdocs
        host: old.alternc.tld
        port: 2121
        user: ssh_acccount
        pass: anypassword
        key: /home/my/.ssh/id_rsa
        path: /any/absolute/path/on/server
        alternc: alternc_name if it's a an alternc server
        database:
            host: 127.0.0.1
            user: "database_user"
            pass: "database_pass"
            name: "database_name"
    target:
        host: new.alternc.tld
        port: 2222
        user: ssh_account
        pass: anypassword
        key: /home/my/.ssh/id_rsa
        path: /any/absolute/path/on/server
        alternc: new_alternc_name
        database:
            host: 127.0.0.1
            user: "new_database_user"
            pass: "new_database_pass"
            name: "new_database_name"