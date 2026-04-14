
# 💻 Ejercicio completo: Snapshot, NTFS y VirtualBox

## 🎯 Objetivo
Analizar y comprender:
- Qué es un snapshot
- Dónde se almacena
- Diferencias entre NTFS, VSS y VirtualBox
- Relación con backup

---

## 🔹 PARTE 1: Experimento con snapshot

Crea un archivo en el escritorio llamado `datos.txt` con contenido `version1`.

Realiza un snapshot desde VirtualBox con nombre `estado_inicial`.

Modifica el archivo a `version2` y crea otro archivo llamado `nuevo.txt`.

Restaura el snapshot.

¿Que ocurre con `datos.txt` tras restaurar?
¿Que ocurre con `nuevo.txt`?
¿Que demuestra este comportamiento?

---

## 🔹 PARTE 2: Búsqueda dentro del sistema (trampa)

Busca dentro de Windows:

- Disco C:
- Escritorio
- Documentos
- Archivos de programa

¿Dónde se encuentran los snapshots?
¿Aparecen como archivos normales?
¿Por qué no puedes encontrarlos?

---

## 🔹 PARTE 3: Investigación fuera de la máquina virtual

Busca en el PC real la carpeta de la máquina virtual.

¿Dónde está ubicada la máquina virtual?
¿Que archivos principales encuentras?
¿Que extensión tiene el disco virtual?
¿Existe una carpeta llamada `Snapshots`?
¿Que tipo de archivos hay dentro?

---

## 🔹 PARTE 4: Análisis técnico

¿Quién crea realmente el snapshot?
¿Depende del sistema de archivos NTFS?
¿Funciona dentro o fuera del sistema operativo?
¿Que diferencia hay entre snapshot de VirtualBox y snapshot de ZFS/Btrfs?

---

## 🔹 PARTE 5: Comparación con NTFS

¿NTFS tiene snapshots reales?
¿Que es VSS (Volume Shadow Copy)?
¿En qué se diferencia VSS de un snapshot real?
¿Que guarda VSS frente a VirtualBox?

---

## 🔹 PARTE 6: Snapshot vs Backup

Imagina que tienes:

- Snapshot pero no backup
- Se rompe el disco del PC

¿Puedes recuperar la máquina?
¿Por qué?

Ahora imagina que tienes backup en otro disco:

¿Puedes recuperar?
¿Que diferencia clave hay?

---

## 🔹 PARTE 7: Funcionamiento interno

Tras crear un snapshot, aparecen nuevos archivos en la carpeta de la VM.

¿Que extensión tienen?
¿Son copias completas?
¿Que almacenan realmente?
¿Que ocurre con el disco base tras el snapshot?

---

## 🔹 PARTE 8: Rendimiento y uso

Crea varios snapshots y trabaja dentro de la máquina.

¿Notas cambios en el rendimiento?
¿A qué crees que se debe?

---

## 🔹 PARTE 9: Dibujo obligatorio

Representa mediante un esquema:

- PC real
- VirtualBox
- Disco base (.vdi)
- Snapshots (.vdi diferenciales)

Explica el flujo de datos entre ellos.

---

## 🔹 PARTE 10: Reflexión final

Explica con tus palabras:

- Qué es un snapshot
- Dónde se guarda realmente
- Por qué no aparece en NTFS
- Cuándo usar snapshot
- Cuándo usar backup

  [Guía](https://raywoodcockslatest.wordpress.com/2018/02/20/virtualbox-snapshots/)
