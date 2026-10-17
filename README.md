# SDE-2 Switch HQ

Responsive interview-preparation tracker for the SDE-2 switch goal.

## Included
- 45-minute and 90-minute study tracks
- Roadmap checklist and readiness gates
- DSA problem tracker with topic, difficulty, status, notes, URL, CSV export
- Job application pipeline and follow-up dates
- Study-hour log and weekly totals
- Google sign-in and per-user cloud sync through Firebase Authentication and Cloud Firestore

## Firebase setup (required for cloud sync)
1. In Firebase Console for project `sde-2-switch-hq`, enable **Authentication → Sign-in method → Google**.
2. In **Authentication → Settings → Authorized domains**, add the exact GitHub Pages hostname, e.g. `ritikpachauri.github.io`.
3. Create a **Cloud Firestore** database.
4. In **Firestore → Rules**, publish the contents of `firestore.rules`.
5. Confirm the web app config in `index.html` matches this Firebase project.

The tracker saves one document at `users/{uid}/tracker/state`. The included rules allow only the authenticated user to read/write their own document.

Firebase web configuration is intended to be included in client-side apps. Do not commit service-account private keys, admin SDK credentials, or passwords.

## Deployment
A GitHub Actions workflow in `.github/workflows/pages.yml` publishes the root directory to GitHub Pages when code is pushed to `main`.

1. In repository **Settings → Pages**, set **Build and deployment → Source** to **GitHub Actions**.
2. Check **Settings → Actions → General** and ensure workflows are allowed.
3. Open the **Actions** tab and wait for the **Deploy to GitHub Pages** workflow to succeed.
4. Find the published URL in **Settings → Pages**.

This repository is currently private. GitHub Pages on GitHub Free for personal accounts generally requires a public repository; if Pages is unavailable, change visibility to Public (the source and website will be public) or use a plan that supports Pages for private repositories.

## Notes
- Before Firebase is configured, the site can still be explored in local-browser mode; cross-device sync requires Google Authentication and Firestore rules.
- If Google sign-in returns an unauthorized-domain error, add the exact hostname shown in the browser address bar to Firebase's Authorized domains.
- Export CSV backups periodically.
