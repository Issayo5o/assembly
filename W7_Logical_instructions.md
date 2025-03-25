
# Logical instructions

## Code 

```
section .data
    value1  dd 0xA5A5A5A5    ; starting number
    result  dd 0             ; will hold answer

section .text
    global _start

_start:
    ; XOR part
    mov eax, [value1]        ; put value into eax
    xor eax, eax             ; make eax zero
    mov [result], eax        ; save zero in result

    ; TEST part
    mov ebx, [value1]        ; put value into ebx
    test ebx, 1              ; check if number is even or odd

    ; exit program
    mov eax, 1               ; say we're done
    xor ebx, ebx             ; return code 0
    int 0x80                 ; system call to exit

```


 ## Challenges
 
At first, I hit a roadblock with GDP but I realized I had to use a breakpoint and after that everything worked like it was supposed to.

## Image of results on Jupyter 

![image](https://github.com/user-attachments/assets/46d5a911-3f9b-4d5a-9163-1b25296d911a)
