# Enlace · Resumen completo de redes

CAPA I: páginas 1–110. CAPA II: páginas 1–72. Apuntes redactados sin imágenes originales; cifras históricas y ampliaciones se distinguen explícitamente.

## Modelos OSI y TCP/IP

Capa 1 · páginas 1–3

### Cómo usar el programa de estudio

Referencia al programa: páginas 1–1

La primera página presenta la asignatura y la carrera; no añade un concepto técnico independiente. La guía conserva su lugar en el mapa de cobertura para que puedas comprobar que se revisó el documento completo.

La ruta de CAPA I va desde los modelos de referencia y las señales hasta los medios guiados, las comunicaciones inalámbricas y los satélites. CAPA II comienza con servicios de enlace y termina con conmutación, STP y la actividad comparativa de switches de la página 72.

### Las siete capas OSI y sus funciones

Referencia al programa: páginas 2–2

El modelo OSI organiza la comunicación en siete niveles. Física representa y transmite bits; enlace delimita tramas, usa direcciones MAC y organiza el acceso al medio; red utiliza direccionamiento lógico y selecciona rutas. Transporte comunica procesos y puede ofrecer control de flujo y recuperación según el protocolo.

Sesión organiza el diálogo; presentación trata la representación, los formatos y el cifrado; aplicación ofrece servicios de red utilizados por programas. HTTP, DNS, FTP, SSH y DHCP son ejemplos del nivel de aplicación. TCP y UDP pertenecen a transporte; IP a red. UDP no promete la confiabilidad de TCP: no atribuyas a toda una capa una garantía que depende del protocolo.

Los puertos identifican servicios o procesos de transporte. El material recuerda HTTP 80, Telnet 23, DNS 53, SSH 22 y DHCP 67/68. No confundas un número de puerto con una dirección MAC ni con un puerto físico de un switch.

### Correspondencia OSI–TCP/IP y encapsulación

Referencia al programa: páginas 3–3

En la comparación del documento, aplicación de TCP/IP reúne aplicación, presentación y sesión de OSI. Transporte corresponde a transporte, Internet a red, y acceso al medio reúne funciones de enlace y física. Algunos textos usan una representación didáctica de cinco capas que separa estas dos últimas.

Al enviar información, cada nivel añade los datos de control que necesita: una unidad de transporte puede ir dentro de un paquete IP, que se transporta dentro de una trama y finalmente se representa como señales. En recepción se interpreta y retira cada envoltura. ARP relaciona direcciones IP y MAC dentro del enlace; su ubicación exacta en esquemas de capas varía, por lo que conviene aprender su función.

## Señales y Fourier

Capa 1 · páginas 4–11

### Señales y trabajo de la capa física

Referencia al programa: páginas 4–5

La capa física especifica cómo representar información sobre un medio: niveles eléctricos u ópticos, temporización, interfaces y características de transmisión. Para transportar bits se hace variar una propiedad observable, como tensión, corriente o luz. El receptor interpreta esas variaciones según un convenio.

Los límites físicos importan: un medio real introduce pérdidas, ruido y distorsión. La temporización permite identificar cuándo corresponde muestrear un símbolo. Por eso no basta con conectar dos equipos: emisor, medio y receptor deben ser compatibles en señalización y sincronización.

### Series de Fourier: fundamental, armónicas y coeficientes

Referencia al programa: páginas 6–9

La idea central de Fourier es representar una señal periódica mediante una componente continua y componentes sinusoidales. En la notación del material: g(t) = c/2 + Σ aₙ sen(2πnft) + Σ bₙ cos(2πnft), para n desde 1. La frecuencia fundamental es f = 1/T y la armónica n tiene frecuencia nf.

Los coeficientes indican cuánto aporta cada seno y coseno. Se calculan en un período: aₙ = (2/T)∫₀ᵀ g(t)sen(2πnft)dt; bₙ = (2/T)∫₀ᵀ g(t)cos(2πnft)dt; c = (2/T)∫₀ᵀ g(t)dt. Conocer la fundamental y los coeficientes permite reconstruir la señal bajo las condiciones usuales de la serie.

Ejemplo: si T = 2 ms, f = 500 Hz; las primeras armónicas están en 500, 1000 y 1500 Hz. Un pulso de forma abrupta necesita más componentes de alta frecuencia que una sinusoide simple.

### Frecuencia de corte, distorsión y ancho de banda

Referencia al programa: páginas 10–11

Un sistema de transmisión no conserva por igual todas las componentes de una señal. En el modelo simplificado de paso bajo del PDF, las frecuencias hasta una frecuencia de corte f꜀ se transmiten mejor y las superiores sufren mayor atenuación. Al cambiar las amplitudes relativas, se modifica la forma de onda recibida.

El ancho de banda físico se expresa en Hz y caracteriza un intervalo de frecuencias; la tasa de datos se expresa en bit/s. Se relacionan por el diseño de señalización y las condiciones del canal, pero no son la misma magnitud. Material, longitud, grosor y construcción del medio afectan su comportamiento. El ejemplo telefónico de unos 3100 Hz ilustra una banda limitada por filtros.

No interpretes la frecuencia de corte como una pared perfecta en un circuito real: es una referencia de su respuesta. Para el examen, relaciona pérdida de armónicas con distorsión y banda limitada con restricciones sobre las señales transmisibles.

Ampliación desde el artículo de Shannon: para un canal de ancho de banda B con ruido blanco gaussiano y potencia media de señal S y ruido N, C = B log₂(1 + S/N). C se expresa en bit/s y B en Hz; S/N es una razón lineal, no un número en decibelios. Por ejemplo, B = 3000 Hz y S/N = 15 dan C = 12.000 bit/s. Es un límite teórico bajo esas hipótesis, no una garantía de rendimiento ni una fórmula que figure en el PDF de clase.

Fuente: Claude E. Shannon. A Mathematical Theory of Communication (1948). https://people.math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf

## Cobre y medios guiados

Capa 1 · páginas 12–22

### Clasificación de medios y nombres de Ethernet

Referencia al programa: páginas 12–15

Los medios guiados conducen la señal por un soporte físico: coaxial, par trenzado y fibra. Los no guiados propagan ondas por el espacio. Para seleccionar un medio, compara ancho de banda, retardo, instalación, mantenimiento, costo y vida útil. Considera el enlace completo y su entorno.

La notación 10BASE-T del ejemplo identifica una familia de Ethernet: 10 expresa 10 Mb/s, BASE indica banda base y T identifica par trenzado. En otras denominaciones un sufijo histórico puede expresar una longitud aproximada; no conviertas cualquier sufijo en metros sin conocer la variante. Un conector parecido tampoco garantiza que dos enlaces soporten las mismas prestaciones.

### Coaxial: estructura, variantes y comparación

Referencia al programa: páginas 16–18

El coaxial consta de un conductor central, un aislante dieléctrico, una pantalla conductora y una cubierta protectora. Su geometría y blindaje ayudan a transportar señales controlando interferencias. La imagen del documento muestra un conector BNC y ejemplos históricos de redes de bus.

El material distingue 50 Ω para transmisión digital y 75 Ω para transmisión analógica, TV por cable, cable módem y aplicaciones metropolitanas. Los ohmios expresan impedancia característica, no velocidad. Sus ejemplos de redes coaxiales y longitudes pertenecen a variantes concretas de Ethernet, no a todo cable coaxial.

En la comparación del PDF, necesita menos repetidores que el par trenzado y resulta más económico que la fibra de su contexto; a cambio, se instala con más dificultad, cuesta más que el par trenzado y ocupa más ducto. Aprende la comparación como criterio relativo, no como una cotización universal.

### UTP, STP y FTP/ScTP

Referencia al programa: páginas 19–20

UTP emplea cuatro pares de cobre trenzados sin pantalla metálica. El trenzado ayuda a reducir acoplamientos e interferencia. El documento menciona RJ-45 y TIA/EIA-568-A/B; conviene distinguir la disposición de los pares de la categoría de prestaciones del cable.

