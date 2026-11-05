# CRUCE — Enunciado vs Base de partida (documento de trabajo; hecho de 0 sobre el planteamiento nuevo)

Objetivo: determinar qué del diseño anterior SIRVE tal cual, qué HAY QUE ADAPTAR y qué está MAL en la iteración anterior. Toda la redacción del documento final será nueva desde cero (no se reutiliza texto de nada).

Estados: [REUTILIZAR] usar tal cual · [ADAPTAR] hay que trabajar/decidir sobre ello · [VERIFICAR] confirmar con fuente web antes de usar · [ERROR] defecto detectado, corregir sí o sí.

AVISO TRAMPA: la memoria anterior contiene la trampa nº 1 del enunciado (la frase de la "arquitectura convergente resiliente", en su punto de tecnologías de la Tarea 2). Queda prohibido heredarla: la reescritura desde 0 debe garantizármelo. No debatir la frase ni contrastar con ella en el documento final.

---

## TAREA 1 — Examinar un modelo WAN

| Requisito del enunciado | Situación sobre la base anterior | Estado |
|---|---|---|
| Estudiar tipos de redes WAN (empresariales, ISP, entre ISP) | contexto académico; basta con dejar constancia de los tres tipos al elegir el rol | [REUTILIZAR] |
| Rol de la red elegido (1 de los 3) | red de EMPRESA: el ayuntamiento conecta LAN central + sucursales + teletrabajadores | [REUTILIZAR] |
| Necesidades de conectividad | 3 pilares: (1) disponibilidad y baja latencia para emergencias, videovigilancia y tránsito en tiempo real; (2) confidencialidad de datos de ciudadanos → segmentar tráfico; (3) acceso remoto cifrado del funcionariado con VoIP | [REUTILIZAR] concepto · [ADAPTAR] redacción |
| Redes, usuarios y servicios a conectar | 4 dominios: nodo central (CPD + administración + portal), sucursal policial (control de tráfico + videovigilancia), oficina de turismo (administrativos + red pública aislada de visitantes), teletrabajador (portátil + router doméstico). La captura corregida (2ª versión, 05-11) fija los equipos: PC0-PC1 (Ayto, colgados del switch de acceso de sede), PC2-PC3 (Policía), PC4-PC5 (Turismo), Laptop (teletrabajo), 2 servidores centrales | [REUTILIZAR] |
| Arquitectura WAN seleccionada | estrella hub-and-spoke con nodo central como concentrador y sucursales/teletrabajo colgadas de la red pública; la captura corregida añade el Cloud-PT del ISP que faltaba | [REUTILIZAR] |
| Tecnologías posibles + comparar alternativas y justificar | la base solo traía una comparación breve contra la línea arrendada; falta el bloque completo de opciones (dedicada, VPN L3 del operador, banda ancha comercial, WAN inalámbrica 4G/5G) con tabla ventajas/desventajas vds. los 6 criterios del enunciado de la Tarea 3 | [ADAPTAR] trabajo nuevo |
| Diagrama lógico inicial Packet Tracer | captura corregida, entregada por el usuario en `aad1_ra.docx` | ✅ HECHO |

## TAREA 2 — Diseñar el modelo WAN

### Cobertura de los tipos de tecnología exigidos
| Tipo exigido | Correspondencia con la base | Estado |
|---|---|---|
| Conexión dedicada de banda ancha | enlace dedicado 1 Gbps R_Ayuntamiento ↔ R_Policia (Metro Ethernet sobre fibra propia del operador) | [REUTILIZAR] |
| Conmutación de paquetes | todo el tránsito por ISP_Internet (Cloud-PT): el operador conmuta paquetes de extremo a extremo; la justificación vieja era débil → explicar desde el acceso (Ethernet + PPPoE) hasta el tránsito | [REUTILIZAR] concepto · [ADAPTAR] justificación |
| Cableada basada en Internet | accesos comerciales FTTx en Ayuntamiento y Turismo con túneles cifrados hacia el nodo central | [REUTILIZAR] |
| Inalámbrica basada en Internet | teletrabajador: se conecta desde Su CASA con medios PROPIOS (Laptop + HomeRouter-PT-AC + su línea residencial) → Internet → túnel VPN cifrado hacia el nodo central; el ayuntamiento NO financia esos equipos ni (por coherencia) su conexión doméstica. Además Wi-Fi público para visitantes en Turismo (requiere AccessPoint-PT si se materializa) | [REUTILIZAR] concepto · [ADAPTAR] redacción propia |

### Capa física y capa de enlace POR tecnología
| Tecnología | Capa física (base anterior) | Capa de enlace (base anterior) | Estado |
|---|---|---|---|
| A) Enlace dedicado Ayto↔Policía | fibra óptica monomodo con transceptores SFP 1000BASE-LX/LH en los routers | Ethernet directa (tramas encapsuladas de extremo a extremo sobre el transporte dedicado) | [REUTILIZAR] |
| B) Acceso comercial a Internet | FTTx hasta el punto de demarcación (terminal óptico de red) + cobre par trenzado al router | PPPoE (sesión inicial + IP pública automática) + IPsec para tráfico corporativo (cifrado AES + autenticación HMAC) | [REUTILIZAR] |
| C) Tránsito por la red del operador | bucle local del ISP: fibra o par trenzado GigE hasta la interfaz del router de sede | Ethernet de extremo a extremo; conmutación interna del operador por etiquetas (MPLS) como detalle del proveedor | [ADAPTAR] aclarar que el MPLS es del operador: no se compra ni presupuesta |
| D) Wi-Fi | bandas 2,4 GHz / 5 GHz | 802.11 con CSMA/CA y WPA2/WPA3 en el tramo local; al llegar al router doméstico se desencapsula a Ethernet y sigue por el túnel | [REUTILIZAR] |

