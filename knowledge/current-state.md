# Current State

- Goal: maintain `/home/astrid/octave-mcp` — server auditado, suite verde,
  skill empaquetada en GitHub privado (`Astrid3333/octave-mcp`).
- Stage: alkahest + maxima + sagebrush + lispium + cadabra2
  (CAS de álgebra tensorial) + **cas_router_math_tool** (router
  unificado de los 4) integradas; ejercicios demo Laplace→ODE, número
  de clase newforms, cross-check multi-motor Lispium, cadena
  tensorial/fermiones Cadabra2, despacho multi-CAS y batería
  cross-check 4-CAS vs oráculo sympy.
- Current task: cross-check multi-motor integrado (decisión del
  usuario): `examples/multi_cas_crosscheck.py` resuelve 13 problemas
  en los 4 motores (derivada, integral, factor, sistema, gcd, limit,
  primalidad, big-int, identidad, det, totient, factorial, Basel) y
  compara contra sympy; adaptadores descubiertos por sonda: sagebrush
  es shim sin Sage real (`x, y = var('x y')` porque `var()` no
  inyecta en globals; `symbolic_sum(expr,var,a,b)` para series),
  maxima `determinant(...)` y noun-forms con ok=True, lispium
  parser s-expr propio + floats en big-int/factorial + eco de
  simplify, cadabra2 `**` sin `D` en eval. 6 pins de quirks.
  Resultado: ruff limpio, ejemplo **34/34 PASS**.
- Verification state: suite 371 registradas / 353 evaluadas /
  353 PASSED / 0 FAILED / 0 ERROR / 18 SKIPPED;
  health_check "healthy" (353 passed / 0 failed / 18 skipped);
  commits `0d61934`…`7f7db8f` + router `dc85ea4` + cross-check
  `f0de65e` pushados a `origin/migracion-mcp-octave-real`.
- Known pending (pasted-7): **ninguno** — todos los CAS integrados
  (alkahest, maxima, sagebrush, lispium, cadabra2, router) o
  descartados con evidencia (calnexus); backlog vacío.
- Next action: pedir al usuario qué sigue; posibles líneas: más
  cross-checks (p. ej. alkahest en la batería, ODE/laplace entre
  motores), documentación, o nueva meta.
