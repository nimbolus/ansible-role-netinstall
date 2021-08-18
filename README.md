nimbolus.netinstall
=========

Install and setup server for netbooting with DHCP.

Role Variables
--------------

```yml
netinstall_interface: eth0
netinstall_network: 10.0.0.0
netinstall_netmask: 255.255.255.0
netinstall_router: 10.0.0.1
netinstall_domain: example.com
netinstall_dns_servers:
  - "{{ netinstall_router }}"
netinstall_ntp_servers:
  - "{{ netinstall_router }}"
netinstall_kickstart_ipv4: static
netinstall_kickstart_ipv6: auto
netinstall_kickstart_template: kickstart.j2

netinstall_hosts: []
  # - name: test
  #   ip: 10.0.0.11
  #   mac: aa:bb:cc:dd:ee:ff
  #   install: true # (optional: default is false)
  #   root_password: # sha512 passwd line (required if install is true)
  #   drive: sda # (optional: default is 'sda')
  #   os_type: centos
  #   os_version: 8-stream

netinstall_dhcp_efi_filename: netboot.xyz.efi
netinstall_dhcp_boot_filename: netboot.xyz.kpxe
netinstall_http_url: http://{{ netinstall_router }}
netinstall_tftp_servername: "{{ ansible_nodename }}"

netinstall_dhcpd_range_start: 10.0.0.20
netinstall_dhcpd_range_end:  10.0.0.200
netinstall_deny_unknown: false

netinstall_kernel_params: initrd=initrd.magic ${cmdline}
```

Example Playbook
----------------

```yml
- hosts: localhost
  roles:
    - { role: nimbolus.netinstall }
```

License
-------

BSD
