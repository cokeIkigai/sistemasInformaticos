📊 BLOQUE I: TIPOS DE ALMACENAMIENTO (Preguntas 1-15)

Pregunta 1

¿Cuál es la velocidad de lectura típica de un disco duro HDD convencional?

A) 5000-7000 MB/s
B) 500-550 MB/s
C) 100-200 MB/s
D) 10-20 MB/s

Pregunta 2
¿Qué componente mecánico permite leer y escribir datos en un HDD moviéndose sobre los platos?

A) Motor paso a paso
B) Brazo mecánico con cabezal
C) Transistor de puerta flotante
D) Controladora PCIe

Pregunta 3
En un SSD, ¿cómo se almacena el dato físicamente?

A) Orientación magnética Norte-Sur en platos
B) Carga eléctrica atrapada en un transistor de puerta flotante
C) Hologramas en cristal fotosensible
D) Pits y lands en una superficie reflectante

Pregunta 4
¿Qué tipo de celda NAND almacena 3 bits por celda y tiene 8 estados eléctricos?

A) SLC
B) MLC
C) TLC
D) QLC

Pregunta 5
¿Qué hace que un SSD NVMe sea mucho más rápido que un SSD SATA?

A) Utiliza platos que giran a 15000 RPM
B) Usa el bus PCIe que permite paralelismo y menor latencia
C) No necesita electricidad para funcionar
D) Utiliza almacenamiento magnético en lugar de flash

Pregunta 6
¿Cuál es la velocidad aproximada de un SSD NVMe moderno?

A) 100-150 MB/s
B) 500-550 MB/s
C) 3000-7000 MB/s
D) 10-20 MB/s

Pregunta 7
¿Qué es el "Wear Leveling" en los SSD?

A) Técnica para aumentar la velocidad de lectura
B) Mecanismo que distribuye las escrituras uniformemente para prolongar la vida útil
C) Sistema de compresión de datos en tiempo real
D) Protocolo de comunicación entre CPU y disco

Pregunta 8
Según la pirámide del almacenamiento, ¿qué nivel ocupa la memoria RAM?

A) Nivel 1 (cima, más velocidad)
B) Nivel 2
C) Nivel 3
D) Nivel 4 (base, más capacidad)

Pregunta 9
¿Cuál de las siguientes es una DESVENTAJA del Cloud Storage?

A) Acceso desde cualquier dispositivo
B) Colaboración en tiempo real
C) Dependencia total de Internet
D) Respaldo remoto automático

Pregunta 10
¿Cuál es el precio aproximado por GB de un HDD?

A) 0,50-1,00 €/GB
B) 0,02-0,04 €/GB
C) 5-10 €/GB
D) 100-200 €/GB

Pregunta 11
¿Qué significa la sigla SLC en memorias NAND?

A) Single Level Cell (1 bit por celda)
B) Super Large Capacity
C) Serial Link Controller
D) Solid Level Cache

Pregunta 12
¿Qué tipo de disco es más resistente a golpes y vibraciones?

A) HDD
B) SSD
C) Ambos por igual
D) Depende de la marca

Pregunta 13
¿Qué empresa fabricó el primer disco duro y en qué año (según los ejercicios prácticos)?

A) Seagate en 1980
B) IBM en 1956
C) Western Digital en 1970
D) Samsung en 1990

Pregunta 14
¿Por qué los discos duros modernos usan helio en su interior?

A) Porque es más barato que el aire
B) Para reducir la fricción y el ruido, permitiendo más platos
C) Para enfriar el disco más rápidamente
D) Porque aumenta la capacidad magnética

Pregunta 15
¿Qué es un Yottabyte según el material?

A) 1000 Gigabytes
B) Unidad de velocidad de disco
C) Una medida de capacidad de almacenamiento extremadamente grande
D) Un tipo de conector para NVMe

