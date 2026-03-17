<div align="center">

<!-- HEADER BANNER -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=200&section=header&text=Data%20Engineering%20101&fontSize=52&fontColor=ffffff&fontAlignY=38&desc=A%20Conversational%20%E2%80%A2%20Hands-On%20Learning%20Notebook&descAlignY=58&descSize=18&descColor=a8d8ea" width="100%"/>

<br/>

<!-- BADGES -->
![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.24+-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner%20→%20Intermediate-22c55e?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-f59e0b?style=for-the-badge)

<br/>

> *"Data Engineering is the foundation upon which all data science and analytics are built."*
>
> This notebook teaches you Data Engineering **the way a senior engineer would explain it** —
> through real stories, honest analogies, and code you can actually run.

<br/>

[**📓 Open Notebook**](#-getting-started) · [**📚 What's Inside**](#-whats-inside) · [**🗺️ Roadmap**](#-6-month-learning-roadmap) · [**🤝 Contributing**](#-contributing)

</div>

---

## 🤔 Why Does This Notebook Exist?

Most Data Engineering tutorials throw tools and jargon at you.
They start with *"install Apache Kafka"* before you even understand why data needs to move in the first place.

This notebook is different. It's written like a **conversation with a senior data engineer over coffee** — asking *"but why?"* at every step, using real-world analogies, and writing code that mirrors what you'd actually do on the job.

```
Traditional Tutorial          This Notebook
─────────────────────         ──────────────────────────
"Install Spark."              "Here's the real problem Spark solves.
"Configure Kafka."             Here's a story showing you why it matters.
"Write a DAG."                 Now let's write code that proves the concept.
                               Now you're ready to learn the tool."
```

---

## 📦 What's Inside

The notebook is split into **11 sections**, each one building on the last.

<table>
<tr>
<td width="50%">

### 📖 Concepts (Markdown)

| # | Section | Key Idea |
|---|---------|----------|
| 1 | **What is Data Engineering?** | The "plumbing" of the data world |
| 2 | **The DE Role** | What they actually do all day |
| 3 | **Core Vocabulary** | Batch, stream, schema, latency |
| 4 | **Data Pipelines** | Assembly lines for data |
| 5 | **ETL vs ELT** | Classic vs modern approach |
| 6 | **Storage Types** | OLTP, Warehouse, Lake, Lakehouse |
| 7 | **Data Formats** | Why Parquet beats CSV at scale |
| 8 | **Tool Stack** | The 5 layers of modern DE |
| 9 | **Data Quality** | Why "garbage in = garbage out" |
| 10 | **Mini Pipeline** | Build a real ETL from scratch |
| 11 | **Summary & Roadmap** | Your 6-month learning plan |

</td>
<td width="50%">

### 💻 Code (Runnable Cells)

| Cell | What It Does |
|------|-------------|
| `code-concepts` | Structured vs semi-structured data |
| `code-flatten` | Flatten nested JSON → clean table |
| `code-formats` | Generate 100k rows, compare CSV vs Parquet size |
| `code-formats-speed` | Benchmark query speed: CSV vs Parquet |
| `code-quality-full` | Load realistically messy data |
| `code-quality-checks` | 6-dimension quality checker with flagging |
| `code-quality-fix` | Smart quarantine system for bad rows |
| `code-pipeline-full` | Full ETL: extract → validate → transform → load → report |
| `code-inspect` | Inspect the final warehouse output |

</td>
</tr>
</table>

---

## 🚀 Getting Started

### Prerequisites

Make sure you have Python 3.10+ and the following packages:

```bash
pip install pandas numpy jupyter pyarrow
```

> **`pyarrow`** is required for reading/writing Parquet files in the format benchmark cells.

### Clone & Run

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/data-engineering-101.git
cd data-engineering-101

# 2. (Optional but recommended) Create a virtual environment
python -m venv venv
source venv/bin/activate        # Mac / Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch Jupyter
jupyter notebook Introduction_to_Data_Engineering.ipynb
```

### Open in VS Code / Cursor IDE

If you prefer VS Code or Cursor:

1. Install the **Jupyter extension** (`ms-toolsai.jupyter`)
2. Open the `.ipynb` file directly
3. Select your Python interpreter (top right of the notebook)
4. Run cells with `Shift + Enter`

```
Cursor IDE tip:
  Ctrl+Shift+P → "Select Notebook Kernel" → choose your Python 3.10+ env
```

---

## 📸 Notebook Preview

<details>
<summary><b>📋 Section 1 — What is Data Engineering?</b> (click to expand)</summary>

```
BEFORE Data Engineering          AFTER Data Engineering
──────────────────────           ──────────────────────
Orders DB     ┐                  Orders DB  ─┐
Support tool  ├──► Manual work   Support    ─┼──► Pipeline ──► Warehouse ──► Dashboard
Spreadsheet   │    (days)        Spreadsheet─┤    (auto)      (always        (seconds)
Ad platform   ┘                  Ad platform─┘                 fresh)
```

</details>

<details>
<summary><b>⚡ Section 7 — File Format Benchmark output</b> (click to expand)</summary>

```
Dataset: 100,000 rows x 8 columns

FILE SIZE COMPARISON:
  CSV     file: 8.21 MB
  Parquet file: 1.43 MB
  Parquet is 5.7x smaller than CSV!

QUERY: SUM of 'amount' column across 100,000 rows
  CSV     time: 0.0421s  |  result: $4,003,847,293.12
  Parquet time: 0.0089s  |  result: $4,003,847,293.12

  Parquet is ~4.7x faster for this column-scan query!
```

</details>

<details>
<summary><b>✅ Section 9 — Data Quality Report output</b> (click to expand)</summary>

```
DATA QUALITY REPORT
═════════════════════════════════════════════════════════════════
  Row  3 | [COMPLETENESS  ] Required field 'amount' is missing
  Row  5 | [UNIQUENESS    ] Duplicate order_id: 1004
  Row  6 | [UNIQUENESS    ] Duplicate order_id: 1004
  Row  6 | [ACCURACY      ] Negative amount: -500.0
  Row  7 | [ACCURACY      ] Suspicious quantity: 0
  Row  2 | [VALIDITY      ] Invalid email format: bob-not-an-email
  Row  8 | [VALIDITY      ] Invalid date format: 13/25/2024
  Row  9 | [COMPLETENESS  ] Required field 'user_id' is missing
═════════════════════════════════════════════════════════════════
  Total issues found: 8 across 9 rows
```

</details>

<details>
<summary><b>🏭 Section 10 — Pipeline Run output</b> (click to expand)</summary>

```
══════════════════════════════════════════════════
PIPELINE START: 2024-06-01 00:00:00
══════════════════════════════════════════════════
  [EXTRACT]   Pulling orders from source system...
              Got 7 raw rows
  [EXTRACT]   Pulling product catalog...
              Got 4 products

  [VALIDATE]  Running data quality checks...
              Passed: 5 rows
              Quarantined: 2 rows (see quarantine log)

  [TRANSFORM] Enriching and modeling data...
              Produced 5 enriched rows

  [LOAD]      Writing 5 rows to 'warehouse.orders_fact'...
              Done!

  [REPORT]    Pipeline Summary
              ─────────────────────────────────────────────
              Orders processed:  5
              Total revenue:     $    134,900.00
              Avg order value:   $     26,980.00
              High-value orders: 3

              Revenue by Category:
                Electronics          $   128,500.00
                Peripherals          $     3,200.00
                Accessories          $     2,400.00
══════════════════════════════════════════════════
PIPELINE DONE in 0.08s
══════════════════════════════════════════════════
```

</details>

---

## 🗺️ 6-Month Learning Roadmap

This notebook is **Month 1 of 6**. Here's the full plan:

```
MONTH 1 — SQL + This Notebook ✅
├── SQL: SELECT, JOIN, GROUP BY, Window Functions
├── Python: basics, functions, loops
└── Read: "Fundamentals of Data Engineering" (Joe Reis) — Ch. 1-3

MONTH 2 — Python for Data
├── Pandas: read, clean, merge, transform DataFrames
├── Parquet, JSON, CSV file handling
├── REST API calls with requests
└── Project: pull data from a public API, clean it, save to Parquet

MONTH 3 — Build Real ETL Pipelines
├── Python ETL without frameworks
├── PostgreSQL or SQLite locally
├── Git version control for data projects
└── Project: ingest → clean → store pipeline for a real dataset

MONTH 4 — dbt (Data Build Tool)
├── dbt models (SQL that auto-builds tables)
├── dbt tests for data quality
├── dbt documentation
└── Project: build a dbt project on top of Month 3 data

MONTH 5 — Orchestration with Apache Airflow
├── Install Airflow locally via Docker
├── Build your first DAG
├── Schedule + monitor your Month 3 pipeline
└── Set up failure alerts

MONTH 6 — Cloud
├── Pick one: GCP (BigQuery + GCS) OR AWS (S3 + Redshift/Athena)
├── Deploy your pipeline to the cloud
├── Connect a BI tool (Metabase or Looker Studio — both free)
└── Optional: pursue a cloud certification
```

---

## 📚 Recommended Resources

| Resource | Type | Why It's Great |
|----------|------|----------------|
| [**Fundamentals of Data Engineering**](https://www.oreilly.com/library/view/fundamentals-of-data/9781098108298/) — Joe Reis & Matt Housley | 📖 Book | The best DE book for beginners. Covers everything conceptually before tools. |
| [**DataTalks.Club DE Zoomcamp**](https://github.com/DataTalksClub/data-engineering-zoomcamp) | 🆓 Course | Free, hands-on, covers the entire modern stack. Highly recommended. |
| [**dbt Learn**](https://courses.getdbt.com/) | 🆓 Course | Official free dbt courses. Start with "dbt Fundamentals". |
| [**Mode SQL Tutorial**](https://mode.com/sql-tutorial/) | 🆓 Online | Best free SQL for analytics tutorial. Very practical. |
| [**Astronomer Airflow Guides**](https://docs.astronomer.io/learn) | 📄 Docs | Best Airflow learning resource available. |
| [**StrataScratch**](https://www.stratascratch.com/) | 🆓/💰 Practice | Real SQL interview questions from top companies. |

---

## 🛠️ Tech Stack Used in This Notebook

| Library | Version | Purpose |
|---------|---------|---------|
| `pandas` | 2.0+ | Data manipulation and transformation |
| `numpy` | 1.24+ | Generating sample datasets |
| `pyarrow` | 12.0+ | Parquet read/write backend |
| `re` | stdlib | Regex for email validation |
| `io` | stdlib | Reading CSV strings as file objects |
| `datetime` | stdlib | Timestamps and pipeline run tracking |
| `time` | stdlib | Benchmarking query performance |
| `os` | stdlib | File size comparisons |

---

## 📁 Repository Structure

```
data-engineering-101/
│
├── 📓 Introduction_to_Data_Engineering.ipynb   ← Main notebook
├── 📄 README.md                                ← You are here
├── 📋 requirements.txt                         ← Python dependencies
└── 📜 LICENSE                                  ← MIT License
```

---

## 🤝 Contributing

Found a typo? Have a better analogy? Want to add a section on Spark or Kafka?

Contributions are very welcome!

```bash
# Fork the repo, then:
git checkout -b feature/add-spark-section
# Make your changes
git commit -m "feat: add Apache Spark mini-tutorial"
git push origin feature/add-spark-section
# Open a Pull Request
```

Please keep the **conversational, story-first tone** of the notebook.
Every new concept should answer: *"Why does this exist? What problem does it solve?"*

---

## 📜 License

This project is licensed under the **MIT License** — feel free to use, share, and modify it.

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=120&section=footer" width="100%"/>

**Made with ☕ and a genuine love for clean data pipelines.**

*If this helped you, consider giving it a ⭐ — it helps others find it too.*

[![GitHub stars](https://img.shields.io/github/stars/YOUR_USERNAME/data-engineering-101?style=social)](https://github.com/YOUR_USERNAME/data-engineering-101)

</div>