STP añade protección metálica: en el ejemplo, cada par lleva una lámina y el conjunto tiene una envoltura. FTP o ScTP se presenta como pares UTP con una pantalla general. En denominaciones más precisas, el blindaje del conjunto y el de los pares se describen por separado.

La protección resulta útil ante interferencia, pero la instalación y las terminaciones también importan. Un blindaje no convierte automáticamente una categoría en otra ni sustituye una instalación correcta.

### Categorías, clases y una corrección importante

Referencia al programa: páginas 21–22

Las tablas del material comparan categoría 3/clase C (16 MHz), categoría 5 y 5e (100 MHz), categoría 6/clase E (200 MHz en el PDF) y categoría 7/clase F (600 MHz). También incluyen tipos de protección y costos relativos respecto a categoría 5: 0,7; 1; 1,2; 1,5 y 2,2. Son cifras del material original, no precios vigentes.

Aclaración verificada: Fluke Networks especifica categoría 6/clase E hasta 250 MHz, no 200 MHz, y categoría 6A/clase EA hasta 500 MHz. Esta diferencia queda explícita para que no memorices una errata como regla técnica. La frecuencia de certificación no se convierte directamente en Mb/s: cada tecnología exige determinadas prestaciones y condiciones de canal.

Corrección: categoría 6/clase E se especifica hasta 250 MHz; categoría 6A/clase EA, hasta 500 MHz.

Fuente: Fluke Networks. Network Engineer Tools and Troubleshooting Guide · tabla de cableado. https://www.flukenetworks.com/expertise/role/network-engineers

## Fibra óptica

Capa 1 · páginas 23–44

### Sistema óptico: emisor, fibra y detector

Referencia al programa: páginas 23–24

Un sistema óptico tiene una fuente de luz, una fibra que transporta la señal y un receptor que la convierte en señal eléctrica. El ejemplo del PDF asigna pulso de luz a 1 y ausencia a 0; es una representación introductoria, no la única señalización óptica posible.

El ancho de banda aprovechable depende también del emisor, detector y electrónica. Las cifras de 50 Tb/s, 10 Gb/s y 100 Gb/s que aparecen en estas páginas se conservan como referencias del contexto histórico de la clase, no como límites universales presentes de la fibra. Distingue capacidad física, capacidad de un equipo y tasa de un enlace específico.

### Refracción, reflexión interna y modos ópticos

Referencia al programa: páginas 25–27

Al pasar entre medios con diferentes índices de refracción, la dirección de la luz puede cambiar. El índice n = c/v compara la velocidad en vacío con la velocidad en el material. En la explicación de rayos de una fibra, el núcleo y el revestimiento permiten confinar luz bajo condiciones de reflexión interna total.

El diagrama compara trayectorias que recorren distancias diferentes. Esa diferencia puede extender temporalmente un pulso al llegar al receptor: es importante para entender la dispersión modal. La fibra monomodo se describe mejor mediante modos guiados que con un dibujo de múltiples rayos rebotando.

Si n = 1,5, la velocidad aproximada de la luz en ese material es 2 × 10⁸ m/s. Esto ayuda a estimar retardos de propagación, distintos del tiempo necesario para introducir todos los bits de una trama en el enlace.

La guía de la FOA explica el confinamiento mediante el índice del núcleo y del revestimiento y la reflexión interna total.

Fuente: The Fiber Optic Association. Total Internal Reflection in Optical Fiber. https://thefoa.org/tech/ref/basic/total_internal_reflection.html

### Multimodo, monomodo y construcción de la fibra

Referencia al programa: páginas 28–32

Multimodo admite varios modos de propagación; al tomar trayectorias distintas, los pulsos pueden ensancharse. Monomodo usa un núcleo mucho menor y permite mayores distancias para determinadas aplicaciones. El documento contrapone fibra multimodo de índice escalonado o gradual y fibra monomodo.

La estructura incluye núcleo, revestimiento óptico y protección. En el cable aparecen además elementos mecánicos de refuerzo y cubierta; distingue el revestimiento que guía la luz de la protección exterior. El material procede de vidrio de sílice de alta pureza; sílice no equivale a silicio elemental.

La elección depende de distancia, tasa, fuente óptica y transceptores compatibles. Los valores de núcleo y distancia que ilustra la comparación son ejemplos de tipos de fibra y enlaces, no una distancia garantizada para cualquier instalación.

### Conectores, paneles y empalmes

Referencia al programa: páginas 33–35

Los conectores permiten uniones desmontables; el material muestra ST, SC, LC, FC y arreglos de fibras. Un panel de parcheo ordena y facilita la conexión de enlaces. No uses el nombre del conector como prueba de que una fibra sea mono o multimodo: debe verificarse el sistema completo.

El empalme mecánico alinea y fija extremos; la fusión alinea y funde la fibra mediante un arco eléctrico. Se requieren corte preciso y limpieza. Toda unión puede introducir pérdida y reflexión. El PDF ejemplifica pérdidas de luz de 10–20 % en conectores y 10 % en empalme mecánico: trátalas como referencias de esa explicación, no como aceptación universal de un enlace.

Para comparar uniones se evalúan pérdidas y reflectancia; un buen empalme por fusión busca una transición de baja pérdida.

### LED, láser, fotodiodo y WDM

Referencia al programa: páginas 36–38

El documento compara LED y diodo láser semiconductor: el LED se presenta como económico, con larga vida y menor tasa; el láser como más eficiente y adecuado para mayores tasas y distancias, con mayor costo y sensibilidad térmica. Son tendencias de la comparación de equipos del material.

El fotodiodo recibe luz y genera una respuesta eléctrica. Su rapidez y la del resto del receptor influyen en la tasa, mientras el ruido exige potencia suficiente para distinguir la señal. La referencia a una respuesta de 1 ns no permite concluir por sí sola un límite de 100 Gb/s: hace falta un modelo completo del receptor y de la señalización.

WDM multiplexa canales mediante distintas longitudes de onda en una misma fibra. Piensa en varios colores de luz que transportan flujos diferenciables; no lo confundas con separar tramas por dirección MAC.

### Redes ópticas, ventajas, aplicaciones y límites

Referencia al programa: páginas 39–44

Las topologías del material incluyen estrella y anillo de enlaces punto a punto. La fibra se usa en LAN, troncales de largo recorrido, MAN y acceso de última milla o bucle del abonado. Puede transportar Ethernet: fibra y Ethernet no son alternativas del mismo nivel, porque una es medio físico y la otra una tecnología de red.

Sus ventajas incluyen alto ancho de banda, baja atenuación, inmunidad electromagnética y poco peso. El ejemplo compara mil pares de cobre de 1 km, con unos 8000 kg, con dos fibras de unos 100 kg para ilustrar la reducción de peso; no es una fórmula de dimensionamiento.

Sus límites incluyen cuidado ante curvaturas y roturas, herramientas y personal de instalación. La comunicación bidireccional puede usar dos fibras o distintas longitudes de onda en una. La dificultad de interceptación es una ventaja relativa, no una garantía de seguridad: el cifrado sigue teniendo sentido. El gráfico final sitúa los medios dentro del espectro electromagnético.

## Datos por la red eléctrica

Capa 1 · páginas 45–46

### Datos sobre líneas eléctricas (PLC)

Referencia al programa: páginas 45–46

PLC aprovecha el cableado eléctrico existente como canal de comunicación de datos. La energía de la red trabaja a frecuencias de 50 o 60 Hz según el sistema; las señales de datos utilizan componentes de frecuencia mucho mayor y deben convivir con un medio diseñado originalmente para energía.

La atenuación a altas frecuencias y el ruido de electrodomésticos dificultan la recepción. Un encendido o apagado puede originar perturbaciones y ráfagas de errores. El material menciona técnicas que toleran frecuencias dañadas y ráfagas, así como un ejemplo de 100 Mb/s; no promete esa tasa en cualquier vivienda.

