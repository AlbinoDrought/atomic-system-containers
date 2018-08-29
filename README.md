Fork of https://github.com/projectatomic/atomic-system-containers, meant _only_ for the ovirt-guest-agent-centos image.

docker-compose.yml:

```
version: '2'
services:
  guest-agent:
    privileged: true
    image: albinodrought/ovirt-guest-agent-centos
    stdin_open: true
    network_mode: host
    volumes:
    - /dev/virtio-ports/com.redhat.spice.0:/dev/virtio-ports/com.redhat.spice.0
    - /dev/virtio-ports/ovirt-guest-agent.0:/dev/virtio-ports/ovirt-guest-agent.0
    - /dev/virtio-ports/org.qemu.guest_agent.0:/dev/virtio-ports/org.qemu.guest_agent.0
    tty: true
    labels:
      io.rancher.container.pull_image: always
      io.rancher.scheduler.global: 'true'
```

rancher-compose.yml
```
version: '2'
services:
  guest-agent:
    start_on_create: true
```
