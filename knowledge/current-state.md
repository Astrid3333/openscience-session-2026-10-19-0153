# Current State

- Goal: maintain `/home/astrid/octave-mcp` — server auditado, suite verde,
  skill empaquetada en GitHub privado (`Astrid3333/octave-mcp`).
- Stage: alkahest + maxima + sagebrush + lispium + cadabra2
  (CAS de álgebra tensorial) + **cas_router_math_tool** (router
  unificado de los 4) integradas; ejercicios demo Laplace→ODE, número
  de clase newforms, cross-check multi-motor Lispium, cadena
  tensorial/fermiones Cadabra2 y despacho multi-CAS.
- Current task: router unificado integrado (decisión del usuario, no
  cerrar el backlog): `cas_router_math_tool` despacha en proceso vía
  tool_registry (sin wire), ruteo engine>field>sniff>default-maxima,
  fallback encadenado con log `attempts[]`, op=guia con tabla; 10
  validate checks (adaptadores descubiertos en smoke: cadabra2 envuelto
  en evaluate(Ex), sagebrush op=sage con nombres Sage `euler_phi` no
  `eulerphi`, lispium potencia `(^ 2 10)` — `expt` es eco silencioso);
  ejemplo `examples/cas_router_dispatch.py` 9/9 PASS.
- Verification state: suite 371 registradas / 353 evaluadas /
  353 PASSED / 0 FAILED / 0 ERROR / 18 SKIPPED;
  health_check "healthy" (353 passed / 0 failed / 18 skipped);
  commits `0d61934`…`7f7db8f` + router pushados a
  `origin/migracion-mcp-octave-real`.
- Known pending (pasted-7): **ninguno** — todos los CAS integrados
  (alkahest, maxima, sagebrush, lispium, cadabra2, router) o
  descartados con evidencia (calnexus); backlog vacío.
- Next action: pedir al usuario qué sigue (backlog vacío); posibles
  líneas: más cross-checks de engines, documentación, o nueva meta.
