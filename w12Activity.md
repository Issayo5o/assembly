
# Code

```
section .data
    even_msg db "Even", 0xA       ; message if number is even
    even_len equ $ - even_msg

    odd_msg db "Odd", 0xA         ; message if number is odd
    odd_len equ $ - odd_msg

section .text
    global _start

_start:
    mov eax, 7                    ; number to check
    push eax                      ; pass number to function
    call check_even_odd           ; call the function

    mov eax, 1                    ; syscall: exit
    int 0x80

check_even_odd:
    push ebp                      ; save base pointer
    mov ebp, esp                  ; set new base pointer

    mov eax, [ebp+8]              ; get the number
    and eax, 1                    ; check last bit
    cmp eax, 0
    je .even                      ; if 0 → even

.odd:
    mov eax, 4                    ; syscall: write
    mov ebx, 1                    ; to stdout
    mov ecx, odd_msg              ; msg = "Odd"
    mov edx, odd_len              ; msg length
    int 0x80
    jmp .done

.even:
    mov eax, 4                    ; syscall: write
    mov ebx, 1                    ; to stdout
    mov ecx, even_msg             ; msg = "Even"
    mov edx, even_len             ; msg length
    int 0x80

.done:
    pop ebp                       ; restore base pointer
    ret                           ; return to caller

```

# Challanges 

Understanding what a stack frame and using it was the hardest part.
