 `markdown
# E-commerce

A serverless single-product digital store built with pure HTML, CSS, and JavaScript.

Live: [abhisheksinghshekhawatsde.github.io/E-commerce](https://abhisheksinghshekhawatsde.github.io/E-commerce)

---

## Stack

| Layer | Technology |
|-------|------------|
| Frontend | HTML5, CSS3, Vanilla JS |
| Backend | Google Apps Script |
| Database | Google Sheets |
| Payments | Razorpay |
| Security | CryptoJS (HMAC-SHA256) |

---

## Setup

**1. Google Sheet**
Create a sheet with headers: `Timestamp`, `Name`, `Email`, `PaymentID`, `SerialNumber`, `Status`, `VerificationToken`. Deploy an Apps Script as a Web App and copy the URL.

**2. Razorpay**
Generate a Test Key ID from `Account & Settings > API Keys`.

**3. Configure**

 js
// script.js
const APPS_SCRIPT_URL = "YOUR_WEB_APP_URL";

// checkout.html
const CONFIG = {
  key: "rzp_test_YOUR_KEY_ID",
  SECRET_KEY: "YOUR_SECRET_KEY"
};
 

**4. Go Live**
Test end-to-end in Test Mode. Switch to Live Key. Deploy to GitHub Pages, Vercel, or Netlify.

---

## Run Locally

 bash
git clone https://github.com/AbhishekSinghShekhawatSDE/E-commerce.git
cd E-commerce
open index.html
 
 `