La idea para el examen es evaluar la ventaja de reutilizar infraestructura frente a un canal eléctrico variable y ruidoso.

## Radio y microondas

Capa 1 · páginas 47–71

### Ondas electromagnéticas: frecuencia y longitud

Referencia al programa: páginas 47–50

Una carga eléctrica en movimiento puede generar ondas electromagnéticas. Maxwell formuló su descripción teórica y Hertz realizó demostraciones experimentales. Las comunicaciones inalámbricas aprovechan antenas para emitir y captar señales sin un cable entre los extremos. El material recuerda ALOHA, desarrollado para comunicar islas de Hawái, como antecedente de las redes inalámbricas.

La frecuencia f mide ciclos por segundo, en Hz. La longitud de onda λ es la distancia entre puntos equivalentes consecutivos, como dos máximos. En vacío λf = c, con c ≈ 3 × 10⁸ m/s. A mayor frecuencia, menor longitud de onda. En otro medio debe usarse su velocidad de propagación.

Ejemplo: a 2,4 GHz, λ en vacío es aproximadamente 0,125 m, es decir, 12,5 cm. Las dimensiones de una antena se relacionan con la longitud de onda, aunque el diseño no se reduce a una única regla de tamaño.

### Espectro y modulación

Referencia al programa: páginas 51–55

Los enlaces no guiados son útiles para movilidad y lugares donde no conviene desplegar cobre o fibra. El PDF organiza el estudio en radio, microondas, infrarrojo y luz. Son partes del espectro electromagnético con usos y comportamientos diferentes; las fronteras de clasificación dependen de la convención.

Se puede representar información modificando amplitud, frecuencia o fase de una portadora. Amplitud indica magnitud de la señal, frecuencia sus oscilaciones y fase su posición dentro del ciclo. Estas ideas preparan la distinción entre la forma física de la señal y los bits representados.

Los nombres de bandas incluyen VLF, LF, MF, HF, VHF, UHF, SHF y EHF. Evita aprender las traducciones informales del material como definición suficiente: la banda debe relacionarse con un rango de frecuencias. Las tablas históricas de aplicaciones no son una autorización para transmitir en esas frecuencias.

### Radio: propagación terrestre e ionosférica

Referencia al programa: páginas 56–61

El documento destaca generación relativamente sencilla, cobertura amplia, emisión omnidireccional y penetración de obstáculos a bajas frecuencias. Las ondas pueden propagarse cerca de la superficie o mediante trayectorias afectadas por la ionosfera. El ejemplo de AM se relaciona con propagación terrestre.

La interacción con obstáculos cambia con la frecuencia: difracción, reflexión, absorción y ruido influyen en el enlace. El esquema de rebote o refracción ionosférica sirve para comprender enlaces más allá del horizonte; no tomes la afirmación de que toda VHF regresa por la ionosfera como una regla general.

El ruido de motores y otras fuentes afecta la comunicación. Que el oído alcance aproximadamente 20 kHz describe sonido, no la capacidad humana de recibir ondas de radio: son fenómenos físicos distintos. Para estudiar, explica por qué el alcance no depende solo de la potencia transmitida.

### Microondas terrestres y línea de vista

Referencia al programa: páginas 62–63

Las microondas permiten enlaces direccionales mediante antenas, por ejemplo parabólicas. El PDF destaca trayectorias aproximadamente rectas, problemas para atravesar edificios y necesidad de repetidores cuando el trayecto es largo. La altura de las torres ayuda a despejar el horizonte; la curvatura terrestre puede obstruirlo.

La absorción atmosférica y la lluvia afectan determinadas bandas. La referencia de torres de 100 m separadas unos 80 km es un ejemplo geométrico de clase, no una garantía de diseño. La viabilidad real exige estudiar el trayecto y el margen del enlace.

Corrección comprobada: el PDF menciona hornos a 4 GHz; una referencia técnica de la FDA indica que la mayoría opera a 2450 MHz, aproximadamente 2,45 GHz. El aprendizaje de redes aquí es que una señal electromagnética puede interactuar con materiales y sufrir atenuación, no memorizar 4 GHz para un horno doméstico.

Aclaración de frecuencia: la mayoría de hornos de microondas opera alrededor de 2450 MHz, no 4 GHz.

Fuente: U.S. Food and Drug Administration. Procedures for Field Testing Microwave Ovens · apéndice I. https://www.hhs.gov/guidance/sites/default/files/hhs-guidance-documents/FDA/Procedures-for-Field-Testing-Microwave-Ovens.pdf

### Administración del espectro y contexto de Ecuador

Referencia al programa: páginas 64–67

El espectro debe coordinarse para evitar interferencias entre servicios. El material enumera radiodifusión, televisión, telefonía celular, navegación, policía, marina y otros usos. Presenta a la UIT/ITU como organismo internacional de coordinación y a FCC dentro del contexto de Estados Unidos.

La pregunta local del PDF se responde con una fuente oficial: ARCOTEL administra, regula y controla las telecomunicaciones y el espectro radioeléctrico en Ecuador. El Plan Nacional de Frecuencias organiza atribuciones y aplicaciones. Los procedimientos concretos pueden cambiar y deben consultarse en la regulación vigente.

El material compara concursos, sorteos y subastas como formas de asignación. Para el examen, diferencia coordinar bandas entre servicios, asignar frecuencias a usuarios y establecer condiciones técnicas; no son exactamente la misma operación.

Respuesta a la pregunta del PDF sobre Ecuador: ARCOTEL es la entidad encargada de administración, regulación y control del espectro.

Fuente: ARCOTEL. Preguntas frecuentes · ¿Qué es la ARCOTEL?. https://www.arcotel.gob.ec/1-preguntas-generales/

### Bandas ISM, 2,4 GHz, 5 GHz y 60 GHz

Referencia al programa: páginas 68–71

ISM significa industrial, científica y médica. El documento las utiliza para introducir aplicaciones que comparten ciertas bandas: redes inalámbricas, Bluetooth, teléfonos, periféricos y controles. Compartir una banda no significa transmitir sin condiciones: pueden existir límites de potencia y otras exigencias.

Las frecuencias de 902–928 MHz, 2,4 GHz y alrededor de 5,7 GHz aparecen como ejemplos del contexto del PDF. No todas tienen idénticas condiciones de uso en todos los países. La mención de LAN 802.3 en la tabla de 2,4 GHz debe distinguirse de 802.11, que corresponde a WLAN; 802.3 es Ethernet.

La página 71 relaciona espacios de televisión liberados con la transición digital y menciona 60 GHz para enlaces rápidos de corto alcance. Son ejemplos de reutilización y propiedades del espectro; las afirmaciones de saturación, costo o poca explotación de una banda pertenecen al momento del material.

## Infrarrojo y luz libre

Capa 1 · páginas 72–76

### Infrarrojo e IrDA

Referencia al programa: páginas 72–73

Los enlaces infrarrojos se usan para corto alcance. El material menciona controles remotos y comunicación entre equipos mediante IrDA. Los describe como económicos y direccionales; una barrera sólida puede impedir la conexión.

Que la señal no atraviese paredes ayuda a contenerla físicamente, pero también limita movilidad y cobertura. No confundas esta ventaja relativa con confidencialidad garantizada. Al pasar hacia frecuencias ópticas, propiedades como reflexión, bloqueo por objetos y alineación se vuelven centrales.

Para comparar con radio: ambos son enlaces electromagnéticos no guiados; el comportamiento frente a obstáculos y las aplicaciones son distintos.

### Óptica de espacio libre y enlace láser

Referencia al programa: páginas 74–76

Un enlace óptico de espacio libre comunica puntos mediante un haz de luz sin fibra. El ejemplo coloca láseres en azoteas para interconectar edificios. Un haz estrecho concentra energía, ofrece gran ancho de banda y exige apuntar con precisión.

