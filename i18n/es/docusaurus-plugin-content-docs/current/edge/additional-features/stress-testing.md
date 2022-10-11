---
id: stress-testing
title:
description:
keywords:
  - docs
  - polygon
  - edge
  - loadbot
  - stress
  - test
---

##  {#prerequisites}



-
-

##  {#overview}





-
-

###  {#transfer-mode}





```bash
# Example
export LOADBOT_0x9A2E59d06899a383ef47C1Ec265317986D026055=154c4bc0cca942d8a0b49ece04d95c872d8f53d34b8f2ac76253a3700e4f1151
```

###  {#deploy-mode}



###  {#terminology}



-
-

##  {#start-the-loadbot}


```bash
polygon-edge loadbot  --jsonrpc http://127.0.0.1:10002 --grpc-address 127.0.0.1:10000 --sender 0x9A2E59d06899a383ef47C1Ec265317986D026055 --count 2000 --value 0x100 --tps 100
```


```bash
=====[LOADBOT RUN]=====

[COUNT DATA]
Transactions submitted = 2000
Transactions failed    = 0

[TURN AROUND DATA]
Average transaction turn around = 3.490800s
Fastest transaction turn around = 2.002320s
Slowest transaction turn around = 5.006770s
Total loadbot execution time    = 24.009350s

[BLOCK DATA]
Blocks required = 11

Block #223 = 120 txns
Block #224 = 203 txns
Block #225 = 203 txns
Block #226 = 202 txns
Block #227 = 201 txns
Block #228 = 199 txns
Block #229 = 200 txns
Block #230 = 199 txns
Block #231 = 201 txns
Block #232 = 200 txns
Block #233 = 72 txns
```
