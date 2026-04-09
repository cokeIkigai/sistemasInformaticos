# 📕 Particiones vs LVM (modo exploración)

**Objetivo**

Configurar almacenamiento en Linux y resolver un problema real de falta de espacio.
Debes investigar, probar y decidir qué comandos son lo que hay que utilizar.

---


### 1. Diseña el disco

Dispones de un disco vacío (`/dev/sdb`).

Debes:

- Crear 3 particiones:
  - Sistema → 300MB (1/3 total)
  - Datos → 500MB (1/2 total)
  - Backup → 200MB (1/3 total)

Se debe guardar en tu documento de entrega lo siguiente:

- Esquema de particiones (tabla o dibujo o captura)
- Comandos utilizados
- Captura de `lsblk` o `fdisk -l`

---

## 2. Preparar el sistema

1. Formatear las particiones creadas anterioremente
2. Montarlas en:
  - `/mnt/os`
  - `/mnt/datos`
  - `/mnt/backup`

Se debe guardar en tu documento de entrega lo siguiente:
- Comandos utilizados
- Captura de `df -h`

---

## 3. Simular uso real

Genera datos dentro de `/mnt/datos` hasta casi llenarlo.

Se debe guardar en tu documento de entrega lo siguiente:
- Comando usado
- Estado final del disco (`df -h`)

---

## 4. Problema real

El volumen `/mnt/datos` se queda sin espacio. Debes intentar aumentar su tamaño usando el espacio de backup

- ¿Has podido hacerlo sin perder datos?
- ¿Qué pasos serían necesarios?
- ¿Qué riesgos hay?
- Conclusión sobre particiones tradicionales

---
<!--
# 🔹 PARTE 2 — LVM (resuelve el problema)

## 🧩 Reto 5: Nuevo diseño con LVM

Usando el mismo disco (o uno nuevo):

Debes:

- Crear un sistema LVM con:
  - 1 PV
  - 1 VG
  - 3 LVs (mismos tamaños que antes)

### 📌 Entrega:
- Esquema:
  - PV → VG → LV
- Comandos utilizados
- Salida de `lvdisplay` o `lsblk`

---

## 🧩 Reto 6: Preparación

Debes:

- Formatear y montar los LVs igual que antes

### 📌 Entrega:
- Evidencia de montaje (`df -h`)

---

## 🧩 Reto 7: Mismo problema

Llena `/mnt/datos` otra vez hasta que esté casi completo.

---

## 🧩 Reto 8: Resolver sin romper nada

👉 Ahora debes ampliar `/mnt/datos`

### ⚠️ Condiciones:
- ❌ No puedes borrar datos  
- ❌ No puedes recrear el sistema desde cero  
- ✅ Debes usar LVM  

### 📌 Entrega:
- Comandos usados
- Resultado final
- Explicación de qué ha pasado internamente

---

# 🔥 PARTE 3 — NIVEL PRO

## 🧩 Reto 9: Añadir nuevo disco

Se añade `/dev/sdc` al sistema.

Debes:

- Integrarlo en el sistema LVM
- Usarlo para ampliar `/mnt/datos`

### ❓ Preguntas:
- ¿Qué ventaja aporta esto frente a particiones?
- ¿Qué capa estás modificando (PV, VG o LV)?

### 📌 Entrega:
- Comandos utilizados
- Explicación breve

---

# 🧠 REFLEXIÓN FINAL (obligatoria)

Responde:

1. ¿Qué sistema es más flexible? ¿por qué?
2. ¿Dónde has tenido más riesgo de pérdida de datos?
3. ¿Qué pasaría en un servidor real?
4. Explica con tus palabras qué es LVM (sin copiar definiciones)

---

# 💡 RETO INICIAL (opcional, nivel avanzado)

Solo con este enunciado:

> “Tienes un disco de 1GB.  
> Necesitas organizarlo para sistema, datos y copias de seguridad.  
> Además, debes poder ampliar ‘datos’ en el futuro sin perder información.”

👉 Diseña la solución SIN comandos al inicio.

Luego ejecútala.

---

# 🎓 OBJETIVO REAL DE LA PRÁCTICA

- Pensar antes de ejecutar  
- Equivocarse de forma controlada  
- Entender el problema real del almacenamiento  
- Descubrir por qué existe LVM  
