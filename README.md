# iotop-extension
An extenstion to the open-source IOTOP tool.


Output fields in IOTOP
Group 1
1. Actual DISK READ: retreived fomr /proc/vmstat
2. Actual DISK WRITE: retreived fomr /proc/vmstat

Group 2
1. DISK READ
2. DISK WRITE

Group 3
1. SWAPIN
2. IO


Additional fields in IOTOP-EXTENSION
1. BUFFER READ
2. BUFFER WRITE
3. READ SYSCALLS
4. WRITE SYSCALLS




A somewhat hacky Linux I/O stack
<img width="995" alt="image" src="https://github.com/hazelnut-99/iotop-extension/assets/130122455/fac62039-5af6-43f8-99e4-223449ec70bf">

Referencing: 
- iotop: http://guichaz.free.fr/iotop/
- Linux kernel struct taskstats documentation: https://docs.kernel.org/accounting/taskstats-struct.html
- Linux kernel netlink: https://docs.kernel.org/userspace-api/netlink/intro.html

