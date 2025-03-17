# W6-Activity Arithmetic instructions

## Code 
```
section .data
    var1 dd 5           ; Define var1 = 5
    var2 dd 3           ; Define var2 = 3
    var3 dd 7           ; Define var3 = 7
    var4 dd 2           ; Define var4 = 2
    result dd 0         ; Storage for result

section .text
    global _start       ; Entry point for the program

_start:
    ; result = -var1 * 10
    mov eax, dword [var1]  ; Load var1 into eax
    imul eax, -10          ; Multiply by -10
    mov dword [result], eax ; Store result

    ; result = var1 + var2 + var3 + var4
    mov eax, dword [var1]  ; Load var1
    add eax, dword [var2]  ; Add var2
    add eax, dword [var3]  ; Add var3
    add eax, dword [var4]  ; Add var4
    mov dword [result], eax ; Store result

    ; result = (-var1 * var2) + var3
    mov eax, dword [var1]  ; Load var1
    neg eax               ; Negate var1 (make it negative)
    imul eax, dword [var2] ; Multiply by var2
    add eax, dword [var3]  ; Add var3
    mov dword [result], eax ; Store result

    ; result = (var1 * 2) / (var2 - 3)
    mov eax, dword [var1]  ; Load var1
    imul eax, 2           ; Multiply by 2
    mov ecx, dword [var2]  ; Load var2
    sub ecx, 3            ; Subtract 3 from var2
    cdq                   ; Convert doubleword to quadword for division
    idiv ecx              ; Divide eax by ecx
    mov dword [result], eax ; Store result

    ; Exit program
    mov eax, 60           ; syscall: exit
    xor edi, edi          ; status: 0
    syscall              ; invoke exit
```

## Challanges

I had challenges with handling signed multiplication and division, especially making sure negative values were processed correctly
