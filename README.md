# ansible-role-zookeeper

Ansible role for installing and configuring Apache Zookeeper.
The role supports installation of Zookeeper version 3.5.5 and higher.
The default version is `3.8.4`

## Supported Platforms

- RedHat 8
- RedHat 9

## Requirements

- Java must be installed on the target system before using this role. This role is independent of the Java role in order to be able to use the Java role you are comfortable with.
- OpenSSL must be installed on the target system if you plan to use a secure Zookeeper installation

## Configuring SSL

If you are going to use self-signed certificates, please see this [gist](https://gist.github.com/dborisov/b5a6f4eb47893d62872449f6fa6aa7e5).

Make sure you encrypt sensitive data using ansible-vault.

```yaml
zookeeper_server_connection_factory: "org.apache.zookeeper.server.NettyServerCnxnFactory"
zookeeper_ssl_client_auth: none
zookeeper_ssl_root_ca_certificate: "{{ vault_zookeeper_ssl_root_ca_certificate }}" # Zookeeper Root CA certificate content in PEM format
zookeeper_ssl_certificate: "{{ vault_zookeeper_ssl_certificate }}" # Zookeeper certificate content in PEM format
zookeeper_ssl_private_key: "{{ vault_zookeeper_ssl_private_key }}" # Zookeeper private key content in PEM format
zookeeper_ssl_trust_store_password: "{{ vault_zookeeper_ssl_trust_store_password }}"
zookeeper_ssl_trust_store_location: "{{ zookeeper_ssl_dir }}/server-truststore.pem" # Can be pem, jks or p12
zookeeper_ssl_key_store_password: "{{ vault_zookeeper_ssl_key_store_password }}"
zookeeper_ssl_key_store_location: "{{ zookeeper_ssl_dir }}/server-keystore.pem" # Can be pem, jks or p12
zookeeper_ssl_quorum: true
zookeeper_ssl_quorum_hostname_verification: false # https://issues.apache.org/jira/browse/ZOOKEEPER-4403
zookeeper_ssl_quorum_root_ca_certificate: "{{ vault_zookeeper_ssl_quorum_root_ca_certificate }}" # Zookeeper Quorum Root CA certificate content in PEM format
zookeeper_ssl_quorum_intermediate_ca_certificate: "{{ vault_zookeeper_ssl_quorum_intermediate_ca_certificate }}" # # Zookeeper Quorum Intermediate certificate content in PEM format (optional).
zookeeper_ssl_quorum_certificate: "{{ vault_zookeeper_ssl_quorum_certificate }}" # Zookeeper Quorum certificate content in PEM format
zookeeper_ssl_quorum_private_key: "{{ vault_zookeeper_ssl_quorum_private_key }}" # Zookeeper Quorum private key content in PEM format
zookeeper_ssl_quorum_trust_store_password: "{{ vault_zookeeper_ssl_quorum_trust_store_password }}"
zookeeper_ssl_quorum_trust_store_location: "{{ zookeeper_ssl_dir }}/quorum-truststore.pem"  # Can be pem, jks or p12
zookeeper_ssl_quorum_key_store_password: "{{ vault_zookeeper_ssl_quorum_key_store_password }}"
zookeeper_ssl_quorum_key_store_location: "{{ zookeeper_ssl_dir }}/quorum-keystore.pem"  # Can be pem, jks or p12
```

## Inventory Example

```ini
[zookeeper_cluster]
zk1.local zookeeper_id=1
zk2.local zookeeper_id=2
zk3.local zookeeper_id=3
```

## Playbook Example

```yaml
---
- hosts: zookeeper_cluster
  roles:
    - role: dborisov.java
    - role: dborisov.zookeeper
```

## Role Variables

Please see `meta/argument_specs.yml`

## Dependencies

`community.general` >= `8.6.0`

## License

MIT
