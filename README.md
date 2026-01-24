# Customer Experience Hub - Review & Feedback Platform

A beautiful, modern QR code-based feedback collection system with emoji responses and smart routing. Built for businesses to collect customer feedback and track individual staff performance.

## Features

- **Beautiful UI**: Modern, responsive design with smooth animations
- **Emoji-Based Feedback**: Simple 3-option feedback (Not Great, Okay, Loved It!)
- **Smart Routing**: Happy customers → Google Reviews (public), Unhappy customers → Google Form (private)
- **QR Code Solutions**:
  - Business QR codes for overall feedback
  - Individual staff QR codes for performance tracking
- **Mobile Optimized**: Perfect experience on all devices
- **Loading States**: Professional loading overlays during redirects

## Project Structure

```
reviews/
├── index.html                    # Landing page showcasing all clients
├── README.md                     # This file
│
├── iskcon-porto/
│   └── business/
│       └── index.html           # O Oriente no Porto feedback page
│
├── dm-usa/
│   └── business/
│       └── index.html           # Divya Motel feedback page
│
├── ttc-usa/
│   └── business/
│       └── index.html           # Trexler Travel Center feedback page
│
└── ltp-usa/
    └── business/
        └── index.html           # Lancaster Travel Plaza feedback page
```

## How It Works

### Business Reviews
1. Generate a QR code for your business feedback page
2. Place the QR code at reception/checkout areas
3. Customers scan and select emoji rating
4. Smart routing directs them to appropriate platform

### Staff Performance Tracking
1. Generate unique QR codes for each employee
2. Provide QR codes to staff (badges, cards, table tents)
3. Staff present QR codes to customers
4. Track individual performance and reward excellence

---

## Adding a New Business

### Step 1: Create Business Directory Structure

Create a new folder for your business:

```bash
mkdir -p your-business-name/business
```

### Step 2: Create Feedback Page

Copy an existing business template:

```bash
cp iskcon-porto/business/index.html your-business-name/business/index.html
```

### Step 3: Update Business Information

Edit `your-business-name/business/index.html`:

#### A. Update Page Title (Line 6)
```html
<title>Share Your Experience - Your Business Name</title>
```

#### B. Update Business Name (Line 341)
```html
<div class="business-name">Your Business Name</div>
```

#### C. Update Google Review URL (Line 395)
To find your Google Review URL:
1. Search for your business on Google
2. Click "Write a review"
3. Copy the URL from your browser
4. Paste it in the configuration:

```javascript
GOOGLE_REVIEW_URL: "https://your-google-review-url-here",
```

#### D. Update Google Form URL (Line 399)
To create a Google Form for negative feedback:
1. Go to https://forms.google.com
2. Create a new form with questions like:
   - "What went wrong?"
   - "How can we improve?"
   - Contact information (optional)
3. Click "Send" → Get link
4. Copy the URL and paste it:

```javascript
GOOGLE_FORM_URL: "https://docs.google.com/forms/d/e/YOUR-FORM-ID/viewform",
```

### Step 4: Update Landing Page (index.html)

Add your business to the clients section in `index.html`:

#### A. Add Animation Delay (Around Line 309)
```css
.client-card:nth-child(5) {
  animation-delay: 0.6s;
}
```

#### B. Add Client Card (Around Line 1093)
```html
<!-- Client 5: Your Business Name -->
<div class="client-card">
  <div class="client-icon warm">🏪</div>
  <h3 class="client-name">Your Business Name</h3>
  <p class="client-description">
    Brief description of your business and what you offer.
    Highlight your commitment to customer satisfaction.
  </p>
  <a href="./your-business-name/business/index.html" class="client-link">
    View Feedback Page
    <svg viewBox="0 0 24 24">
      <path d="M5 12h14M12 5l7 7-7 7" />
    </svg>
  </a>
</div>
```

**Icon Options:**
- 🏪 Store
- 🍽️ Restaurant
- 🏨 Hotel
- ⛽ Gas Station
- 🚗 Travel Center
- 🏢 Business
- 🕉️ Spiritual/Cultural
- 🎯 Service Center

**Gradient Options:**
- `warm` - Peachy orange to coral pink
- `purple` - Purple to blue (add class to parent div: `<div class="client-card purple">`)

#### C. Update Client Count (Around Line 1050)
```html
<div class="stat-number">5+</div>
<div class="stat-label">Happy Clients</div>
```

### Step 5: Generate QR Code

