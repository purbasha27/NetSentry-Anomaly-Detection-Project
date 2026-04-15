# Vercel Deployment Fix Guide

## Issue
Getting **404 NOT_FOUND** error when accessing deployed dashboard on Vercel.

## Root Cause
Vercel wasn't configured to serve the `index.html` from the correct dashboard folder path.

## Solution - Re-deploy with Correct Configuration

### Option 1: Quick Fix (Recommended)
Your student should **redeploy** using these exact settings:

1. **Go to Vercel Dashboard** → Project Settings → General
2. **Set Root Directory to**: `network_anomaly_detection/dashboard`
3. **Leave Build Command blank** (it's a static site)
4. **Trigger Redeploy**: Click "Redeploy"

### Option 2: Using vercel.json (Already Added)
The `vercel.json` file has been added to the repo. The student should:

1. **Git pull** the latest changes
   ```bash
   git pull origin main
   ```

2. **Redeploy on Vercel**
   - Vercel will auto-detect `vercel.json`
   - It will serve the dashboard correctly
   - No manual configuration needed

### Option 3: Full Redeployment
If redeployment doesn't work:

1. **Delete current Vercel project**
2. **Go to Vercel Dashboard** → Remove the project
3. **Redeploy from GitHub**:
   - Click "Add New" → "Project"
   - Select the forked repository
   - Click "Import"
   - **Framework Preset**: Other
   - **Root Directory**: `network_anomaly_detection/dashboard`
   - Click "Deploy"

## After Deployment Works

### Important: Backend API Won't Work on Vercel
⚠️ **Note**: This dashboard uses **simulated attacks by default**, which work fine on Vercel.

For **real Kali attacks detection**, users need to:
1. Run the backend locally: `python run_with_real_capture.py`
2. Or deploy backend to Heroku/Railway and update `API_BASE` in `app.js`

### Test the Deployment

Once deployed, the dashboard should show:
- ✅ All HTML content loads
- ✅ Dashboard tabs visible (Dashboard, Live Detection, Model Matrices, System Upgrades)
- ✅ Simulate Attacks button works
- ✅ Dark/Light mode toggle works
- ✅ No 404 errors

## Student's Forked Repository
Since the student forked the project, they should:
1. Update their fork with `git pull`
2. Verify `vercel.json` is in their fork
3. Redeploy on Vercel with the configuration above

## Deployment Links Status
- netsentry-iota.vercel.app
- netsentry-git-main-juleemahato25s-projects.vercel.app
- netsentry-fr3zswabk-juleemahato25s-projects.vercel.app

After redeployment, these should all **show the dashboard** (no 404 error).

## Questions?
If still getting 404:
- Check Vercel logs: Project Settings → Deployments → Logs
- Verify `vercel.json` is in repository root
- Ensure Root Directory is set to `network_anomaly_detection/dashboard`
