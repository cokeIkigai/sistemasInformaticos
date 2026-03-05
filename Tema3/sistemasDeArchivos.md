# ⚡Sistemas de archivos (NTFS, EXT4, APFS, ZFS, Btrfs)

## Introducción

- Un sistema de archivos define cómo un sistema operativo:  **ORGANIZA**, **ALMACENA** y **RECUPERA** la información en un dispositivo.

- Además **CONTROLA** la integridad de los datos, los **PERMISOS**, el **RENDIMIENTO** y la **CAPACIDAD** de recuperación ante errores.-  

- Cada sistema tiene objetivos distintos: **COMPATIBILIDAD**, **ESTABILIDAD**, **OPTIMIZACIÓN**  o máxima **PROTECCIÓN** frente a corrupción.

<p align="center">
  <img src="./img/sistemas01.jpg" width="950px">
</p>

---

## 🗃 FAT32  (Windows, Linux, macOS, cámaras, consolas, TVs)

### ¿Qué es FAT32?

- **FAT**: File Allocation Table (Tabla de Asignación de Archivos).
- Es una **tabla** o índice que **GUARDA** el sistema para saber en qué partes del disco está almacenado cada archivo.
- En lugar de guardar un archivo en un único lugar continuo, el sistema puede dividirlo en varios **clusters** (bloques del disco).
- La FAT es la estructura que registra qué bloques pertenecen a cada archivo y en qué orden se deben leer.

---

### ¿Cómo está estructurado?

En una partición FAT32 suele haber estas zonas:

* **Boot Sector / BPB**
* **FSInfo**
* **FAT #1 y FAT #2**
* **Zona de datos**

---
###  🔛 Boot Sector / BPB (sector de arranque):
  
Describe la estructura del sistema de archivos para que el sistema operativo pueda leer el disco correctamente:

- **Tamaño de sector:** Unidad física mínima del disco (normalmente 512 bytes o 4096 bytes)
- **Tamaño de cluster:** Grupo de sectores que el sistema de archivos usa para almacenar datos
- **Número de FATs**
- **Dónde empieza la zona de datos** 

---

### 🔎 FSInfo (típico en FAT32): 

Sirve para saber cuántos clusters libres hay en el sistema. Debe recorrer toda la FAT, lo que podía ser lento en discos grandes.

**FSInfo guarda dos datos orientativos:**

- Número estimado de clusters libres ( ¿espacio disponible? )
- Próximo cluster libre sugerido ( ¿Dónde empezar a buscar espacio libre cuando se guarda un archivo nuevo? )

ℹ️ FSInfo es una pista rápida para encontrar espacio libre sin revisar toda la tabla FAT.

⚠️ *Si se quedan desactualizados, el sistema detecta incoherencias, vuelve a comprobar la FAT completa.*

---

### 🚩FAT #1 y FAT #2 (copia): 

Si la FAT principal se corrompe (apagado brusco), el sistema puede recuperar la información usando la copia. Esto existe para proteger el sistema de archivos.

En la **tabla FAT**, cada posición corresponde a **un cluster del disco**.  
El valor almacenado indica **qué ocurre con ese cluster**.

| Valor en la FAT   | Significado                                                                                       |
|-------------------|---------------------------------------------------------------------------------------------------|
| 0                 | El cluster está **libre** y puede usarse para guardar datos                                       |
| Número de cluster | El cluster **pertenece a un archivo** y apunta al **siguiente cluster donde continúa el archivo** |
| EOF (End Of File) | Ese cluster es **el último del archivo**                                                          |
| BAD               | Cluster **defectuoso**, no se utiliza para almacenar datos                                        |

--- 

### 📗 Ejemplo de cómo se guarda un archivo

Supongamos que un archivo ocupa **tres clusters del disco**: 120, 121 y 122.

La tabla FAT registraría la siguiente información:

| Cluster | Valor en la FAT | Interpretación |
|---|---|---|
| 120 | 121 | El archivo continúa en el cluster 121 |
| 121 | 122 | El archivo continúa en el cluster 122 |
| 122 | EOF | Este es el **último cluster del archivo** |

---

#### 🏝️ Zona de datos (Data Region)

- En este está el contenido real de los archivos (en clusters) y también los directorios, incluido el directorio raíz.
- Concepto clave: cluster = unidad mínima de asignación (grupo de sectores).
- Si un archivo ocupa 1 byte, consume 1 cluster entero.

---

### Comparación de FAT32 con otros sistemas de archivos

