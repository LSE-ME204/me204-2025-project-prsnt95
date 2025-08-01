# Reproducing Findings (TMDb)

This repository contains scripts for reproducing findings using data from **The Movie Database (TMDb)**.

---

## Requirements

* Python **3.9+**
* `pip` (bundled with most Python installs)
* A **TMDb API key** (free; create an account at [https://www.themoviedb.org/](https://www.themoviedb.org/))

> ⚠️ Only one secret is required: `TMDB_API_KEY` in a `.env` file at the repo root.

---

## Quick Start

```bash
# 1) Clone the repository
git clone <YOUR_REPO_URL>
cd <YOUR_REPO_NAME>

# 2) (Optional) Create & activate a virtual environment
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows (PowerShell)
# .venv\Scripts\Activate.ps1

# 3) Install dependencies
pip install -r requirements.txt

# 4) Create the .env file with your TMDb key
printf "TMDB_API_KEY=your_api_key_here\n" > .env

# 5) Run the scripts in order (replace names with your actual scripts)
python script1.py
python script2.py
python script3.py
```

---

## Environment Variables

Create a file named `.env` at the **root** of the project with the following content:

```env
TMDB_API_KEY=your_api_key_here
```

* Keep `.env` **out of version control**. Ensure `.gitignore` contains a `.env` entry:

  ```gitignore
  .env
  ```

* If your scripts are using `python-dotenv`, the variables will load automatically from `.env` when the scripts start. If not, export the variable in your shell before running:

  ```bash
  # macOS/Linux
  export TMDB_API_KEY=your_api_key_here

  # Windows (PowerShell)
  # $env:TMDB_API_KEY = "your_api_key_here"
  ```

---

## Script Execution Order

Run the three scripts **sequentially**. Replace the placeholders below with your actual filenames:

```bash
python script1.py   # e.g., data_fetch.py
python script2.py   # e.g., process_features.py
python script3.py   # e.g., reproduce_findings.py
```

If your scripts accept CLI arguments (e.g., output paths, date ranges), document them here. For example:

```bash
python data_fetch.py --min-votes 200 --language en-US
python process_features.py --input data/raw --output data/processed
python reproduce_findings.py --report reports/summary.md
```

---

## Troubleshooting

* **`KeyError: 'TMDB_API_KEY'` or authentication failures**
  Ensure your `.env` exists, is at the repo root, and contains a valid key.

* **Dependencies not found**
  Re-run `pip install -r requirements.txt` inside your active virtual environment.

* **Virtual environment issues**
  Verify activation: `which python` (macOS/Linux) or `Get-Command python` (PowerShell) should point to `.venv`.

* **Rate limits**
  TMDb enforces request limits. If you hit rate limits, try running again after a short wait.

---

## Project Structure (suggested)

```
<repo>/
├─ data/
│  ├─ raw/
│  └─ processed/
├─ reports/
├─ script1.py
├─ script2.py
├─ script3.py
├─ requirements.txt
├─ .env               # not committed
└─ README.md
```

---

## Reproducibility Notes

* Pin versions in `requirements.txt` for consistent environments.
* Consider adding a `requirements.lock` (via `pip-tools`) or a `pyproject.toml` for stricter builds.
* If results depend on remote data that can change over time, cache snapshots under `data/raw/` and note the retrieval date.

---

## License

This project is provided for research and educational purposes. See [LICENSE](./LICENSE) for details.
