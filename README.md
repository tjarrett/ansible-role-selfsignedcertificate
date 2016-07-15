# Ansible Role: Self Signed Certificate

An Ansible Role that generates self signed certificates on RHEL/CentOS.

## Requirements

You must already have openssl instead. We do not check and we do not have openssl as a dependency for this role.

## Role Variables

The primary variable that you must set in your own playbook is: 

    selfsignedcertificates: ""

Which must have properties of:
* filename (e.g. ep.jhu.edu -- extension for key and certificate will be appended)
* country (e.g. US)
* state (e.g. Maryland)
* locality (e.g. Baltimore) 
* organization (e.g. Johns Hopkins University)
* domain (e.g. ep.jhu.edu)

See `defaults/main.yml` for more information.

They are also path variables for keys and certs that are defaulted based on the operating system. They can also be overridden. 

    key_path: ""
    certs_path: ""

See `vars/RedHat.yml` for RedHat/Centos.

## Dependencies

None.

## Example Playbook

    - hosts: webservers
      vars_files:
        - vars/main.yml
      roles:
        - { role: geerlingguy.apache }

*Inside `vars/main.yml`*:

    apache_listen_port: 8080
    apache_vhosts:
      - {servername: "example.com", documentroot: "/var/www/vhosts/example_com"}

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Tim Jarrett](https://github.com/tjarrett).
