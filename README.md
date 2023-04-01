# ansible-role-acme_sh
Install and configure [acme.sh](https://github.com/acmesh-official/acme.sh) 
using ansible.

This has some assumptions which are true for my case, e.g. identifier
validation is done using FreeDNS, but it should be easily possible to modify
the tasks for a more generalized environment.

## Features

* Run acme.sh as unprivileged user.
* Custom acme.sh installation with split install/config/certificate paths.
* Use systemd timer instead of cron.

## Configuration

    acme_domains:
      - domain: example.com
        keylength: ec-384
        san: 
          - www.example.com
          - host.example.com
        reloadcmd: "sudo systemctl reload nginx.service"
        key_group: www-data
        key_mode: 0640
      - domain: example.org
        keylength: 3072
