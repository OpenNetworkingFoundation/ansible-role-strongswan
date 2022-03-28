# strongSwan

strongSwan IPSec VPN daemon


## Requirements

Requires BIRD to be installed if the VPNs are dynamic route based.

Minimum ansible version: 2.9.5


## Examples

### Example: policy-based VPN
```yaml
strongswan_conf_install_routes: yes
strongswan_conf_connections:
  - name: tunnel1
    psk: secret
    left: 10.0.0.3
    leftid: 128.105.144.189
    left_subnets: 0.0.0.0/0
    right: 34.124.6.243
    right_subnets: 0.0.0.0/0
```

### Example: dynamic route-based VPN

```yaml
strongswan_conf_connections:
  - name: tunnel1
    vti:
      local: 169.254.0.2/30
      remote: 169.254.0.1/30
    psk: secret
    left: 10.0.0.3
    leftid: 128.105.144.189
    left_subnets: 0.0.0.0/0
    right: 34.124.6.243
```

### Example: playbook
```yaml
- hosts: all
  vars:
  roles:
    - bird
    - strongswan
```

## License and Author

© 2020 Open Networking Foundation <support@opennetworking.org>

License: Apache-2.0
