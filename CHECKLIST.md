# CHECKLIST — AAD1 Smart City (vivo; actualizar en cada paso cerrado)

Estado: 🟡 en curso · Última actualización: 2026-11-05 (Paso 3 cerrado: cruce enunciado vs base)

## Tareas
- [x] Paso 1: Leer el enunciado completo (`AAD1.Smart_City.pdf`) y extraer la lista de requisitos limpia.
- [x] Crear `AGENTS.md` con reglas de trabajo y lista negra de exclusión.
- [x] `git init` + commit + push ✅ — remoto: `https://github.com/pabloregidor/aad1_ra.git` (rama `main`). Per-commit por cerrar cada paso.
- [x] Paso 2: Fijar base de partida. DECISIÓN DEL USUARIO (2026-11-05): se reutiliza NO solo la topología sino TODO el planteamiento general de la memoria anterior. Documento de trabajo: `aad1_ra.docx`. TOPOLOGÍA DEFINITIVA (2ª captura, 05-11): R_Ayuntamiento (ISR4331) → SW_Core_Ayto (3650-24PS) → Switch0/SW_Ayto (2960-24TT) con Servidor_BaseDatos, Servidor_Web, PC0, PC1 · R_Policia (ISR4331) → SW_Policia (2960-24TT) con PC2, PC3 · R_Turismo (ISR4331) → SW_Turismo (2960-24TT) con PC4, PC5 · Teletrabajador (HomeRouter-PT-AC + Laptop) — todo vía Cloud-PT ISP_Internet. 3 switches de acceso con sede (el 3650 queda como núcleo L3+PoE). NOTA ABIERTA: renombrar `Switch0` → `SW_Ayto` (decisión usuario en .pkt).
- [x] Paso 3: Cruce enunciado vs base → `CRUCE_Enunciado_vs_Base.md`. Estado por requisito [REUTILIZAR|ADAPTAR|VERIFICAR|x HECHO]. 3(ERROR): nº switches presupuesto (3 vs 2), equipos teletrabajo fuera de listado/presupuesto, incoherencia DSL vs HomeRouter-PT-AC; además la memoria vieja cae en la trampa nº 1 → reescritura desde 0 SIEMPRE.
- [ ] Paso 4 (propuesto): preparar con el usuario la comparación de alternativas tecnológicas (Tarea 1, opción [ADAPTAR] del cruce) → pendiente de "ok".
- [ ] Definir rol de la red WAN (empresa / ISP clientes / ISP-ISP) y necesidades de conectividad (Tarea 1).
- [ ] Identificar redes, usuarios y servicios a conectar (Tarea 1).
- [ ] Seleccionar arquitectura WAN + comparar alternativas tecnológicas con justificación (Tarea 1).
- [ ] Diagrama lógico inicial en Packet Tracer (lo monta el usuario; nosostros damos lista de dispositivos/topología/direccionamiento).
- [ ] Defensa 1 preparada.
- [ ] Tarea 2: tecnologías seleccionadas (capa física + capa de enlace por cada una).
- [ ] Tarea 2: listado de equipos y medios con referencias web verificadas (comprobar EOL antes de proponer).
- [ ] Tarea 2: presupuesto de implantación.
- [ ] Cambio imprevisto: analizar → modificar → actualizar diagrama/tecnologías/presupuesto → justificar (NO adelantar hasta que llegue).
- [ ] Defensa 2 preparada.
- [ ] Tarea 3: reflexión (elementos clave, decisiones, alternativa si cambian necesidades, ventajas/desventajas, mejora concreta, dificultades).
- [ ] Defensa 3 preparada.
- [ ] Revisión técnica de otro proyecto (10 %).

## Datos verificados (con fuente y estado)
| Dato | Fuente (URL) | Estado |
|---|---|---|
| Enunciado completo read (2 páginas, v3 Sep 2026) | `AAD1.Smart_City.pdf` (local) | VERIFICADO |
| Pesos de evaluación: 40/20/30/10 | `AAD1.Smart_City.pdf` p.2 | VERIFICADO |
| — (pendiente: equipos, precios) | — | NO VERIFICADO |

## Errores abiertos / avisos
- [x] Los 7 defectos detectados por el cruce están listados en `CRUCE_Enunciado_vs_Base.md` § "Defectos detectados".
- La carpeta `projects/smart_city_wan_granada_20261021/` es material de la iteración anterior: solo sirve de referencia de topología; NO reutilizar textos.
- LA MEMORIA VIEJA CAE EN LA TRAMPA nº 1 (frase de la arquitectura convergente): prohibido heredar; todo texto final se redacta de 0.