Un trayecto óptico simple es unidireccional; una comunicación en ambos sentidos requiere equipos o canales de retorno. La comparación del PDF presenta costo bajo e instalación relativamente sencilla, pero el diseño debe considerar alineación, vibraciones y ambiente.

La lluvia y niebla densa atenúan o dispersan la luz. El diagrama del día soleado ilustra turbulencia térmica que desvía el haz: no significa que todo enlace láser falle siempre con sol. Para estudiar, explica cómo el medio abierto puede alterar incluso una señal muy direccional.

## Satélites de comunicaciones

Capa 1 · páginas 77–110

### Del reflector pasivo al transpondedor

Referencia al programa: páginas 77–78

La introducción histórica compara señales reflejadas en globos o en la Luna con satélites artificiales. Un reflector pasivo devuelve una fracción de la señal; un repetidor activo recibe y amplifica antes de retransmitir.

Un satélite de comunicaciones tiene transpondedores que atienden partes del espectro. En el diseño de tubo doblado recibe una señal, la amplifica y la retransmite en otra frecuencia. Separar frecuencias de subida y bajada ayuda a distinguir ambos trayectos. Uplink es Tierra–satélite; downlink es satélite–Tierra.

Aprende la secuencia física del enlace antes de memorizar ejemplos de operadores.

### Órbitas, período, cobertura y retardo

Referencia al programa: páginas 79–81

La relación de Kepler indica que, para órbitas comparables alrededor de la Tierra, el período aumenta con el tamaño de la órbita: T es proporcional a a^(3/2), donde a es el semieje mayor. En una órbita circular, a coincide con el radio medido desde el centro terrestre; no es únicamente la altura sobre la superficie.

El gráfico compara GEO, MEO y LEO en altura, retardo y número de satélites necesarios. Una órbita alta suele abarcar más superficie y requerir más recorrido de señal; una baja suele tener una huella menor y exigir más satélites para cobertura continua.

Los retardos ilustrativos de 270 ms, 35–85 ms y 1–7 ms del cuadro dependen del trayecto considerado. No son latencias garantizadas de Internet. Distingue ida, ida y vuelta, enlaces con hub y retrasos de procesamiento.

### GEO, Clarke y antecedentes históricos

Referencia al programa: páginas 82–85

Una órbita geoestacionaria mantiene al satélite aproximadamente fijo respecto a un punto del ecuador. Es circular, ecuatorial y su período coincide con la rotación terrestre. El PDF redondea la altura a 35.800 km; NOAA indica unos 35.786 km. Una antena terrestre puede apuntar a una posición fija sin seguir el movimiento aparente de un LEO.

El material atribuye a Arthur C. Clarke la propuesta de comunicaciones geoestacionarias de 1945 e introduce el cambio de posibilidades con la electrónica de estado sólido. Las referencias a Sputnik I (1957) y Telstar (1962) sitúan hitos históricos. La diapositiva con citas de Clarke es contexto cultural, no una ley que permita calcular capacidad o latencia.

NOAA sitúa la órbita geoestacionaria aproximadamente a 35.786 km sobre el ecuador.

Fuente: NOAA CoastWatch. Geostationary Earth Orbit Satellite (GEO). https://oceanwatch.noaa.gov/cwn/platform-types/geostationary-earth-orbit-satellite-geo.html

### Posiciones orbitales, bandas y huellas

Referencia al programa: páginas 86–89

El material introduce coordinación internacional de posiciones orbitales y frecuencias para limitar interferencia entre sistemas. Las perturbaciones gravitatorias pueden modificar la posición y se utilizan maniobras de mantenimiento orbital. Las masas y potencias mostradas son ejemplos de satélites grandes, no requisitos de toda misión.

La tabla ilustra bandas L, S, C, Ku y Ka. Sus pares aproximados de bajada/subida son 1,5/1,6 GHz, 1,9/2,2 GHz, 4/6 GHz, 11/14 GHz y 20/30 GHz, respectivamente. Aprende la separación subida–bajada y las diferencias entre interferencia terrestre y atenuación por lluvia, sin asumir que esos valores sustituyan una atribución oficial.

La huella o footprint es el área cubierta por un haz. Un haz amplio puede cubrir una fracción grande de la Tierra; varios haces puntuales permiten concentrar cobertura en regiones más pequeñas. La cobertura de un satélite no equivale a la capacidad disponible para cada usuario.

### VSAT: topología, medio rural y seguridad

Referencia al programa: páginas 90–95

VSAT designa terminales terrestres de antena pequeña. El documento muestra terminales remotos, un satélite y un hub, así como antenas de bandas C, Ku y Ka. Sus ejemplos de potencia y tasas son ilustrativos de la tecnología del material.

Si dos terminales se comunican a través de un hub, la señal recorre más tramos que una sola subida y bajada. Esto explica el ejemplo de unos 540 ms para ese recorrido, sin convertirlo en una constante de toda VSAT. Como aproximación física, propagación por espacio es del orden de 3,3 μs/km y en fibra de unos 5 μs/km: es indispensable indicar la distancia.

Una instalación alimentada con paneles solares puede conectar lugares rurales donde tender infraestructura resulte difícil. La difusión permite atender varias estaciones bajo una huella, pero deben protegerse acceso y privacidad. El cifrado es pertinente porque la propagación no restringe la señal a un cable individual.

### MEO, navegación y cinturones de Van Allen

Referencia al programa: páginas 96–97

MEO se ubica entre las órbitas bajas y GEO y se utiliza, entre otras aplicaciones, en navegación. A diferencia de GEO, estos satélites cambian su posición aparente. Los cinturones de Van Allen son regiones de partículas cargadas atrapadas por el campo magnético terrestre; el diagrama ilustra el entorno de radiación.

La página 96 menciona seis horas para MEO y después GPS: no generalices ese período. La fuente oficial GPS.gov sitúa GPS alrededor de 20.200 km y describe dos vueltas diarias, aproximadamente doce horas por vuelta. El período depende de la órbita, no solo de la etiqueta MEO. Tampoco memorices el número de satélites de una diapositiva antigua como cantidad permanentemente vigente.

Corrección de GPS: órbita MEO de unos 20.200 km y dos vueltas diarias; no un período de seis horas.

Fuente: GPS.gov. Space Segment. https://www.gps.gov/space-segment

### LEO y continuidad de cobertura

Referencia al programa: páginas 98–99

Los satélites en órbita baja se encuentran mucho más cerca de la Tierra que GEO. El documento los relaciona con servicios de voz y comunicaciones de aviación, barcos y exploración en zonas sin infraestructura terrestre. Los ejemplos preparan el estudio de Iridium, Globalstar y pequeños satélites.

El recorrido más corto puede reducir la componente de propagación del retardo; cada satélite cubre una región menor y se desplaza respecto al usuario. Una constelación permite que otro satélite tome el relevo cuando el anterior deja de ser utilizable.

El límite de menos de 5000 km y las cifras de retardo del PDF son convenciones o ejemplos del material. No definen por sí solos todas las clasificaciones orbitales ni el rendimiento total de un servicio.

### Iridium: arquitectura, historia y aplicaciones

Referencia al programa: páginas 100–107

El nombre del proyecto se vincula en el material con una propuesta inicial de 77 satélites y el elemento químico iridio. La explicación histórica cita la solicitud de 1990, inicio del servicio en 1998 y dificultades comerciales frente al crecimiento de la telefonía celular. Los montos de inversión y compra son contexto histórico del PDF.

La arquitectura ilustrada usa órbitas polares y enlaces entre satélites. Los diagramas de collares alrededor de la Tierra explican una cobertura distribuida y el relevo; las alturas y cantidades del dibujo corresponden a esa descripción, no a un inventario actualizado de la flota.

