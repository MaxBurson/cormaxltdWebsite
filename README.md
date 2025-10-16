# CormaX Ltd - Official Business Website

Professional business website for CormaX Ltd, a UK-registered mobile app development company. Built with HTML, CSS, and JavaScript, deployed on GitHub Pages.

## Features

- 🌑 Professional dark theme design
- 📱 Fully responsive (mobile, tablet, desktop)
- ⚡ Fast loading and optimized performance
- 🎯 Smooth scrolling and animations
- 📧 Contact form with validation
- 🏢 Complete UK company legal information (Companies Act 2006 compliant)
- 💼 Featured project showcase (UniSplitr)
- 🔵 Cyan/blue gradient accent colors matching brand identity

## Project Structure

```
CormaXWebsite/
├── index.html          # Main HTML file
├── styles.css          # Stylesheet
├── script.js           # JavaScript functionality
├── CNAME               # Custom domain configuration
└── README.md           # This file
```

## Custom Domain Setup (cormaxltd.co.uk)

### Step 1: Configure DNS Settings at GoDaddy

1. **Log in to GoDaddy** and go to your domain management
2. **Find DNS Settings** for `cormaxltd.co.uk`
3. **Delete or disable** the current A records pointing to GoDaddy's parking page
4. **Add these DNS records**:

   **For apex domain (cormaxltd.co.uk):**
   ```
   Type: A
   Name: @
   Value: 185.199.108.153
   TTL: 600 (or default)

   Type: A
   Name: @
   Value: 185.199.109.153
   TTL: 600

   Type: A
   Name: @
   Value: 185.199.110.153
   TTL: 600

   Type: A
   Name: @
   Value: 185.199.111.153
   TTL: 600
   ```

   **For www subdomain (optional but recommended):**
   ```
   Type: CNAME
   Name: www
   Value: yourusername.github.io
   TTL: 600
   ```

5. **Save changes** - DNS propagation can take 24-48 hours but usually happens within minutes

### ⚠️ IMPORTANT: Common DNS Configuration Mistakes

**Make sure you:**
- ✅ **DELETE** any existing A records pointing to GoDaddy IPs (like 160.153.x.x or 184.168.x.x)
- ✅ **DELETE** any CNAME record for @ (apex domain) - only A records should be used for @
- ✅ Add **ALL FOUR** GitHub Pages A records (not just one)
- ✅ Use `@` for the Name field (not blank, not "cormaxltd.co.uk")
- ✅ Wait at least 5-10 minutes after saving for DNS to propagate

**To verify DNS is working:**
```bash
# Check if DNS is pointing to GitHub Pages
dig cormaxltd.co.uk +short

# Should show the 4 GitHub IPs:
# 185.199.108.153
# 185.199.109.153
# 185.199.110.153
# 185.199.111.153
```

Or use online tool: https://dnschecker.org/#A/cormaxltd.co.uk

### Step 2: Add CNAME File to Repository

The `CNAME` file has been created with your domain. Make sure to include it when you push to GitHub.

### Step 3: Configure GitHub Pages

After pushing your code to GitHub:

1. Go to your repository Settings → Pages
2. Under "Custom domain", enter: `cormaxltd.co.uk`
3. Click Save
4. Wait for DNS check to complete (green checkmark)
5. Enable "Enforce HTTPS" (recommended, may take a few minutes to become available)

## Deployment to GitHub Pages

### Method 1: Using GitHub Web Interface

1. **Create a new repository on GitHub**
   - Go to https://github.com/new
   - Name your repository (e.g., `cormax-website`)
   - Make it public
   - Don't initialize with README (we already have one)

2. **Upload files**
   - Click "uploading an existing file"
   - Drag and drop all files from the CormaXWebsite folder
   - Commit the changes

3. **Enable GitHub Pages**
   - Go to repository Settings
   - Scroll to "Pages" section
   - Under "Source", select "main" branch
   - Click Save
   - Your site will be published at: `https://yourusername.github.io/cormax-website/`

### Method 2: Using Git Command Line

