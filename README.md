# Farm2Wealth website

Plain static site: HTML + 2 CSS files. No build step, no JavaScript framework, no cookies.
Total size is about 150 KB. Host it anywhere that serves static files.

```
index.html          landing page (uses the app mock-up screens)
privacy.html        Privacy Policy      -> Play Console "Privacy policy" URL
delete-account.html Account deletion    -> Play Console "Delete account URL"
terms.html          Terms of Service
support.html        Help + contact
404.html  robots.txt  sitemap.xml  _headers
assets/style.css  assets/mockups.css  assets/favicon.svg
```

## 1. Before you publish: replace placeholders

Yellow `[bracketed]` text on the pages marks things only you can fill in:

| Placeholder | Where |
| --- | --- |
| Company legal name, registered address | footer, privacy, terms |
| ODPC registration number, DPO name and email | privacy |
| Retention periods (30 days, 12 months, 7 years, 24 months, 90 days) | privacy, delete-account |
| Commission percentages | terms |
| List of your actual vendors | privacy section 4 |

Search-and-replace these strings in every file:

| Find | Replace with |
| --- | --- |
| `REPLACE_WITH_PACKAGE_ID` | your Android package name (the `id=` in your Play Store URL) |
| `REPLACE_WITH_YOUR_DOMAIN` | your domain, e.g. `Farm2Wealth.example.co.ke` |

Then delete the yellow highlight by removing `class="k-todo"` (or leave it until each value is confirmed).
Have a lawyer review the Privacy Policy and Terms before launch. They are written as a sound starting
point under the Kenya Data Protection Act, 2019, not as legal advice.

Support email used everywhere: `support@inuafund.co.ke` (taken from the app). Change it if needed.

## 2. Deploy (pick one)

- **Cloudflare Pages / Netlify**: drag this folder in. `_headers` adds security headers.
- **GitHub Pages**: push the folder, enable Pages. Add a `CNAME` file for a custom domain.
- **Any web host / cPanel**: upload the folder contents to `public_html`.

Use HTTPS. Make sure `https://your-domain/privacy.html` opens without login.

## 3. Play Console: where each URL goes

| Play Console field | Value |
| --- | --- |
| Store listing > Website | `https://your-domain/` |
| Store listing > Email | `support@inuafund.co.ke` |
| App content > Privacy policy | `https://your-domain/privacy.html` |
| App content > Data safety > Delete account URL | `https://your-domain/delete-account.html` |
| Data deletion: "also delete data without deleting account" | not offered yet (say No, or add later) |

### Official badge
The "Get it on Google Play" buttons are plain buttons. Google requires its official badge for marketing:
generate it at <https://play.google.com/intl/en_us/badges/> and swap it in once your app is live.

### Data safety form: suggested answers
Check these against what the final app really does.

| Data type | Collected | Shared | Optional | Purpose |
| --- | --- | --- | --- | --- |
| Name, phone number, email | Yes | With order counterparties (name only) | Email optional | Account, app functionality |
| Precise location | Yes | Rider live location to the farmer/agrovet on an active order | Yes (permission) | App functionality |
| Photos | Yes | With counterparties (listings, dispute evidence) | Yes | App functionality |
| Files / documents (ID, licences) | Yes | No (staff only) | Role-based | Verification |
| Payment info (M-Pesa number, transactions) | Yes | With payment provider | No | Payments |
| Messages | Yes | With the other chat party | No | App functionality |
| Device or other IDs (push token) | Yes | With push provider | No | App functionality |
| Crash logs / diagnostics | Yes | With analytics provider | No | Analytics |

Also answer: data is **encrypted in transit**; users **can request deletion**; app is **not** designed for children;
data is **not sold**.

### Other App content declarations
- Target audience: **18+** (matches Terms).
- Ads: none. Financial features: the wallet / M-Pesa payments (declare if asked; you partner with a licensed PSP).
- Permissions you must be able to justify: location (nearby matching, rider delivery tracking), camera/photos (listings, evidence), notifications.
- If a Riders' background-location permission is used, Play requires a prominent in-app disclosure and a video.

## 4. Store listing text (ready to paste)

**App name:** Farm2Wealth

**Short description (80 chars max):**
`Buy farm inputs, get delivery, ask experts and sell produce.` (60)

**Full description:**
```
Farm2Wealth connects farmers, agrovets, agricultural professionals and bike riders in one app.

FARMERS
- Find verified agrovets near you and buy seeds, fertilizer and tools
- Track your delivery live on a map
- Book paid consultations with agronomists and vets
- List and sell your own produce
- Weather, season alerts and a free knowledge base

AGROVETS
- Digital storefront and catalogue, order dashboard, low-stock alerts
- Delivery handled by nearby riders, sales reports and payouts

BIKE RIDERS
- See pickup, drop-off and payout before you accept
- Navigate, deliver and confirm, then withdraw earnings to M-Pesa

PROFESSIONALS
- A verified profile, your own rates, and requests from farmers nearby

SAFE BY DESIGN
- M-Pesa payments are held until you confirm everything is right
- Verified badges, two-way ratings and a Report a problem option
- Consent-first privacy under the Kenya Data Protection Act

Growing jobs. Connecting farms.
```

## 5. Notes
- The app screens on the home page are reused from your mock-up file (pure HTML/CSS, no images).
  Re-run the same approach to refresh them when the UI changes.
- The home page names the app **Farm2Wealth**, following the scope document. The in-app Terms text still says
  "Farm2Wealth"; align the two before release so the store listing, website and app agree.
- The delete-account page uses an email-based request (works with no backend). If you later add
  in-app deletion, update the steps on that page, which Google checks.
