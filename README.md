# 🗄️ Text-to-SQL AI Assistant

> Convert plain English questions into accurate SQL queries — no SQL knowledge needed. Schema-aware prompt injection ensures the LLM generates correct queries against your actual database structure.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Streamlit-FF4B4B?style=for-the-badge&logo=streamlit)](https://palakbiradar-text-to-sql.streamlit.app)
[![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python)](https://python.org)

---

## The core problem this solves

Generic Text-to-SQL systems hallucinate column names because the LLM doesn't know your schema. This system injects the live schema into every prompt — the LLM sees your actual table names, column names, and data types before generating any query.

```
User question (plain English)
        │
        ▼
SQLite schema inspector
(extracts table names, columns, types)
        │
        ▼
Schema-aware prompt construction:
"Given this schema: {schema}
 Answer this question: {question}
 Return only valid SQL."
        │
        ▼
Gemini API (LLM)
        │
        ▼
Generated SQL query
        │
        ▼
Execute against live SQLite DB
        │
        ▼
Results table + natural language summary
```

**Why schema injection matters:**
Without it, the LLM might generate `SELECT customer_name FROM users` when your table is actually called `customers` with a column called `full_name`. Schema injection eliminates this class of error entirely.

---

## Run locally

```bash
git clone https://github.com/pratikshabiradar19/text-to-sql-ai.git
cd text-to-sql-ai

pip install -r requirements.txt

# Add GOOGLE_API_KEY to .env
streamlit run app.py
```

---

## Tech stack

`LangChain` `Gemini API` `SQLite` `Python` `Streamlit`

---

*Built by [Pratiksha Biradar](https://github.com/pratikshabiradar19) — Gen AI Engineer*