| Comparación | Diferencia principal |
|---|---|
| **FAT16 vs FAT32** | FAT32 permite **muchos más clusters**, por lo que puede manejar **volúmenes mucho más grandes**. Además, el **directorio raíz no está en una posición fija** como en FAT16. |
| **FAT32 vs exFAT** | **exFAT** está diseñado para **memorias flash modernas** y soporta **archivos mucho más grandes**, mientras que FAT32 tiene un **límite de 4 GB por archivo**. |
| **FAT32 vs NTFS / EXT4 / APFS** | FAT32 es más simple y compatible, pero **carece de funciones avanzadas** presentes en sistemas modernos. |

---

### Funciones que FAT32 no tiene

| Característica | Explicación |
|---|---|
| Permisos / ACL | No permite definir **seguridad por usuario o grupo** |
| Journaling | No registra cambios antes de realizarlos, por lo que es **más vulnerable a corrupción** si se apaga el sistema inesperadamente |
| Cifrado / Compresión | No tiene **cifrado ni compresión integrada** como NTFS |
| Tolerancia a fallos | Tiene **peor recuperación ante cortes de energía o errores** |

---

### Limitaciones de FAT32

1. **Tamaño máximo de archivo:**  4 GB − 1 byte
2. **Tamaño de partición:** Técnicamente hasta ~2 TB, aunque muchas herramientas como Windows solo permiten formatear hasta 32 GB en FAT32 

---

4) Cómo funciona (la idea esencial)

FAT32 funciona como un “mapa” de clusters.

4.1 Guardar un archivo

El sistema busca clusters libres.

Escribe el contenido del archivo en esos clusters.

En la FAT guarda la “cadena”:

Ejemplo:

Archivo ocupa clusters: 120, 121, 130

La FAT indica:

120 → 121

121 → 130

130 → EOF (fin)

4.2 Leer un archivo

En el directorio, localiza la entrada del archivo (nombre, tamaño, cluster inicial).

Va a ese cluster y sigue la cadena por la FAT hasta EOF.

Reconstruye el archivo leyendo los clusters en orden.

4.3 Borrar un archivo (importante para clase)

Normalmente no borra el contenido inmediatamente.

Marca la entrada del directorio como “borrada” y en la FAT marca sus clusters como libres.

Por eso se pueden “recuperar” archivos borrados si no se sobrescribe.

4.4 Fragmentación

Como un archivo puede acabar en clusters no contiguos (120, 121, 130…), se produce fragmentación y baja el rendimiento en discos mecánicos (en USB/flash el efecto es distinto, pero sigue existiendo “dispersión”).

Si quieres, lo convierto en un guion de 10 minutos para clase con un ejemplo de pizarra (clusters numerados y una mini-tabla FAT) y un ejercicio práctico para que lo simulen a mano.

## 🗃 NTFS (Windows)

<img src="./img/nfts01.jpg" width="130px" align="right" style="margin-left: 80px;">

NTFS es el sistema de archivos estándar en Windows desde la familia Windows NT. 
Está diseñado para entornos profesionales donde se necesita control detallado y seguridad.

Características principales:

<img src="./img/ntfs02.jpg" width="150px" align="right" style="margin-left: 80px;">

**1. Permisos avanzados mediante ACLs (`Access Control List`):**
  - Lectura
  - Escritura
  - Modificación
  - Ejecución
  - Eliminación
  - Control total
   
---

**2. Journaling para evitar corrupción tras apagones.**

<img src="./img/journal.jpg" width="300px" align="right" style="margin-left: 80px;">

- NTFS registra en un log los cambios antes de aplicarlos.
- Escribir en el journal lo que va a cambiar.
- Ejecutar cambio.
- Confirmar en el journal.
  > chkdsk C:

---
   
