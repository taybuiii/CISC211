```

section .data
        x DD 20
        y DD 40
        z DD 60         ;creating x y z variables for main code

segment .bss
        result resd 1

section .text
        global _start


addthreevar:
        push ebp                ;pushing ebp into stack
        mov ebp,esp             ;moving ebp into esp register, point to same location
        sub esp,16              ;space for local var

        mov eax,[ebp+8]
        add eax,[ebp+12]
        add eax,[ebp+16]
        pop ebp
        ret

_start:
        push DWORD [x]
        push DWORD [y]
        push DWORD [z]          ;pushing x y z variables (previously defined) into stack

        call addthreevar        ;calling procedure 
        call exit

exit:
        mov eax,1
        int 0x80

```


segment .bss
        result resd 1
