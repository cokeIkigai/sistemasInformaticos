## 🗃️ index.css → cluster inicial 8

inicio_FAT = 00002000 cluster inicial = 8 dirección = inicio_FAT + (cluster × 4) 
dirección = 00002000 + (8 × 4) 8 × 4 = 32 32 en hexadecimal = 0x20 dirección = 00002000 + 0000020 
dirección = 00002020 

00002020 09 00 00 00 0a 00 00 00 0b 00 00 00 0c 00 00 00 

09 00 00 00 → 0x09 0x09 = 9 en decimal
---- 

Paso 2 (cluster = 9)
inicio_FAT = 00002000
cluster = 9

dirección = inicio_FAT + (cluster × 4)
dirección = 00002000 + (9 × 4)

9 × 4 = 36
36 en hexadecimal = 0x24

dirección = 00002000 + 0000024
dirección = 00002024
00002020  09 00 00 00  0a 00 00 00  0b 00 00 00  0c 00 00 00
0a 00 00 00 → 0x0A
0x0A = 10 en decimal

Cluster siguiente = 10

---

Paso 3 (cluster = 10)
inicio_FAT = 00002000
cluster = 10

dirección = inicio_FAT + (cluster × 4)
dirección = 00002000 + (10 × 4)

10 × 4 = 40
40 en hexadecimal = 0x28

dirección = 00002000 + 0000028
dirección = 00002028
00002020  09 00 00 00  0a 00 00 00  0b 00 00 00  0c 00 00 00
0b 00 00 00 → 0x0B
0x0B = 11 en decimal

Cluster siguiente = 11

---

Paso 4 (cluster = 11)
inicio_FAT = 00002000
cluster = 11

dirección = inicio_FAT + (cluster × 4)
dirección = 00002000 + (11 × 4)

11 × 4 = 44
44 en hexadecimal = 0x2C

dirección = 00002000 + 000002C
dirección = 0000202C
00002020  09 00 00 00  0a 00 00 00  0b 00 00 00  0c 00 00 00
0c 00 00 00 → 0x0C
0x0C = 12 en decimal

Cluster siguiente = 12

---

Paso 5 (cluster = 12)
inicio_FAT = 00002000
cluster = 12

dirección = inicio_FAT + (cluster × 4)
dirección = 00002000 + (12 × 4)

12 × 4 = 48
48 en hexadecimal = 0x30

dirección = 00002000 + 0000030
dirección = 00002030
00002030  0d 00 00 00  ff ff ff 0f  00 00 00 00  00 00 00 00
0d 00 00 00 → 0x0D
0x0D = 13 en decimal

Cluster siguiente = 13

---

Paso 6 (cluster = 13)
inicio_FAT = 00002000
cluster = 13

dirección = inicio_FAT + (cluster × 4)
dirección = 00002000 + (13 × 4)

13 × 4 = 52
52 en hexadecimal = 0x34

dirección = 00002000 + 0000034
dirección = 00002034
00002030  0d 00 00 00  ff ff ff 0f  00 00 00 00  00 00 00 00
ff ff ff 0f → 0x0FFFFFFF

EOF (fin de archivo)

**Resultado final**
```
8 → 9 → 10 → 11 → 12 → 13 → EOF
```
