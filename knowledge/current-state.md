# Current State

- Goal: maintain `/home/astrid/octave-mcp` — server auditado, suite verde,
  skill empaquetada en GitHub privado (`Astrid3333/octave-mcp`), conectado
  a Claude Desktop.
- Stage: 5-CAS + router; ciclo «5 adiciones en orden» (T1–T5) CERRADO y
  PUSHEADO (hasta `78d2ff4`): router `operation=crosscheck` (validate
  15/15), `sympy_eval_tool` (quinto motor, 9/9), cobertura validate
  **372/372 con 0 SKIPPED**, fuzzing diferencial en la batería (semilla
  `FUZZ_SEED=20261024`, 12 rondas, **99/99 PASS** = 63+36, determinista)
  y **CI en GitHub Actions** (jobs lint sobre manifiesto
  `ci/ruff_files.txt` + smoke `ci/smoke.py` vía stdio con
  `requirements.txt`). README generado con `render_readme.py` (check OK).
- Ciclo 2 (2026-10-25) — Claude Desktop: config corregida
  (`claude_desktop_config.json` apuntaba al server viejo `mcp_octave`;
  ahora `.venv/bin/python server.py`, backup `.bak-20261025`), servidor
  conectado y sirviendo (log `mcp-server-octave.log`: connected + 5
  tools/call OK). **No había diálogo de aprobación pendiente.**
  `health_check_tool` diagnosticado: no es crash ni proxy — corre la
  suite en SERIE (~5.5 min) y el cliente cancela a los 4 min
  (`notifications/cancelled`); el server sí respondió 70 s después.
- Verification state: suite completa rerun **372 registradas / 372
  evaluadas / 372 PASSED / 0 FAILED / 0 ERROR / 0 SKIPPED / 144.3 s**
  (4 workers, `run_all_validations.py` desprendido con `setsid --fork`,
  log `/tmp/opencode/validations_full.log`); batería **99/99**; guard
  exit 0; ruff 0 en los 17 archivos del manifiesto (`server.py` excluido,
  815 errores pre-existentes no tocados); pdelta `buckling_load` funcional
  (fix bug `N_max`), valores deterministas timber/concrete/pdelta intactos.
- CI en GitHub Actions verde y sin anotaciones (commit `78d2ff4`:
  checkout@v7 + setup-python@v7 node24, runner fijo ubuntu-24.04);
  README drift check también verde.
- Known pending (pasted-8 + ciclo 2): `alkahest` crashea con SIGILL y
  cae a sympy sin avisar; `statmech_partition_tool` sin paquete symbolic
  de Octave (validate saltado); `lispium`/`cadabra2` pasan por bugs
  conocidos anclados, no por camino real; `health_check_tool` sigue
  secuencial (candidato a `PARALLEL_WORKERS=4` para caber en 4 min).
- Next action: pedir al usuario qué sigue (candidatos: hacer
  `health_check_tool` paralelo, ruff de `server.py`, revisar los 4
  pending anteriores, nueva funcionalidad).