El material enumera voz, datos, mensajería, fax y navegación como usos, con clientes marítimos, aviación, exploración petrolera, periodistas y viajeros en lugares remotos. Las fotografías del equipo y del satélite ilustran terminales y componentes; aquí se sustituyen por esta explicación. La lista de representantes en ciudades de Ecuador es una referencia histórica, no un directorio comercial verificado.

### Globalstar y la alternativa de tubo doblado

Referencia al programa: páginas 108–109

La comparación del documento muestra dos formas de encaminar una comunicación satelital: transferirla de satélite a satélite, o llevarla a una estación terrestre para continuar la comunicación por la infraestructura de tierra. Globalstar aparece como ejemplo de la segunda opción, con diseño de tubo doblado.

El número de 48 satélites que presenta la página es una referencia de ese diseño histórico. La diferencia conceptual es dónde se realiza el relevo y qué infraestructura necesita el sistema. No concluyas que todas las generaciones de un servicio deben conservar idéntica cantidad de satélites o equipamiento.

### CubeSat y cierre de CAPA I

Referencia al programa: páginas 110–110

CubeSat es un formato modular de satélite pequeño, no una órbita ni un operador. El PDF presenta la unidad de aproximadamente 10 × 10 × 10 cm, su origen académico asociado a Cal Poly y Stanford y ejemplos de comunicación en UHF/VHF. La clase relaciona el formato con misiones de bajo tamaño y masa.

NASA confirma la idea modular 1U y extensiones a varias unidades. Evita convertir la masa de 1 kg del ejemplo de clase en una restricción universal de todos los CubeSat. La misión determina subsistemas, enlace y órbita.

Con esta sección queda cubierto el primer PDF hasta su página 110. Comprueba que puedes relacionar señal, ancho de banda, medio guiado, medio no guiado, órbita y cobertura sin mezclar propiedades físicas con funciones de protocolo.

NASA describe una unidad 1U de aproximadamente 10 cm de lado y formatos de varias unidades.

Fuente: NASA Small Spacecraft Systems Virtual Institute. What are SmallSats and CubeSats?. https://www.nasa.gov/smallsat-institute/what-are-smallsats-and-cubesats/

## Funciones y servicios de enlace

Capa 2 · páginas 1–12

### Enlace: funciones y estructura de trama

Referencia al programa: páginas 1–5

Las primeras páginas sitúan el tema de enlace. Esta capa utiliza la transmisión física para ofrecer un servicio a red, agrupa bits en tramas, incorpora direccionamiento MAC y puede manejar errores y regular el flujo. El protocolo determina cuáles de estas funciones se implementan y con qué garantías.

La encapsulación ilustrada coloca un paquete de red como carga útil de una trama, con encabezado y final. El receptor interpreta la trama y entrega el paquete al nivel superior. Los campos adicionales consumen capacidad: tasa física y rendimiento útil no son idénticos.

Control de flujo protege a un receptor lento; control de errores aborda corrupción, pérdida o duplicación según el servicio. Pueden existir funciones parecidas en transporte, pero el enlace actúa entre extremos de un enlace y transporte en una comunicación entre procesos.

### Servicios sin conexión: con y sin confirmación

Referencia al programa: páginas 6–9

Un servicio sin conexión no establece un diálogo previo de conexión antes de enviar unidades independientes. Sin confirmación, no solicita un acuse por cada trama; puede ser apropiado en enlaces con pocos errores o aplicaciones sensibles al retardo. Con confirmación, el emisor recibe evidencia de recepción y puede repetir unidades no confirmadas.

La ausencia de ACK no equivale a ausencia de detección de errores. Ethernet puede verificar FCS y descartar tramas corruptas, pero su MAC no ofrece confirmación y retransmisión de cada trama como un servicio confiable. Este punto aclara la formulación ambigua de la página 8.

Los enlaces inalámbricos motivan confirmaciones porque el canal puede ser variable. El diseño equilibra costo de control, retardo y recuperación.

### Servicio orientado a conexión y seguimiento de tramas

Referencia al programa: páginas 10–12

En el modelo confiable orientado a conexión se establece estado entre los extremos y se numeran tramas. El objetivo es controlar orden, repetición y recepción para entregar las unidades según lo que promete el protocolo.

La implementación mantiene información de lo enviado, lo recibido y lo pendiente. El diagrama coloca el protocolo de enlace entre red y el medio, con lógica de control que puede implementarse en software, firmware o hardware. No atribuyas una técnica de implementación única a toda una clase de dispositivos.

La numeración ayuda a detectar duplicados; las confirmaciones y los mecanismos de recuperación permiten gestionar pérdidas. Ningún medio físico por sí solo sustituye ese estado lógico.

## Entramado

Capa 2 · páginas 13–27

### Entramado por longitud o conteo de bytes

Referencia al programa: páginas 13–15

Entramar significa reconocer dónde empieza y termina una unidad dentro de un flujo. Los cuatro enfoques del material son conteo de bytes, banderas de bytes con escape, banderas de bits con relleno y violaciones de codificación física.

En conteo de bytes, un campo del encabezado informa la longitud. Si se altera, el receptor puede interpretar mal no solo esa trama sino el límite de la siguiente. La figura compara un flujo correcto y otro que pierde sincronización por un valor de longitud erróneo.

La idea clave es distinguir una secuencia de bits válida de una secuencia correctamente separada en tramas: reconocer bits y reconocer unidades son problemas relacionados, pero diferentes.

### Banderas y relleno de bytes

Referencia al programa: páginas 16–19

Un delimitador especial señala principio o final de una trama. Si ese mismo byte aparece en los datos, debe representarse sin confundirlo con el delimitador. El esquema usa un byte ESC para indicar que el siguiente elemento tiene significado de dato o representación especial.

Ejemplo didáctico: si el dato contiene FLAG, se transmite una forma escapada; si contiene ESC, también debe protegerse. El receptor deshace el escape y entrega la carga útil original. Quitar delimitadores y quitar escapes son pasos distintos. Los valores concretos y transformaciones dependen del protocolo: no todos se limitan a duplicar caracteres.

El PDF señala su asociación a unidades de ocho bits; el siguiente método opera sobre secuencias de bits. Si se pierde sincronía, encontrar una nueva bandera puede ayudar a recuperar los límites.

RFC 1662 especifica entramado con escapes de octetos y relleno de bits para PPP de tipo HDLC.

Fuente: W. Simpson (editor). RFC 1662 · PPP in HDLC-like Framing (1994). https://www.rfc-editor.org/rfc/rfc1662.html

### Relleno de bits con ejemplo resuelto

Referencia al programa: páginas 20–21

La bandera de esta técnica es 01111110. Para que el mismo patrón no aparezca por accidente dentro de los datos, el emisor inserta un cero después de cinco unos consecutivos de la carga. El receptor elimina ese cero de relleno. Las banderas reales no se someten a ese relleno como si fueran datos.

Ejemplo: la carga 01111110 se envía, dentro del campo de datos, como 011111010. Se conserva el cero inicial, se cuentan cinco unos, se inserta 0 y se continúa con el uno y cero restantes. Al retirar el cero añadido se recupera exactamente 01111110.

El relleno aumenta la cantidad de bits transmitidos en función de los datos. No es compresión ni corrección de errores; resuelve transparencia y delimitación.

### Violaciones de codificación, LLC y topologías

Referencia al programa: páginas 22–24

Si la codificación física reserva determinadas señales que no se usan para datos ordinarios, esas señales pueden delimitar tramas. Se evita así que una secuencia normal de datos se confunda con la marca. Manchester introduce transiciones temporales que ayudan a sincronizar; la correspondencia entre dirección de transición y bit depende de la convención.

Los esquemas IEEE del material muestran LLC por encima de tecnologías MAC y físicas. Una familia puede definir tanto acceso al medio y tramas como señalización y cableado. No es contradictorio estudiar Ethernet en capas 1 y 2.

El documento compara Ethernet compartido con bus lógico y estrella física, Token Ring con anillo lógico y estrella física, y FDDI con doble anillo. Son configuraciones históricas concretas: Ethernet con switches y enlaces full-duplex no equivale a un único bus compartido.

