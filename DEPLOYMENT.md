# Deployment Guide for AIBrief

This guide covers deploying the AIBrief application to Vercel (frontend) and Railway/Render (backend).

## Deployment Architecture

- **Frontend**: Vercel (React + Vite)
- **Backend**: Railway or Render (FastAPI)
- **Database**: SQLite (file-based, included in backend)

## Step 1: Prepare Repository for Git

### 1.1 Initialize Git (if not already done)

```bash
git init
git add .
git commit -m "Initial commit"
```

### 1.2 Create GitHub Repository

1. Go to https://github.com/new
2. Create a new repository (e.g., `aibrief`)
3. **Don't** initialize with README, .gitignore, or license
4. Copy the repository URL

### 1.3 Push to GitHub

```bash
git remote add origin https://github.com/YOUR_USERNAME/aibrief.git
git branch -M main
git push -u origin main
```

## Step 2: Deploy Backend (Railway)

### 2.1 Railway Setup

1. Go to https://railway.app
2. Sign up/login with GitHub
3. Click **"New Project"**
4. Select **"Deploy from GitHub repo"**
5. Select your repository
6. Railway will detect Python automatically

### 2.2 Configure Backend on Railway

1. **Settings → Service Name**: `aibrief-backend`
2. **Root Directory**: Set to `backend`
3. **Start Command**: `cd backend && python main.py`
4. **Python Version**: 3.11 (or latest)

### 2.3 Environment Variables (if needed)

Railway will auto-detect Python, but you can add:
- `PORT` (Railway sets this automatically)
- `PYTHON_VERSION=3.11`

### 2.4 Get Backend URL

1. Go to **Settings → Networking**
2. Generate domain or use provided one
3. Copy the URL (e.g., `https://aibrief-backend.railway.app`)
4. **Important**: Add `/api` prefix if needed, or use root URL

### 2.5 Update Railway Start Command (if needed)

If the backend needs adjustments:
- Go to **Settings → Start Command**
- Set to: `cd backend && uvicorn main:app --host 0.0.0.0 --port $PORT`

## Step 3: Deploy Frontend (Vercel)

### 3.1 Vercel Setup

1. Go to https://vercel.com
2. Sign up/login with GitHub
3. Click **"Add New..." → "Project"**
4. Import your GitHub repository

### 3.2 Configure Frontend on Vercel

1. **Framework Preset**: Vite
2. **Root Directory**: `frontend`
3. **Build Command**: `npm run build` (auto-detected)
4. **Output Directory**: `dist` (auto-detected)
5. **Install Command**: `npm install` (auto-detected)

### 3.3 Environment Variables

Add environment variable:
- **Key**: `VITE_API_URL`
- **Value**: Your Railway backend URL (e.g., `https://aibrief-backend.railway.app`)

**Important**: Do NOT include `/api` prefix in `VITE_API_URL` - the frontend API client handles paths.

### 3.4 Deploy

Click **"Deploy"** and wait for build to complete.

### 3.5 Get Frontend URL

Vercel will provide a URL like: `https://aibrief.vercel.app`

## Step 4: Update CORS on Backend

### 4.1 Update Backend CORS

Edit `backend/main.py`:

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=[
        "http://localhost:5173",  # Local dev
        "https://your-app.vercel.app",  # Your Vercel URL
        "https://*.vercel.app",  # All Vercel preview deployments
    ],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

Or for production (allow all Vercel deployments):
```python
allow_origins=["*"]  # Less secure, but works for all domains
```

### 4.2 Redeploy Backend

Push changes and Railway will auto-redeploy.

## Step 5: Test Deployment

1. Visit your Vercel URL
2. Check browser console for errors
3. Test API calls to backend
4. Verify articles are loading

## Alternative: Render for Backend

If you prefer Render over Railway:

### Render Setup

1. Go to https://render.com
2. Sign up/login
3. Click **"New +" → "Web Service"**
4. Connect GitHub repository
5. Configure:
   - **Name**: `aibrief-backend`
   - **Root Directory**: `backend`
   - **Environment**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `uvicorn main:app --host 0.0.0.0 --port $PORT`
6. Add environment variables if needed
7. Deploy

## Troubleshooting

### Frontend can't connect to backend

- Check `VITE_API_URL` environment variable
- Verify backend URL is accessible
- Check CORS settings in backend
- Check browser console for errors

### Backend not starting

- Check Railway/Render logs
- Verify Python version
- Check requirements.txt is correct
- Verify database file permissions

### Database issues

- SQLite file is created automatically
- Ensure backend has write permissions
- Database persists between deployments on Railway/Render

## Notes

- **Database**: SQLite file persists on Railway/Render
- **RSS Feeds**: Will work from deployed backend
- **HTTPS**: Both Vercel and Railway provide HTTPS automatically
- **Updates**: Push to GitHub to trigger automatic deployments
