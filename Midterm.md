# Midterm

## Question #1
### Code 

```
section .data
    var1   dd 6          ; var1 = 6
    var2   dd 2          ; var2 = 2
    var3   dd 10         ; var3 = 10
    result dd 0          ; will hold final result

section .text
    global _start

_start:
    ; Calculate numerator: var1 + 2
    mov eax, [var1]      ; eax = var1
    add eax, 2           ; eax = var1 + 2

    mov ebx, eax         ; store numerator in ebx

    ; Calculate denominator: var3 - var2
    mov eax, [var3]      ; eax = var3
    sub eax, [var2]      ; eax = var3 - var2

    mov ecx, eax         ; ecx = denominator

    ; Perform division
    mov eax, ebx         ; eax = numerator
    cdq                  ; sign-extend eax into edx
    idiv ecx             ; eax = quotient, edx = remainder

    mov [result], eax    ; store result

    mov eax, 1
    xor ebx, ebx
    int 0x80



```

### Table

#### Register Name__________________Value

#### EAX  ------------------------> Quotient (result): 1
#### EDX  ------------------------> Remainder, in this case: 0


### Screenshot #1
<img width="1382" alt="image" src="https://github.com/user-attachments/assets/ddab09e6-f425-4f63-8f86-a1104f543608" />






## Question #2

Y = a + b


## Question #3

### Code 

```
section .data
    odd_msg db "Odd number", 0
    even_msg db "Even number", 0

section .text
    global _start

_start:
    mov eax, 7         ; number to check
    mov ebx, 2
    mov edx, 0
    div ebx            ; remainder in edx

    cmp edx, 0
    je even_case

odd_case:
    mov edx, 11
    mov ecx, odd_msg
    jmp print_message

even_case:
    mov edx, 12
    mov ecx, even_msg

print_message:
    mov ebx, 1
    mov eax, 4
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80

```





