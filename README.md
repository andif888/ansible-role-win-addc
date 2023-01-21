# ansible-role-win-addc

Role to promote a windows server to a domain controller into an existing AD domain

## Table of content

- [Default Variables](#default-variables)
  - [win_addc_dns_client_adapter](#win_addc_dns_client_adapter)
  - [win_addc_dns_client_dns_server_ips](#win_addc_dns_client_dns_server_ips)
  - [win_addc_dns_domain_name](#win_addc_dns_domain_name)
  - [win_addc_dns_forwarders](#win_addc_dns_forwarders)
  - [win_addc_dns_listenaddresses](#win_addc_dns_listenaddresses)
  - [win_addc_domain_admin_password](#win_addc_domain_admin_password)
  - [win_addc_domain_admin_user](#win_addc_domain_admin_user)
  - [win_addc_safe_mode_password](#win_addc_safe_mode_password)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Default Variables

### win_addc_dns_client_adapter

Adapter name or list of adapter names for which to manage DNS settings (’*’ is supported as a wildcard value). The adapter name used is the connection caption in the Network Control Panel or the InterfaceAlias of Get-DnsClientServerAddress. Example: win_addc_dns_client_adapter: "{{ ansible_interfaces[0].connection_name }}"

#### Default value

```YAML
win_addc_dns_client_adapter:
```

### win_addc_dns_client_dns_server_ips

Single or ordered list of DNS servers (IPv4 and IPv6 addresses) to configure for lookup. An empty list will configure the adapter to use the DHCP-assigned values on connections where DHCP is enabled, or disable DNS lookup on statically-configured connections. IPv6 DNS servers can only be set on Windows Server 2012 or newer, older hosts can only set IPv4 addresses.

#### Default value

```YAML
win_addc_dns_client_dns_server_ips:
```

### win_addc_dns_domain_name

The DNS name of the domain for which the targeted Windows host should be a DC

#### Default value

```YAML
win_addc_dns_domain_name: acme.local
```

### win_addc_dns_forwarders

List of IP addresses of upstream DNS servers

#### Default value

```YAML
win_addc_dns_forwarders:
  - 8.8.8.8
  - 8.8.4.4
```

### win_addc_dns_listenaddresses

List of IP address of the host on which it should listen to DNS requests

#### Default value

```YAML
win_addc_dns_listenaddresses:
  - '{{ ansible_interfaces[0].ipv4.address }}'
```

### win_addc_domain_admin_password

Password for the specified domain admin user.

#### Default value

```YAML
win_addc_domain_admin_password: SomeSecret343434
```

### win_addc_domain_admin_user

Username of a domain admin for the target domain (necessary to promote a domain controller).

#### Default value

```YAML
win_addc_domain_admin_user: administrator@acme.local
```

### win_addc_safe_mode_password

Safe mode password for the domain controller

#### Default value

```YAML
win_addc_safe_mode_password: SomeSecret343434_safemode
```



## Dependencies

None.

## License

license (GPL-2.0-or-later, MIT, etc)

## Author

andif888
