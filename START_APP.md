# How to Use Your AI News App

## ✅ Your App is Running!

The frontend is showing at **http://localhost:3000** - perfect!

## Next Step: Collect News

**Click the blue "Refresh" button** in the top-right corner of the page.

This will:
1. ✅ Fetch AI/ML news from RSS feeds
2. ✅ Filter and categorize articles
3. ✅ Display them in organized sections

## What You'll See

After clicking "Refresh", articles will appear in these sections:

- **🔥 Top AI Updates** - Most important AI news
- **📄 Research & Breakthroughs** - Latest research papers and discoveries
- **🚀 Startups & Funding** - AI startup news and investments
- **🛠 New AI Tools** - New AI products and tools

## Using the App

### View Articles
- **Click any article card** to expand it
- See key points and read the original article
- Articles show source and timestamp

### Navigation
- **Home** - Main news feed
- **Bookmarks** - Saved articles (click star icon on articles)
- **Settings** - App settings

### Collect News
- Click **"Refresh"** anytime to get latest news
- News is filtered to last 24 hours
- Articles are ranked by relevance

## Troubleshooting

### Page is blank after Refresh?
- Check if backend is running (should be on port 8000)
- Wait a few seconds for news collection to complete
- Try clicking Refresh again

### Backend not running?
1. Open a PowerShell window
2. Run:
   ```powershell
   cd C:\Users\Admin\Downloads\AI_news_Agent\backend
   .\venv\Scripts\Activate.ps1
   python main.py
   ```
3. Keep this window open (backend must stay running)

### No articles showing?
- First time: It's normal if no articles match (last 24 hours filter)
- Try clicking Refresh multiple times
- Check browser console for errors (F12)

## Enjoy Your AI News App! 🚀