📁 BLOQUE II: SISTEMAS DE ARCHIVOS (Preguntas 16-30)
Pregunta 16
¿Qué significa la sigla FAT en FAT32?

A) Fast Allocation Table
B) File Allocation Table
C) Folder Access Technology
D) Flash Address Table

Pregunta 17
¿Cuál es el límite máximo de tamaño por archivo en FAT32?

A) 2 GB
B) 4 GB
C) 16 GB
D) No tiene límite

Pregunta 18
¿Qué función cumple la FAT duplicada (FAT1 y FAT2) en FAT32?

A) Duplicar los datos del usuario
B) Permitir redundancia si una FAT se corrompe
C) Aumentar la velocidad de lectura
D) Comprimir los archivos automáticamente

Pregunta 19
¿Qué valor en la tabla FAT indica que un cluster es el último de un archivo?

A) 0
B) BAD
C) EOF (End Of File)
D) NULL

Pregunta 20
¿Qué característica de seguridad avanzada ofrece NTFS que FAT32 no tiene?

A) Journaling
B) Permisos mediante ACLs (Access Control Lists)
C) Cuotas de disco
D) Todas las anteriores

Pregunta 21
¿Qué es el "journaling" en un sistema de archivos como NTFS o EXT4?

A) Un diario donde se registran los cambios antes de aplicarlos para evitar corrupción
B) Un sistema de compresión de archivos
C) Un tipo de cifrado militar
D) Un método para desfragmentar el disco

Pregunta 22
¿Cuál es el sistema de archivos estándar y moderno de Apple para SSD?

A) HFS+
B) EXT4
C) APFS
D) NTFS

Pregunta 23
¿Qué característica distintiva tienen ZFS y Btrfs que los diferencia de NTFS y EXT4?

A) Solo funcionan en Windows
B) Integran sistema de archivos y gestión de volúmenes en una sola capa
C) No soportan archivos grandes
D) No tienen journaling

Pregunta 24
¿Qué hace ZFS cuando detecta corrupción silenciosa ("bit rot") al leer un archivo?

A) Ignora el error y continúa
B) Apaga el sistema inmediatamente
C) Si hay redundancia, repara automáticamente el dato corrupto
D) Borra el archivo completo

Pregunta 25
¿Qué comando de Linux se usa para iniciar un "scrub" (revisión completa) en un pool ZFS?

A) zfs scrub datos
B) zpool scrub datos
C) zfs check datos
D) zpool repair datos

Pregunta 26
¿Qué significa "Copy-on-Write" (COW) en sistemas como ZFS o APFS?

A) Copiar el archivo antes de cada escritura
B) No sobrescribir el bloque antiguo, sino escribir uno nuevo y actualizar referencias
C) Escribir dos veces el mismo dato por seguridad
D) Comprimir el dato antes de escribirlo

Pregunta 27
En FAT32, si un archivo ocupa 1 byte, ¿cuánto espacio consume realmente en el disco?

A) 1 byte exactamente
B) 1 cluster completo
C) 1 sector
D) Depende del sistema operativo

Pregunta 28
¿Qué sistema de archivos introduce el concepto de "subvolúmenes" y snapshots instantáneos?

A) FAT32
B) NTFS
C) Btrfs
D) HFS+

Pregunta 29
¿Qué herramienta de Windows permite ver la temperatura, horas de uso y estado S.M.A.R.T. de un disco?

A) Defraggler
B) WinDirStat
C) CrystalDiskInfo
D) AIDA64 (aunque también muestra, la pregunta pide la específica)

Pregunta 30
¿Cuál es la REGLA 3-2-1 de copias de seguridad profesional?

A) 3 discos, 2 particiones, 1 sistema operativo
B) 3 copias, 2 tipos de almacenamiento diferentes, 1 copia fuera de ubicación física
C) 3 backups diarios, 2 semanales, 1 mensual
D) 3 GB de datos, 2 horas de trabajo, 1 disco externo

