# iotop-extension
An extenstion to the open-source IOTOP tool.


## Output fields in IOTOP
Group 1
1. Actual DISK READ: retreived fomr /proc/vmstat
2. Actual DISK WRITE: retreived fomr /proc/vmstat

Group 2
1. DISK READ
2. DISK WRITE

Group 3
1. SWAPIN
2. IO


## Additional fields available in IOTOP-EXTENSION
1. BUFFER READ:     read_char field in struct taskstats, denoting the bytes read
2. BUFFER WRITE:    write_char field in struct taskstats, denoting the bytes write
3. READ SYSCALLS:   read_syscalls field in struct taskstats, denoting # of read system calls on the vfs layer
4. WRITE SYSCALLS:  write_syscalls field in struct taskstats, denoting # of # of times waiting for blkio
5. BLKIO CNT:       blkio_cnt field in struct taskstats, denoting # # of times waiting for swap in

## A few more words


## A somewhat hacky Linux I/O stack
<img width="995" alt="image" src="https://github.com/hazelnut-99/iotop-extension/assets/130122455/fac62039-5af6-43f8-99e4-223449ec70bf">

## struct taskstats in detail
<img width="1020" alt="image" src="https://github.com/hazelnut-99/iotop-extension/assets/130122455/35951285-bf0c-4587-8318-5e42efab6906">


## Referencing: 
- iotop: http://guichaz.free.fr/iotop/
- Linux kernel struct taskstats documentation: https://docs.kernel.org/accounting/taskstats-struct.html
- Linux kernel netlink: https://docs.kernel.org/userspace-api/netlink/intro.html
- Linux I/O stack: https://www.thomas-krenn.com/en/wiki/Linux_Storage_Stack_Diagram 

