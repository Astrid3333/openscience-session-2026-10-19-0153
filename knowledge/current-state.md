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
- Ciclo 4-5 (2026-10-27) — pendientes aprobados «todo pero en orden»
  CERRADOS y PUSHEADOS (`0a1fa72`, `2a22160`+`fa37a76`, `5114529`):
  2a alkahest SIGILL (FLINT/MPFR sin ADX, script
  `scripts/fix_alkahest_adx_flint.sh`), 2b statmech con symbolic real
  (sin skipped), 2c lispium/cadabra2 con fixes reales en el wrapper
  (20/20 cada uno; pins de bugs upstream con `known_bug=True` +
  `known_bugs` en payload) y ruff de `server.py` 816→0 (fix manual +
  `.ruff.toml` per-file-ignores E402/F401 documentados; `server.py`
  ya está en `ci/ruff_files.txt`, 18 archivos).
- Verification state: suite completa rerun **372 registradas / 372
  evaluadas / 372 PASSED / 0 FAILED / 0 ERROR / 0 SKIPPED / 144.3 s**
  (4 workers, `run_all_validations.py` desprendido con `setsid --fork`,
  log `/tmp/opencode/validations_full.log`); batería **99/99**; guard
  exit 0; ruff 0 en los 18 archivos del manifiesto; pdelta
  `buckling_load` funcional (fix bug `N_max`), valores deterministas
  timber/concrete/pdelta intactos.
- CI en GitHub Actions verde y sin anotaciones (commit `78d2ff4`:
  checkout@v7 + setup-python@v7 node24, runner fijo ubuntu-24.04);
  README drift check también verde.
- Known pending: item 4 (nueva funcionalidad) sin tema propuesto por
  el usuario; reintento de `health_check_tool` en Claude Desktop
  (GUI, usuario); notas del ciclo 2026-10-27 sin push.
- Next action: preguntar al usuario el tema del item 4.
