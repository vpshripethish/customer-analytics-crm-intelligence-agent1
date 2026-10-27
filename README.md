# Customer Analytics & CRM Intelligence Agent

A Streamlit web application for evidence-aware CRM capability research and comparison, transparent gap assessment, customer-data profiling, conditional analytics, automatic interpretation, and report exports.

> **Demo and privacy note:** The bundled data is synthetic. This prototype has no login, role-based access control, tenant-specific CRM connection, or production data-retention controls. Do not upload confidential or personal customer data to a publicly deployed instance. The hosted app is a demonstration until an appropriate security/privacy review and access controls are added.

## Deploy to GitHub + Streamlit Community Cloud

### 1. Create a GitHub repository

1. Extract this project ZIP on your computer.
2. Open [GitHub](https://github.com/) and sign in.
3. Click **+ → New repository**.
4. Name it `customer-analytics-crm-intelligence-agent` (or another name you prefer).
5. Choose **Public** for the simplest Streamlit Community Cloud setup. Use private only after connecting the required repository permissions.
6. Create the repository. If you upload through the browser, upload the **contents of this project folder**, not a parent folder that contains the project as a nested subfolder.
7. Make sure the GitHub repository root contains `app.py`, `requirements.txt`, `src/`, `data/`, and `.streamlit/config.toml`.

You can also publish the extracted local folder using GitHub Desktop: add the existing local repository/folder, commit the files, then **Publish repository**.

### 2. Deploy on Streamlit Community Cloud

1. Go to [https://share.streamlit.io/](https://share.streamlit.io/) and sign in with GitHub.
2. Click **Create app** → **Yup, I have an app** (wording may vary).
3. Choose your repository, branch `main`, and main file path `app.py`.
4. Open **Advanced settings** and choose **Python 3.12** for a conservative dependency-compatible environment.
5. Leave Secrets empty for the core demo; an API key is not needed for deterministic analytics.
6. Click **Deploy** and wait for the build logs. Streamlit will give you a URL ending in `streamlit.app`.

Official guide: https://docs.streamlit.io/deploy/streamlit-community-cloud/deploy-your-app/deploy

### 3. Updating the website

Commit and push updated files to GitHub. Streamlit Community Cloud watches the linked repository and normally redeploys code changes automatically. Dependency changes in `requirements.txt` trigger environment resolution.

## Run locally on Windows CMD

Use Python 3.12 if possible. Open CMD in this project folder, then run:

```bat
py -3.12 -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements-dev.txt
python -m pytest -q
python -m streamlit run app.py
```

The app now adds `src/` to `sys.path` itself; `set PYTHONPATH=src` is no longer required. Open the local URL printed by Streamlit, usually `http://localhost:8501`.

## Core features

- Six-platform CRM capability evidence matrix with explicit `not_verified` states.
- Capability search/comparison and gap assessment with configurable prioritization.
- CSV and Excel upload, workbook sheet selection, conservative field mapping, profiling and data-quality audits.
- Data-driven suggestions for the inactivity proxy window, CSAT threshold and exploratory cluster count; suggestions remain editable and include explanatory notes.
- Conditional customer metrics and feasibility refusals when required data or definitions are absent.
- Automatic deterministic interpretations, statistical testing, optional exploratory churn-model evaluation and report exports.
- Markdown, HTML, CSV, Excel and JSON outputs.

## AI narration (optional)

Core analytics and deterministic interpretations require no API key. Optional OpenAI narration is separately configured using `requirements-llm.txt` and the `OPENAI_API_KEY` environment variable. For hosted use, put secrets only in Streamlit Community Cloud's **Advanced settings → Secrets** panel, and only after reviewing the privacy impact. Never commit API keys to GitHub.

## Important limitations

- CRM research is a curated initial inventory, not an exhaustive product catalogue; many records remain `not_verified`.
- No live OAuth/API integration with a CRM tenant and no write actions are included.
- Metrics are conditional on validated field mappings and business definitions. Historical revenue/customer is not predictive CLV; inactivity is a proxy unless a churn outcome is explicitly defined.
- Exploratory churn models need temporal validation, calibration and fairness review before any operational use.
- This prototype is not production-hardened for sensitive data or multiple users.
