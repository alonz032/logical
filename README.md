; logical.asm
; Demonstrates XOR and TEST instructions
; NASM x86 Linux

section .data
    value1  dd 25          ; Example value
    result  dd 0

section .text
    global _start

_start:

    ; --------------------------------------
    ; Example 1: XOR register with itself
    ; eax = value1
    ; xor eax,eax makes eax = 0
    ; --------------------------------------

    mov eax, [value1]
    xor eax, eax
    mov [result], eax

    ; --------------------------------------
    ; Example 2: TEST instruction
    ; Check whether value1 is even or odd
    ;
    ; TEST performs a bitwise AND
    ; without changing the operands.
    ;
    ; Least significant bit:
    ; 0 = even
    ; 1 = odd
    ; --------------------------------------

    mov ebx, [value1]

    test ebx, 1
    jz even_number

odd_number:
    mov ecx, 1
    jmp finish

even_number:
    mov ecx, 0

finish:

    ; Exit Linux

    mov eax, 1
    xor ebx, ebx
    int 0x80
