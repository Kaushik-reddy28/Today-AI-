# Filtering Improvements

## Changes Made

### 1. Relaxed Keyword Filtering

**Before:** Only matched exact phrases like "Artificial Intelligence", "Machine Learning"

**After:** 
- Added shorter keywords: `ai`, `ml`, `llm`, `gpt`, `openai`, `deepmind`, `neural`, `algorithm`, `model`, `learning`, `intelligence`, `transformer`, `chatbot`, `automation`
- More flexible matching - matches if ANY keyword appears in title or summary
- Still excludes: crypto, memes, politics

**Result:** Articles with "AI", "GPT", "LLM" in titles will now be included

### 2. Extended Freshness Filter

**Before:** Only stored articles from last 24 hours

**After:** Stores articles from last 7 days (matches collector range)

**Result:** More articles get stored in database, frontend filters handle time ranges

### 3. Improved Error Handling

- Added better error messages in backend console
- Shows `raw_articles_fetched` vs `articles_collected` in API response
- Added stack traces for debugging RSS feed issues

### 4. Increased Article Limits

- Increased from 15 to 20 articles per RSS source
- Better coverage of available articles

### 5. Better Summary Extraction

- Uses `description` field if `summary` is not available
- More articles will have summaries

## How to Use

1. **Restart your backend server:**
   ```powershell
   # Stop the backend (Ctrl+C)
   cd backend
   python main.py
   ```

2. **Click "Refresh" in your browser**

3. **Check the backend console** - You should see:
   ```
   Collected X raw articles from RSS feeds
   Stored Y articles after filtering
   ```

4. **Use filters in the UI** to find articles by:
   - Category
   - Source
   - Time range (24h, 3d, 7d, 30d, All time)

## Expected Results

- **More articles collected** - Shorter keywords catch more AI-related content
- **Better matching** - "AI model" now matches even without "Artificial Intelligence"
- **More articles stored** - 7-day window vs 24-hour window
- **Better debugging** - Console shows what's happening

## Notes

- Articles are still filtered for AI/ML content
- Excluded keywords (crypto, memes, politics) still apply
- Frontend time range filters still work as expected
- If you still see 0 articles, check backend console for RSS feed errors
