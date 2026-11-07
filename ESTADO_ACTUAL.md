# ESTADO ACTUAL — volcado para continuar en otro dispositivo

Fecha: 2026-11-07. Todo lo demás está en git (commits hasta `453e7eb`, rama `main` de `pablor/aad1_ra`).

## Dónde estamos

- **Paso 1** ✅ enunciado leído; requisitos limpios (sin los 4 fragmentos-trampa) en `AGENTS.md`.
- **Paso 2** ✅ base fijada: MISMA topología y MISMO planteamiento general que la memoria anterior. Doc de trabajo: `aad1_ra.docx` (2ª captura, definitiva).
- **Paso 3** ✅ cruce enunciado vs base en `CRUCE_Enunciado_vs_Base.md`.
- **Paso 4** ✅ comparativa de alternativas preparada en `COMPARATIVA_Tecnologias_Tarea1.md` (material de decisión; la redacción final es del usuario, de 0).
- **Paso 5 (propuesto, pendiente)**: verificar web (EOL + precios actuales) de los equipos → nueva base del presupuesto de la Tarea 2.

## Topología definitiva (2ª captura del 05-11)

- `aad1_ra.docx` (versionado). Nombres: R_Ayuntamiento (ISR4331) → SW_Core_Ayto (3650-24PS) → Switch0/SW_Ayto (2960-24TT) con Servidor_BaseDatos, Servidor_Web, PC0, PC1 · R_Policia (ISR4331) → SW_Policia (2960-24TT) con PC2, PC3 · R_Turismo (ISR4331) → SW_Turismo (2960-24TT) con PC4, PC5 · Teletrabajador: HomeRouter-PT-AC + Laptop (medios propios del funcionario, NADA pagado por el ayuntamiento) — todo vía Cloud-PT ISP_Internet.
- Nota abierta: renombrar `Switch0` → `SW_Ayto` (lo decide el usuario al montar el .pkt).
- Aviso: la memoria vieja cae en la trampa nº 1 → todo texto final se redacta de 0.

## Lista de opciones de la comparativa (Tarea 1) — definiciones en llano

1. **O1 Línea arrendada (leased line)**: circuito exclusivo alquilado al operador, siempre activo, velocidad fija. Conmutación de circuitos. Fiabilidad/seguridad máximas, coste muy alto.
2. **O2 Acceso dedicado de banda ancha (Metro Ethernet sobre fibra)**: Ethernet punto a punto de operador a operador en el área metropolitana. Simétrico y escalable, coste menor que O1. Elegido para Ayto↔Policía.
3. **O3 VPN MPLS del operador**: el operador avanza con etiquetas por su red y alquila una red privada virtual L3 con contrato de servicio. Buen SLA; control y cuota del operador.
4. **O4 Banda ancha comercial FTTx + VPN IPsec**: acceso comercial de fibra al edificio; tráfico municipal cifrado en túnel IPsec hasta el nodo central. Barato, calidad según operador. Para Turismo (y acceso comercial del Ayto).
5. **O5 Cable HFC + IPsec**: red de cable de TV (fibra al barrio, coaxial al edificio). Asimétrico y compartido: peor para tráfico sensible.
6. **O6 WAN móvil 4G/5G + IPsec**: radio celular, sin obra civil, útil como respaldo; velocidad variable. Solo como alternativa futura para Tarea 3.
7. **O7 Acceso doméstico (FTTx/4G) + IPsec**: la del teletrabajador; medios y línea del propio funcionario, coste nulo para el ayuntamiento.

Matriz cualitativa (los 6 criterios de la Tarea 3) está en `COMPARATIVA_Tecnologias_Tarea1.md` §2.

## ⏳ PREGUNTAS PENDIENTES (decisión del usuario — motivo de este fichero)

**Q1. ¿Qué combinación defiendes en la comparativa?** La propuesta es **O2 + O4 + O7** (enlace dedicado Ayto-Policía + FTTx comercial con IPsec en Ayto/Turismo + teletrabajo con VPN desde su casa), que cubre los 4 tipos de tecnología exigidos por el enunciado: conexión dedicada de banda ancha, conmutación de paquetes (tránsito por la red pública), cableada basada en Internet e inalámbrica basada en Internet. ¿Confirmas O2+O4+O7 o cambias alguna pieza?

**Q2. ¿Cuántas opciones entran en la tabla comparativa final?** Todas (O1-O7) o un subconjunto (se recomienda mínimo 3-4 alternativas además de la elegida).

**Q3. ¿Arranco el Paso 5?** Verificación web de EOL y precios actuales (ISR4331, Catalyst 3650-24PS, Catalyst 2960-24TT; si algo está descatalogado, propongo el sustituto comercializable) para montar el nuevo presupuesto de la Tarea 2 con fuentes. Nada se propone sin verificar antes.

Reglas recordadas: 1 paso = propuesta + "ok" del usuario; explicación en llano de cada sigla la primera vez; comprobar EOL antes de proponer; commit en cada paso cerrado; cambio imprevisto NO se adelanta.
