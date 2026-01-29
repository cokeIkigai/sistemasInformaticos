# Seguridad en redes: Wi-Fi (WPA2/WPA3), VPN y firewalls básicos

## 1. ¿Por qué importa la seguridad en redes?
En una red, los datos viajan por cables o por el aire (Wi-Fi). Si no protegemos la red, alguien puede:
- **Escuchar** el tráfico (robo de datos).
- **Manipular** comunicaciones (cambiar lo que llega).
- **Bloquear** servicios (dejarte sin conexión).

**Objetivo de la seguridad (CIA):**
- **Confidencialidad:** que no lo lea quien no debe.
- **Integridad:** que no lo modifiquen.
- **Disponibilidad:** que el servicio funcione.

📷 *Imagen sugerida:* diagrama “Dispositivo → Router/AP → Internet” con un atacante cerca (Wi-Fi) y otro en la red.

---

## 2. Wi-Fi segura: del WPA2 al WPA3

### 2.1. WPA2 (lo clásico)
**WPA2** ha sido el estándar más usado durante años.
- Usa **AES** para cifrar el tráfico (cifrado fuerte).
- Normalmente se configura como **WPA2-PSK** (una contraseña para todos).

**Punto clave:** aunque el cifrado sea fuerte, el sistema puede sufrir ataques si la contraseña es débil o si se explotan vulnerabilidades del protocolo.

📷 *Imagen sugerida:* icono de candado + “AES” + “WPA2”.

---

### 2.2. Vulnerabilidades conocidas (idea general)
Con el tiempo se han encontrado fallos en cómo se negocian claves o se gestiona la conexión. Ejemplo famoso: **KRACK (2017)**, que mostró que WPA2 no era “perfecto”.

**Traducción a lenguaje simple:** no significa que “WPA2 no sirva”, sino que **hay casos donde un atacante experto puede aprovechar debilidades** si se cumplen ciertas condiciones.

📷 *Imagen sugerida:* línea de tiempo: WPA2 → (KRACK 2017) → WPA3.

---

### 2.3. WPA3 (el salto)
**WPA3** mejora la seguridad, sobre todo contra:
- contraseñas adivinables,
- ataques de diccionario,
- capturas que luego se prueban “offline”.

Cambia la autenticación típica de WPA2-PSK por **SAE** (*Simultaneous Authentication of Equals*).

**SAE explicado fácil:**
- En WPA2-PSK, si alguien captura el “saludo” de conexión, puede intentar adivinar la contraseña **sin estar conectado** muchas veces (offline).
- En WPA3-SAE, esos intentos son mucho más difíciles: **cada intento obliga a interactuar**, y el protocolo está diseñado para resistir mejor fuerza bruta.

📷 *Imagen sugerida:* comparación visual:
- WPA2: “capturo handshake → pruebo miles offline”
- WPA3: “necesitas interacción → más difícil y más lento”

---

## 3. WPA2 vs WPA3 (comparativa rápida)

| Característica | WPA2 | WPA3 |
|---|---|---|
| Cifrado | AES (habitual) | AES (mejoras en el proceso de autenticación) |
| Autenticación doméstica | PSK (contraseña compartida) | SAE (más resistente a fuerza bruta) |
| Ataques de diccionario offline | Más viable si capturas tráfico y la clave es débil | Mucho más difícil |
| Recomendación actual | Solo si WPA3 no está disponible | Preferido siempre que se pueda |

📷 *Imagen sugerida:* tabla convertida a infografía.

---

## 4. Ejemplos prácticos (muy claros)

### Ejemplo 1: Casa / piso compartido (configuración recomendada)
**Objetivo:** Wi-Fi segura sin complicarse.
1. Activar **WPA3-Personal** (o **WPA2/WPA3 mixed** si hay dispositivos antiguos).
2. Contraseña larga: **mínimo 14–16 caracteres**, con frases tipo:
   - `M