### Campos de una trama y detección de errores

Referencia al programa: páginas 25–27

La capa física transporta símbolos que pueden llegar alterados; enlace proporciona una estructura para interpretar unidades y comprobar errores según el protocolo. La trama genérica del PDF incluye inicio, direcciones, longitud/tipo/control, datos, secuencia de verificación y final. No todos los protocolos tienen exactamente los mismos campos.

FCS es un campo de verificación; CRC es un procedimiento de cálculo utilizado para detectar errores. Un CRC no corrige por sí mismo todos los bits corruptos ni garantiza por sí solo entrega confiable. El receptor puede descartar una trama y otra función puede encargarse de recuperarla.

Un paquete IP, una trama Ethernet y una unidad TCP tienen propósitos y encabezados distintos. Al estudiar una captura, identifica cuál contiene a cuál y qué información pertenece a cada nivel.

## IEEE y redes inalámbricas

Capa 2 · páginas 28–33

### Familia IEEE 802 y comités históricos

Referencia al programa: páginas 28–29

IEEE 802 agrupa estándares de redes locales y metropolitanas. El listado de clase incluye 802.1 para funciones de interconexión, 802.2 LLC, 802.3 Ethernet, 802.4 Token Bus, 802.5 Token Ring, 802.11 WLAN, 802.15 PAN y 802.16 acceso inalámbrico de banda ancha, entre otros grupos históricos.

El directorio oficial permite comprobar las áreas: 802.3 corresponde a Ethernet y 802.11 a LAN inalámbrica. La tabla del PDF también relaciona enmiendas como 802.3u con 100 Mb/s, 802.3z con variantes Gigabit y 802.3ab con Gigabit sobre pares.

No todos los comités de una lista antigua siguen activos. Para el examen identifica el propósito de cada familia; para diseñar una red usa la especificación y revisión que corresponden.

El directorio oficial identifica 802.3 como Ethernet y 802.11 como Wireless LAN.

Fuente: IEEE 802 LAN/MAN Standards Committee. Directorio oficial IEEE 802. https://ieee802.org/

### Variantes WLAN y adaptadores

Referencia al programa: páginas 30–31

La comparación histórica menciona 802.11 original a 1–2 Mb/s y DSSS; 802.11b a 1, 2, 5,5 y 11 Mb/s; 802.11a a 54 Mb/s en 5 GHz; y 802.11g a 54 Mb/s con compatibilidad con equipos 802.11b en su banda. El documento muestra 300 Mb/s como ejemplo para 802.11n, no como la única configuración posible.

La velocidad nominal de enlace no equivale al rendimiento de una aplicación. Acceso compartido, control, interferencias, distancia y condiciones del receptor afectan la tasa útil. Las imágenes de adaptadores PCI, PCMCIA y USB ilustran interfaces de conexión del equipo.

Aunque una diapositiva se titule Wireless WAN Standards, 802.11 se refiere a WLAN. Esta distinción evita confundir cobertura geográfica con la familia de acceso al medio.

### CSMA/CA y práctica de campus

Referencia al programa: páginas 32–33

WLAN utiliza un medio radioeléctrico compartido. Escuchar antes de transmitir ayuda a evitar ocupar un canal ya usado, pero no permite detectar una colisión como en el Ethernet compartido clásico. El material contrasta CSMA/CA, prevención, con CSMA/CD, detección.

Como ampliación didáctica, CA utiliza espera y reglas de acceso para reducir colisiones; no promete que nunca ocurran. Un transmisor no puede deducir siempre qué oyó el receptor a partir de su propia escucha del canal.

Para la práctica de campus, diseña una topología con switches, un punto de acceso y laptops. Explica qué enlaces son guiados o no guiados, cómo se conecta cada NIC y qué camino sigue una trama. La tarea de simulación se describe como ejercicio de estudio; aquí no se ejecuta ninguna instrucción del PDF sobre tu equipo.

## Ethernet y codificación

Capa 2 · páginas 34–50

### Ethernet: variantes y campos de trama

Referencia al programa: páginas 34–37

Ethernet es una familia de tecnologías LAN. Las tablas comparan ejemplos como 10BASE5 coaxial (500 m por segmento), 10BASE-T (100 m) y 10BASE-FL óptico (2 km), junto a Fast y Gigabit Ethernet. Son valores de variantes y condiciones específicas, no el alcance general de todos los medios.

La página 36 compara 1000BASE-T en cuatro pares y variantes ópticas SX y LX. Las distancias dependen del tipo de fibra y transceptor. Parte de las imágenes de las páginas 34 y 37 presenta degradación visual en el archivo; se conserva su asunto de Ethernet y tramas mediante explicación escrita, sin inventar contenido ilegible.

Ampliación: una trama Ethernet básica tiene MAC de destino, MAC de origen, un campo tipo/longitud, datos y FCS; el preámbulo y el delimitador ayudan al inicio de la recepción. Los campos de capa 2 no deben confundirse con direcciones IP o puertos TCP.

### Fast Ethernet y codificación 4B/5B

Referencia al programa: páginas 38–41

Fast Ethernet se presenta a 100 Mb/s: 100BASE-TX utiliza pares de cobre y 100BASE-FX fibra. Se conserva el formato MAC de la familia mientras cambian componentes físicos. El bloque de páginas estudia dos pasos: codificación de grupos y codificación de línea.

4B/5B transforma cada grupo de cuatro bits de datos en cinco bits de código. Su eficiencia de datos es 4/5 = 80 % y el volumen codificado crece 25 % respecto al original: son dos formas distintas de expresar la relación. Las tablas también muestran símbolos especiales de control e inactividad.

Para evitar una generalización del PDF, distingue el código de bloque de la codificación de línea específica de cada variante: 100BASE-TX y 100BASE-FX no tienen exactamente la misma señalización eléctrica/óptica. Ejemplo de la tabla: 0000 se representa por 11110.

### Gigabit Ethernet, 8B/10B y transmisión óptica

Referencia al programa: páginas 42–45

Gigabit Ethernet transmite a 1 Gb/s, equivalente a 1000 Mb/s, y tiene variantes de cobre y fibra. El material asocia 802.3z con 1000BASE-X y 802.3ab con 1000BASE-T. Para cobre conviene distinguir 1000BASE-T de otras denominaciones similares: no son nombres intercambiables.

Las variantes ópticas 1000BASE-SX y LX se relacionan con longitudes de onda corta y larga. La figura muestra fibras separadas de transmisión y recepción para funcionamiento full-duplex. 8B/10B representa ocho bits mediante diez, con eficiencia de bloque de 80 %.

La codificación exacta depende de la variante: no atribuyas 8B/10B a todo Gigabit sobre cobre. El documento ilustra su empleo en troncales internas, enlaces entre switches, servidores y estaciones que necesitan más capacidad.

### NRZ, NRZI y sincronización

Referencia al programa: páginas 46–47

NRZ representa valores mediante niveles que se mantienen durante el intervalo del bit. Una secuencia larga sin cambios puede complicar la sincronización de relojes. La figura compara representaciones unipolares y bipolares.

NRZI representa información mediante transición o ausencia de transición. Debes indicar el convenio: en un ejemplo frecuente, 1 produce transición y 0 no; existen convenios inversos. El nivel inicial modifica el dibujo de tensión pero no necesariamente la secuencia decodificada si se conocen las reglas.

El propósito es distinguir el dato de su señal: un 1 no significa siempre tensión alta. A diferencia de NRZI, Manchester impone una transición dentro del intervalo del bit y facilita la recuperación temporal a costa de más actividad de señalización.

### 10 Gigabit Ethernet y límites de las comparaciones históricas

Referencia al programa: páginas 48–49

