# Vulnity API

FastAPI backend for the Vulnity web security assessment application. It provides authentication, scan management, vulnerability records, SQL injection and XSS scanner modules, and a WebSocket route.

## Requirements

- Python 3.8+
- pip

## Run locally

From this directory:

    python -m venv .venv

Activate the environment with the command for your shell: .venv\Scripts\Activate.ps1 in Windows PowerShell or source .venv/bin/activate on macOS/Linux. Then install dependencies and copy the development settings:

    pip install -r requirements.txt
    cp .env.example .env
    uvicorn app.main:app --reload

The API defaults to SQLite. With DEBUG enabled, interactive API documentation is available at http://127.0.0.1:8000/docs.

## Tests

    pytest

## Safety

Only scan systems that you own or are explicitly authorized to assess. The scanner sends crafted requests and its results require manual validation. Replace example secrets and review trusted hosts, CORS, cookie settings, and debug mode before deployment.

See the [root README](../README.md) for the full project overview.

