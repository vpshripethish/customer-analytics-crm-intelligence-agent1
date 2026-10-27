# GitHub + Streamlit Community Cloud Checklist

## Before publishing

- [ ] Extract the project archive.
- [ ] Verify `app.py`, `requirements.txt`, `src/`, `data/`, and `.streamlit/config.toml` are at the repository root.
- [ ] Do not upload `.env`, `.venv/`, `secrets.toml`, actual customer data, or API keys.
- [ ] Keep only synthetic example data in the public repository.

## GitHub

1. Create a new repository.
2. Publish the files in this folder to the repository root (not as a nested parent-folder upload).
3. Confirm the repo shows `app.py` and `requirements.txt` at the top level.
4. The included GitHub Actions workflow runs the syntax check and 80 unit tests on each push/pull request.

## Streamlit Community Cloud

1. Sign in at https://share.streamlit.io/ with GitHub.
2. Select **Create app** and the repository.
3. Branch: `main`.
4. Main file path: `app.py`.
5. Advanced settings: choose Python `3.12`.
6. No secrets are required for the core demo. Only configure an optional provider secret if you deliberately enable the external LLM narration and have reviewed its privacy implications.
7. Deploy and inspect build logs if it fails.

## Smoke test after deployment

1. Open Overview; confirm six platform labels and evidence coverage render.
2. Open CRM Intelligence and search `customer churn`.
3. Open Customer Analytics and upload `data/synthetic_customer_transactions.csv`.
4. Confirm the mapping and the three data-driven suggestions are visible.
5. Run analyses and check that interpretations and downloads appear.
6. Verify that missing CAC inputs cause a limitation/feasibility result rather than an invented CAC.

## Security caveat

The prototype does not have login, tenant roles, or production-grade data isolation controls. Treat the public deployment as a professor-demo only. Do not upload real customer personal data, secrets, or confidential business datasets.
