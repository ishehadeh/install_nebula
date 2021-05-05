JonTheNiceGuy.Install_Nebula
=========

This is an Ansible Role for install Nebula from [Defined Networking](https://defined.net)

Requirements
------------

None

Role Variables
--------------

| Variable               | Required |    Type    | Description                                                                                                                                                                                                                                                  |
| ---------------------- | :------: | :--------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `nebula_release`       |    no    |   string   | The release tag name to install. Defaults to "latest"                                                                                                                                                                                                        |
| `nebula_key`           |    no    |   string   | The text of the Nebula certificate key file for this node. Left blank does not create the service files.                                                                                                                                                     |
| `nebula_cert`          |    no    |   string   | The text of the Nebula certificate file for this node. Left blank does not create the service files.                                                                                                                                                         |
| `nebula_ca_cert`       |    no    |   string   | The text of the Nebula Certificate Authority root certificate file for this node. Left blank does not create the service files.                                                                                                                              |
| `nebula_lighthouses`   |    no    | list(dict) | A list of dictionary entries containing the keys `nebula_ip` and `public_ip`, like this `[{"nebula_ip": "192.0.2.1", "public_ip": ["198.51.100.10:4242", "nebula.example.com:4242"]}, {"nebula_ip": "192.0.2.2", "public_ip": ["nebula.example.org:4242"]}]` |
| `nebula_am_lighthouse` |    no    |  boolean   | Whether to treat this node as a lighthouse or not. Default to `false`.                                                                                                                                                                                       |
| `nebula_host`          |    no    | IP Address | The host to bind the Nebula Service to. Default to `0.0.0.0`.                                                                                                                                                                                                |
| `nebula_port`          |    no    |  Integer   | The port to bind the Nebula Service to. Default to `4242`.                                                                                                                                                                                                   |
| `nebula_ssh_users`     |    no    | list(dict) | A list of dictionary entries containing the keys `username` and `keys`, like this `[{"username": "user", "keys": ["ssh-rsa AAAA...", "ssh-ed25519 AAAA..."]}]`                                                                                               |
| `nebula_tun_disabled`  |    no    |  boolean   | Whether to disable the TUN interface (only really useful on Lighthouses). Default to `false`.                                                                                                                                                                |
| `nebula_tun_name`      |    no    |   string   | The name of the interface.                                                                                                                                                                                                                                   |
| `drop_local_broadcast` |    no    |  boolean   | Whether to drop broadcast packets. Defaults to `true`.                                                                                                                                                                                                       |
| `drop_multicast`       |    no    |  boolean   | Whether to drop multicast packets. Defaults to `true`.                                                                                                                                                                                                       |
| `nebula_outbound`      |    no    | list(dict) | A list of dictionary entries for the outbound firewall rules. Default to `any/any allow`.                                                                                                                                                                    |
| `nebula_inbound`       |    no    | list(dict) | A list of dictionary entries for the firewall rules for outbound traffic. Default to `any/any allow`.                                                                                                                                                        |

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      tasks:
      - include_role:
          name: jontheniceguy.install_nebula

License
-------

MIT
