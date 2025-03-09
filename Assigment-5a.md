## This is my assignment code for 5a first AL Program

```
section .data
    msg db "I came,", 0Ah
        db "I saw,", 0Ah
        db "I conquered.", 0Ah
    len equ $ - msg

section .text
    global _start

_start:
    ; write syscall
    mov edx, len       ; message length
    mov ecx, msg       ; message address
    mov ebx, 1         ; file descriptor (stdout)
    mov eax, 4         ; syscall number (sys_write)
    int 0x80           ; call kernel

  ; exit syscall
    mov eax, 1         ; syscall number (sys_exit)
    xor ebx, ebx       ; exit code 0
    int 0x80           ; call kernel
```
