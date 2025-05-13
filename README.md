# Examen-de-redes

*MISION 1*

Partimos de la red 172.16.0.0/24 y hacemos subnetting con VLSM para crear subredes eficientes. Las necesidades son:

Comando Central: ~50 hosts
Defensa Perimetral: ~30 hosts
Centro Médico: ~20 hosts
Hangar y Taller: ~14 hosts
Enlace troncal: 2 hosts (enlace punto a punto)
Realizamos el diseño:

Departamento	Subred asignada	Máscara	Hosts útiles	Rango de Hosts	Broadcast
Comando Central	172.16.0.0/26	255.255.255.192	62	172.16.0.1 – 172.16.0.62	172.16.0.63
Defensa Perimetral	172.16.0.64/27	255.255.255.224	30	172.16.0.65 – 94	172.16.0.95
Centro Médico	172.16.0.96/27	255.255.255.224	30	172.16.0.97 – 126	172.16.0.127
Hangar y Taller	172.16.0.128/28	255.255.255.240	14	172.16.0.129 – 142	172.16.0.143
Enlace Troncal	172.16.0.144/30	255.255.255.252	2	172.16.0.145 – 146	172.16.0.147

*EJERCICIO 2*

El enrutamiento estático lo configura un administrador manualmente. Es sencillo, consume pocos recursos y da control total, pero si un enlace cae, no se adapta. Sería como si un Jedi tuviera que redibujar el mapa cada vez que cambia el terreno.
En cambio, el enrutamiento dinámico (como OSPF) aprende automáticamente las rutas y se adapta si algo falla. Es ideal para redes grandes como la HoloRed, aunque usa más recursos del router.
También hay diferentes estilos de protocolos dinámicos:

RIP, que solo cuenta saltos, es simple pero lento.
OSPF, más avanzado, construye un mapa completo de la red y calcula la mejor ruta. Es más rápido y preciso.


*EJERCICIO 3*

En una red, no solemos escribir direcciones IP para comunicarnos con otros dispositivos. Es mucho más cómodo usar nombres como planes.secretos. Pero los ordenadores no entienden nombres, solo entienden direcciones IP. Por eso usamos DNS.

El DNS es como una guía telefónica. Cuando un ordenador necesita hablar con otro usando un nombre, pregunta al servidor DNS cuál es la dirección IP correspondiente. Por ejemplo, si escribes planes.secretos, el PC consulta al DNS y este le responde: "la IP es 192.168.50.100". Entonces el PC ya sabe a dónde enviar los paquetes.

Esto pasa automáticamente cada vez que usas un navegador, haces ping a un nombre o accedes a un servidor. Si el DNS no funciona, los nombres no se resuelven y aparece un error que dice que el host no se ha encontrado.

En esta misión, configurar un servidor DNS en la red de Coruscant permite que tanto el PC Bothan como el PC de la Flota puedan usar nombres en lugar de memorizar direcciones. Sin DNS, sería imposible comunicarse usando nombres, y todo sería más lento y propenso a errores.

*EJERCICIO 4*

Cifrado simétrico
El cifrado simétrico utiliza una única clave secreta para cifrar y descifrar los mensajes. Es rápido y eficiente, pero tiene una gran debilidad: la clave debe compartirse previamente.
Si Leia y Luke acuerdan una frase secreta para comunicarse, eso es cifrado simétrico. Pero si esa clave es interceptada, el enemigo podría leer todos los mensajes.

Cifrado asimétrico
El cifrado asimétrico usa dos claves diferentes: una pública y otra privada.

La clave pública se puede compartir con cualquiera.
Solo quien tenga la clave privada correspondiente puede descifrar el mensaje.
Esto permite que un nuevo aliado rebelde reciba información sin haber acordado una clave secreta antes. Basta con que reciba la clave pública y tenga su clave privada a salvo.

Autenticación y no repudio
Además de cifrar, es vital asegurarse de que:

El mensaje no ha sido modificado (integridad).
Viene de quien dice ser (autenticación).
El emisor no pueda negar que lo envió (no repudio).
Esto se logra con firmas digitales, certificados y protocolos como HTTPS o SSH.

SSH y Telnet
Telnet transmite la información en texto plano, incluidas las contraseñas. SSH, en cambio, cifra toda la sesión, lo que hace que sea seguro administrar routers y switches de forma remota.

Por eso, la Alianza debe usar SSH siempre. Si se usara Telnet y el Imperio intercepta el tráfico, podría capturar credenciales y tomar el control de los equipos.

*EJERCICIO 5*
1. Cifrado simétrico

Se usa una sola clave secreta.
La misma clave sirve para cifrar y descifrar.
Es rápido, pero tiene un problema: hay que compartir la clave antes con el otro.
Si la clave cae en manos del enemigo, puede leerlo todo.

2. Cifrado asimétrico

Usa dos claves diferentes: una pública y una privada.
Tú compartes tu clave pública con cualquiera.
Solo tú puedes leer los mensajes que se cifran con ella, porque solo tú tienes la clave privada.
Es ideal cuando necesitas enviar mensajes sin haber compartido una clave antes.

