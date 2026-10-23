# Current State

- Goal: maintain `/home/astrid/octave-mcp` — server auditado, suite verde,
  skill empaquetada en GitHub privado (`Astrid3333/octave-mcp`).
- Stage: alkahest + maxima + sagebrush + lispium + cadabra2
  (CAS de álgebra tensorial) + **cas_router_math_tool** (router
  unificado de los 4) integradas; ejercicios demo Laplace→ODE, número
  de clase newforms, cross-check multi-motor Lispium, cadena
  tensorial/fermiones Cadabra2, despacho multi-CAS y batería
  cross-check **5-CAS** (4 + alkahest) + sección ODE/Laplace vs
  oráculo sympy, documentada en SKILL.md.
- Current task: «solucionemos lo roto» resuelto — el supuesto bug de
  `desolve` en sagebrush era **falsa alarma**: `function('y', t)`
  devuelve un closure sin aplicar (TypeError al sumar); la forma
  correcta `function('y')(t)` funciona y coincide con maxima (1ª y 2ª
  orden, ics, forzada — verificado por residuo). Batería **55/55**
  (+4 checks ODE sagebrush, pin renombrado `pin-sage-function-aplica`);
  `laplace` es gap real de sagebrush (NameError, documentado).
  SKILL.md + skill_content actualizados (`check_sync() == True`).
- Verification state: suite 371 registradas / 353 evaluadas /
  353 PASSED / 0 FAILED / 0 ERROR / 18 SKIPPED;
  commits `0d61934`…`f0de65e` + cross-check v2 `8a07df3` pushados;
  commit de la fase desolve pendiente de push.
- Known pending (pasted-7): **ninguno** — no hay nada roto abierto:
  ODEs cubiertas por maxima + sagebrush; `laplace` solo maxima
  (gap upstream documentado); alkahest/lispium/cadabra2 sin ODE por
  diseño (feature absence, no bug).
- Next action: commit+push de la fase desolve y checkpoint; después
  pedir al usuario qué sigue.
