# 🧪 Actividad 2: Particiones vs LVM (práctica)

Entender la diferencia entre particiones tradicionales y LVM mediante práctica o simulación.

### **Ejercicio 1**

Imagina un disco de **100GB**.

Define cómo lo particionarías para:

- Sistema operativo → 30GB  
- Datos → 50GB  
- Backup → 20GB  

Responde:

- ¿Qué tipo de particiones crearías?  
- ¿Qué pasaría si necesitas más espacio en “Datos”?  
- ¿Qué limitaciones encuentras?

---

### **Ejercicio 2 (análisis)**

- ¿Se puede ampliar una partición fácilmente?  
- ¿Qué riesgos hay al modificar particiones?

---

## ⚙️ Parte B: LVM aplicado

### **Ejercicio 3**

Ahora con el mismo disco (100GB):

Diseña el mismo esquema usando LVM:

- Define:
  - PV  
  - VG  
  - LVs (con tamaños)

---

### **Ejercicio 4 (escenario real)**

El volumen de **Datos (50GB)** se queda pequeño.

Responde:

- ¿Qué harías en LVM?  
- ¿Necesitas borrar algo?  
- ¿Cómo sería el proceso?

---

### **Ejercicio 5 (ampliación)**

Añades un nuevo disco de **100GB** al sistema.

Responde:

- ¿Cómo lo añadirías a LVM?  
- ¿Qué comando o paso conceptual realizarías?  
- ¿Cómo ampliarías un LV existente?
