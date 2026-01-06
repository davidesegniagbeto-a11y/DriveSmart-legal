# DriveSmart UK - Legal Documents (Web Version)

This folder contains HTML versions of DriveSmart UK's legal documents, ready for immediate deployment to the web.

## Files

- **index.html**: Landing page with links to all legal documents
- **privacy.html**: Complete Privacy Policy (HTML version)
- **terms.html**: Complete Terms of Service (HTML version)
- **README.md**: This file

## Quick Deploy Options

### Option 1: GitHub Pages (Fastest - 5 minutes)

1. **Commit this folder to your repository**:
   ```bash
   git add docs/
   git commit -m "Add legal documents HTML for web deployment"
   git push origin main
   ```

2. **Enable GitHub Pages**:
   - Go to your repository on GitHub
   - Click **Settings** → **Pages**
   - Under "Source", select **Deploy from a branch**
   - Select **main** branch and **/docs** folder
   - Click **Save**

3. **Access your documents**:
   - After 2-3 minutes, visit: `https://<your-username>.github.io/<repo-name>/`
   - Privacy Policy: `https://<your-username>.github.io/<repo-name>/privacy.html`
   - Terms: `https://<your-username>.github.io/<repo-name>/terms.html`

4. **Optional: Add custom domain**:
   - Create a file `CNAME` in the `docs` folder with your domain (e.g., `docs.drivesmart.uk`)
   - Configure DNS at your domain registrar:
     ```
     Type: CNAME
     Host: docs (or @ for root domain)
     Value: <your-username>.github.io
     ```

### Option 2: Vercel (Professional - 10 minutes)

1. **Install Vercel CLI**:
   ```bash
   npm install -g vercel
   ```

2. **Deploy**:
   ```bash
   cd docs
   vercel --prod
   ```

3. **Configure custom domain** in Vercel dashboard

### Option 3: Netlify (Alternative)

1. **Drag and drop the `docs` folder** to https://app.netlify.com/drop
2. **Or use Netlify CLI**:
   ```bash
   npm install -g netlify-cli
   cd docs
   netlify deploy --prod
   ```

3. **Configure custom domain** in Netlify dashboard

### Option 4: Firebase Hosting

1. **Install Firebase CLI**:
   ```bash
   npm install -g firebase-tools
   ```

2. **Initialize and deploy**:
   ```bash
   firebase init hosting
   # Select docs folder as public directory
   firebase deploy
   ```

## After Deployment

### Update App References

Once deployed, update the URLs in your mobile app:

**Frontend files to update**:
- `src/screens/auth/RegisterScreen.tsx`
- `src/screens/auth/LoginScreen.tsx`
- `src/screens/profile/ProfileScreen.tsx`
- Any other screens that link to legal documents

Replace placeholder URLs:
```typescript
// Before
const PRIVACY_POLICY_URL = "https://drivesmart.uk/privacy";
const TERMS_URL = "https://drivesmart.uk/terms";

// After (example with GitHub Pages)
const PRIVACY_POLICY_URL = "https://your-username.github.io/drivesmart/privacy.html";
const TERMS_URL = "https://your-username.github.io/drivesmart/terms.html";

// Or with custom domain
const PRIVACY_POLICY_URL = "https://docs.drivesmart.uk/privacy.html";
const TERMS_URL = "https://docs.drivesmart.uk/terms.html";
```

### Add to App Store

**Apple App Store Connect**:
1. Go to **App Information**
2. Add **Privacy Policy URL**: Your deployed privacy.html URL
3. Save

**Google Play Console**:
1. Go to **Store presence** → **Privacy policy**
2. Add **Privacy Policy URL**: Your deployed privacy.html URL
3. Save

## Testing Checklist

Before submitting to app stores:

- [ ] All three HTML files load correctly
- [ ] Links between pages work (index → privacy, index → terms)
- [ ] Links within documents work (terms ↔ privacy)
- [ ] URLs return HTTP 200 (not 404)
- [ ] Pages are mobile-responsive (test on phone)
- [ ] HTTPS is enabled (required by app stores)
- [ ] No authentication required to view (must be public)
- [ ] Contact email links work
- [ ] External links (ICO, etc.) work

## Verify Deployment

Test your deployment:

```bash
# Check if URL is accessible
curl -I https://your-deployed-url.com/privacy.html

# Should return: HTTP/2 200
```

Or open in browser:
- Incognito/Private mode (to test without cache)
- Mobile device (to test responsiveness)

## Updating Documents

When you need to update the legal documents:

1. **Edit the source markdown files**:
   - `PRIVACY_POLICY.md`
   - `TERMS_OF_SERVICE.md`

2. **Regenerate HTML** (or manually update HTML files)

3. **Redeploy**:
   - GitHub Pages: Just push changes (auto-deploys)
   - Vercel/Netlify: Push to Git or run deploy command
   - Manual: Re-upload files

## Custom Domain Setup (Optional)

### DNS Configuration

For `docs.drivesmart.uk`:

| Type  | Host | Value                      | TTL  |
|-------|------|----------------------------|------|
| CNAME | docs | your-username.github.io.   | 3600 |

For root domain `drivesmart.uk`:

| Type  | Host | Value                      | TTL  |
|-------|------|----------------------------|------|
| A     | @    | 185.199.108.153            | 3600 |
| A     | @    | 185.199.109.153            | 3600 |
| A     | @    | 185.199.110.153            | 3600 |
| A     | @    | 185.199.111.153            | 3600 |

(GitHub Pages IP addresses - verify current ones at https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

### Create CNAME File

Create `docs/CNAME` with your domain:
```
docs.drivesmart.uk
```

## Troubleshooting

**404 Error**:
- Wait 5-10 minutes after deployment
- Check that files are in correct folder
- Verify GitHub Pages is enabled

**HTTPS Not Working**:
- GitHub Pages: Wait up to 24 hours for SSL certificate
- Vercel/Netlify: Automatic (instant)

**Changes Not Showing**:
- Clear browser cache (Ctrl+Shift+R or Cmd+Shift+R)
- Check if deployment completed
- Verify correct branch/folder selected

**Mobile Not Responsive**:
- HTML files include responsive meta tags
- Test on actual device, not just browser resize

## Support

For deployment help:
- **GitHub Pages**: https://docs.github.com/en/pages
- **Vercel**: https://vercel.com/docs
- **Netlify**: https://docs.netlify.com

## Files Overview

| File | Purpose | Lines | Status |
|------|---------|-------|--------|
| index.html | Landing page | ~70 | ✅ Ready |
| privacy.html | Privacy Policy | ~420 | ✅ Ready |
| terms.html | Terms of Service | ~850 | ✅ Ready |

## Next Steps

1. ✅ HTML files created
2. 🔄 Deploy to hosting (choose option above)
3. ⏳ Test URLs are accessible
4. ⏳ Update app code with deployed URLs
5. ⏳ Add URLs to App Store Connect / Play Console
6. ⏳ Submit app for review

---

**Created**: December 31, 2024
**Last Updated**: December 31, 2024
