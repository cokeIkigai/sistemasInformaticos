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

1. Leer la primera entrada de la taba:

La FAT empieza en `00002000`** y que **cada entrada ocupa 4 bytes**, así que siempre usamos la fórmula:

 > dirección = inicio_FAT + (cluster × 4)

En esa dirección leemos **4 bytes en little endian**, que indican el **siguiente cluster**.

---

### A.txt → cluster inicial 4

Buscamos **FAT[4]**.

**Cálculo de la dirección**

- inicio_FAT = `00002000`
- cluster = `4`
- tamaño entrada = `4 bytes`

**00002000 + (4 × 4) = 00002010**

En la dirección **00002010** encontramos:

**14 00 00 00**

Interpretación en little endian:

- `0x14` = **20**

Resultado:

**4 → 20**

---

### Siguiente cluster: 20

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