El material enumera 10GBASE-SR para distancias cortas en fibra, LX4 con multiplexión de longitudes de onda, LR para 10 km y ER para 40 km en los ejemplos monomodo. También menciona SW, LW y EW en el contexto de variantes WAN. La distancia real debe verificarse para el tipo de fibra y transceptor.

La página 49 anticipa crecimiento de cobre, radio y fibra. Las cifras presentadas como futuro pertenecen a la fecha del documento; no son máximos actuales. Para estudiar la idea duradera, relaciona ancho de banda, medio, electrónica, distancia, costo y compatibilidad.

Pasar de 100 Mb/s a 1 Gb/s o 10 Gb/s aumenta la tasa, pero no hace que la propagación de una señal viaje diez veces más rápido en el mismo medio. Se reduce el tiempo de serialización de una unidad de igual tamaño.

Ampliación desde el libro de Dordal: serialización t = L/R (L en bits y R en bit/s); propagación t = d/v. Para 1200 bytes a 100 Mb/s, la serialización es 9600/100.000.000 = 96 μs. Si además el recorrido es 2 km y v = 2 × 10⁸ m/s, la propagación es 10 μs. Sin colas ni procesamiento, el último bit llega a los 106 μs. Elevar R reduce la primera componente, pero no cambia por sí mismo d/v.

Fuente: Peter L. Dordal. An Introduction to Computer Networks · sección Packet Delay (edición 1.9.21). https://intronetworks.cs.luc.edu/current1/html/packets.html

### Práctica de análisis de tráfico

Referencia al programa: páginas 50–50

La actividad propone reconocer Telnet, ping, IP, Ethernet, UDP, TCP, ARP, HTTP, HTTPS y SMTP en una captura. La guía de estudio consiste en observar encapsulación y campos, no en atribuir todos los protocolos a una misma capa.

Ethernet describe la trama local; ARP relaciona IP y MAC; IP corresponde al encaminamiento; TCP y UDP a transporte; HTTP, Telnet y SMTP a aplicaciones. Ping es una herramienta que utiliza mensajes ICMP. En HTTPS no debes esperar leer el contenido de aplicación cifrado como si fuera HTTP en texto claro.

Ejercicio: sobre una captura propia o de laboratorio autorizada, identifica MAC origen/destino, tipo de trama, paquete IP y protocolo superior. Explica qué información cambia al cruzar un router y cuál permanece según el caso.

## NIC, puentes y switches

Capa 2 · páginas 51–61

### NIC y puente

Referencia al programa: páginas 51–54

Una NIC proporciona la interfaz de red de un equipo. El material propone elegirla según tecnología y tasa, medio (cobre, fibra o radio) e interfaz del sistema (por ejemplo PCI, PCMCIA o USB). Compatibilidad física y lógica deben revisarse juntas.

Un bridge o puente conecta segmentos y filtra o reenvía tramas según direcciones MAC. Su aprendizaje construye una relación entre direcciones y puertos. El documento compara puentes tradicionales y switches para introducir evolución de prestaciones; no todos los puentes posibles tienen solo dos puertos ni se implementan únicamente en software.

Las MAC se usan como identificadores de enlace. Aunque se asignan direcciones de fábrica, pueden existir direcciones administradas localmente y duplicaciones por configuración; no las confundas con identidades de usuario garantizadas.

### Switches y dominios de colisión

Referencia al programa: páginas 55–59

Un switch de capa 2 es un puente multipuerto. Aprende asociaciones MAC–puerto, filtra tráfico que no debe salir de un segmento y reenvía hacia el destino cuando lo conoce. El hardware permite conmutación eficiente, con capacidad de la matriz y búferes que también condicionan el rendimiento.

Frente a un hub, los enlaces de cada puerto separan el medio compartido. En Ethernet conmutado full-duplex no se opera con colisiones como en un bus half-duplex. La frase de un dominio de colisión por puerto es una comparación útil con redes compartidas, no una indicación de que existan colisiones normales en full-duplex.

Un switch no manda siempre cada trama por un único puerto: broadcasts y destinos desconocidos requieren un tratamiento distinto. Las ventajas de clase incluyen segmentación, capacidad por puerto y VLAN.

### Conmutación de capa 3, simetría y búferes

Referencia al programa: páginas 60–61

Un switch de capa 3 añade funciones de encaminamiento a las de enlace y utiliza información IP para decidir rutas. Es una función distinta del reenvío MAC dentro de una VLAN. El nombre comercial del equipo no sustituye identificar qué función está realizando.

La conmutación simétrica conecta enlaces de tasas equivalentes; la asimétrica permite enlaces de distinta capacidad. El diagrama muestra un enlace de mayor tasa hacia un servidor y conexiones más lentas a otros equipos. Si llega tráfico más rápido de lo que puede salir, se requieren búferes y puede haber espera o descarte.

El aumento de capacidad de un uplink puede aliviar un cuello de botella, pero no garantiza que todas las transferencias alcancen su tasa nominal simultáneamente.

## Métodos de conmutación

Capa 2 · páginas 62–65

### Store-and-forward, cut-through y fragment-free

Referencia al programa: páginas 62–63

Store-and-forward recibe la trama completa antes de reenviarla; puede comprobar FCS/CRC y descartar una unidad corrupta antes de enviarla. Introduce espera asociada a recibir la unidad.

Cut-through empieza a reenviar después de obtener la información necesaria del encabezado, sin esperar toda la trama. Reduce latencia de inicio, pero puede propagar una unidad cuyo error se detecte más tarde. Fragment-free espera los primeros 64 bytes según el método descrito, buscando evitar fragmentos cortos derivados de colisiones de redes compartidas.

No confundas recibir 64 bytes con validar el CRC de una trama larga: el campo de verificación está al final. Para comparar métodos, explica cuánto esperan, qué errores pueden descartar antes de reenviar y por qué el entorno importa.

### Broadcast, aprendizaje MAC e inundación

Referencia al programa: páginas 64–65

El switch aprende la MAC de origen y el puerto de entrada de una trama. Después busca la MAC de destino: si la conoce en otro puerto, reenvía por ese puerto; si corresponde al mismo puerto de entrada, no necesita reenviarla a ese segmento; si la desconoce, inunda los puertos habilitados del mismo dominio, salvo el de entrada.

Un broadcast se distribuye dentro de su VLAN. Si todos los puertos pertenecen a una sola VLAN, un switch no separa por sí solo ese dominio de broadcast. Varias VLAN sí crean dominios distintos. Un router o función de capa 3 permite comunicación entre redes con decisiones diferentes del flooding local.

Ejemplo: A entra por puerto 1 y su destino B es desconocido. Se aprende A→1 y se inunda. Cuando B responde por puerto 3, se aprende B→3; los siguientes unicast A→B pueden enviarse por 3. No se aprende una MAC mirando exclusivamente el destino.

## STP y segmentación

Capa 2 · páginas 66–72

### Bucles de capa 2 y BPDU

Referencia al programa: páginas 66–66

Los enlaces redundantes mejoran alternativas de conectividad, pero un bucle lógico puede hacer circular tramas, duplicar tráfico y desestabilizar el aprendizaje MAC. Los broadcasts e inundaciones son especialmente problemáticos porque se replican.

STP construye una topología lógica sin ciclos utilizando enlaces físicos disponibles; algunos puertos dejan de reenviar tráfico de usuario. Los switches intercambian BPDU con información del árbol. Si cambia un enlace, el protocolo puede recalcular y habilitar una alternativa; la recuperación no es necesariamente instantánea.

STP no elimina físicamente cables redundantes ni es un protocolo de encaminamiento IP. Su objetivo aquí es mantener conectividad de enlace con un árbol de reenvío.

### Elección de raíz y roles de puertos

Referencia al programa: páginas 67–68

La raíz se elige por el menor identificador de bridge. Se compara prioridad y luego los componentes que completan ese identificador, incluida MAC; en implementaciones con identificador extendido se incorpora información de instancia/VLAN. No es una suma aritmética simple de MAC y prioridad. El valor base habitual de prioridad es 32768.

