## Boot Sector / BPB (FAT32)

| Campo | Tamaño | Qué indica |
|------|------|-------------|
| Jump Instruction | 3 bytes | Instrucción para saltar al código de arranque |
| OEM Name | 8 bytes | Identificador del sistema que formateó el disco |
| Bytes per Sector | 2 bytes | Tamaño de cada sector físico (512 o 4096 bytes) |
| Sectors per Cluster | 1 byte | Número de sectores que forman un cluster |
| Reserved Sectors | 2 bytes | Sectores reservados antes de la FAT |
| Number of FATs | 1 byte | Número de copias de la FAT (normalmente 2) |
| Root Entry Count | 2 bytes | Número de entradas del directorio raíz (en FAT32 suele ser 0) |
| Total Sectors (16) | 2 bytes | Tamaño total del volumen si es pequeño |
| Media Descriptor | 1 byte | Tipo de medio (ej. F8 para disco duro) |
| FAT Size (16) | 2 bytes | Tamaño de la FAT en sectores (FAT12/16) |
| Sectors per Track | 2 bytes | Sectores por pista (parámetro histórico del disco) |
| Number of Heads | 2 bytes | Número de cabezas del disco |
| Hidden Sectors | 4 bytes | Sectores ocultos antes de la partición |
| Total Sectors (32) | 4 bytes | Tamaño total del volumen en sectores |
| FAT Size (32) | 4 bytes | Número de sectores que ocupa cada FAT en FAT32 |
| Extended Flags | 2 bytes | Información de control de la FAT |
| File System Version | 2 bytes | Versión del sistema FAT |
| Root Cluster | 4 bytes | Cluster inicial del directorio raíz |
| FSInfo Sector | 2 bytes | Sector donde se guarda información de clusters libres |
| Backup Boot Sector | 2 bytes | Sector donde se guarda una copia del Boot Sector |
| Reserved | 12 bytes | Espacio reservado |
| Drive Number | 1 byte | Número de unidad |
| Boot Signature | 1 byte | Indica presencia de campos extendidos |
| Volume ID | 4 bytes | Identificador del volumen |
| Volume Label | 11 bytes | Nombre del volumen |
| File System Type | 8 bytes | Tipo de sistema (FAT32) |
| Boot Code | ~420 bytes | Código ejecutable de arranque |
| Boot Sector Signature | 2 bytes | Firma final `55 AA` que valida el sector |
