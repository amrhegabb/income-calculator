[README.md](https://github.com/user-attachments/files/32221551/README.md)
# Income Calculation Tool

A browser-based income calculator built for LIHTC/HUD property compliance work. It helps
calculate and document annualized income across the three most common income
verification types: **Social Security**, **Pay Stubs**, and **Employment Verification**.

Everything runs client-side in a single `index.html` file — there's no backend, no build
step, and no data ever leaves the browser. It's built with React (loaded via CDN) and
Babel Standalone for in-browser JSX, so it can be opened directly from disk or hosted
anywhere as a static file.

## Features

### Social Security
- Add multiple benefits per household member (Social Security, SSI, SSP) — each is
  calculated and shown separately, not added together.
- Optional **EIV Report** tracking, with its own annualized total alongside the
  Award/Benefit Letter total (HUD-50059 vs. LIHTC TIC reporting).
- Optional **COLA (Cost-of-Living Adjustment)** support per benefit, prorated by the
  number of months before/after the COLA effective date. COLA applies to both the
  Award Letter and EIV amounts, but not to SSP.
- 120-day document staleness warnings.

### Pay Stubs
- Supports 2 (HOTMA minimum), 4, 6, or 9 (Rhode Island) pay stubs.
- Calculates average gross pay and annualizes it against the selected pay frequency
  (Weekly, Bi-Weekly, Semi-Monthly, Monthly).
- Optional YTD (Year-to-Date) income calculation, with an automatic comparison against
  the pay-stub-based total — the higher of the two is used for reporting.
- Warns only when *every* pay stub on file is more than 120 days old.

### Employment Verification
- Base wages/salary, Overtime & Shift Differential, Commissions/Tips/Bonuses, and
  Anticipated Changes are each their own collapsible Yes/No section.
- Anticipated pay changes can be entered as a flat new rate or a percentage increase,
  with an option to also increase Overtime/Shift rates (auto by the same % or manual).
- Blended annualization by pay period (not just calendar months) when a pay change has
  a known effective date.
- Optional YTD income calculation, mirroring the Pay Stubs YTD logic.
- Full income breakdown showing every component that feeds into the final total.

### General
- Print / Download PDF, with a suggested filename built from Property Name,
  Certification Type, Effective Date, Unit #, Household Member Name, and income type.
- Save/load past entries locally in the browser ("My Saved Work") — nothing is sent to
  a server.
- Share a filled-out entry via a URL-encoded link.
- Mobile-friendly responsive layout.
- A built-in guided tour for first-time users.

## Screenshots

**Social Security** — add multiple benefits (SS/SSI/SSP), each with optional EIV and COLA:

![Social Security tab](screenshots/social-security.png)

**Pay Stubs** — average gross pay, annualization, and optional YTD comparison:

![Pay Stubs tab](screenshots/pay-stubs.png)

**Employment Verification** — collapsible income sections with a full income breakdown:

![Employment Verification tab](screenshots/employment-verification.png)

## Usage

This is a single self-contained HTML file. To use it:

1. Open `index.html` directly in a browser, **or**
2. Host it anywhere that serves static files (GitHub Pages, Netlify, Vercel, S3, etc.)

No installation, build step, or server is required.

## Tech Stack

- [React 18](https://react.dev/) (via CDN, UMD build)
- [Babel Standalone](https://babeljs.io/docs/babel-standalone) for in-browser JSX
  transformation
- Plain CSS (no framework/build tooling)
- Browser `localStorage` for saved entries

## Disclaimer

Calculations follow standard HUD/LIHTC annualization conventions and are provided for
informational purposes only. Always confirm figures against your property's compliance
manual and current HUD guidance before using them in official documentation.

## Deployment

To host this for free with a live URL:

**GitHub Pages**
1. Push `index.html` to a repository.
2. Go to Settings → Pages → set Source to "Deploy from a branch" → select the `main`
   branch and `/ (root)` folder → Save.
3. Your site will be live at `https://<username>.github.io/<repo-name>/` within a
   couple of minutes.

**Netlify**
- Drag and drop the `index.html` file (or connect the GitHub repo) at
  [app.netlify.com](https://app.netlify.com) for an instant deploy.

## Credits

Developed by Amr Hegab.
