# Sistemas de archivos (NTFS, EXT4, APFS, ZFS, Btrfs)

## Introducción
Un sistema de archivos define cómo un sistema operativo organiza, almacena y recupera la información en un dispositivo. 
No solo gestiona nombres y carpetas, también controla la integridad de los datos, los permisos, el rendimiento y la capacidad de recuperación ante errores. 
Cada sistema tiene objetivos distintos: compatibilidad, estabilidad, optimización para SSD o máxima protección frente a corrupción.

---

## NTFS (Windows)
NTFS es el sistema de archivos estándar en Windows desde la familia Windows NT. 
Está diseñado para entornos profesionales donde se necesita control detallado y seguridad.

Características principales:
- Permisos avanzados mediante ACLs.
- Journaling para evitar corrupción tras apagones.
- Compresión y cifrado (EFS).
- Cuotas de disco y soporte para archivos grandes.
- Enlaces duros y simbólicos.

Limitaciones:
- Compatibilidad parcial fuera de Windows.
- Algunas funciones avanzadas no están disponibles en otros sistemas operativos.

Uso recomendado: estaciones de trabajo y servidores Windows.

---

## EXT4 (Linux)
EXT4 es uno de los sistemas de archivos más utilizados en GNU/Linux. Prioriza estabilidad y rendimiento constante.

Características principales:
- Journaling mejorado.
- Extents para gestionar archivos grandes de forma eficiente.
- Alta estabilidad y herramientas maduras como `e2fsck`.
- Soporte para grandes volúmenes y timestamps precisos.

Limitaciones:
- No integra snapshots ni verificación end-to-end de serie.

Uso recomendado: entornos Linux generales, servidores y estaciones de desarrollo.

---

## APFS (Apple)
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

## ZFS y Btrfs: nueva generación
ZFS y Btrfs representan una evolución al integrar sistema de archivos y gestión de volúmenes en una sola capa. Ambos utilizan Copy-on-Write y checksums para detectar corrupción silenciosa.

### ZFS
- Pools de almacenamiento dinámicos (zpool).
- Protección end-to-end mediante checksums.
- Snapshots y clones eficientes.
- Scrubs periódicos para detectar y reparar errores.
- Compresión y deduplicación opcional.

Enfoque: integridad y fiabilidad en NAS y servidores críticos.

### Btrfs
- Subvolúmenes y snapshots rápidos.
- RAID por software.
- Envío y recepción de snapshots para replicación.
- Administración flexible y moderna.

Enfoque: flexibilidad en estaciones Linux y servidores.

---

## Elección según escenario
- NTFS: integración completa en Windows.
- EXT4: estabilidad en Linux.
- APFS: rendimiento en macOS con SSD.
- ZFS/Btrfs: integridad avanzada, snapshots y gestión de almacenamiento.
- exFAT: compatibilidad entre sistemas en discos externos.

---

## Conceptos clave
- **Journaling:** registro previo de cambios para evitar corrupción.
- **Copy-on-Write:** escritura en nuevos bloques sin sobrescribir datos existentes.
- **Checksums:** verificación de integridad real de los datos.
- **Snapshots:** estado del sistema en un momento concreto para restauración rápida.

---

## Caso de estudio: ZFS Project
ZFS nació en Sun Microsystems con el objetivo de unificar RAID, gestor de volúmenes y sistema de archivos. 
Su arquitectura basada en pools dinámicos y checksums end-to-end permite detectar corrupción silenciosa y autoreparar datos usando redundancia. 
Gracias a snapshots, clones y tareas de mantenimiento como `scrub`, ZFS se ha convertido en una referencia en NAS y entornos empresariales donde la integridad y disponibilidad son prioritarias.

---

## Buenas prácticas
- Programar snapshots automáticos en ZFS/Btrfs.
- Realizar scrubs periódicos para verificar integridad.
- Evitar llenar completamente los SSD para mantener rendimiento.
- Usar compresión cuando los datos sean textuales o logs.

---

## Resumen
Los sistemas de archivos determinan cómo se guardan y protegen los datos. 
NTFS, EXT4 y APFS son opciones nativas optimizadas para su sistema operativo, mientras que ZFS y Btrfs añaden integridad avanzada mediante checksums y Copy-on-Write.
Para compartir información entre plataformas, exFAT ofrece la mejor compatibilidad.
