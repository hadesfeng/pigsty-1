# DCS (ansible role)

This role will provision dcs (consul or etcd)

* install etcd or consul according to `dcs_type` (consul by default)
* cleaning existing dcs instance
* create fresh new dcs instance


### Tasks

[tasks/main.yml](tasks/main.yml)

```yaml
tasks:
    dcs : Check consul service not running		TAGS: [consul_purge, infra, infra_consul]
    dcs : Purge existing consul instance		TAGS: [consul_purge, infra, infra_consul]
    dcs : Set default consul node name			TAGS: [consul_setup, infra, infra_consul]
    dcs : Get hostname as consul node name		TAGS: [consul_setup, infra, infra_consul]
    dcs : Set consul node name to hostname		TAGS: [consul_setup, infra, infra_consul]
    dcs : Copy /etc/consul.d/consul.json		TAGS: [consul_setup, infra, infra_consul]
    dcs : Copy consul server service unit		TAGS: [consul_setup, infra, infra_consul]
    dcs : Launch consul server service first	TAGS: [consul_setup, infra, infra_consul]
    dcs : Copy consul agent service unit		TAGS: [consul_setup, infra, infra_consul]
    dcs : Launch consul agent service first		TAGS: [consul_setup, infra, infra_consul]
    dcs : Wait for consul service online		TAGS: [consul_setup, infra, infra_consul]
```

### Default variables

[defaults/main.yml](defaults/main.yml)

```yaml
dcs_type:    consul                               # default dcs server type: consul
dcs_servers: []                                   # default dcs servers
dcs_purge: false                                  # force remove existing server
# dcs_check_interval: 15s                         # default service check interval (not used)
# dcs_check_timeout:  3s                          # default service check timeout  (not used)
```