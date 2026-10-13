# Employee Attendance & Analytics API

FastAPI service for punch-in, punch-out, manual corrections with an audit trail, and attendance analytics. All application code is in `app/main.py`.

## Run

Python 3.11+ and MongoDB 6 or newer.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
copy .env.example .env
```

Set `MONGO_URI` and `MONGO_DB` in `.env`. For a local server:

```powershell
docker run -d --name emp-mongo -p 27017:27017 mongo:7
```

```powershell
python sample_seed.py
uvicorn app.main:app --port 8000 --reload
```

Open http://127.0.0.1:8000/docs. `GET /health` returns `{"status":"ok"}` when MongoDB answers.

`sample_data/` has nine sample documents only. Analytics are defined for a larger set as well.

## What is included

- Employees, punch-in, punch-out, attendance list, and regularization
- Monthly employee summary, department summary, late leaderboard, department trend
- `GET /admin/explain/{endpoint}`

Do not commit `.env`.
