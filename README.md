# Reproducing Findings (TMDb)

This repository contains scripts for reproducing findings using data from **The Movie Database (TMDb)**.

---

## Requirements

* Python
* `pip` 
* A **TMDb API key** (free; create an account at [https://www.themoviedb.org/](https://www.themoviedb.org/))

> ⚠️ Only one secret is required: `TMDB_API_KEY` in a `.env` file at the repo root.

---

## Quick Start

```bash
# 1) Clone the repository
git clone https://github.com/LSE-ME204/me204-2025-project-prsnt95.git
cd https://github.com/LSE-ME204/me204-2025-project-prsnt95.git

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

---

## Script Execution Order

Run the three scripts **sequentially**. Replace the placeholders below with your actual filenames:

```bash
python notebooks/NB01-data-collection.ipynb   
python notebooks/NB02-data-processing.ipynb 
python notebooks/NB01-data-analysis.ipynb 
```


## Project Structure

```
<repo>/
├─ data/
│  ├─ raw/
│  └─ database.db
├─ docs/
│  ├─ plots/
│  └─ index.html
├─ notebooks/
│  ├─ NB01-data-collection.ipynb   
│  └─ NB02-data-processing.ipynb 
|  └─ NB01-data-analysis.ipynb 
├─ .env               # not committed
└─ README.md
└─ .gitignore
```

---