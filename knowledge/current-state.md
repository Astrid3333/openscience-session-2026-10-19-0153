# Current State

- Goal: maintain `/home/astrid/octave-mcp` — server auditado, suite verde,
  skill empaquetada en GitHub privado (`Astrid3333/octave-mcp`).
- Stage: alkahest + maxima + sagebrush + lispium + **cadabra2**
  (CAS de álgebra tensorial, Kasper Peeters) integradas; ejercicios
  demo Laplace→ODE, número de clase newforms, cross-check multi-motor
  Lispium y cadena tensorial/fermiones Cadabra2.
- Current task: integración Cadabra2 cerrada (commit pushado, ver
  `git log`): `cadabra2` 2.6.0 (módulo C++ .so + API python, input
  LaTeX), tool one-shot (subprocess fresh por llamada — propiedades
  Indices/Metric son estado global), ops estructuradas
  canonicalise/collect_terms/substitute/eliminate_metric/
  sort_product/distribute/evaluate/simplify/to_sympy + eval libre +
  guia, 18 validate checks con quirks fijados como pins (list-
  properties solo con comas; canonicalise no cancela → collect_terms;
  fermiones vía sort_product; evaluate() para numerales; expand no
  expande potencias; substitute no desciende a base de potencia;
  SympyBridge `x^2`→`x(UP2)`, usar `x**2`; Ex() nunca lanza —
  trunca en silencio; δ de Kronecker no contrae, metric sí). Ejercicio
  `examples/cadabra2_tensor_canonicalisation.py` **12/12 PASS**.
- Verification state: suite 370 registradas / 352 evaluadas /
  352 PASSED / 0 FAILED / 0 ERROR / 18 SKIPPED;
  health_check "healthy" (352 passed / 0 failed / 18 skipped);
  commits `0d61934`…`32e4a64` + ciclo Cadabra2 pushados a
  `origin/migracion-mcp-octave-real`.
- Known pending (pasted-7): **ningún CAS sin integrar** — lispium
  cerrado, cadabra2 cerrado, calnexus descartado con evidencia (app
  Streamlit, no CAS); router unificado de CAS (opcional) a decisión
  del usuario.
- Next action: pedir decisión sobre el router unificado (integrar o
  cerrar el backlog pasted-7).