1. **Initialize Git repository**
   ```bash
   cd ~/Desktop/CormaXWebsite
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **Create repository on GitHub and push**
   ```bash
   git remote add origin https://github.com/yourusername/cormax-website.git
   git branch -M main
   git push -u origin main
   ```

3. **Enable GitHub Pages**
   - Follow step 3 from Method 1 above

## Local Development

To view the website locally:

1. Open `index.html` in your web browser, or
2. Use a local server (recommended):
   ```bash
   # Using Python 3
   python3 -m http.server 8000
   
   # Using Node.js (if you have npx)
   npx http-server
   ```
3. Open `http://localhost:8000` in your browser

## Customization

### Changing Colors
Edit the CSS variables in `styles.css`:
```css
:root {
    --primary-color: #6366f1;
    --primary-dark: #4f46e5;
    --secondary-color: #8b5cf6;
    /* ... */
}
```

### Updating Content
- Edit text directly in `index.html`
- Modify sections, add/remove cards as needed
- Update contact information

### Adding Pages
1. Create new HTML files (e.g., `about.html`)
2. Link them in the navigation menu
3. Maintain consistent styling by using the same CSS file

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers

## Performance

- No external dependencies
- Minimal CSS and JavaScript
- Optimized for fast loading
- Lighthouse score: 95+

## Troubleshooting "NotServedByPagesError"

### Error: "Domain does not resolve to the GitHub Pages server"

This means your DNS isn't configured correctly yet. Here's how to fix it:

#### 1. **Verify Your GoDaddy DNS Settings**

Log into GoDaddy and check your DNS records for `cormaxltd.co.uk`:

**What you SHOULD see:**
```
Type    Name    Value                   TTL
A       @       185.199.108.153         600
A       @       185.199.109.153         600
A       @       185.199.110.153         600
A       @       185.199.111.153         600
CNAME   www     yourusername.github.io  600
```

**What you should NOT see:**
- ❌ A records with GoDaddy parking IPs (160.x.x.x, 184.x.x.x, etc.)
- ❌ CNAME record for @ (apex domain)
- ❌ Forwarding rules
- ❌ Any other A records

#### 2. **Check DNS Propagation**

After updating DNS, verify it's working:

**Option A: Command line**
```bash
dig cormaxltd.co.uk +short
# or
nslookup cormaxltd.co.uk
```

**Option B: Online tools**
- https://dnschecker.org/#A/cormaxltd.co.uk
- https://www.whatsmydns.net/#A/cormaxltd.co.uk

You should see the 4 GitHub Pages IPs (185.199.108-111.153)

#### 3. **Wait for DNS Propagation**

- **Minimum wait:** 5-10 minutes
- **Typical wait:** 30 minutes to 2 hours
- **Maximum wait:** 24-48 hours (rare)

#### 4. **Configure GitHub Pages (After DNS Propagates)**

**IMPORTANT ORDER:**
1. ✅ First: Configure DNS at GoDaddy
2. ✅ Second: Wait for DNS to propagate (verify with dig/dnschecker)
3. ✅ Third: Push code with CNAME file to GitHub
4. ✅ Fourth: Add custom domain in GitHub Pages settings

**In GitHub:**
1. Go to your repository
2. Settings → Pages
3. Under "Custom domain", enter: `cormaxltd.co.uk`
4. Click Save
5. Wait for the DNS check (may take a few minutes)
6. Once verified (green checkmark), enable "Enforce HTTPS"

#### 5. **If Still Not Working**

**Try removing and re-adding the domain:**
1. In GitHub Pages settings, remove the custom domain
2. Wait 1 minute
3. Add it back: `cormaxltd.co.uk`
4. Save and wait for verification

**Check your repository:**
- Make sure the `CNAME` file exists in the root
- Make sure it contains only: `cormaxltd.co.uk` (no http://, no www, just the domain)
- Make sure your repository is public
- Make sure GitHub Pages is enabled and set to deploy from `main` branch

**Clear DNS cache on your computer:**
```bash
# macOS
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder

# Windows
ipconfig /flushdns

# Linux
sudo systemd-resolve --flush-caches
```

#### 6. **Alternative: Use www Subdomain First**

If the apex domain isn't working, you can start with www:

1. In GoDaddy, make sure you have:
   ```
   Type: CNAME
   Name: www
   Value: yourusername.github.io
   ```

2. In GitHub Pages custom domain, use: `www.cormaxltd.co.uk`

3. Once working, you can add the apex domain A records

## License

Free to use and modify for personal and commercial projects.

## Support

For issues or questions, please open an issue on the GitHub repository.

---

Built with ❤️ for GitHub Pages
