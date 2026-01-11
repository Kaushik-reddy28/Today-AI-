# How to Use AIBrief - Quick Guide

## What You're Looking At

The **Swagger UI** page (http://localhost:8000/docs) is an interactive API documentation tool. It lets you:
- See all available API endpoints
- Test endpoints directly from your browser
- View request/response formats
- Try out the API without writing code

## Quick Start Guide

### Option 1: Use Swagger UI (Easiest)

1. **On the Swagger UI page**, find the endpoint you want:
   - **POST /api/collect** - Collect news from RSS feeds
   - **GET /api/articles/today/feed** - Get today's news
   - **GET /api/articles/** - Get all articles with filters

2. **Click on an endpoint** to expand it

3. **Click "Try it out"** button (grey button on the right)

4. **Fill in parameters** (if any)

5. **Click "Execute"** button

6. **See the results** below (response code, response body)

### Option 2: Use PowerShell Commands

```powershell
# 1. Collect news from RSS feeds
Invoke-RestMethod -Uri "http://localhost:8000/api/collect" -Method Post

# 2. Get today's news feed (grouped by category)
Invoke-RestMethod -Uri "http://localhost:8000/api/articles/today/feed"

# 3. Get all articles
Invoke-RestMethod -Uri "http://localhost:8000/api/articles/"

# 4. Health check
Invoke-RestMethod -Uri "http://localhost:8000/api/health"
```

## Step-by-Step: First Time Setup

### Step 1: Collect News Data
The database starts empty. You need to collect news first:

**In Swagger UI:**
1. Find **POST /api/collect**
2. Click it to expand
3. Click **"Try it out"**
4. Click **"Execute"**
5. You'll see: `{"status": "success", "articles_collected": X}`

**Or use PowerShell:**
```powershell
Invoke-RestMethod -Uri "http://localhost:8000/api/collect" -Method Post
```

### Step 2: View the News
After collecting, view the articles:

**In Swagger UI:**
1. Find **GET /api/articles/today/feed**
2. Click **"Try it out"** → **"Execute"**
3. See articles grouped by category

**Or use PowerShell:**
```powershell
$feed = Invoke-RestMethod -Uri "http://localhost:8000/api/articles/today/feed"
$feed | ConvertTo-Json -Depth 5
```

### Step 3: Explore Other Endpoints

- **GET /api/articles/** - Get articles with filters (category, source, limit)
- **GET /api/articles/{article_id}** - Get a specific article
- **GET /api/bookmarks/** - Get bookmarked articles
- **POST /api/bookmarks/** - Bookmark an article

## View the Full UI (Frontend)

The React frontend provides a beautiful web interface. To run it:

1. **Install Node.js** (if not installed):
   - Download from: https://nodejs.org/
   - Install the LTS version

2. **Open a new terminal/PowerShell window**

3. **Run these commands:**
   ```powershell
   cd C:\Users\Admin\Downloads\AI_news_Agent\frontend
   npm install
   npm run dev
   ```

4. **Open browser** to: http://localhost:3000

5. **Click "Refresh"** button to collect news

6. **Browse articles** in a beautiful newsletter-style UI!

## Common Tasks

### Collect News Daily
Run the collect endpoint once per day (or as needed):
```powershell
Invoke-RestMethod -Uri "http://localhost:8000/api/collect" -Method Post
```

### Get Articles by Category
```powershell
# Top news only
Invoke-RestMethod -Uri "http://localhost:8000/api/articles/?category=top_news"

# Research articles only
Invoke-RestMethod -Uri "http://localhost:8000/api/articles/?category=research"

# Startups only
Invoke-RestMethod -Uri "http://localhost:8000/api/articles/?category=startups"

# Tools only
Invoke-RestMethod -Uri "http://localhost:8000/api/articles/?category=tools"
```

### Bookmark an Article
```powershell
# First, get article ID from the feed
$feed = Invoke-RestMethod -Uri "http://localhost:8000/api/articles/today/feed"
$articleId = $feed.top_news.articles[0].id

# Then bookmark it
$body = @{article_id=$articleId} | ConvertTo-Json
Invoke-RestMethod -Uri "http://localhost:8000/api/bookmarks/" -Method Post -Body $body -ContentType "application/json"
```

## Troubleshooting

### No articles showing?
- Run **POST /api/collect** first to fetch news
- Check if RSS feeds are accessible
- Articles are filtered to last 24 hours only

### Frontend not working?
- Make sure Node.js is installed
- Run `npm install` in the frontend directory
- Check if port 3000 is available

### API not responding?
- Check if backend is running (look for Python process)
- Try the health check: http://localhost:8000/api/health
- Restart the backend server

## Next Steps

1. ✅ **Test the API** using Swagger UI
2. ✅ **Collect some news** using POST /api/collect
3. ✅ **View articles** using GET /api/articles/today/feed
4. ⏭️ **Install Node.js** to run the frontend UI
5. ⏭️ **Customize config.json** to add more sources or change filters

Enjoy exploring AIBrief! 🚀
