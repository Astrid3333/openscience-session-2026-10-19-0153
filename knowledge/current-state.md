# Current State

- Goal: maintain `/home/astrid/octave-mcp` — server auditado, suite verde,
  skill empaquetada en GitHub privado (`Astrid3333/octave-mcp`).
- Stage: alkahest + maxima + sagebrush + **lispium_math_tool** (CAS Lisp
  de cross-check) integradas; ejercicios demo Laplace→ODE, número de
  clase newforms y cross-check multi-motor Lispium.
- Current task: integración Lispium cerrada (commit `32e4a64` pushado):
  `lispium` 0.16.0 (binario Zig vía `lispium.cli.get_binary_path()`),
  tool one-shot (temp `.lspm` + `lispium run` por llamada; sin sesión),
  17 validate checks con bugs de motor fijados como pins (factorial
  float n∈{18,19,20}; `(fact n)` no existe y funciones desconocidas
  silenciosas con exit 0; binomial float >~10^15; `solve` en formato
  `(solutions a b)`; **`prime?` solo fiable ~≤2^53** — M61 `2^61-1`
  devuelve 0, sagebrush/sympy dicen primo). Ejercicio
  `examples/lispium_crosscheck.py` **14/14 PASS** cruzando Maxima,
  sagebrush y referencias Python.
- Verification state: suite 369 registradas / 351 evaluadas /
  351 PASSED / 0 FAILED / 0 ERROR / 18 SKIPPED;
  health_check "healthy" (351 passed / 0 failed / 18 skipped);
  commits `0d61934`, `734d1e9`, `7727af8`, `5184ba3`, `a43bb5e`,
  `cb01c4c`, `32e4a64` pushados a `origin/migracion-mcp-octave-real`.
- Known pending (pasted-7): `cadabra2` 2.6.0 (tensores/física) — único
  CAS pendiente, verificar autenticidad + smoke tensorial antes de
  decidir; `calnexus` descartado con evidencia (app Streamlit, no CAS);
  router unificado de CAS (opcional) a decisión del usuario.
- Next action: ciclo Cadabra2 (verificar import + smoke), luego pedir
  decisión sobre el router unificado.
