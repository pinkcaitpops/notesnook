# Vercel Configuration Settings

## CORRECT SETTINGS FOR VERCEL DASHBOARD

When importing your repository to Vercel, use these exact settings:

### Project Settings

**Framework Preset:** Vite (or Other)

**Root Directory:**
```
./
```
*(Leave empty or use root directory)*

**Build Command:**
```
npm ci && npm run bootstrap -- --scope=web && npm run build:web
```

**Output Directory:**
```
apps/web/build
```

**Install Command:**
```
# Leave empty - will use npm ci from build command
```

---

## WHY THESE SETTINGS?

1. **Root Directory = `./`**
   - Vercel starts at repository root
   - Can find package-lock.json ✅
   - Can access all workspace packages ✅

2. **Build Command includes all steps:**
   - `npm ci` - Clean install from package-lock.json
   - `npm run bootstrap -- --scope=web` - Install web workspace dependencies
   - `npm run build:web` - Build the web application

3. **Output Directory = `apps/web/build`**
   - Points to where Vite outputs the build
   - Relative to repository root

---

## WRONG SETTINGS (What caused your error)

❌ **Root Directory: `apps/web`**
❌ **Install Command: `cd ../.. && npm ci && npm run bootstrap -- --scope=web`**

This causes Vercel to start in `apps/web`, then try to `cd ../..` which can fail in some build environments.

---

## AFTER CHANGING SETTINGS

1. Click "Save" in Vercel dashboard
2. Go to "Deployments" tab
3. Click "Redeploy" on latest deployment
4. Watch it succeed! 🚀

---

## ALTERNATIVE: Deploy Pre-Built App

If you want to skip the build step entirely:

**Root Directory:** `apps/web`
**Build Command:** (leave empty)
**Output Directory:** `build`

Then Vercel will just deploy your pre-built `build` folder as-is.

Note: You'll need to rebuild and commit the build folder each time (not recommended for production).
