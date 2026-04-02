# haproxy role (reverseproxy)

Install and configure HAProxy as a reverse proxy / load balancer.

## Requirements

- Ansible >= 2.14
- Debian/Ubuntu hosts
- Facts gathering enabled

## Role Variables

Main variables (see `defaults/main.yml` for full list):

- `haproxy_package_name`: package name, default `haproxy`
- `haproxy_service_name`: service name, default `haproxy`
- `haproxy_config_path`: HAProxy config path, default `/etc/haproxy/haproxy.cfg`
- `haproxy_bind_interface`: interface used to detect bind address, default `eth1`
- `haproxy_bind_address`: bind IP address (auto-detected by default)
- `haproxy_bind_port`: listening port, default `80`
- `haproxy_backend_group`: inventory group used as backend pool, default `web`
- `haproxy_backend_port`: backend port, default `80`
- `haproxy_stats_socket`: path to stats socket, disabled when empty

Optional host vars for each backend host:

- `haproxy_backend_weight`: backend server weight (default: `haproxy_backend_weight_default`)
- `haproxy_backend_address`: explicit backend IP/hostname (fallback: `ansible_host` then inventory hostname)

## Example Playbook

```yaml
- name: HAProxy
  hosts: haproxy
  become: true
  roles:
    - role: reverseproxy
      vars:
        haproxy_bind_port: 80
        haproxy_backend_group: web
        haproxy_stats_socket: /tmp/sock
```

## Dependencies

None.

## License

MIT
