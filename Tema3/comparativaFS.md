📊 Comparativa de sistemas de archivos
|Característica	|FAT32	|exFAT	|NTFS	|EXT4	|APFS	|ZFS	|Btrfs|
|---|---|---|---|---|---|---|---|
|Tipo	|Básico	|Básico moderno	|Journaling	|Journaling	|CoW	|CoW	|CoW|
|Compatibilidad	|Muy alta	|Muy alta	|Alta (Windows)	|Linux	|Apple	|Unix/Linux	|Linux|
|Tamaño máx archivo	|4 GB	|Muy alto	|Muy alto	|Muy alto	|Muy alto	|Muy alto	|Muy alto|
|Tamaño máx volumen	|~2 TB	|Muy alto	|Muy alto	|Muy alto	|Muy alto	|Muy alto	|Muy alto|
|Journaling	|❌	|❌	|✅	|✅	|❌	|❌	|❌
|Copy-on-Write	|❌	|❌	|❌	|❌	|✅	|✅	|✅
|Snapshots	|❌	|❌	|❌	|❌	|✅	|✅	|✅
|Integridad de datos	|Baja	|Baja	|Media	|Media-alta	|Alta	|Muy alta	|Alta|
|Recuperación fallos	|❌	|❌	|✅	|✅	|✅	|✅	|✅|
|Fragmentación	|Alta	|Media	|Media	|Baja	|Baja	|Baja	|Media|
|Rendimiento	|Alto (simple)	|Alto	|Alto	|Muy alto	|Alto	|Medio	|Medio|
|Uso típico	|USB antiguos	|USB modernos	|Windows	|Linux general	|macOS/iOS	|Servidores críticos	|Linux avanzado|
