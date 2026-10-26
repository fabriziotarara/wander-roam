# Wander & Roam Website Documentation
Bespoke Travel Advisory website for Courtney Tarara, hosted on Netlify.

Dancing Script - Google Fonts

---

## 🌟 How to Update Customer Testimonials

Customer testimonials are stored in [`testimonials.json`](file:///d:/My%20Drive/Business/Wander%20&%20Roam/Wander%20&%20Roam%20Website/testimonials.json). You can edit this file directly in any text editor, GitHub, or Netlify dashboard.

### Adding a New Testimonial

Open `testimonials.json` and add a new entry to the array using this format:

```json
[
  {
    "quote": "Courtney organized the most incredible safari trip for us! Every detail was seamless.",
    "name": "Sarah M.",
    "trip": "South Africa, 2026"
  },
  {
    "quote": "Courtney’s knowledge was invaluable. She helped us plan our Costa Rica family vacation.",
    "name": "Cris S.",
    "trip": "Costa Rica, 2025"
  }
]
```

**Fields:**
- `quote`: The text of the review.
- `name`: The client's name or initial (e.g. `"Jane D."`).
- `trip`: The trip location or type and year (e.g. `"Italy, 2026"`).

Once saved and published to Netlify, the website will automatically load and render your updated testimonials in the slider!

---

## 📩 Netlify Forms & Inquiry Submissions

The contact form is configured to work natively with **Netlify Forms** (free tier included).

### How It Works:
1. When a site visitor fills out the contact form, Netlify intercepts the submission.
2. The user sees a sleek "Thank You!" message instantly without reloading the page.
3. Netlify logs the submission under your site's **Forms** dashboard.

### How to Receive Email Notifications:
1. Log in to your [Netlify Dashboard](https://app.netlify.com).
2. Select your website (**Wander & Roam**).
3. Go to **Site configuration > Forms > Form notifications**.
4. Click **Add notification** -> **Email notification**.
5. Select the form named `contact` and enter your email address to receive inquiry notifications instantly whenever a potential traveler submits the form.

---

## 🚀 Deploying Updates to Netlify

- **If connected to GitHub/Git repository**: Every time you commit and push updates to `testimonials.json` or `index.html`, Netlify will deploy the site automatically.
- **If using manual drag-and-drop upload**: Upload the entire project folder to Netlify's site upload interface.
