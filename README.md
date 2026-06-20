# AWS dbt Snowflake - Airbnb Project

This project (`aws-dbt-snowflake`) is a data engineering project that uses [dbt (data build tool)](https://www.getdbt.com/) and Snowflake to process and model Airbnb data.

## Project Structure

- `dbt_airbnb/`: The main dbt project folder containing the models, macros, tests, and seeds.
- `pyproject.toml` / `uv.lock`: Python dependencies and project metadata. The project requires Python >= 3.12 and uses `dbt-core` and `dbt-snowflake`.
- `main.py`: A simple entry point for Python executions.

## Data Architecture

The dbt project implements a Medallion architecture with the following layers configured in `dbt_project.yml`:

- **Bronze**: Raw data layer (`models/bronze/`).
- **Silver**: Cleansed and conformed data layer (`models/silver/`).
- **Gold**: Business-level aggregates and curated data layer (`models/gold/`).

## Setup and Installation

1. Ensure you have Python 3.12+ installed.
2. Install the project dependencies using `uv` (recommended) or pip:
   ```bash
   # Using uv
   uv sync
   
   # Using pip
   pip install -e .
   ```
3. Navigate into the dbt project directory:
   ```bash
   cd dbt_airbnb
   ```
4. Set up your Snowflake connection profile in `~/.dbt/profiles.yml` under the profile name `dbt_airbnb`.
5. Run `dbt deps` to install any required dbt packages (if any).

## Usage

To build the models, execute the following command from the `dbt_airbnb` directory:

```bash
dbt run
```

To test the models:

```bash
dbt test
```
