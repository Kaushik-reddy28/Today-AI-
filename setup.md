# Quick Setup Guide

## Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Create virtual environment:
```bash
python -m venv venv
```

3. Activate virtual environment:
   - Windows: `venv\Scripts\activate`
   - Linux/Mac: `source venv/bin/activate`

4. Install dependencies:
```bash
pip install -r ../requirements.txt
```

5. Run backend:
```bash
python main.py
```

Backend will run on http://localhost:8000

## Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Run frontend:
```bash
npm run dev
```

Frontend will run on http://localhost:3000

## First Run

1. Start the backend server
2. Start the frontend server
3. Open http://localhost:3000 in your browser
4. Click "Refresh" to collect news from configured sources

## Collecting News

News is collected from RSS feeds. Currently configured sources:
- TechCrunch
- VentureBeat  
- arXiv (AI research papers)
- Towards Data Science

Click the "Refresh" button in the UI or call:
```bash
curl -X POST http://localhost:8000/api/collect
```
