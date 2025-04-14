# W9-Activity Condition instructions

## Code
```
section .data
    num1 dd 14
    num2 dd 7
    num3 dd 20
    num4 dd 11
    num5 dd 18

section .bss
    even resb 1
    largest resd 1

section .text
    global _start

_start:

    mov ecx, 0         ; start at 0

loop_check:
    mov eax, ecx
    and eax, 1         ; check if even
    cmp eax, 0
    jne skip           ; skip if odd

    mov [even], ecx    ; store even

skip:
    inc ecx
    cmp ecx, 21
    jl loop_check      ; repeat if less than 21

    mov eax, [num1]    ; start with num1

    cmp eax, [num2]
    jge check3
    mov eax, [num2]

check3:
    cmp eax, [num3]
    jge check4
    mov eax, [num3]

check4:
    cmp eax, [num4]
    jge check5
    mov eax, [num4]

check5:
    cmp eax, [num5]
    jge store
    mov eax, [num5]

store:
    mov [largest], eax ; store largest

    mov eax, 1
    int 0x80

```

## Challanges 

One challenge that I had was to make sure that I stored and compared values without overwriting the wrong register. I handled it carefully by keeping track of each step which became a little tedious. 
