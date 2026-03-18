# 🧪 Ejercicios prácticos II — Resueltos

## 🟣 Ejercicio 1. Evolución memoria y velocidad

### 1) Tabla de evolución

- Valores aproximados y típicos de consumo/generalista, no de un único modelo concreto. 
- Sirven para ver la tendencia histórica:
  - Los HDD de mediados de los 2000 solían rondar 200–400 GB con velocidades secuenciales del orden de 50–70 MB/s;
  - Hacia 2010 los HDD de 1 TB eran comunes.
  - SSD de 80–256 GB ya se movían en torno a 250–520 MB/s.
  - 2015 los SSD SATA ya estaban cerca del techo de SATA (~540 MB/s).
  - 2025 los NVMe PCIe 4.0 de 1 TB rondan 7.450 MB/s de lectura.

### 2) Gráficas que haría en Excel

### 3) ¿En 20 años qué se estima de velocidad/capacidad?

Como estimación razonable para **2045–2046**:
- Lo más probable es que el almacenamiento dominante siga siendo de estado sólido, con más apilamiento 3D, mejor eficiencia y mayor paralelismo.
- En consumo, sería razonable imaginar SSD de varios TB por unidad doméstica y velocidades muy superiores a PCIe 4.0 actuales;
- Enn centros de datos seguirán coexistiendo SSD y HDD de muy alta densidad, porque el HDD mantiene ventaja de coste por TB y sigue creciendo con tecnologías como HAMR.

Estimación docente simple:

**SSD doméstico: 8–32 TB habituales**

**NVMe doméstico: 15–40 GB/s**

**HDD datacenter: decenas o incluso más de 100 TB por unidad**

Archivado masivo: podrían entrar tecnologías como DNA Storage o sistemas ópticos/holográficos, pero todavía no como almacenamiento normal de usuario.

### 4) ¿Qué es el límite de Shannon?

El **límite de Shannon** indica la máxima cantidad de información que puede transmitirse o almacenarse de forma fiable en un canal con un cierto ancho de banda y con ruido. En términos simples: aunque mejores la tecnología, hay un punto en que el ruido y las interferencias impiden seguir aumentando indefinidamente la cantidad de información útil.

¿Qué es el “ruido” en un SSD?
En SSD el ruido NO es solo eléctrico, también es físico:

- 🔋 Interferencias entre celdas
- 🌡️ Variaciones térmicas
- ⚡ Errores al leer cargas eléctricas
- 🧬 Desgaste de las celdas (wear)

### 5) Factores que determinan el límite de Shannon

Los factores clave son:

- Ancho de banda disponible
- Relación señal/ruido (SNR)
- Nivel de ruido del sistema
- Calidad de la codificación/corrección de errores

### 6) Cuatro dificultades principales para sobrepasarlo

- Aplicado al almacenamiento magnético y a la electrónica real, las dificultades más importantes son:
- Ruido e interferencias
- Límite físico al reducir el tamaño del bit
- Problemas de estabilidad térmica de bits muy pequeños
- Dificultad de leer/escribir señales cada vez más débiles y densas
- En HDD modernos esto se relaciona mucho con el límite superparamagnético y con la necesidad de tecnologías como HAMR para seguir aumentando densidad.

### 7) ¿Qué propiedad ha crecido más rápido?

La propiedad que más rápido ha crecido en estas décadas ha sido la capacidad, especialmente por:

- aumento de densidad de grabación en HDD,
- apilamiento 3D NAND en SSD,
- mejora de la fabricación de chips.

*La velocidad ha mejorado mucho, pero la capacidad ha crecido más de forma más espectacular.*

### 8) ¿Qué es la Ley de Moore?

La Ley de Moore es la observación de que el número de transistores en un chip integrado tendía a duplicarse aproximadamente cada dos años. No es una ley física, sino una tendencia histórica de la industria.

### 9) Tabla de transistores aproximados
Año	Transistores aproximados
1971	2.300
1982	134.000
1993	3.100.000
2006	291.000.000
2020	39.000.000.000

### 10) ¿Qué hecho hizo que la Ley de Moore se disparara y cuándo?

Lo que la disparó fue, sobre todo, la industrialización del circuito integrado y después la expansión de la tecnología MOS y de la fotolitografía cada vez más fina, especialmente desde los años 60–70. Gordon Moore señaló como factores clave la adopción de MOS, el aumento del tamaño de los chips con mejores rendimientos de fabricación y la reducción continua de las dimensiones mínimas.

