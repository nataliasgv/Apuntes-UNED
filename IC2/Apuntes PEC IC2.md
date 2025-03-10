```
.data
.align 2
n: .float 3.0

U: .float 1.0, 6.0, 5.0, 
 .float 0.0, 1.0, 4.0, 
 .float 0.0, 0.0, 1.0, 
 
 x: .float 1.0, 1.0, 1.0, 
 .float 1.0, 1.0, 1.0, 
 .float 1.0, 1.0, 1.0, 
 
 b: .float 2.0, 
 .float 3.0, 
 .float 1.0, 

.text
.global main
main:

ld f4, n             ;copia el contenido de n (3) en f4
add r1, r0, U
addi r2, r1, #36     ;9 elementos por 4 bytes de cada entero
add r3, r0, x        ;aqui igual puedo poner r1 en vez de r3, r1 debería estar vacio
addi r4, r3, #36  
add r5, r0, b
add r6, r5, #36


inicio:
blt f4, fin_bucle1       ;si n es menor que cero salta a la etiqueta fin_bucle1

 
```