**3. Compresión y cifrado (EFS): [BitLoker](https://blog.elhacker.net/2021/12/diferencias-entre-el-cifrado-bitlocker-y-EFS-en-Windows.html).**

<img src="./img/efs.jpg" width="350px" align="right" style="margin-left: 80px;">

- Comprime archivos sin software externo.
- Propiedades → Avanzados → Comprimir contenido. (windows)
- Ideal para:  Documentación | Logs | Texto plano | ⛔ Videos

---

**4.  Cuotas de disco y soporte para archivos grandes.**

- Permite limitar el espacio que puede usar cada usuario.
  - Útil para: Servidores educativos, Entornos corporativos, Escritorios.
  - Propiedades del disco -> Pestaña Cuota -> Activar y definir límite.

**5. Enlaces duros y simbólicos.**

Limitaciones:
- Compatibilidad parcial fuera de Windows.
- Algunas funciones avanzadas no están disponibles en otros sistemas operativos.

Uso recomendado: estaciones de trabajo y servidores Windows.

---

## 🗃 EXT4 (Linux)
EXT4 es uno de los sistemas de archivos más utilizados en `GNU/Linux`. Prioriza estabilidad y rendimiento constante.

Características principales:
- Journaling mejorado.
- Extents para gestionar archivos grandes de forma eficiente.
- Alta estabilidad y herramientas maduras como `e2fsck`.
- Soporte para grandes volúmenes y timestamps precisos.

Limitaciones:
- No integra snapshots ni verificación end-to-end de serie.

Uso recomendado: entornos Linux generales, servidores y estaciones de desarrollo.

---

## 🗃 APFS (Apple)
APFS es el sistema de archivos moderno de Apple, optimizado para SSD y NVMe.

Características principales:
- Copy-on-Write para evitar sobreescrituras peligrosas.
- Snapshots rápidos.
- Cifrado nativo por volumen o archivo.
- Clones instantáneos que ahorran espacio y tiempo.

Limitaciones:
- Compatibilidad limitada fuera del ecosistema Apple.

Uso recomendado: macOS y dispositivos Apple, especialmente en unidades SSD.

---

## 🗃 ZFS y Btrfs: nueva generación

**ZFS y Btrfs** representan una `evolución` al integrar sistema de archivos y gestión de volúmenes en una sola capa. Ambos utilizan `Copy-on-Write` y `checksums` para detectar corrupción silenciosa.

En los sistemas clásicos (NTFS, EXT4):
```
Disco → RAID → Gestor de volúmenes → Sistema de archivos
```

En ZFS y Btrfs:
```
Disco → ZFS/Btrfs (todo integrado)
```

### ZFS

1️⃣ Pools de almacenamiento dinámicos (zpool). Tienes 3 discos de 4 TB. Puede crecer añadiendo discos. Gestiona redundancia internamente. Reparte datos de forma inteligente.
*Clave: abstrae el almacenamiento físico.*

```  
zpool create datos disk1 disk2 disk3
```

2️⃣ **Protección `end-to-end` mediante checksums**. Cada bloque de datos tiene un checksum (huella digital matemática).
  - **Cuando lees un archivo:** ZFS recalcula el checksum. Lo compara con el guardado.
  - **Si no coincide:** Detecta corrupción silenciosa (bit rot). Si hay redundancia (RAID-Z), repara automáticamente.
  - **!importante!:** La corrupción silenciosa NO la detectan NTFS ni EXT4 de forma completa.
  
3️⃣ **Snapshots y clones eficientes:** ZFS usa Copy-on-Write (COW).
  - Cuando modificas un archivo: No sobrescribe el bloque antiguo. Escribe uno nuevo. Actualiza referencias.
  - Un snapshot:
    Es simplemente un puntero al estado actual. No copia datos completos. Solo guarda bloques modificados después.

Ejemplo:

```
Archivo de 10 GB
Snapshot creado
Modificas 200 MB
```

*El snapshot solo “bloquea” los 200 MB originales.*

---

4️⃣ Scrubs periódicos para detectar y reparar errores.

Un *scrub* es una revisión completa del almacenamiento.

```
zpool scrub datos
```
¿Qué hace?

- Lee todos los bloques.
- Verifica checksums.
- Repara si detecta error (si hay redundancia).

Es mantenimiento preventivo real.



- 5️⃣ Compresión y deduplicación opcional.

Compresión:

- Reduce tamaño automáticamente.

- Transparente para el usuario.

Deduplicación:

- Si dos bloques son idénticos, solo guarda uno.

- Muy útil en backups o máquinas virtuales.

*Consume mucha RAM.*

**Enfoque:** integridad y fiabilidad en NAS y servidores críticos.

---

### 🧪 PARTE 1 – Entendiendo Btrfs de verdad (sin definiciones vacías)

**Btrfs**

Cada apartado debe incluir:

1. Explicación técnica (cómo funciona internamente)

2. Un ejemplo real

3. Un pequeño esquema o dibujo simple

4. Al menos un comando real de Linux

---

🔹 1️⃣ Subvolúmenes

1. ¿Qué es exactamente un subvolumen?

2. ¿Es una partición física?

3. ¿Comparte espacio con otros subvolúmenes?

4. ¿Tiene su propio sistema de permisos?

5. ¿Puede eliminarse sin afectar a los demás?

---

🔹 2️⃣ Snapshots rápidos

1. ¿Qué significa que el snapshot sea instantáneo?

2. ¿Qué papel juega Copy-on-Write?

3. ¿Copia los datos físicamente?

4. ¿Qué ocurre si modifico un archivo después del snapshot?

---


[FAT32](https://recoverit.wondershare.es/file-system/fat32-file-system.html)
