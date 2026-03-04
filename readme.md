
# E-commerce

A lightweight, serverless single-product digital store. No frameworks. No backend servers. Just HTML, CSS, JavaScript, Razorpay, and Google Sheets.

Live demo: [abhisheksinghshekhawatsde.github.io/E-commerce](https://abhisheksinghshekhawatsde.github.io/E-commerce)

---

## What Is This

A complete, production-ready template for selling a single digital product online. A customer lands on the product page, fills in their details, pays via Razorpay, and their order gets logged to a Google Sheet automatically. Fulfillment happens manually from there.

The entire system runs on free infrastructure. Clone it, configure three things, and you have a working store.

---

## Features

- Fully responsive landing page with hero, product showcase, and image carousel
- Multi-page checkout flow using `sessionStorage` to carry user data
- Razorpay integration supporting Cards, UPI, Netbanking, and Wallets
- Serverless order logging via Google Apps Script to Google Sheets
- HMAC-SHA256 client-side token for payment verification and fraud prevention
- Full SEO setup: meta tags, Open Graph, Twitter Cards, JSON-LD schema
- Legal pages included: Terms of Service, Privacy Policy, Shipping, Refunds

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Backend / API | Google Apps Script |
| Database | Google Sheets |
| Payments | Razorpay |
| Security | CryptoJS (HMAC-SHA256) |
| Hosting | GitHub Pages / Vercel / Netlify / Cloudflare Pages |

---

## System Flow


User lands on index.html
    → Fills name + email → clicks Buy Now
    → Redirected to checkout.html (data via sessionStorage)
    → Razorpay popup triggers
    → Payment succeeds → redirect back to index.html with ?status=success
    → script.js packages order + verificationToken → POST to Apps Script URL
    → Apps Script generates serial number → appends row to Google Sheet
    → Owner verifies in Razorpay dashboard → fulfills order manually


---

## Project Structure


E-commerce/
├── index.html        # Product landing page + order success handler
├── checkout.html     # Checkout page with Razorpay integration
├── script.js         # Core logic: payment handling, order submission, HMAC token
├── style.css         # All styling
├── contact.html      # Contact page
├── privacy.html      # Privacy Policy
├── terms.html        # Terms of Service
├── shipping.html     # Shipping Policy
├── refunds.html      # Refund Policy


---

## Setup Guide

### 1. Backend: Google Sheet + Apps Script

1. Create a new Google Sheet, name it whatever suits your product
2. Add these exact headers in row 1:
   `Timestamp`, `Name`, `Email`, `PaymentID`, `SerialNumber`, `Status`, `VerificationToken`
3. Open `Extensions > Apps Script`, paste in your `Code.gs` logic
4. Deploy as a Web App:
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Copy the generated Web App URL

### 2. Payment Gateway: Razorpay

1. Create a Razorpay account and complete KYC
2. Go to `Account & Settings > API Keys`
3. Generate a Test Mode key and copy the Key ID (`rzp_test_...`)

### 3. Frontend Configuration

**In `script.js`:**

const APPS_SCRIPT_URL = "YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL";


**In `checkout.html`:**

const CONFIG = {
  key: "rzp_test_YOUR_KEY_ID",
  SECRET_KEY: "YOUR_LONG_RANDOM_SECRET_KEY"
};


**In `index.html`:**
Replace all instances of `https://YOUR_FINAL_WEBSITE_URL.com/` with your actual deployed domain.

### 4. Test and Go Live

1. Run a full end-to-end test in Razorpay Test Mode
2. Confirm the order row appears correctly in your Google Sheet
3. Switch to Razorpay Live Mode, update the key in `checkout.html`
4. Deploy the project folder to your hosting provider

---

## Getting Started

No build step required.


git clone https://github.com/AbhishekSinghShekhawatSDE/E-commerce.git
cd E-commerce
open index.html


For production, push to GitHub and connect the repo to GitHub Pages, Vercel, Netlify, or Cloudflare Pages. Set root directory to `/`.

---

## Contributing

1. Fork the repo
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes
