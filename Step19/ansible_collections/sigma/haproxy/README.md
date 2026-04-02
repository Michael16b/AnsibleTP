# sigma.haproxy collection

Reusable HAProxy automation for Sigma projects.

## Included content

- Role: `haproxy`

## Usage

```yaml
- name: Configure HAProxy
  hosts: haproxy
  become: true
  collections:
    - sigma.haproxy
  roles:
    - role: haproxy
```

## Build

```bash
ansible-galaxy collection build
```
