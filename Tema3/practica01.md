# Ejercicio: “Forense de almacenamiento en una empresa”

Imaginaos que trabajas como técnico/a junior de sistemas en una pequeña empresa que tiene varios equipos y servidores.
Te encargan analizar qué sistema de archivos conviene en cada caso y detectar riesgos reales.

La empresa tiene estas necesidades:

- **PC de administración con Windows**
  - Guarda documentos, PDFs, hojas Excel y datos sensibles.
  - Hay varios usuarios en el mismo equipo.
  - Quieren permisos por usuario y cifrado.
- **Servidor Linux de desarrollo**
  - Guarda proyectos, bases de datos de pruebas y logs.
  - Necesitan estabilidad y buen rendimiento.
  - No quieren complicarse demasiado.
- **MacBook del diseñador**
  - Trabaja con SSD.
  - Necesita seguridad, rapidez y copias rápidas del sistema.
- **NAS de copias de seguridad**
  - Guarda backups de máquinas virtuales y carpetas compartidas.
  - Lo más importante es detectar corrupción silenciosa y poder recuperar datos.
- **Pendrive para intercambiar archivos**
  - Se conecta en Windows, Linux, macOS, televisores y consolas.
  - A veces meten vídeos grandes de más de 4 GB.

## 🔹Tarea principal

Debes elaborar un informe técnico comparativo proponiendo el sistema de archivos más adecuado para cada caso. No vale solo con poner el nombre. Hay que justificarlo técnicamente.

### 🔹 Parte 1. Tabla comparativa completa

Completa estemodelo de tabla, en caso de ser pequeña, utilizar excel para completarla.

|Caso	|Sistema recomendado	|Razón principal	|Ventajas	|Limitaciones	|Alternativa posible|
|---|---|---|---|---|---|
|FAT32||||||
|NTFS||||||
|EXT4||||||
|APFS||||||
|ZFS||||||
|Btrfs||||||
|exFAT||||||

---

### 🔹 Parte 2. Justificación técnica real

Para cada uno de los 5 necesidades, escribe entre 8 y 12 líneas explicando:

- ¿Por qué ese sistema sí encaja? ¿Qué problema resuelve? ¿Qué funciones usa? ¿Qué pasaría si eligieras mal otro sistema?

*Ejemplo de ideas que deben aparecer según el caso, así podemos expresarnos con el lenguajes correcto para el tema específico.*

`permisos` `journaling` `compatibilidad` `límite de tamaño de archivo` `snapshots` `copy-on-write` `checksums`  
`cifrado` `compresión` `tolerancia a fallos` `rendimiento en SSD` `recuperación ante errores` 

---

### 🔹 Parte 3. “Corregir al técnico”

En cada necesidad, imagina que un técnico ha elegido mal el sistema de archivos. Debes explicar qué fallo real aparecería.

Ejemplos del tipo de respuesta que se espera:

*“Si en el pendrive usamos FAT32, un vídeo de 8 GB no se podrá copiar”.*

|Caso Mala elección	   |Problema que aparecería	|Consecuencia real|
|----------------------|-------------------------|-----------------|
| *Pendrive / FAT32* | *FAT32 tiene un límite de tamaño de archivo de **4 GB − 1 byte**.* | *El sistema no permitirá copiar el vídeo de 8 GB y mostrará un error de tamaño de archivo* |

---

### 🔹 Parte 4. Caso práctico de incidencia

“Tras un apagón, un usuario dice que varios archivos del servidor parecen corruptos. Además, en el NAS de copias hay sospecha de corrupción silenciosa en algunos datos antiguos.”

**Debes responder:**

¿En qué sistema sería más grave este problema: FAT32, NTFS, EXT4, APFS o ZFS? ¿Porqué?

¿Cuál tendría mejores mecanismos de protección? ¿Porqué?

¿Qué tecnología ayuda a prevenir o detectar el problema en cada caso? ¿Porqué?

¿Qué comando, herramienta o acción revisarías primero? ¿Porqué?

---

### 🔹 Parte 5. Diseño de propuesta final

La empresa te pide una propuesta definitiva. Debes entregar una arquitectura breve como esta:

**Equipo administración → ______**
(justificar)

**Servidor Linux → ______**
(justificar)

**MacBook diseño → ______**
(justificar)

**NAS backups → ______**
(justificar)

**Pendrive intercambio → ______**
(justificar)

---

### 🔹 Parte 6. Parte de investigación

Busca y explica:

- Diferencia entre journaling y copy-on-write.

- Diferencia entre checksum y redundancia.

- Por qué ZFS detecta mejor corrupción silenciosa que NTFS o EXT4.

- Por qué APFS está tan orientado a SSD.

- Cuándo usarías exFAT en vez de FAT32.

---

### 📕 ENTREGA

Se realizará por grupos

El trabajo debe incluir:

- Portada
- Introcucción al problema que se nos plantea de forma general
- Cada parte del análisis
- Conclusión final grupal de 8 líneas
- Formato de entrega:
    - Markdown
    - Word
    - PDF
 
- Preparación de la exposición.
