# CHECKLIST — AAD1 Smart City (vivo; actualizar en cada paso cerrado)

Estado: 🟡 en curso · Última actualización: 2026-11-05 (Paso 3 cerrado: cruce enunciado vs base)

## Tareas
- [x] Paso 1: Leer el enunciado completo (`AAD1.Smart_City.pdf`) y extraer la lista de requisitos limpia.
- [x] Crear `AGENTS.md` con reglas de trabajo y lista negra de exclusión.
- [x] `git init` + commit + push ✅ — remoto: `https://github.com/pabloregidor/aad1_ra.git` (rama `main`). Per-commit por cerrar cada paso.
- [x] Paso 2: Fijar base de partida. DECISIÓN DEL USUARIO (2026-11-05): se reutiliza NO solo la topología sino TODO el planteamiento general de la memoria anterior. Documento de trabajo: `aad1_ra.docx` con la captura de topología CORREGIDA (ahora incluye Cloud-PT ISP_Internet, que faltaba). Topología: R_Ayuntamiento+SW_Core (3650-24PS, servers, PC0-PC1) · R_Policia+SW (2960, PC2-PC4) · R_Turismo+SW (2960, PC5-PC6) · Teletrabajador (HomeRouter-PT-AC + Laptop), todo vía Cloud-PT ISP.
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