### 11) ¿Qué tamaño tenían antes los transistores y qué relación hay con los actuales?

Como referencia clara, el Intel 4004 de 1971 usaba un proceso de 10 micrómetros (10 µm). Hoy se habla de nodos de 2 nm en prototipos avanzados. 
Eso significa, a nivel lineal, una reducción de unas 5.000 veces; dicho al revés, 2 nm es solo el 0,02% de 10 µm. 
Si lo miras por superficie, el salto es muchísimo mayor todavía.

### 12) ¿Qué tamaño tendría un disco de 1 Tb si los transistores fueran del tamaño anterior?

Aquí hay que contestar con cuidado: no se puede calcular de forma exacta porque la capacidad de un disco no depende solo del tamaño del transistor, sino también de la densidad del medio de almacenamiento, del cabezal, de la electrónica de control y del sistema de codificación.

**Como aproximación didáctica:**

- si la electrónica integrada tuviera tamaños de hace 1971, sería enorme comparada con la actual;

- la miniaturización de transistores ha sido una condición clave para controlar y gestionar almacenamientos masivos modernos;

- en un SSD, mantener la misma capacidad con transistores muchísimo mayores implicaría dispositivos físicamente descomunales.

13) ¿Qué tamaño físico tendría un sistema para almacenar 1 TB con tecnología de HDD de hace décadas?

El IBM RAMAC de 1956 almacenaba unos 5 millones de caracteres de 6 bits, aproximadamente del orden de unos pocos MB, en una unidad del tamaño de grandes armarios/refrigeradores. Si tomas la cifra popular aproximada de 5 MB, para llegar a 1 TB necesitarías unas 200.000 unidades equivalentes. Eso no sería “un disco”, sino prácticamente un edificio o varios pabellones llenos de armarios de almacenamiento.

### 🔴 Ejercicio 2. Limpieza de disco / Defraggler

Qué pondrías en la práctica
Pasos

Abrir Defraggler

Seleccionar unidad C:

- Analizar

- Elegir limpieza si procede

- Desfragmentar

Hacer captura de:

ventana principal

proceso de desfragmentación

resultado final

Partes de la ventana que puedes describir

Lista de unidades

Mapa de bloques del disco

Porcentaje de fragmentación

Archivos fragmentados

Botón Analizar

Botón Desfragmentar

Estado / progreso

Información del disco (capacidad, libre, sistema de archivos)

¿Qué es lo que no se puede desfragmentar y por qué?

Normalmente no se pueden desfragmentar fácilmente algunos archivos del sistema en uso, porque Windows los tiene bloqueados mientras el sistema está funcionando. Entre ellos suelen estar:

- archivos de sistema críticos,

- algunos metadatos del sistema de archivos,

- el archivo de hibernación,

- y en ciertos casos el archivo de paginación o partes protegidas del sistema.

La razón es que están siendo usados por el sistema operativo y moverlos en caliente puede comprometer la estabilidad del arranque o del propio sistema.

🟢 Ejercicio 3. Liberar espacio y compresión
1) Tres acciones para liberar espacio sin borrar archivos importantes

Vaciar temporales y cachés

Desinstalar programas que no se usan

Mover archivos pesados a otro disco o a la nube

Comprimir carpetas poco usadas

Vaciar papelera

Eliminar versiones duplicadas de archivos

2) ¿Cuál es el proceso de comprimir archivos en Windows?

En Windows, con NTFS, la compresión puede ser transparente: el sistema guarda el archivo comprimido en disco, pero cuando una aplicación lo abre lo ve como si estuviera normal. También puede hacerse creando archivos .zip u otros formatos. Microsoft indica que la compresión NTFS se realiza de forma transparente para las aplicaciones.

Pasos típicos

Clic derecho sobre archivo o carpeta

Propiedades

Opciones avanzadas

Marcar Comprimir contenido para ahorrar espacio en disco

3) ¿Qué % de eficacia hace?

No existe un porcentaje fijo. Depende totalmente del tipo de archivo:

Texto, código, CSV, logs, documentos: comprimen muy bien

JPG, MP4, MP3, PDF ya optimizados: comprimen poco

Programas y binarios: compresión media

Como orientación:

archivos ya comprimidos pueden quedarse en 95–100% del tamaño original

archivos de texto o código pueden reducirse mucho más.

4) Diferencias entre .rar, .zip y .7z

En general:

ZIP: más compatible, suele comprimir menos

