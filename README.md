# Vulnity

Vulnity is an experimental web security assessment application with a FastAPI backend and a React/TypeScript frontend. Its current scanner modules check for SQL injection and reflected cross-site scripting (XSS) indicators.

> Use the scanner only on systems you own or have explicit permission to assess. Scanner results are signals for manual validation, not proof that a system is secure or vulnerable.

## Features

- Account registration, login, and token-based authentication
- Scan creation, status tracking, and scan history
- SQL injection and XSS checks for URL parameters
- Vulnerability records and scan summaries
- FastAPI health endpoint and interactive API documentation in development mode

The repository also contains draft or incomplete areas. CSRF scanning and production deployment are not presented as available features.

## Architecture

| Component | Location | Stack |
| --- | --- | --- |
| API and scanner | [`backend/`](backend/) | Python, FastAPI, SQLAlchemy |
| Web interface | [`frontend/`](frontend/) | React, TypeScript, Vite |
| Backend tests | [`backend/tests/`](backend/tests/) | pytest |

## Requirements

- Python 3.8 or newer
- Node.js and npm

The backend defaults to a local SQLite database. Review the environment settings before exposing the service to a network.

## Run locally

### Backend

```bash
git clone https://github.com/Rimaestro/vulnity-web-security-scanner.git
cd vulnity-web-security-scanner/backend
python -m venv .venv
```

Activate the virtual environment, then install and configure the backend:

```bash
# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS/Linux
# source .venv/bin/activate

pip install -r requirements.txt
cp .env.example .env
uvicorn app.main:app --reload
```

On Windows, copy `.env.example` to `.env` with `Copy-Item .env.example .env` if `cp` is unavailable.

The API listens on `http://127.0.0.1:8000`. When debug mode is enabled, the OpenAPI UI is at [`/docs`](http://127.0.0.1:8000/docs) and the health endpoint is [`/health`](http://127.0.0.1:8000/health).

### Frontend

In a second terminal:

```bash
cd ../frontend
npm install
npm run dev
```

Open the local URL printed by Vite. Check the frontend API client and backend CORS settings if the browser cannot reach the API.

## Tests and checks

```bash
cd backend
pytest
```

Frontend scripts are available from `frontend/`:

```bash
npm run lint
npm run build
```

These commands are provided for contributors; this README does not imply that they have been run for every revision.

## Security and limitations

- Scans send crafted HTTP requests to the configured target. Use an isolated lab such as DVWA for experiments.
- Test authorization and target scope before every scan.
- Change the example `SECRET_KEY` and review `DEBUG`, trusted hosts, CORS, and cookie settings before deployment.
- Findings can be false positives or false negatives and need manual verification.

## License

See [`LICENSE`](LICENSE).

