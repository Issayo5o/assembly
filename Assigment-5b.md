## W5b-Activity Variables and constants



```
section .text
    global _start

_start:
    ; Load values from memory into registers
    mov eax, [var1]  ; Load var1 (10) into eax
    add eax, [var2]  ; Add var2 (15) to eax
    mov [result], eax ; Store the sum in result

    ; Exit program
    mov eax, 1        ; syscall: exit
    int 0x80          ; invoke syscall

section .bss
    result resb 4     ; Uninitialized variable to store the result

section .data
    var1 dd 10        ; Initialize var1 with 10
    var2 dd 15        ; Initialize var2 with 15
```

# This is my flow chart

![flowchart assignment 5b](https://github.com/user-attachments/assets/af530959-9d8c-4347-abee-92545c185956)


# Challenges I faced 
Learning how to manipulate different variables. Debugging using gdb to verify the result variable.
