# Installing Node.js for AIBrief News App

## Current Status

✅ **Node.js installer found**: `node-v24.12.0-x64 (1).msi`

## Installation Steps

### Step 1: Install Node.js

1. **Double-click** the file: `node-v24.12.0-x64 (1).msi`
   - This will open the Node.js installer

2. **Follow the installation wizard**:
   - Click "Next" on all screens
   - Click "Install" when prompted
   - The installer will install Node.js to: `C:\Program Files\nodejs\`
   - **Make sure to check the box** "Automatically install the necessary tools" if prompted

3. **Wait for installation to complete**

4. **Click "Finish"** when done

### Step 2: Verify Installation

1. **Close your current PowerShell/terminal window**

2. **Open a NEW PowerShell window**

3. **Test Node.js**:
   ```powershell
   node --version
   ```
   Should show: `v24.12.0` (or similar)

4. **Test npm**:
   ```powershell
   npm --version
   ```
   Should show: `10.x.x` (or similar)

### Step 3: Run the News App

Once Node.js is installed, run these commands:

```powershell
cd C:\Users\Admin\Downloads\AI_news_Agent\frontend
npm install
npm run dev
```

Then open your browser to: **http://localhost:3000**

## Quick Start Script

After Node.js is installed, you can use:

```powershell
cd C:\Users\Admin\Downloads\AI_news_Agent\frontend
npm install
npm run dev
```

## Troubleshooting

### "node is not recognized"
- Make sure you **closed and reopened** PowerShell after installation
- Node.js should be in your PATH automatically
- Try: `refreshenv` in PowerShell (if you have Chocolatey)

### Installation Errors
- Make sure you have administrator rights
- Try running the installer as Administrator (right-click → Run as administrator)

### Still Having Issues?
- Check if Node.js installed: `Test-Path "C:\Program Files\nodejs\node.exe"`
- If it exists, you can use the full path: `"C:\Program Files\nodejs\node.exe" --version`
