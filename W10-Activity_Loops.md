# Code 
```
section .data
    array dd 4, 12, 7, 9    ; four numbers in memory

section .text
    global _start

_start:

    mov ebx, 10         ; start at 10
    xor eax, eax        ; set eax to 0

counter_loop:
    inc eax             ; add 1 to eax
    dec ebx             ; take away 1 from ebx
    jnz counter_loop    ; keep going if not zero

    mov ecx, 8          ; how many times to repeat
    xor eax, eax        ; first number = 0
    mov ebx, 1          ; second number = 1

fibonacci_loop:
    mov edx, ebx        ; save second number
    add ebx, eax        ; add two numbers
    mov eax, edx        ; update first number
    loop fibonacci_loop ; repeat

    mov ecx, 4          ; 4 numbers to check
    mov esi, array      ; start of the array
    mov eax, [esi]      ; set first number as biggest

find_max_loop:
    add esi, 4          ; move to next number
    dec ecx             ; one less to check
    jz end              ; done if zero

    mov edx, [esi]      ; get next number
    cmp edx, eax        ; is it bigger?
    jle find_max_loop   ; if not, skip
    mov eax, edx        ; update biggest

    jmp find_max_loop

end:
    mov eax, 1
    int 0x80

```

# Challenges 
A challenge that I faced was keeping track of the different register values without overwriting the wrong one during the loops.
