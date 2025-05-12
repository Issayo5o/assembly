# Code
```
SECTION .data
    filename db 'quotes.txt', 0     ; file name
    quote1 db 'To be, or not to be, that is the question.', 10
    quote2 db 'A fool thinks himself to be wise, but a wise man knows himself to be a fool.', 10
    quote3 db 'Better three hours too soon than a minute too late.', 10
    quote4 db 'No legacy is so rich as honesty.', 10

SECTION .bss
    fd resb 4   ; reserve space for file descriptor

SECTION .text
    global _start

_start:

    ; CREATE the file (sys_creat = 8)
    mov eax, 8              ; syscall number for sys_creat
    mov ebx, filename       ; filename
    mov ecx, 0777o          ; file permission
    int 0x80
    mov [fd], eax           ; save file descriptor

    ; WRITE quote1
    mov eax, 4              ; syscall: sys_write
    mov ebx, [fd]           ; file descriptor
    mov ecx, quote1         ; buffer
    mov edx, 44             ; length of quote1
    int 0x80

    ; WRITE quote2
    mov eax, 4
    mov ebx, [fd]
    mov ecx, quote2
    mov edx, 74             ; length of quote2
    int 0x80

    ; CLOSE file (sys_close = 6)
    mov eax, 6
    mov ebx, [fd]
    int 0x80

    ; OPEN file again for writing (sys_open = 5)
    mov eax, 5
    mov ebx, filename
    mov ecx, 2              ; read-write mode
    mov edx, 0777o
    int 0x80
    mov [fd], eax

    ; SEEK to end of file (sys_lseek = 19)
    mov eax, 19             ; syscall: sys_lseek
    mov ebx, [fd]           ; file descriptor
    mov ecx, 0              ; offset
    mov edx, 2              ; SEEK_END
    int 0x80

    ; APPEND quote3
    mov eax, 4
    mov ebx, [fd]
    mov ecx, quote3
    mov edx, 52             ; length of quote3
    int 0x80

    ; APPEND quote4
    mov eax, 4
    mov ebx, [fd]
    mov ecx, quote4
    mov edx, 39             ; length of quote4
    int 0x80

    ; CLOSE file
    mov eax, 6
    mov ebx, [fd]
    int 0x80

    ; EXIT program (sys_exit = 1)
    mov eax, 1
    xor ebx, ebx
    int 0x80
```
