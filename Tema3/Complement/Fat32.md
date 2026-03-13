# LECTURA DE LA TABLA FAT32

**Hay que busar en los siguientes archivos:**

index.html  → cluster inicial 4

index.css  → cluster inicial 8

index.js  → cluster inicial 20

**Tabla FAT32:**

```
00002000  f0 ff ff 0f  ff ff ff 0f  f8 ff ff 0f  ff ff ff 0f
00002010  14 00 00 00  00 00 00 00  32 00 00 00  00 00 00 00
00002020  09 00 00 00  0a 00 00 00  0b 00 00 00  0c 00 00 00
00002030  0d 00 00 00  ff ff ff 0f  00 00 00 00  00 00 00 00
00002040  2d 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00
00002050  0c 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00
00002060  05 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00
00002070  ff ff ff 0f  ff ff ff 0f  00 00 00 00  00 00 00 00

........  ...........  ...........  ...........  ...........
........  ...........  ...........  ...........  ...........

00004000  f0 ff ff 0f  ff ff ff 0f  f8 ff ff 0f  ff ff ff 0f
00004010  14 00 00 00  00 00 00 00  32 00 00 00  00 00 00 00
00004020  09 00 00 00  0a 00 00 00  0b 00 00 00  0c 00 00 00
00004030  0d 00 00 00  ff ff ff 0f  00 00 00 00  00 00 00 00
00004040  2d 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00
00004050  0c 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00
00004060  05 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00
00004070  ff ff ff 0f  ff ff ff 0f  00 00 00 00  00 00 00 00
```

### index.html

Primero leémos la primera entrada de la tabla. La FAT empieza en `00002000` y que cada entrada ocupa 4 bytes, así que siempre usamos la fórmula:
El cluster inicial para index.html es 4, por lo que buscamos su FAT[4]. ¿Cómo lo hacemos? Pues buscando su claster correspondiente.

```dirección = inicio_FAT + (cluster × 4)```

- inicio_FAT = `00002000`
- cluster = `4`

```
dirección = inicio_FAT + (cluster × 4)
dirección = 00002000   + (4    ×    4) 
Pasar (4 × 4) = 16 -> Hexadecimal 0000010
dirección = 00002000 + 0000010 = 00002010
-----------------------------------------
dirección = 00002010

TABLA FAT
*00002010  14 00 00 00  00 00 00 00  32 00 00 00  00 00 00 00*
```

En la dirección **00002010** encontramos *14 00 00 00*, pero eso está en litte endian, ppor lo que tenemos que interpretarlo:

```
14 00 00 00  -> 0x14
0x14         -> 1x16 + 4x1 = 20
Cluster siguiente = 20 
``` 

Repetimos la búsqueda

- inicio_FAT = `00002000`
- cluster = `20`

```
dirección = inicio_FAT + (cluster × 4)
dirección = 00002000   + (4    ×    20) 
Pasar (4 × 20) = 80 -> Hexadecimal 0000050
dirección = 00002000 + 0000050 = 00002050
-----------------------------------------
dirección = 00002050

TABLA FAT
*00002050  0c 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00*
``` 


Buscamos **FAT[20]**

**00002000 + (20 × 4) = 00002050**

En **00002050** encontramos:

**0c 00 00 00**

Interpretación:

- `0x0C` = **12**

Resultado:

**20 → 12**

---

### Siguiente cluster: 12

Buscamos **FAT[12]**

**00002000 + (12 × 4) = 00002030**

En **00002030** encontramos:

**0d 00 00 00**

Interpretación:

- `0x0D` = **13**

Resultado:

**12 → 13**

---

### Siguiente cluster: 13

Buscamos **FAT[13]**

**00002000 + (13 × 4) = 00002034**

En esa posición aparece:

**ff ff ff 0f**

Este valor significa:

**EOF (fin de archivo)**

---

### Cadena final de clusters de A.txt

**4 → 20 → 12 → 13 → EOF**
