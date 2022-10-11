---
id: set-up-ibft-on-the-cloud
title:
description: ""
keywords:
  - docs
  - polygon
  - edge
  - cloud
  - setup
  - genesis
---

:::info




:::

##  {#requirements}



###  {#setting-up-the-vm-connectivity}





##  {#overview}







0.
1.
2.
3.
4.

:::info





:::

##  {#step-1-initialize-data-folders-and-generate-validator-keys}




````bash
node-1> polygon-edge secrets init --data-dir data-dir
````

````bash
node-2> polygon-edge secrets init --data-dir data-dir
````

````bash
node-3> polygon-edge secrets init --data-dir data-dir
````

````bash
node-4> polygon-edge secrets init --data-dir data-dir
````



:::warning



:::

:::warning


:::

##  {#step-2-prepare-the-multiaddr-connection-string-for-the-bootnode}






```
/ip4/<ip_address>/tcp/<port>/p2p/<node_id>
```



:::info


:::








```
/ip4/<public_or_private_ip>/tcp/1478/p2p/16Uiu2HAmJxxH1tScDX2rLGSU9exnuvZKNM9SoK3v315azp68DLPW
```

```
/ip4/<public_or_private_ip>/tcp/1478/p2p/16Uiu2HAmS9Nq4QAaEiogE4ieJFUYsoH28magT7wSvJPpfUGBj3Hq
```
:::info





:::

##  {#step-3-generate-the-genesis-file-with-the-4-nodes-as-validators}





```
[SECRETS INIT]
Public key (address) = 0xC12bB5d97A35c6919aC77C709d55F6aa60436900
BLS Public key       = 0x9952735ca14734955e114a62e4c26a90bce42b4627a393418372968fa36e73a0ef8db68bba11ea967ff883e429b3bfdf
Node ID              = 16Uiu2HAmVZnsqvTwuzC9Jd4iycpdnHdyVZJZTpVC8QuRSKmZdUrf
```



````bash
polygon-edge genesis --consensus ibft --ibft-validator=0xC12bB5d97A35c6919aC77C709d55F6aa60436900 --ibft-validator=<2nd_validator_pubkey> --ibft-validator=<3rd_validator_pubkey> --ibft-validator=<4th_validator_pubkey> --bootnode=<first_bootnode_multiaddr_connection_string_from_step_2> --bootnode <second_bootnode_multiaddr_connection_string_from_step_2> --bootnode <optionally_more_bootnodes>
````



*
*

:::info







```
--premine=0x3956E90e632AEbBF34DEB49b71c28A83Bc029862:1000000000000000000000
```



:::

:::info



```go title="command/helper/helper.go"
const (
	GenesisFileName       = "./genesis.json"
	DefaultChainName      = "example"
	DefaultChainID        = 100
	DefaultPremineBalance = "0x3635C9ADC5DEA00000"
	DefaultConsensus      = "pow"
	GenesisGasUsed        = 458752
	GenesisGasLimit       = 5242880 // The default block gas limit
)
```



```shell
--block-gas-limit 1000000000
```

:::

:::info




-
```shell title="ulimit -a"
ubuntu@ubuntu:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 15391
max locked memory       (kbytes, -l) 65536
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 15391
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

-
	-
	```shell
	ulimit -u 65535
	```
	-
	```shell
	sudo vi /etc/security/limits.conf  # we use vi, but you can use your favorite text editor
	```
	```shell title="/etc/security/limits.conf"
	# /etc/security/limits.conf
	#
	#Each line describes a limit for a user in the form:
	#
	#<domain>        <type>  <item>  <value>
	#
	#Where:
	#<domain> can be:
	#        - a user name
	#        - a group name, with @group syntax
	#        - the wildcard *, for default entry
	#        - the wildcard %, can be also used with %group syntax,
	#                 for maxlogin limit
	#        - NOTE: group and wildcard limits are not applied to root.
	#          To apply a limit to the root user, <domain> must be
	#          the literal username root.
	#
	#<type> can have the two values:
	#        - "soft" for enforcing the soft limits
	#        - "hard" for enforcing hard limits
	#
	#<item> can be one of the following:
	#        - core - limits the core file size (KB)
	#        - data - max data size (KB)
	#        - fsize - maximum filesize (KB)
	#        - memlock - max locked-in-memory address space (KB)
	#        - nofile - max number of open file descriptors
	#        - rss - max resident set size (KB)
	#        - stack - max stack size (KB)
	#        - cpu - max CPU time (MIN)
	#        - nproc - max number of processes
	#        - as - address space limit (KB)
	#        - maxlogins - max number of logins for this user

	#        - maxsyslogins - max number of logins on the system
	#        - priority - the priority to run user process with
	#        - locks - max number of file locks the user can hold
	#        - sigpending - max number of pending signals
	#        - msgqueue - max memory used by POSIX message queues (bytes)
	#        - nice - max nice priority allowed to raise to values: [-20, 19]
	#        - rtprio - max realtime priority
	#        - chroot - change root to directory (Debian-specific)
	#
	#<domain>      <type>  <item>         <value>
	#

	#*               soft    core            0
	#root            hard    core            100000
	#*               hard    rss             10000
	#@student        hard    nproc           20
	#@faculty        soft    nproc           20
	#@faculty        hard    nproc           50
	#ftp             hard    nproc           0
	#ftp             -       chroot          /ftp
	#@student        -       maxlogins       4

	*               soft    nofile          65535
	*               hard    nofile          65535

	# End of file
	```

:::


1.
2.
3.





##  {#step-4-run-all-the-clients}

:::note






####  {#example}





`polygon-edge ... --libp2p 0.0.0.0:10001 --nat 192.0.2.1`



`polygon-edge ... --libp2p 0.0.0.0:10001 --dns dns/example.io`



:::




````bash
node-1> polygon-edge server --data-dir ./data-dir --chain genesis.json  --libp2p 0.0.0.0:1478 --nat <public_or_private_ip> --seal
````



````bash
node-2> polygon-edge server --data-dir ./data-dir --chain genesis.json --libp2p 0.0.0.0:1478 --nat <public_or_private_ip> --seal
````



````bash
node-3> polygon-edge server --data-dir ./data-dir --chain genesis.json --libp2p 0.0.0.0:1478 --nat <public_or_private_ip> --seal
````



````bash
node-4> polygon-edge server --data-dir ./data-dir --chain genesis.json --libp2p 0.0.0.0:1478 --nat <public_or_private_ip> --seal
````



:::info



````bash
polygon-edge server --config <config_file_path>
````


````bash
polygon-edge server --config ./test/config-node1.json
````


:::

:::info



````bash
polygon-edge server --data-dir <directory_path> --chain <genesis_filename>  --libp2p <IPAddress:PortNo> --nat <public_or_private_ip>
````


````bash
polygon-edge server --data-dir ./data-dir --chain genesis.json --libp2p 0.0.0.0:1478 --nat<public_or_private_ip>
````
:::

:::info











````bash
polygon-edge server --price-limit 100000 ...
````


:::

:::info



````bash
ws://localhost:10002/ws
````



````bash
wss://rpc-edgenet.polygon.technology/ws
````
:::