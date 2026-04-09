# PARTICIONES

## Ejercicio práctico 1 (manos a la obra)

Crear las particiones del ejercicio:

```
sudo fdisk /dev/sdb
```

Dentro de fdisk:

n → nueva partición

Crear 3 particiones:
- 300MB (simula 30GB)
- 500MB
- 200MB

p → ver tabla

w → guardar

---

## Ejercicio práctico 2 (formateo y montaje)

Formatear:

```
sudo mkfs.ext4 /dev/sdb1
sudo mkfs.ext4 /dev/sdb2
sudo mkfs.ext4 /dev/sdb3
```

Montar:
```
sudo mkdir /mnt/os /mnt/datos /mnt/backup

sudo mount /dev/sdb1 /mnt/os
sudo mount /dev/sdb2 /mnt/datos
sudo mount /dev/sdb3 /mnt/backup
```

Comprobar:
```
df -h
```
---

## Ejercicio práctico 3 (llenar y provocar problema)

**Simular uso real:**
```
sudo dd if=/dev/zero of=/mnt/datos/archivo_grande bs=1M count=400
```
---

## Ejercicio práctico 4 (dolor real 😈)

Plantearles:

👉 “Ahora DATOS necesita más espacio”

Que intenten:

¿pueden coger espacio de backup?
¿pueden ampliar sin borrar?

👉 Que prueben (y fallen):

sudo fdisk /dev/sdb

Conclusión práctica:

No es flexible
Riesgo de pérdida de datos
Muy limitado
⚙️ PARTE 2 — LVM (aquí viene la magia)

👉 Borrar particiones anteriores (o usar otro disco /dev/sdc)

## Ejercicio práctico 5 (crear LVM)

1. Crear PV

```
sudo pvcreate /dev/sdb
```

2. Crear VG

```  
sudo vgcreate mi_vg /dev/sdb
```

3. Crear LVs

```
sudo lvcreate -L 300M -n lv_os mi_vg
sudo lvcreate -L 500M -n lv_datos mi_vg
sudo lvcreate -L 200M -n lv_backup mi_vg
```

## Ejercicio práctico 6 (formatear y montar)

```js
sudo mkfs.ext4 /dev/mi_vg/lv_os
sudo mkfs.ext4 /dev/mi_vg/lv_datos
sudo mkfs.ext4 /dev/mi_vg/lv_backup

sudo mount /dev/mi_vg/lv_os /mnt/os
sudo mount /dev/mi_vg/lv_datos /mnt/datos
sudo mount /dev/mi_vg/lv_backup /mnt/backup
```

## Ejercicio práctico 7 (mismo problema… distinta solución)

👉 Volver a llenar /mnt/datos
```
sudo dd if=/dev/zero of=/mnt/datos/archivo_grande bs=1M count=450
```
🚀 Ejercicio clave (lo potente)

👉 “DATOS necesita más espacio”

SIN borrar nada:
```
sudo lvextend -L +200M /dev/mi_vg/lv_datos
```
Y luego:

```
sudo resize2fs /dev/mi_vg/lv_datos
```
👉 Comprobar:
```
df -h
```