#### Nota de revisión del 05-11 (2ª captura del usuario)
NOTA DE REVISIÓN 05-11 (2ª captura del usuario): la captura definitiva del `aad1_ra.docx` coloca también en el Ayuntamiento un switch de acceso 2960-24TT (por defecto "Switch0"; sugerencia: renombrarlo SW_Ayto) entre los equipos finales y el switch núcleo 3650-24PS, que a su vez une con R_Ayuntamiento. Consecuencias: (a) la topología tiene 3 switches de acceso de sede (Ayto + Policía + Turismo), así que las 3 unidades del presupuesto anterior eran correctas; (b) el 3650-24PS queda con rol de núcleo: enrutamiento entre subredes internas y alimentación PoE; (c) los PCs de Turismo pasan a ser PC4-PC5 y Policía PC2-PC3.

ACLARACIÓN DEL USUARIO (05-11) sobre el teletrabajo: el HomeRouter-PT-AC y la Laptop son el entorno doméstico PROPIO del funcionario (teletrabajo desde casa con VPN): no los compra ni financia el ayuntamiento. En la memoria se describen como acceso desde el domicilio, no como activos municipales; el presupuesto solo cubre equipos y líneas de Ayto, Policía y Turismo.

### Listado de equipos, medios y presupuesto
- [CLARIFICACIÓN DEL USUARIO] el HomeRouter-PT-AC y la Laptop del teletrabajador son medios PROPIOS del funcionario: NO van en el listado comprado por el ayuntamiento ni en el presupuesto; en la memoria se describen como entorno doméstico del teletrabajo. Por coherencia, la línea de acceso de su casa tampoco entra en el OPEX municipal (solo Ayto + Turismo en las cuotas de acceso).
- [ERROR] incoherencia: el texto viejo hablaba de "equipo de acceso DSL" para el acceso remoto, pero la captura usa HomeRouter-PT-AC. Unificar en un único acceso.
- [VERIFICAR] comprobar EOL de los modelos con fuente web antes de presupuestar (ISR 4331, Catalyst 3650-24PS y en especial Catalyst 2960-24TT-L, línea con años en fin de vida; si está descatalogado, proponer sustituto comercializable, p. ej. gama Catalyst 1300). Por cada equipo: URL de fabricante/mayorista + precio unitario, buscados de 0.
- [ADAPTAR] presupuesto: la estructura CAPEX (equipos + tendido) + OPEX (líneas WAN 12 meses) sirve de esqueleto, pero recalcular con precios verificados hoy.

### Cambio imprevisto (no se adelanta; sólo se deja anotado)
El escenario de la iteración anterior (nuevo grupo de usuarios en Turismo: VLANs + subinterfaces router-on-a-stick + ACL extendida + partida pequeña de latiguillos) es factible sobre esta topología sin comprar router ni switch. DECISIÓN ABIERTA (peso 20 %): repetir ese escenario o elegir otro de la lista del enunciado (más usuarios, nuevas sedes, más seguridad, más disponibilidad, menos presupuesto, nuevos servicios municipales). Se decide cuando llegue el paso (regla 6).

## TAREA 3 — Reflexión
- íntegramente material nuevo según los requisitos de la Tarea 3 (elementos clave, decisiones, alternativa si cambian necesidades, ventajas/desventajas en las 6 dimensiones, mejora concreta, dificultades). Configura la lista de decisiones que alimentas al redactar en su momento.

## Defectos detectados en la iteración anterior (resumen; tras 2ª captura del 05-11)
1. ~~Cantidad de switches de acceso en presupuesto (3 vs 2)~~ → FALSA ALARMA: la 2ª captura añade SW_Ayto (Switch0) en Ayuntamiento; las 3 unidades son correctas [RESUELTO]
2. ~~HomeRouter-PT-AC + Laptop fuera del listado y del presupuesto~~ → ACLARACIÓN DEL USUARIO: medios propios del teletrabajador, correcto que NO se presupuesten [RESUELTO]
3. Incoherencia DSL vs HomeRouter-PT-AC en el acceso remoto [ERROR]
4. Justificación de conmutación de paquetes insuficiente (tecnología obligatoria) [ADAPTAR]
5. Comparativa de alternativas de la Tarea 1 incompleta [ADAPTAR]
6. Referencias web + precios sin re-verificación 2026 y sin comprobar EOL [VERIFICAR]
7. La memoria vieja cae en la frase-trampa nº 1 del enunciado → no reutilizar [ERROR]

## Siguientes pasos (a confirmar por el usuario)
1. Bloque de comparación tecnológica de la Tarea 1: preparo lista de opciones y criterios para que decidas/redactes.
2. Verificación web (EOL + precios actuales) de los equipos → nueva base del presupuesto de la Tarea 2.