1. Use any QR code generator (e.g., https://qr-code-generator.com)
2. Enter your feedback page URL: `https://yourdomain.com/your-business-name/business/`
3. Download the QR code as PNG/SVG
4. Print and display at your business location

---

## Adding Staff Members

### Step 1: Create Staff Directory

```bash
mkdir -p your-business-name/staff/01
mkdir -p your-business-name/staff/02
# ... create more as needed
```

### Step 2: Create Staff Feedback Pages

Copy the business template for each staff member:

```bash
cp your-business-name/business/index.html your-business-name/staff/01/index.html
cp your-business-name/business/index.html your-business-name/staff/02/index.html
```

### Step 3: Customize Staff Pages

Edit each staff member's `index.html`:

#### Update Title
```html
<title>Rate My Service - John Doe</title>
```

#### Update Business/Staff Name
```html
<div class="business-name">John Doe - Server #01</div>
```

#### Update Heading (Optional)
```html
<h1>How was my service?</h1>
<p class="subtitle">Please rate my service today</p>
```

### Step 4: Configure URLs

Same as business setup - update Google Review URL and Google Form URL in the configuration section.

**Pro Tip**: You can create separate Google Forms for each staff member to track individual feedback, or use one shared form with a hidden field to identify which staff member it's for.

### Step 5: Generate Staff QR Codes

For each staff member:
1. Generate QR code with URL: `https://yourdomain.com/your-business-name/staff/01/`
2. Print on:
   - Name badges
   - Table tent cards
   - Business cards
   - Stickers
3. Staff presents QR code: "Please scan to rate my service!"

---

## URL Configuration Guide

### Finding Your Google Review URL

**Method 1: Direct Link**
1. Open Google Maps
2. Search for your business
3. Click on your business listing
4. Scroll down and click "Write a review"
5. Copy the URL from your browser's address bar
6. Should look like: `https://www.google.com/maps/place/...` or `https://g.page/r/...`

**Method 2: Google Business Profile**
1. Log in to Google Business Profile
2. Go to "Get more reviews"
3. Copy the short URL provided

### Creating a Google Form for Negative Feedback

1. **Go to Google Forms**: https://forms.google.com
2. **Create New Form**: Click the "+" button
3. **Add Questions**:
   - "What went wrong with your experience?" (Long answer)
   - "How can we improve?" (Long answer)
   - "Would you like us to contact you?" (Multiple choice: Yes/No)
   - "Your email" (Short answer - optional)
   - "Your phone" (Short answer - optional)
4. **Configure Settings**:
   - Settings → Collect email addresses (optional)
   - Settings → Limit to 1 response (optional)
5. **Get Link**:
   - Click "Send" button
   - Click link icon 🔗
   - Copy the URL
   - Should look like: `https://docs.google.com/forms/d/e/1FAIpQLSe.../viewform`

### Updating URLs in Feedback Pages

Open `your-business-name/business/index.html` and find the CONFIG section (around line 391):

```javascript
const CONFIG = {
  // Your Google Business Review URL
  GOOGLE_REVIEW_URL: "PASTE_YOUR_GOOGLE_REVIEW_URL_HERE",

  // Your Google Form URL for collecting negative feedback
  GOOGLE_FORM_URL: "PASTE_YOUR_GOOGLE_FORM_URL_HERE",
};
```

Replace the placeholder URLs with your actual URLs.

---

## Design Customization

### Color Scheme

The project uses CSS variables for easy customization. Edit the `:root` section in any HTML file:

```css
:root {
  --bg-primary: #fdf8f3;      /* Cream background */
  --bg-card: #ffffff;          /* White cards */
  --text-dark: #1a1a1a;        /* Dark text */
  --text-muted: #6b6b6b;       /* Muted text */
  --accent-warm: #e8a87c;      /* Peachy orange */
  --accent-coral: #f67280;     /* Coral pink */
  --shadow-soft: 0 20px 60px rgba(0, 0, 0, 0.08);
  --shadow-hover: 0 30px 80px rgba(0, 0, 0, 0.12);
}
```

### Emoji Options

You can change the emoji ratings (around line 349-373):

```html
<!-- Option 1: Sad -->
<span class="emoji">😔</span>
<span class="emoji-label">Not Great</span>

<!-- Option 2: Okay -->
<span class="emoji">🙂</span>
<span class="emoji-label">Okay</span>

<!-- Option 3: Happy -->
<span class="emoji">😍</span>
<span class="emoji-label">Loved It!</span>
```

**Alternative Emoji Sets:**
- Stars: ⭐ ⭐⭐ ⭐⭐⭐
- Faces: 😞 😐 😊
- Thumbs: 👎 👌 👍
- Hearts: 💔 ❤️ 💕

---

## Testing Your Setup

### Local Testing

1. Open the HTML file in a browser:
   ```bash
   # Using Python
   python -m http.server 8000

   # Then visit: http://localhost:8000
   ```

2. Test each emoji button:
   - Click "Not Great" → Should redirect to Google Form
   - Click "Okay" → Should redirect to Google Reviews
   - Click "Loved It!" → Should redirect to Google Reviews

### QR Code Testing

1. Generate a QR code with your local URL or staging URL
2. Scan with your phone
3. Verify the page loads correctly on mobile
4. Test all three feedback options
5. Verify redirects work properly

---

## Deployment

### GitHub Pages

1. **Push to GitHub**:
   ```bash
   git add .
   git commit -m "Add feedback system"
   git push origin main
   ```

2. **Enable GitHub Pages**:
   - Go to repository Settings
   - Navigate to "Pages"
   - Source: Deploy from branch
   - Branch: main, folder: / (root)
   - Save

3. **Access Your Site**:
   - URL: `https://yourusername.github.io/reviews/`
   - Business page: `https://yourusername.github.io/reviews/your-business-name/business/`
   - Staff page: `https://yourusername.github.io/reviews/your-business-name/staff/01/`

### Custom Domain

1. Add CNAME file:
   ```bash
   echo "reviews.yourdomain.com" > CNAME
   ```

2. Configure DNS:
   - Add CNAME record: `reviews` → `yourusername.github.io`
   - Or A records pointing to GitHub's IPs

3. Enable HTTPS in GitHub Pages settings

### Other Hosting Options

- **Netlify**: Drag and drop the folder
- **Vercel**: Connect GitHub repository
- **Traditional Hosting**: Upload via FTP to public_html folder

---

## Best Practices

### QR Code Placement

**Business QR Codes:**
- Reception desk (highly visible)
- Checkout counter
- Exit areas
- Table tents (restaurants)
- Receipt holders

**Staff QR Codes:**
- Name badges
- Table tent cards with staff photo
- Business cards
- Server check presenters

### Print Specifications

**QR Code Size:**
- Minimum: 2x2 inches (5x5 cm)
- Recommended: 3x3 inches (7.5x7.5 cm)
- Include text: "Scan to share feedback" or "Rate my service"

**Materials:**
- Laminated cards (durable)
- Acrylic stands (professional)
- Stickers (versatile)
- Vinyl banners (large format)

### Monitoring Feedback

1. **Google Reviews**: Monitor your Google Business Profile regularly
2. **Google Forms**:
   - Set up email notifications for new responses
   - Review Form responses daily
   - Create a spreadsheet to track trends
3. **Staff Performance**:
   - Weekly reports from individual staff forms
   - Recognize top performers
   - Provide coaching for improvement areas

---

## Troubleshooting

### QR Code Not Working

- Verify URL is correct and accessible
- Test URL in browser first
- Ensure no extra spaces in QR code generator
- Regenerate QR code if corrupted

### Redirects Not Working

- Check CONFIG object has correct URLs
- Remove any trailing/leading spaces
- Test URLs directly in browser
- Check browser console for errors (F12)

### Page Not Loading

- Verify file path is correct
- Check for typos in filenames
- Ensure index.html is in correct directory
- Clear browser cache

### Mobile Display Issues

- The design is responsive and should work on all devices
- Test on actual mobile devices
- Check for JavaScript errors in mobile browser
- Ensure viewport meta tag is present

---

## Support & Contribution

### Reporting Issues

If you encounter any issues:
1. Check this README first
2. Test in different browsers
3. Verify all URLs are correct
4. Create an issue with details

### Customization Requests

This is a template project. Feel free to:
- Modify colors and styles
- Change emoji sets
- Add more feedback options
- Integrate with other platforms
- Add analytics tracking

---

## License

This project is provided as-is for business use. Feel free to customize and deploy for your business needs.

---

## Quick Reference Card

### Adding New Business Checklist

- [ ] Create folder: `business-name/business/`
- [ ] Copy template HTML file
- [ ] Update page title
- [ ] Update business name
- [ ] Get Google Review URL
- [ ] Create Google Form for feedback
- [ ] Update CONFIG section with URLs
- [ ] Add client card to index.html
- [ ] Update client count in stats
- [ ] Generate QR code
- [ ] Print and deploy QR code
- [ ] Test all functionality

### Adding New Staff Member Checklist

- [ ] Create folder: `business-name/staff/##/`
- [ ] Copy template HTML file
- [ ] Update title with staff name
- [ ] Update business/staff name display
- [ ] Configure URLs (can use same or separate forms)
- [ ] Generate QR code with staff URL
- [ ] Print QR code for staff member
- [ ] Train staff on presenting QR code
- [ ] Test functionality
- [ ] Monitor feedback

---

**Built with care for amazing businesses ♥**

© 2026 Experience Hub. All rights reserved.