Cada bridge no raíz selecciona un puerto raíz para su mejor camino hacia la raíz. En cada segmento se selecciona un puerto designado; los otros roles permiten evitar bucles. Menor coste no significa siempre menor número de saltos: depende de los costos de los enlaces.

Ejemplo: si A y B tienen igual prioridad y A tiene menor MAC, A resulta raíz en esa comparación. Después los switches eligen caminos respecto a A; no se elige una nueva raíz independiente por cada enlace.

La documentación de Cisco detalla bridge ID, prioridad base 32768, selección de raíz y estados de puertos.

Fuente: Cisco. STP Configuration Guide · Spanning Tree Protocol. https://www.cisco.com/c/en/us/td/docs/switches/lan/c9000/lyr2-fwd/stp/stp-configuration-guide/m-stp.html

### Estados STP y ejemplo de triángulo

Referencia al programa: páginas 69–70

En el STP clásico, bloqueado no reenvía tráfico de usuario; escuchando participa en la selección de la topología; aprendiendo incorpora MAC sin reenviar todavía esos datos; enviando o forwarding ya aprende y reenvía. Un puerto deshabilitado queda fuera del funcionamiento normal. No mezcles sin aclaración estos estados con los del protocolo rápido RSTP.

En un triángulo de tres switches, si todos los enlaces reenviaran broadcasts indefinidamente, existiría un ciclo. Al elegir una raíz y los roles de puertos, un extremo redundante queda sin reenvío y el camino lógico se vuelve un árbol.

Si falla el camino activo, el protocolo puede modificar roles para usar una alternativa. Para resolver un ejercicio: elige raíz, calcula caminos de menor coste, identifica puertos raíz, designados y bloqueados, y comprueba que el reenvío no forme ciclos.

### Segmentación con routers y actividad comparativa

Referencia al programa: páginas 71–72

El diagrama de la página 71 conecta varios segmentos mediante un router. La función de red separa dominios de broadcast y permite comunicación entre redes. Un switch de capa 3 puede desempeñar funciones equivalentes de encaminamiento; lo importante es reconocer cuándo se cruza una frontera lógica.

La última actividad pide comparar tres switches de distintos fabricantes. Puedes estructurar el cuadro con modelo exacto, cantidad y tasa de puertos, uplinks, gestión, VLAN, STP/RSTP, capacidad de conmutación, PoE si corresponde y fuente oficial. La comparación debe apoyarse en fichas técnicas de modelos concretos, no atribuir a toda una marca las prestaciones de un equipo.

Esta es una propuesta de ejercicio derivada del programa. No se inventan especificaciones comerciales ni se incluye el contenido de CAPA III posterior a la página 72.

## Bibliografía y alcance de consulta

- Peter L. Dordal. An Introduction to Computer Networks, 2.ª edición · capítulo 6: Links. Consulta directa del capítulo: codificación NRZ, NRZI, Manchester, 4B/5B y entramado. https://intronetworks.cs.luc.edu/current/ComputerNetworks/links.html

- Peter L. Dordal. An Introduction to Computer Networks · capítulo 2: Ethernet Basics. Consulta directa: mecanismos básicos de Ethernet, aprendizaje y conmutación. https://intronetworks.cs.luc.edu/current/ComputerNetworks/ethernet1.html

- Peter L. Dordal. An Introduction to Computer Networks · capítulo 3: Advanced Ethernet. Consulta directa: árbol de expansión y redes virtuales. https://intronetworks.cs.luc.edu/current/ComputerNetworks/ethernet2.html

- Andrew S. Tanenbaum, Nick Feamster y David J. Wetherall. Computer Networks, 6.ª edición · capítulos 2, 3 y 4. Editorial e índice verificados: capa física, enlace y subcapa MAC. No se consultó íntegramente el libro comercial; se ofrece como lectura complementaria. https://www.pearson.com/en-us/subject-catalog/p/computer-networks/P200000003188/9780136958505

- James F. Kurose y Keith W. Ross. Computer Networking: A Top-Down Approach · recursos oficiales, capítulo 6. Índice oficial consultado: servicios de enlace, detección de errores, acceso múltiple, Ethernet, switches y VLAN. https://gaia.cs.umass.edu/kurose_ross/videos/6/

- James F. Kurose y Keith W. Ross. Computer Networking: A Top-Down Approach · recursos oficiales, capítulo 7. Recursos oficiales para características del enlace inalámbrico y WLAN. No implica lectura íntegra del libro. https://gaia.cs.umass.edu/kurose_ross/videos/7/

- Robert M. Metcalfe y David R. Boggs. Ethernet: Distributed Packet Switching for Local Computer Networks (1976). Artículo histórico de Communications of the ACM; copia académica alojada por Cornell. Describe Ethernet de medio compartido; no debe tomarse como descripción completa de Ethernet moderno. https://www.cs.cornell.edu/courses/cs414/2001FA/papers/ethernet/ethernet.htm

- W. Simpson (editor). RFC 1662 · PPP in HDLC-like Framing (1994). Secciones 4 y 5: transparencia con escapes de octetos y relleno de bits. https://www.rfc-editor.org/rfc/rfc1662.html

- The Fiber Optic Association. Total Internal Reflection in Optical Fiber. Explicación de núcleo, revestimiento, índices y reflexión interna total. https://thefoa.org/tech/ref/basic/total_internal_reflection.html

- Fluke Networks. Network Engineer Tools and Troubleshooting Guide · tabla de cableado. Tabla de categorías: Cat 6/clase E a 250 MHz y Cat 6A/clase EA a 500 MHz. https://www.flukenetworks.com/expertise/role/network-engineers

- U.S. Food and Drug Administration. Procedures for Field Testing Microwave Ovens · apéndice I. Verificación puntual de la frecuencia habitual de 2450 MHz; corrige el ejemplo de 4 GHz. https://www.hhs.gov/guidance/sites/default/files/hhs-guidance-documents/FDA/Procedures-for-Field-Testing-Microwave-Ovens.pdf

- ARCOTEL. Preguntas frecuentes · ¿Qué es la ARCOTEL?. Identifica la entidad encargada de administrar, regular y controlar el espectro radioeléctrico en Ecuador. https://www.arcotel.gob.ec/1-preguntas-generales/

- IEEE 802 LAN/MAN Standards Committee. Directorio oficial IEEE 802. Identificación de grupos: 802.1, 802.3 y 802.11, entre otros. https://ieee802.org/

- NOAA CoastWatch. Geostationary Earth Orbit Satellite (GEO). Altura aproximada de 35.786 km sobre el ecuador y perspectiva fija de GEO. https://oceanwatch.noaa.gov/cwn/platform-types/geostationary-earth-orbit-satellite-geo.html

- GPS.gov. Space Segment. GPS en MEO, aproximadamente 20.200 km y dos órbitas diarias. https://www.gps.gov/space-segment

- NASA Small Spacecraft Systems Virtual Institute. What are SmallSats and CubeSats?. Formato modular CubeSat 1U y tamaños de varias unidades. https://www.nasa.gov/smallsat-institute/what-are-smallsats-and-cubesats/

- Cisco. STP Configuration Guide · Spanning Tree Protocol. Verificación de bridge ID, prioridad base y estados del STP clásico. https://www.cisco.com/c/en/us/td/docs/switches/lan/c9000/lyr2-fwd/stp/stp-configuration-guide/m-stp.html

- Claude E. Shannon. A Mathematical Theory of Communication (1948). Artículo original de Bell System Technical Journal, reimpresión con correcciones en Harvard. Ampliación sobre capacidad de un canal con ruido blanco gaussiano. https://people.math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf

- Peter L. Dordal. An Introduction to Computer Networks · sección Packet Delay (edición 1.9.21). Sección consultada directamente: serialización, propagación y efecto del tamaño de los paquetes sobre el retardo. https://intronetworks.cs.luc.edu/current1/html/packets.html
