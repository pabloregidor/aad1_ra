# COMPARATIVA de tecnologías WAN — Tarea 1 (material de decisión; hecho de 0)

Uso: base para que el usuario elija y redacte su comparativa. Aquí no hay precios ni modelos: eso va en el paso de equipos de la Tarea 2, con fuentes web. Valores cualitativos para ordenar ideas: ALTA / MEDIA / BAJA. La elección final la hace el usuario y puede desviarse de esta lectura rápida si su justificación lo apoya.

## 1. Opciones candidatas (definiciones en llano)

**O1 · Línea arrendada (leased line)** — Circuito dedicado que el operador alquila en exclusiva al cliente: siempre activo, velocidad fija garantizada y sin compartir el canal con nadie. Corresponde a conmutación de circuitos: se reserva el canal aunque no haya tráfico. Fiabilidad y seguridad máximas, pero coste muy alto.

**O2 · Acceso dedicado de banda ancha (Metro Ethernet sobre fibra)** — Enlace dedicado de fibra que entrega Ethernet de operador a operador, de punto a punto, dentro del área metropolitana. Ancho de banda simétrico y escalable, con coste menor que una línea arrendada clásica. Es lo elegido en la base para el enlace dedicado entre el nodo central y la sucursal crítica.

**O3 · VPN MPLS del operador (red privada virtual de capa 3, gestionada)** — El operador avanza por sus enlaces usando etiquetas cortas en la ruta, en lugar de consultar la tabla de encaminamiento completa IP en cada salto, y alquila una red privada virtual que separa el tráfico del cliente del resto de sus clientes. Buena calidad con contrato de servicio; la contratación y el control son del operador.

**O4 · Banda ancha comercial FTTx + VPN IPsec (basada en Internet, cableada)** — Acceso comercial de fibra hasta el edificio. El tráfico municipal viaja cifrado en un túnel IPsec (paquetes IP cifrados y autenticados entre dos extremos) hasta el nodo central. Barata y rápida de conseguir; la calidad del tránsito depende del operador, no de nosotros.

**O5 · Cable coaxial HFC + VPN IPsec (basada en Internet, cableada)** — Alternativa cableada a O4 que usa la red de cable de TV: fibra hasta el barrio y coaxial hasta el edificio. Ancho de banda asimétrico y compartido entre vecinos: peor que la fibra para tráfico sensible.

**O6 · WAN móvil 4G/5G + VPN IPsec (inalámbrica basada en Internet)** — Acceso por radio celular. Único medio viable donde no llega cable, y útil como respaldo si cae el enlace principal. Cobertura y velocidad dependen del operador; el ancho de banda es variable.

**O7 · Acceso doméstico (FTTx/4G) + VPN IPsec** — La del teletrabajador: los medios son del funcionario (portátil, router doméstico y su línea). El ayuntamiento solo habilita el extremo receptor del túnel VPN. No gasta presupuesto (aclarado el 05-11).

## 2. Matriz comparativa (cualitativa)

| Opción | Simplicidad | Calidad (latencia/estabilidad) | Disponibilidad | Ancho de banda | Seguridad | Coste |
|---|---|---|---|---|---|---|
| O1 Línea arrendada | MEDIA (gestión simple pero circuito rígido) | ALTA | ALTA | MEDIA (fija y cara de ampliar) | ALTA (canal exclusivo) | MUY ALTO |
| O2 Metro Ethernet dedicado | ALTA (habla el mismo lenguaje que la LAN) | ALTA | ALTA | ALTA (simétrico y escalable) | ALTA (enlace dedicado; cifrado añadible si los datos extremos lo exigen) | MEDIO-ALTO |
| O3 VPN MPLS del operador | MEDIA (dependencia del proveedor) | ALTA (clases de servicio del operador) | ALTA (contrato de servicio) | MEDIA-ALTA | ALTA (separación lógica de otros clientes) | MEDIO-ALTO (cuota anual) |
| O4 FTTx comercial + IPsec | ALTA (equipos estándar) | MEDIA (sin garantía del operador) | MEDIA | ALTA en descarga; simétrica según plan | MEDIA en el tránsito público; ALTA extremo a extremo con IPsec | BAJO |
| O5 HFC + IPsec | ALTA | MEDIA-BAJA (tráfico compartido) | MEDIA | MEDIA y asimétrica | como O4 | BAJO |
| O6 4G/5G + IPsec | ALTA (sin obra civil) | MEDIA-BAJA (radio compartida) | MEDIA-BAJA | VARIABLE | como O4 | BAJO-MEDIO (por consumo) |
| O7 Doméstico + IPsec | ALTA (sin implantación municipal) | MEDIA | MEDIA-BAJA | MEDIA (plan residencial) | como O4 | NULO para el ayuntamiento |

## 3. Lectura hacia la solución base (a confirmar por el usuario)

- La línea arrendada (O1) era la alternativa clásica, y se descarta por coste frente a O2.
- Enlace crítico y de más rendimiento: O2 (conexión dedicada de banda ancha, exigida por el enunciado) para Ayto-Policía.
- Sede comercial: O4 (cableada basada en Internet, exigida) con IPsec, para Turismo y el acceso comercial del Ayto.
- Teletrabajo: O7 (basada en Internet en su modalidad inalámbrica doméstica, exigida) con IPsec desde el domicilio.
- Tránsito del operador: la conmutación de paquetes (exigida) queda cubierta por los accesos O4 y O7 sobre la red pública.
- Combinación final propuesta para defender: O2 + O4 + O7.

## 4. Decisiones que le tocan al usuario (para la redacción)

1. Confirmar que la combinación O2 + O4 + O7 es la que quiere defender (cubre todos los tipos exigidos).
2. Decidir si la comparativa muestra todas las opciones O1-O7 o un subconjunto (se recomienda al menos 3-4 alternativas más la elegida).
3. Opcional para la Tarea 3 (alternativa si cambian las necesidades): O6 como respaldo de enlace y O3 como opción de operador. Solo son alternativas posibles: no se implantan en la solución base y no se adelanta ese paso.
4. Justificación final por el eje crítico-no crítico: tráfico crítico a enlace dedicado (O2); tráfico no crítico a acceso comercial con IPsec (O4 y O7).

## 5. Qué falta para cerrar el bloque

- Cuando toque el bloque de equipos de la Tarea 2: verificación web de planes y precios para O2 y O4, que será la base mensual del presupuesto.
