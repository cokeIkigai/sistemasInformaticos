# ⚡Sistemas de archivos (NTFS, EXT4, APFS, ZFS, Btrfs)

## Introducción

Un sistema de archivos define cómo un sistema operativo:
`organiza`, `almacena` y `recupera` la información en un dispositivo. 
No solo gestiona nombres y carpetas, también controla la integridad de los datos, los `permisos`, el `rendimiento` y la `capacidad` de recuperación ante errores. 
Cada sistema tiene objetivos distintos: `compatibilidad`, `estabilidad`, `optimización` para SSD o máxima `protección` frente a corrupción.

<p align="center">
  <img src="./img/sistemas01.jpg" width="950px">
</p>

---


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
