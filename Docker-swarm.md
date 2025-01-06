version: '3'
services:
  netdata:
    image: netdata/netdata:stable
    pid: host
    network_mode: host
    cap_add:
      - SYS_PTRACE
      - SYS_ADMIN
    security_opt:
      - apparmor:unconfined
    volumes:
      - netdataconfig:/etc/netdata
      - netdatalib:/var/lib/netdata
      - netdatacache:/var/cache/netdata
      - /:/host/root:ro,rslave
      - /etc/passwd:/host/etc/passwd:ro
      - /etc/group:/host/etc/group:ro
      - /etc/localtime:/etc/localtime:ro
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /etc/os-release:/host/etc/os-release:ro
      - /etc/hostname:/etc/hostname:ro
      - /var/log:/host/var/log:ro
      - /var/run/docker.sock:/var/run/docker.sock:ro
    environment:
      - NETDATA_CLAIM_TOKEN=OzQgkVVQm6VNXy1UBbKPQyXphqeafM-K5GHWlbXgDYgUrMPHEMPazQhx-6SvmLHJEMFGWxfPj2kDgGh-Jx5lZmQytW_eJA97VnIB4iBPlNk7pFykw5ZkfGtJNlw_X8pvKKo975k
      - NETDATA_CLAIM_URL=https://app.netdata.cloud
      - NETDATA_CLAIM_ROOMS=f05818bf-cc3a-4821-aa74-cf692de2a77c
    deploy:
      mode: global
      restart_policy:
        condition: on-failure
volumes:
  netdataconfig:
  netdatalib:
  netdatacache:
