# 🧪 Actividad ampliada: Investigación sobre LVM

Comprender en profundidad cómo funciona LVM y su utilidad real en la gestión de almacenamiento. Responde de forma desarrollada (no tipo definición corta):

### **1. Definición y contexto**

- ¿Qué es LVM? Explica la idea general con un ejemplo sencillo  
- ¿Qué limitaciones tienen las particiones tradicionales?  
- ¿En qué situaciones reales usarías LVM? (servidores, bases de datos, etc.)

---

### **2. Conceptos clave (explicación + ejemplo)**

Explica cada uno con:
- definición  
- ejemplo real  

- **PV (Physical Volume)**  
- **VG (Volume Group)**  
- **LV (Logical Volume)**  

---

### **3. Funcionamiento (razonamiento)**

Explica el flujo completo: Disco → PV → VG → LV → Sistema de archivos


- ¿Qué ocurre si añades un disco nuevo al sistema?  
- ¿Qué pasaría si necesitas más espacio en un LV ya creado?

---

### **4. Ventajas y comparativa**

- Enumera al menos **4 ventajas** de LVM  
- Compara LVM vs particiones tradicionales en:
  - Flexibilidad  
  - Escalabilidad  
  - Mantenimiento  

---

### **5. Caso práctico razonado**

Tienes:
- Disco 1 → 500GB  
- Disco 2 → 500GB  

Responde:
- ¿Cómo los unirías con LVM?  
- ¿Qué VG crearías?  
- ¿Qué LVs podrías definir? (ej: sistema, datos, backups)  
- ¿Qué ventaja tiene frente a usar 2 discos separados?

---

### **6. Investigación extra (nivel medio-alto)**

- ¿Qué es un **snapshot en LVM**?  
- ¿Para qué se usa en entornos reales?  
- ¿Tiene alguna limitación?

---

## 🧠 Entrega

- Documento estructurado  
- Uso de esquemas o dibujos  
- Lenguaje propio (no copiar/pegar)

---
