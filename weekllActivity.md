# Code

```
section .data
    newline db 0xA      ; newline

section .text
    global _start

_start:
    mov ecx, 'A'        ; start at A

print_loop:
    cmp ecx, 'Z'+1      ; end after Z
    jge done

    push ecx            ; save letter
    call print_char     ; print letter
    pop ecx             ; restore letter

    inc ecx             ; next letter
    jmp print_loop      ; repeat

done:
    mov eax, 1          ; exit syscall
    xor ebx, ebx        ; status 0
    int 0x80            ; exit

print_char:
    mov eax, 4          ; write syscall
    mov ebx, 1          ; stdout
    mov edx, 1          ; length 1

    mov al, cl          ; letter to buffer
    mov [char_buf], al
    mov ecx, char_buf
    int 0x80            ; print char

    mov eax, 4          ; write syscall
    mov ebx, 1          ; stdout
    mov ecx, newline    ; print newline
    mov edx, 1
    int 0x80

    ret                 ; return

section .bss
    char_buf resb 1     ; buffer

```

# Challange

Ensuring I didn't confuse similar sounding names and terms presented a difficulty. To prevent errors, I had to confirm the specifics in the source twice over.

