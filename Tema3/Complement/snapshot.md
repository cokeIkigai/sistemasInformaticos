
# 💻 Ejercicio completo: Snapshot, NTFS y VirtualBox

### 🔹1. Conceptos básicos

¿Qué es un snapshot?

¿Qué problema resuelve frente a un sistema sin snapshots?

¿En qué se diferencia un snapshot de un backup?

---

### 🔹 2. Crear snapshots

* Crea un archivo en el escritorio llamado datos.txt con contenido: version1.
* Crea un snapshot en VirtualBox llamado estado_inicial.
* Modifica datos.txt a version2.
* Crea un nuevo archivo llamado nuevo.txt.
* Restaura el snapshot.

**Guarda con capturas de pantalla**

* Captura el archivo modificado y su versión de instantánea
* Házlo para la instantánea inicio como la modificada.

---

### 🔹 3. Exploración dentro de la máquina (Windows)

¿Dónde se encuentran los snapshots?

¿Aparecen como archivos visibles?

¿Qué tipo de archivos son, qué extensión tienen?

¿Qué pasa cuando borras uno de ellos?

---

### 🔹 4 . Comparativa técnica

¿Dependen los snapshots de VirtualBox del sistema de archivos (NTFS)?

¿Funcionan dentro o fuera del sistema operativo?

¿Qué diferencia hay entre, Snapshot de VirtualBox, Snapshot de ZFS o Btrfs?

---

### 🔹 5. NTFS y VSS

¿NTFS tiene snapshots reales?

¿Qué es VSS (Volume Shadow Copy)?

¿Qué guarda exactamente VSS?

¿En qué se diferencia de un snapshot de VirtualBox?

---

### 🔹 6. Snapshot vs Backup

Caso 1: Solo tienes snapshot y se rompe el disco.

¿Puedes recuperar la máquina? ¿Por qué?

Caso 2: Tienes backup en otro disco. ¿Puedes recuperar? ¿Qué cambia respecto al snapshot?

---

### 🔹 7. Rendimiento

¿Notas cambios en el rendimiento al hacer varios snapshot? ¿Sería cuestión de muchos snapshot creados o del tamaño de los cambios?

¿Por qué ocurre esto?
