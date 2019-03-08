# Connection Establishment Process

Following are the steps for establishing a connection from client to server:

- client -> server: SYN packet
- server: places connection to SYN-RECV queue
- server: places connection to ACCEPT queue
- application layer/userland program: invokes accept(), removes conn from accept queue and connection is established

## SYN Queue Length and What happens on Overflow

- In linux, the SYN queue length should be 1024 by default
- You can use sysctl config to update `net.core.somaxconn` to bigger values
- If SYN queue is full, the connection is dropped
- Client backs off and re-sends another SYN packet
- Using `SO_REUSEPORT` socket options and running multiple applications bound to same PORT can help enhance performance
