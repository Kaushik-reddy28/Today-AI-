# TodayAI - AI/ML News Intelligence Agent

A personalized news aggregator for AI and Machine Learning articles with a modern, Twitter like interface.

## Features

- 📰 **AI/ML News Aggregation** - Collects articles from multiple RSS sources
- 🎯 **Personalized Recommendations** - "For You" feed based on your reading preferences
- 🔖 **Bookmarking** - Save articles for later
- 🔍 **Search & Filter** - Find articles by category, source, or keywords
- 📱 **Modern UI** - Dark theme with social media-style cards
- ⚡ **Real-time Updates** - Get notified about new articles
- 🎨 **Visual Design** - Gradient accents, thumbnails, and engagement metrics

## Tech Stack

### Frontend
- React + Vite
- Modern CSS with dark theme
- Responsive design

### Backend
- FastAPI (Python)
- SQLAlchemy (SQLite)
- RSS feed parsing
- Content processing pipeline

## Project Structure

```
AI_news_Agent/
├── backend/          # FastAPI backend
│   ├── app/
│   │   ├── routers/  # API routes
│   │   ├── services/ # Business logic
│   │   ├── models.py # Database models
│   │   └── schemas.py # Pydantic schemas
│   ├── main.py       # FastAPI app entry point
│   └── requirements.txt
├── frontend/         # React frontend
│   ├── src/
│   │   ├── components/
│   │   ├── services/
│   │   └── utils/
│   ├── package.json
│   └── vite.config.js
└── config.json       # Application configuration
```

## Local Development

### Backend Setup

```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
python main.py
```

Backend runs on `http://localhost:8000`

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Frontend runs on `http://localhost:5173`

## Deployment

### Frontend (Vercel)

1. Push code to GitHub
2. Connect repository to Vercel
3. Set environment variable:
   - `VITE_API_URL` = Your backend API URL (e.g., `https://your-backend.railway.app`)
4. Deploy

### Backend (Railway or Render)

See deployment instructions in the backend directory.

## Environment Variables

### Frontend
- `VITE_API_URL` - Backend API URL (default: `http://localhost:8000`)

### Backend
- Database is SQLite (local file)
- RSS feeds are configured in `config.json`

## API Documentation

When the backend is running, visit:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

## License

MIT

