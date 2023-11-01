winrm_cert
=========

This role configures winrm https listeners. It can either create and use a self-signed certificate, or one specified by the user.

Requirements
------------

Windows requires that all certificates are in `pfx` format. So, once you receive your certificate, in order to use it with `winrm` https listeners, you need to do something like this:

```
openssl pkcs12 -export -out certificate.pfx -inkey privkey.pem -in fullchain.pem -name "servermame.server.com" -passout pass:
```

Role Variables
--------------

There are two important variables for this role, `winrm_certfile` and `winrm_cert_selfsigned`. If you set `winrm_cert_selfsigned` to *true* then you must define `winrm_certfile` with the name of a file that contains a pfx-format certificate and key.

```
winrm_certfile: 'fullchain-win2k22-dc.pfx'
winrm_cert_selfsigned: false
```

Dependencies
------------

The only external dependency is the same for all winrm roles and playbooks: pywinrm.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - winrm_cert

License
-------

GPLv3+

Author Information
------------------

Alexander Jacocks <alexander@redhat.com>
