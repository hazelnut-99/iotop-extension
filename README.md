# iotop-extension
An extenstion to the open-source IOTOP tool.
Basically we fetch more fields out of taskstats when using netlink to talk with Linux kernel.
It can help to pinpoint the services responsible for I/O spikes 

## Usage
1. cd into iotop-extension directory
2. and then run python run-iotop.py
3. there you go!

## Output fields in IOTOP
Group 1
1. Actual DISK READ: retrieved fomr /proc/vmstat
2. Actual DISK WRITE: retrieved fomr /proc/vmstat

Group 2
1. DISK READ:  The number of bytes which this task has caused to be read from storage. "accounted in kernel function submit_bio()"
2. DISK WRITE: The number of bytes which this task has caused, or shall cause to be written to disk. (the accounting happens before the actual disk write!) "accounted in kernel function account_page_dirtied()"

Group 3
1. SWAPIN
2. IO


## Additional fields available in IOTOP-EXTENSION
1. BUFFER READ:     read_char field in struct taskstats, denoting # of bytes read on the vfs layer
2. BUFFER WRITE:    write_char field in struct taskstats, denoting # of bytes written on the vfs layer
3. READ SYSCALLS:   read_syscalls field in struct taskstats, denoting # of read system calls on the vfs layer
4. WRITE SYSCALLS:  write_syscalls field in struct taskstats, denoting # of write system calls on the vfs layer
5. BLKIO CNT:       blkio_cnt field in struct taskstats, denoting # of times waiting for block io (in_iowait)

## A few more words
Monitoring disk write can be challenging due to the gap between the vfs layer and block layer ("page cache, dirty writeback, kworkerflush....")
It's hard to credit disk write to the specific application processes. 
In production, we've even observed weird write spikes in system disk when I/O pressure is high in data directories. 


## How to understand BLKIO CNT/DELAY
<img width="743" alt="image" src="https://github.com/hazelnut-99/iotop-extension/assets/130122455/a13d6da9-79dc-4bfe-a511-7cafb10d2b48">


## A somewhat hacky Linux I/O stack
<img width="995" alt="image" src="https://github.com/hazelnut-99/iotop-extension/assets/130122455/fac62039-5af6-43f8-99e4-223449ec70bf">

## struct taskstats in detail
<img width="1020" alt="image" src="https://github.com/hazelnut-99/iotop-extension/assets/130122455/35951285-bf0c-4587-8318-5e42efab6906">


## Referencing: 
- iotop: http://guichaz.free.fr/iotop/
- Linux kernel struct taskstats documentation: https://docs.kernel.org/accounting/taskstats-struct.html
- Linux kernel netlink: https://docs.kernel.org/userspace-api/netlink/intro.html
- Linux I/O stack: https://www.thomas-krenn.com/en/wiki/Linux_Storage_Stack_Diagram 

