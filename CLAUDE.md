# CLAUDE.md · PF-XX <Titulo del proyecto>

## Contexto
Proyecto de portafolio personal de analítica de datos (seguros y finanzas del Perú).
Acta: docs/01_acta.md · Plan: docs/02_edt_gantt.md · Datos: docs/03_diccionario_datos.md

## Reglas obligatorias
- Usar solo datos públicos o sintéticos. Nunca datos personales reales ni información
  confidencial de empleadores, clientes o terceros.
- Toda cifra, tabla o gráfico que se publique lleva su fuente:
  "Fuente: <entidad>, <documento>, <fecha de corte>" o "Elaboración propia ...".
- Ninguna credencial en el código: usar variables de entorno (.env, fuera de Git).
- No hacer merge, release ni push a main: abrir un PR y esperar la revisión de José.

## Entorno
- Python 3.13 gestionado con uv (pyproject.toml + uv.lock).
- Instalar: `uv sync` · Calidad: `uv run ruff check .` y `uv run ruff format --check .`
- Pruebas: `uv run pytest` · Oracle: `docker compose up -d` (python-oracledb, modo Thin).

## Convenciones
- Nombres en inglés técnico; comentarios y docstrings en español.
- SQL Oracle-first en sql/oracle/; variante T-SQL en sql/sqlserver/ si aplica.
- Scripts SQL idempotentes, numerados (01_, 02_ ...) y con variables enlazadas.
- data/raw es inmutable; las transformaciones escriben en data/interim y data/processed.
- Gráficos con assets/jc-editorial.mplstyle: hallazgo en #B0593A, contexto en #C0BEBB.
- Antes de publicar texto: skill revision-anti-estilo-ia (scripts/lint_texto.py).

## Git
- Rama por issue: <tipo>/<n>-<descripcion-corta> (feat, fix, docs, data, chore).
- Commits: <tipo>: <descripción en español> (#<n>). El PR incluye "Closes #<n>".
