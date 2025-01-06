docker run -d --name=netdata \
--pid=host \
--network=host \
-v netdataconfig:/etc/netdata \
-v netdatalib:/var/lib/netdata \
-v netdatacache:/var/cache/netdata \
-v /:/host/root:ro,rslave \
-v /etc/passwd:/host/etc/passwd:ro \
-v /etc/group:/host/etc/group:ro \
-v /etc/localtime:/etc/localtime:ro \
-v /proc:/host/proc:ro \
-v /sys:/host/sys:ro \
-v /etc/os-release:/host/etc/os-release:ro \
-v /var/log:/host/var/log:ro \
-v /var/run/docker.sock:/var/run/docker.sock:ro \
--restart unless-stopped \
--cap-add SYS_PTRACE \
--cap-add SYS_ADMIN \
--security-opt apparmor=unconfined \
-e NETDATA_CLAIM_TOKEN=OzQgkVVQm6VNXy1UBbKPQyXphqeafM-K5GHWlbXgDYgUrMPHEMPazQhx-6SvmLHJEMFGWxfPj2kDgGh-Jx5lZmQytW_eJA97VnIB4iBPlNk7pFykw5ZkfGtJNlw_X8pvKKo975k \
-e NETDATA_CLAIM_URL=https://app.netdata.cloud \
-e NETDATA_CLAIM_ROOMS=f05818bf-cc3a-4821-aa74-cf692de2a77c \
netdata/netdata:stable



For open source use this..
--------------------------
    
    docker run -d --name=netdata \
      --pid=host \
      --network=host \
      -v netdataconfig:/etc/netdata \
      -v netdatalib:/var/lib/netdata \
      -v netdatacache:/var/cache/netdata \
      -v /:/host/root:ro,rslave \
      -v /etc/passwd:/host/etc/passwd:ro \
      -v /etc/group:/host/etc/group:ro \
      -v /etc/localtime:/etc/localtime:ro \
      -v /proc:/host/proc:ro \
      -v /sys:/host/sys:ro \
      -v /etc/os-release:/host/etc/os-release:ro \
      -v /var/log:/host/var/log:ro \
      -v /var/run/docker.sock:/var/run/docker.sock:ro \
      --restart unless-stopped \
      --cap-add SYS_PTRACE \
      --cap-add SYS_ADMIN \
      --security-opt apparmor=unconfined \
      netdata/netdata


if you are running on localhost then access this with http://localhost:19999 or for remote access this with http://remote-address:19999
