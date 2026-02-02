# IPv6 - Protocolo de Internet versión 6

**IPv6** (Internet Protocol version 6) es la versión más reciente del Protocolo de Internet (IP), la capa de comunicaciones que proporciona un sistema de identificación y localización para ordenadores en redes y enruta el tráfico a través de Internet. IPv6 fue desarrollado por el *Internet Engineering Task Force* (IETF) para abordar el agotamiento a largo plazo de direcciones IPv4.

| **Aspecto** | **Detalle** |
|-------------|-------------|
| **Estado** | Estándar de Internet (RFC 8200) |
| **Introducido** | Diciembre de 1998 |
| **Reemplaza a** | IPv4 (RFC 791) |
| **Longitud de dirección** | 128 bits |
| **Espacio de direcciones** | 3.4×10³⁸ direcciones |
| **Notación** | Hexadecimal, ocho grupos de cuatro dígitos |

## Contenido
1. [Historia](#historia)
2. [Motivación y desarrollo](#motivación-y-desarrollo)
3. [Características técnicas](#características-técnicas)
4. [Formato de dirección](#formato-de-dirección)
5. [Tipos de direcciones](#tipos-de-direcciones)
6. [Transición desde IPv4](#transición-desde-ipv4)
7. [Estado de implementación](#estado-de-implementación)
8. [Véase también](#véase-también)
9. [Referencias](#referencias)

---

## Historia

### Antecedentes
El desarrollo de IPv6 comenzó a principios de la década de 1990 cuando se hizo evidente que el espacio de direcciones de 32 bits de IPv4 (aproximadamente 4.300 millones de direcciones) sería insuficiente para el crecimiento futuro de Internet. La IETF formó el Grupo de Trabajo de IP de Próxima Generación (IPng) en 1994 para estandarizar el protocolo.

### Publicación del estándar
La especificación inicial de IPv6 se publicó como **RFC 1883** en diciembre de 1995. La versión actual del estándar es **RFC 8200**, publicada en julio de 2017, que obsoleta el RFC 2460.

### Línea de tiempo clave
- **1994**: Formación del grupo de trabajo IPng
- **1995**: RFC 1883 (primera especificación)
- **1998**: RFC 2460 (especificación principal)
- **2008**: ICANN añade registros AAAA al DNS raíz
- **2011**: Agotamiento del pool central de IPv4 (IANA)
- **2012**: Lanzamiento mundial de IPv6 (World IPv6 Launch)
- **2017**: RFC 8200 (estándar actual)

## Motivación y desarrollo

### Agotamiento de IPv4
El principal impulsor para IPv6 fue el **agotamiento del espacio de direcciones IPv4**. El último bloque de direcciones IPv4 fue asignado por la IANA a los Registros Regionales de Internet (RIR) el 3 de febrero de 2011.

| **Región** | **Fecha agotamiento IPv4** |
|------------|----------------------------|
| APNIC (Asia-Pacífico) | 15 abril 2011 |
| RIPE NCC (Europa) | 14 septiembre 2012 |
| LACNIC (América Latina) | 10 junio 2014 |
| ARIN (Norteamérica) | 24 septiembre 2015 |
| AFRINIC (África) | (Todavía disponible) |

### Limitaciones de IPv4
1. **Espacio de direcciones insuficiente**
2. **Complejidad del enrutamiento** debido a fragmentación CIDR
3. **Falta de características de seguridad integradas**
4. **Configuración manual** o dependencia de DHCP
5. **NAT extensivo** que rompe el modelo end-to-end

### Equipo de diseño
Los principales diseñadores de IPv6 fueron:
- **Steve Deering** (Xerox PARC)
- **Robert Hinden** (Nokia/ICANN)
- **Paul Francis** (NTT)
- **Erik Nordmark** (Sun Microsystems)

## Características técnicas

### Mejoras sobre IPv4
IPv6 introduce varias mejoras significativas sobre IPv4:

#### 1. Espacio de direcciones ampliado
- **128 bits** frente a 32 bits de IPv4
- **2128 = 340.282.366.920.938.463.463.374.607.431.768.211.456 direcciones**
- Aproximadamente **6.7×1017 direcciones por mm²** de superficie terrestre
