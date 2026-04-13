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

---

## 📊 Diferencias clave: Journaling vs Copy-on-Write vs Snapshot vs Backup

| Concepto | 🧾 Journaling | 🧬 Copy-on-Write (CoW) | 📸 Snapshot | 💾 Backup |
|----------|--------------|------------------------|-------------|-----------|
| **Qué es** | Registro previo de operaciones | Escritura en copia nueva | “Foto” del estado del sistema | Copia completa de datos |
| **Objetivo** | Evitar corrupción tras fallos | Garantizar integridad total | Recuperar estados anteriores | Recuperación ante pérdida total |
| **Cómo funciona** | Escribe en journal → luego en disco | No sobrescribe → crea nuevos bloques | Usa CoW para congelar estado | Copia datos a otro medio |
| **Protege contra** | Apagones, errores de sistema | Corrupción de datos | Cambios accidentales | Borrado, ransomware, fallo físico |
| **Nivel de protección** | Medio | Alto | Alto (local) | Muy alto |
| **Recuperación** | Reejecuta operaciones del journal | Siempre consistente | Vuelve a un punto anterior | Restaura copia completa |
| **Impacto rendimiento** | Bajo | Medio | Muy bajo | Alto (depende tamaño) |
| **Uso de espacio** | Bajo | Medio | Bajo (solo cambios) | Alto |
| **Tiempo de recuperación** | Rápido | Inmediato | Muy rápido | Lento |
| **Depende de…** | Sistema de archivos | Sistema de archivos | Normalmente CoW | Sistema externo |
| **Ejemplos** | EXT4, NTFS | ZFS, Btrfs, APFS | ZFS, Btrfs, APFS | NAS, cloud, discos externos |

