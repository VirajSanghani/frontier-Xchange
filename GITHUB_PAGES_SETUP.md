# 🌐 GitHub Pages Deployment Guide

## Quick Setup (3 Steps)

### Step 1: Enable GitHub Pages
1. Go to: https://github.com/frontiertower/Frontier-Xchange/settings/pages
2. Under **Source**, select **GitHub Actions**
3. Click **Save**

### Step 2: Run the Deployment
The deployment will automatically trigger when you push to main. You can also manually trigger it:
1. Go to: https://github.com/frontiertower/Frontier-Xchange/actions
2. Click on **"Deploy to GitHub Pages"** workflow
3. Click **"Run workflow"** → **"Run workflow"**

### Step 3: Access Your Site
Once deployed (takes ~2-3 minutes), your site will be available at:
- **🔗 https://frontiertower.github.io/Frontier-Xchange/**

---

## 📋 Detailed Setup Instructions

### Prerequisites
- GitHub Pages must be enabled in repository settings
- Repository must be public (or you need GitHub Pro for private repos)
- GitHub Actions must be enabled

### Automatic Deployment
The `.github/workflows/deploy.yml` file is already configured to:
1. **Trigger on every push to main branch**
2. **Build the React application**
3. **Deploy to GitHub Pages automatically**

### Manual Deployment Steps
If you prefer to deploy manually:

```bash
# 1. Clone the repository
git clone https://github.com/frontiertower/Frontier-Xchange.git
cd Frontier-Xchange

# 2. Install dependencies
npm install

# 3. Build for production
npm run build

# 4. Deploy to GitHub Pages
npm install -g gh-pages
gh-pages -d dist
```

---

## 🔧 Configuration Details

### Vite Configuration
The `vite.config.ts` has been configured with:
```javascript
base: '/Frontier-Xchange/'
```
This ensures all assets load correctly from the GitHub Pages subdirectory.

### GitHub Actions Workflow
The workflow (`.github/workflows/deploy.yml`) includes:
- **Node.js 20** setup
- **Dependency caching** for faster builds
- **Automatic artifact upload**
- **GitHub Pages deployment**

### Environment Variables
For GitHub Pages deployment, you'll need to:
1. Create a `.env.production` file (if using environment variables)
2. Add your production Supabase credentials:
```env
VITE_SUPABASE_URL=your_production_supabase_url
VITE_SUPABASE_ANON_KEY=your_production_anon_key
```

⚠️ **Important**: Never commit `.env` files with real credentials!

---

## 🚀 First-Time Setup Checklist

- [ ] **Enable GitHub Pages** in repository settings
- [ ] **Select "GitHub Actions"** as the source
- [ ] **Push to main branch** or manually trigger workflow
- [ ] **Wait 2-3 minutes** for deployment
- [ ] **Visit** https://frontiertower.github.io/Frontier-Xchange/

---

## 🔄 Updating the Site

To update the deployed site:
1. Make your changes locally
2. Commit and push to main branch:
```bash
git add .
git commit -m "Update: your changes"
git push origin main
```
3. GitHub Actions will automatically rebuild and deploy

---

## 🐛 Troubleshooting

### Site Not Loading?
- **Check GitHub Pages is enabled**: Settings → Pages
- **Verify workflow ran successfully**: Actions tab
- **Wait a few minutes**: Initial deployment can take up to 10 minutes
- **Clear browser cache**: Hard refresh (Ctrl+Shift+R or Cmd+Shift+R)

### Build Failures?
- **Check Actions tab** for error messages
- **Verify all dependencies** are in package.json
- **Test build locally** with `npm run build`

### Assets Not Loading?
- **Check base path** in vite.config.ts matches repository name
- **Ensure all imports** use relative paths
- **Verify dist folder** contains all necessary files

### 404 Errors on Routes?
For React Router to work with GitHub Pages, add a `404.html` file:
1. Copy `index.html` to `404.html` in the public folder
2. This handles client-side routing correctly

---

## 📊 Monitoring Deployment

### Check Deployment Status
1. Go to: https://github.com/frontiertower/Frontier-Xchange/actions
2. Look for green checkmark ✅ (success) or red X ❌ (failure)
3. Click on workflow run for detailed logs

### View Deployment History
- Visit: https://github.com/frontiertower/Frontier-Xchange/deployments
- See all past deployments and their status

---

## 🔒 Security Considerations

### For Production Deployment
1. **Use environment variables** for sensitive data
2. **Never commit API keys** or secrets
3. **Configure CORS** properly in your backend
4. **Use HTTPS** (GitHub Pages provides this automatically)
5. **Implement rate limiting** for API calls

### Supabase Configuration
For production, update your Supabase project:
1. Add `https://frontiertower.github.io` to allowed URLs
2. Configure Row Level Security (RLS) policies
3. Enable appropriate authentication providers

---

## 🎯 Custom Domain (Optional)

To use a custom domain:
1. Go to Settings → Pages
2. Add your custom domain under "Custom domain"
3. Configure DNS:
   - Add CNAME record pointing to `frontiertower.github.io`
   - Or add A records for GitHub Pages IPs
4. Enable "Enforce HTTPS"

---

## 📚 Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Vite Static Deploy Guide](https://vitejs.dev/guide/static-deploy.html#github-pages)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

---

**🎉 Your Frontier Xchange platform is now ready for GitHub Pages deployment!**

**Live URL**: https://frontiertower.github.io/Frontier-Xchange/

---

**🤖 Generated with [Claude Code](https://claude.ai/code)**