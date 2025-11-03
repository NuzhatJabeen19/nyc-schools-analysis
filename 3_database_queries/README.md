# Day 3 — SQL via Python (nyc schools)

Concise summary of the notebook: SQL queries executed from Python (psycopg2 / pandas) and their outcomes.

Purpose
- Run SQL from a Jupyter notebook to explore NYC high school tables (`high_school_directory`, `school_demographics`).
- Load results into pandas for inspection and simple analyses.

How connection is handled
- Notebook reads DB credentials from an environment file via python-dotenv and connects with psycopg2.
- (Ensure .env is not committed and contains DB_NAME, DB_USER, DB_PASSWORD, DB_HOST, DB_PORT, DB_SSLMODE.)

SQL queries run (high-level)
- Select full tables:
  - SELECT * FROM nyc_schools.high_school_directory
  - SELECT * FROM nyc_schools.school_demographics
  - Outcome: tables loaded into pandas DataFrames for analysis.
- School distribution by borough:
  - COUNT(DISTINCT dbn) grouped by borough.
  - Outcome: Brooklyn 121, Bronx 118, Manhattan 106, Queens 80, Staten Island 10.
- Average ELL % by borough (LEFT JOIN):
  - AVG(sd.ell_percent) grouped by borough.
  - Outcome: Manhattan shows 7.57%; other boroughs returned NaN — join/data coverage issue.
- Top schools by SPED % per borough using window functions:
  - ROW_NUMBER() OVER (PARTITION BY borough ORDER BY sped_percent DESC) and filter rank <= 3.
  - Outcome: repeated single-school entries (same DBN across years) — `school_demographics` contains multiple years per DBN, causing duplicate school-year ranking.
- Python-side checks:
  - Merges and groupby operations used to confirm SQL results and inspect missing values.

Key outcomes / takeaways
- School counts per borough are reliable (435 total schools).
- Data quality issues identified:
  - `school_demographics` appears to include multiple years; aggregate queries must deduplicate or filter by year.
  - ELL aggregation returned NaNs for most boroughs — likely DBN mismatches, missing rows, or null values in `school_demographics`.
- Analysis implications:
  - Time dimension must be handled (choose a year or aggregate across years properly).
  - Fix/align DBN keys and inspect missingness before generalizing demographic metrics.

Next practical steps (short)
- Choose/filter a single `schoolyear` or deduplicate `school_demographics` before ranking.
- Inspect and align DBN values between tables; fill or document missing demographic rows.
- Keep credentials out of repo (.env in .gitignore); use .env.example for collaborators.

Location
- Notebook: 3. database_queries/day3_sql_analysis.ipynb