RAR: buena compresión, formato propietario

7Z: normalmente la mejor compresión, aunque puede tardar más y no siempre es el más compatible por defecto

Respuesta tipo para el ejercicio

Para el mismo archivo, normalmente 7z consigue el tamaño más pequeño, RAR queda cerca y ZIP suele ocupar algo más. Sin embargo, el resultado cambia según el tipo de archivo: en vídeos, música o imágenes ya comprimidas, la diferencia entre formatos puede ser mínima.

🟠 Ejercicio 4. Diferenciar conceptos
Desfragmentación

Reorganiza los fragmentos de archivos en un HDD para que queden más continuos y el cabezal tenga que moverse menos. En SSD no aporta el mismo beneficio y puede ser contraproducente si se hace como en un HDD.

TRIM

Es una orden para SSD que avisa qué bloques ya no contienen datos útiles, para que el SSD los prepare internamente y mantenga rendimiento y vida útil.

CHKDSK

Es una utilidad de Windows que comprueba el sistema de archivos y busca/corrige errores lógicos del disco. No reorganiza archivos como la desfragmentación; su objetivo es verificar y reparar estructuras del sistema de archivos.

Wear Leveling

Es una técnica propia de memorias flash/SSD que reparte las escrituras entre distintas celdas para que no se desgasten siempre las mismas.

Esquema rápido

Desfragmentación → ordena archivos en HDD

TRIM → optimiza espacio libre en SSD

CHKDSK → busca y corrige errores

Wear Leveling → reparte desgaste en SSD

🔴 Ejercicio 5. ¿Qué pasaría si…?
1) ¿Qué pasaría si todos los ordenadores usaran solo HDD?

Tendríamos:

arranques más lentos,

apertura de programas más lenta,

peor rendimiento general,

peor respuesta en multitarea,

aunque seguiría siendo una solución barata por TB.

Los HDD siguen siendo muy valiosos en almacenamiento masivo, pero para sistema operativo y uso interactivo el SSD es claramente superior en latencia y velocidad.

2) ¿Qué pasaría si solo existieran SSD y no HDD?

Ganaríamos en:

velocidad,

silencio,

menor latencia,

resistencia a golpes,

menor consumo en muchos escenarios.

Pero perderíamos la gran ventaja del HDD: coste bajo por TB para copias masivas, archivado y centros de datos de gran capacidad. Por eso hoy siguen coexistiendo.

3) ¿Qué tecnología dominará dentro de 20 años?

La apuesta más razonable es:

SSD/NVMe y sus sucesores en equipos personales y rendimiento,

HDD de ultra alta densidad en archivado y centros de datos mientras sigan siendo más baratos por TB,

y tecnologías como DNA Storage u opciones ópticas/holográficas para nichos de archivo a largo plazo, no como reemplazo inmediato del SSD del usuario medio.

Tecnologías futuras
DNA Storage

Consiste en codificar bits digitales en secuencias de ADN sintético usando las bases A, C, G y T. Tiene enorme densidad y potencial para archivado muy largo, pero hoy sigue siendo compleja y cara para uso normal.

Memoria 3D XPoint

Fue una tecnología no volátil desarrollada por Intel y Micron, situada entre NAND y DRAM en latencia/rendimiento. Comercialmente se conoció sobre todo por Intel Optane. Su problema fue la dificultad de escalarla económicamente, y tanto Micron como Intel acabaron frenando o finalizando su desarrollo comercial.

Holographic Storage

Almacena datos como patrones de interferencia de luz dentro de un medio óptico o cristalino, usando láseres. Su idea fuerte es guardar mucha información en volumen, no solo en superficie. Sigue siendo prometedora para nube/archivo, pero todavía no es tecnología doméstica común.

✅ Conclusión final corta

La evolución del almacenamiento ha seguido dos caminos claros:

más capacidad, gracias a mayor densidad y miniaturización;

más velocidad, sobre todo con el salto de HDD a SSD y después a NVMe.

La capacidad ha sido la propiedad que más ha crecido, mientras que la Ley de Moore y la miniaturización del transistor han hecho posible controlar y fabricar dispositivos muchísimo más potentes y compactos. A futuro, el usuario normal seguirá dependiendo sobre todo de almacenamiento sólido, y las tecnologías experimentales quedarán primero para archivado masivo o casos muy especializados.

Puedo convertirte esto en una versión para alumnos, más corta, con lenguaje más directo y formato Markdown para entregar.
