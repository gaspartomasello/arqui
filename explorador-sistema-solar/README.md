# Explorador del Sistema Solar 3D

Juego educativo en un único archivo (`index.html`) con Three.js r128. Se abre con doble clic en cualquier navegador moderno (necesita internet para cargar Three.js y las tipografías).

## Qué cambió respecto de la versión original

### Física y escala real
- **Escala 1:1 en kilómetros**: radios, distancias y órbitas son los reales. La nave mide 40 m. Para que los astros diminutos se encuentren, hay marcadores de tamaño constante en pantalla y etiquetas.
- **Posiciones reales de hoy**: los planetas se calculan con los elementos keplerianos de JPL (Standish, válidos 1800–2050) a partir de la fecha y hora actuales; la Luna con una teoría lunar simplificada (fases reales); el Halley con su perihelio de 1986 (hoy está casi en el afelio, inactivo y sin colas, como en la realidad).
- **Órbitas elípticas** dibujadas con el Sol en un foco, con inclinación, nodo y perihelio correctos. Velocidad orbital por la ecuación de vis-viva.
- **Ejes y rotación IAU**: cada planeta gira con su polo y período reales (Venus, Urano y Plutón retrógrados). La Tierra muestra el lado iluminado correcto según la hora UTC. Júpiter y Saturno están achatados en los polos.
- **Lunas en su plano real** (ecuador del planeta), con rotación síncrona (siempre la misma cara hacia el planeta). Tritón en órbita retrógrada; Plutón y Caronte giran alrededor de un baricentro que está fuera de Plutón.
- **Nave con marco de referencia**: cerca de un planeta, la nave lo acompaña en su órbita (esfera de influencia de Laplace). La velocidad es adaptativa para no atravesar astros; para cruzar el sistema usa un “motor de curvatura” ficticio y la interfaz muestra cuánto tardaría la luz.

### Visuales
- Cielo de fondo con **estrellas reales** (Sirio, Betelgeuse, la Cruz del Sur…), 12 constelaciones en sus coordenadas reales y la **Vía Láctea orientada** según el polo galáctico, con las Nubes de Magallanes y Andrómeda.
- Texturas procedurales por astro: la **Tierra con sus continentes reales**, nubes, océanos con brillo especular y luces nocturnas de ciudades; Marte con Tharsis, Valles Marineris, Hellas y casquetes; Júpiter con bandas y la Gran Mancha Roja; Saturno con el hexágono polar; Ío, Europa, Plutón (el “corazón”), etc.
- Atmósferas con brillo de limbo dependiente del Sol, **anillos de Saturno con su estructura real** (División de Cassini, Encke) y la sombra del planeta sobre ellos; anillos tenues de Júpiter, Urano y Neptuno.
- Cinturón de asteroides con huecos de Kirkwood, troyanos de Júpiter y cinturón de Kuiper (densidad exagerada para que se vean, se aclara en el menú).

### Aterrizajes con cinemática
Aproximación (con estelas a velocidades extremas) → órbita baja → entrada atmosférica con plasma (o frenado propulsado si no hay aire) → descenso final con paracaídas, paracaídas + retrocohetes (Marte, como Curiosity) o retrocohetes (mundos sin aire), polvo que se levanta (balístico en el vacío) y contacto. Telemetría en pantalla con valores reales de gravedad y presión. Se puede saltar con **Esc**. También hay cinemática de despegue.

### Entornos de superficie según las misiones
- Cielos: azul de Rayleigh con atardeceres rojizos (Tierra), **caramelo de día y azul al atardecer** (Marte), naranja cubierto (Venus, Venera 13), bruma de tolinas (Titán, Huygens), capas de bruma azul (Plutón, New Horizons), negro con estrellas en mundos sin aire.
- El **planeta padre en el cielo con su tamaño angular real**: Marte ocupa 42° desde Fobos, Júpiter 19,5° desde Ío, Saturno 29° desde Encélado con los anillos de canto, la Tierra 1,9° desde la Luna, Caronte fijo sobre Plutón.
- El Sol se ve del tamaño correcto para cada distancia. Un control de **hora local** mueve el Sol por el cielo.
- Terreno con la **curvatura real** de cada astro (en Fobos el horizonte está a pocos cientos de metros), cráteres, crestas dobles de Europa, celdas de Sputnik Planitia y montañas de hielo en Plutón, terreno “piel de melón” de Tritón, acantilado Verona Rupes en Miranda, cañones en Titania, Ahuna Mons en Ceres, mar y bosques en la Tierra, lago de metano y guijarros en Titán.
- Fenómenos: remolinos y polvo en Marte, llovizna de metano en Titán, penacho volcánico y lago de lava en Ío, géiseres en Encélado y Tritón, aurora en Ganímedes.
- **Gigantes gaseosos**: descenso de una sonda con paracaídas a través de las capas de nubes reales (amoníaco, hidrosulfuro de amonio, agua, metano, H₂S) con presión y temperatura en vivo, relámpagos en las nubes de agua y el arco de los anillos en el cielo de Saturno.
- **Sol**: sonda sobre la fotosfera con granulación animada y protuberancias.

### Interfaz
- Barra superior (puntaje, fecha, velocidad del tiempo, capas), barra inferior contextual (objetivo, distancia, tiempo luz, acelerador, ir, aterrizar, datos) y dos paneles laterales plegables que nunca se superponen: en pantallas angostas solo se abre uno a la vez y en móvil el radar arranca cerrado.
- Las etiquetas no se pisan entre sí y se ocultan si el astro está detrás de otro. Retícula y flecha que indican dónde está el objetivo.
- Panel de datos con pestañas **Cielo, Aire, Clima, Geología, Órbita y Reto** (preguntas con respuestas mezcladas).
- Controles táctiles opcionales y zoom con pellizco.

### Correcciones de datos y errores del código original
- Vientos de superficie de Titán (eran 40 km/h; son ~1–2 m/s), los relámpagos de Venus (hoy en discusión científica), composición de Marte, rangos de temperatura, etc.
- El botón “Aterrizar” tras volver a órbita mostraba el identificador interno en lugar del nombre.
- Las lunas con rotación síncrona miraban al Sol en lugar de a su planeta.
- La velocidad orbital de las lunas era una fórmula inventada: ahora usa vis-viva con la masa del planeta.
- La respuesta correcta de los retos era siempre la opción A.
- Las teclas quedaban “pegadas” al cambiar de ventana; los atajos funcionaban con el modal de bienvenida abierto.

## Controles
| Tecla | Acción |
|---|---|
| W / S | Acelerar / frenar |
| A / D | Girar |
| Q / E | Subir / bajar la nariz |
| X | Detener |
| Shift | Impulso ×5 |
| G | Piloto automático al objetivo |
| L | Aterrizar / volver a órbita |
| F o clic en el suelo | Láser espectrométrico |
| V | Cámara en nave / en el objetivo |
| R / T / H | Radar / Datos / ocultar interfaz |
| Esc | Cancelar piloto o saltar cinemática |

## Fuentes
NASA/JPL Planetary Fact Sheets y elementos orbitales aproximados (E. M. Standish); IAU WGCCRE 2015 (polos y rotación); misiones Apolo, Venera 13/14, Viking, Curiosity, Perseverance, Galileo, Juno, Cassini‑Huygens, Voyager 2, Dawn, MESSENGER, New Horizons y Giotto.
