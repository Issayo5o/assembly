# Code


```
section .data
    num     dd 6
    msg     db 'Result: ', 0
    nl      db 10
    buffer  db 12 dup(0)

section .text
    global _start

_start:
    mov     ecx, [num]
    mov     eax, 1

.factorial_loop:
    test    ecx, ecx
    jz      .convert_result
    mul     ecx
    dec     ecx
    jmp     .factorial_loop

.convert_result:
    mov     esi, buffer
    add     esi, 11
    mov     byte [esi], 0
    mov     ebx, 10

.convert_loop:
    dec     esi
    xor     edx, edx
    div     ebx
    add     dl, '0'
    mov     [esi], dl
    test    eax, eax
    jnz     .convert_loop

    mov     eax, 4
    mov     ebx, 1
    mov     ecx, msg
    mov     edx, 8
    int     0x80

    mov     eax, 4
    mov     ebx, 1
    mov     ecx, esi
    mov     edx, buffer
    add     edx, 12
    sub     edx, esi
    int     0x80

    mov     eax, 4
    mov     ebx, 1
    mov     ecx, nl
    mov     edx, 1
    int     0x80

    mov     eax, 1
    xor     ebx, ebx
    int     0x80

```
