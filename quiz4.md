
# Code

```
section .text
    global _start

_start:
    push 10          ; z
    push 20          ; y
    push 30          ; x
    call add_three   ; call function

    mov eax, 1       ; exit
    int 0x80

add_three:
    push ebp         ; save base pointer
    mov ebp, esp     ; set new base pointer
    sub esp, 16      ; make space for local vars

    ; eax = x + 2, store at [ebp-4]
    mov eax, [ebp+8]
    add eax, 2
    mov [ebp-4], eax

    ; eax = y + 3, stor at [ebp-8]
    mov eax, [ebp+12]
    add eax, 3
    mov [ebp-8], eax

    ; eax = z + 4, store at [ebp-12]
    mov eax, [ebp+16]
    add eax, 4
    mov [ebp-12], eax

    ; eax = (x+2) + (y+3) + (z+4), store at [ebp-16]
    mov eax, [ebp-8]
    mov edx, [ebp-4]
    lea eax, [edx+eax]
    add eax, [ebp-12]
    mov [ebp-16], eax

    leave            ; restore stack frame
    ret              ; return

```
