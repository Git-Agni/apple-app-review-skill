---
name: app-review-notes
description: Avoid an App Store rejection. Audit an iOS app against the guidelines that cause most rejections, write the App Store Connect "Notes for Review" for an iOS app, answer Apple's 9 questions after a Guideline 4.3 / 4.2.6 rejection, or build the Guideline 2.1 "limited App Review history" packet. Use when someone is about to submit an app or update, got an App Store rejection, or asks how to fill the App Review notes field.
---

# app-review-notes

Do the reviewer's homework before they open the build. A reviewer gets roughly 13 minutes for a new app and 6 for an update (Phillip Shoemaker, who ran App Review 2009-2016). Anything they can't find or reach in that time becomes a rejection.

## Apple's own rules for this field (App Store Review Guidelines + App Store Connect Help)

- **Notes** hold up to **4000 bytes**, any language. Count bytes, not characters, and trim if over.
- **2.3.1(a):** "All new features, functionality, and product changes must be described with specificity in the Notes for Review section... (generic descriptions will be rejected)."
- **Before You Submit:** give full access (active demo account or fully featured demo mode), keep backend services live during review, explain non-obvious features and in-app purchases in the notes.
- **2.1(a):** test on device first, include demo account info and turn the backend on.
- **2.1(b):** every in-app purchase must be visible and working; if one can't be found or reviewed, say why in the notes.
- The **Sign-in** fields take one demo account that **must not expire**. Extra accounts go in Notes.
- Streaming video over cellular: give a test stream URL.

## Pick the mode

1. **notes** (default): about to submit an app or update. Output the Notes for Review text.
2. **answer-4.3**: got a 4.3 / 4.2.6 rejection with Apple's 9 questions. Output the reply. Do not tell the user to resubmit.
4. **audit**: before any submit, walk the rejection map in `GUIDE.md` against the code and listing, and print pass/fail with the guideline number and fix for each.
3. **packet-2.1**: got "This app has been submitted by a developer account that has a limited App Review history." Output the 6-item packet plus a recording shot list.

## Step 1: gather facts (read the code first, ask only for what the code can't tell you)

From the repo, find and list:
- What the app does, every main screen, every paywalled or gated feature and how to reach it.
- Account flows: sign up, login, **account deletion** (Guideline 5.1.1(v) needs it in-app if accounts exist).
- User content: posting, **reporting and blocking** (Guideline 1.2).
- In-app purchases and subscriptions (product ids, what each unlocks).
- Every SDK and external service: auth, payments, analytics, crash reporting, ads, AI providers (name the model vendor), data APIs. Check Package.swift, Podfile, package.json, build.gradle, Info.plist, network calls.
- Anything switched on from a server, remote config or feature flags. Say so plainly; hidden server switches read as bait-and-switch (Guideline 2.5.19).
- Regional differences, or confirm none.
- Changes in this build (git log since the last tag or release), described specifically. Since October 16, 2026 Apple rejects generic descriptions of new features.

Ask the user only for: who it's for, the market gap with a dated competitor count, beta testing (build numbers, dates, feedback that changed the app), other apps on the account and how each differs, the company that publishes it, the app's own website (privacy, terms, support), a demo login, and a hosted screen recording link.

## Step 2: write it

Rules for every mode:
- Plain sentences, numbers over adjectives, dates in YYYY-MM-DD.
- Never paste the App Store marketing description (Apple's question 1 forbids it).
- Name every other app on the developer account and say in one line why it is different.
- List every SDK and service. Reviewers can see them; leaving one off looks worse.
- Offer proof: screen recording, sample files, demo account.
- No claims the user hasn't confirmed. Leave `[TO CONFIRM: ...]` instead.

### notes template
```
WHAT IT DOES
<2-3 sentences, the user problem and what the app does about it>

WHO IT'S FOR
<named groups>

HOW TO TEST
Demo login: <email> / <password> (kept active)
1. <step to reach main feature>
2. <step to reach paid feature> (sandbox purchase works / promo code: ...)
Account deletion: Settings > <path>
Report / block: <path>   (or: no user content)

NEW IN THIS VERSION
- <feature>: <where it is, what it does>

SERVICES
<auth, payments, analytics, AI provider + what it's used for>, nothing switched remotely after approval
Regional differences: none / <list>

OTHER APPS ON THIS ACCOUNT
<app>: <one line, how it differs>   (or: none)

WEBSITE
<domain> - privacy <url>, terms <url>, support <email on the app's own domain>

Screen recording (from launch, physical device, latest iOS): <link that needs no sign-in>
```

### answer-4.3 template
Open with one line: you don't think the app is spam or a template, and you'll answer each question directly. Then nine headed answers in Apple's order:
1. What it does 2. Who it's for 3. The gap (dated search, competitor count, ratings) 4. Beta testing (builds, dates, feedback applied) 5. Standalone or suite 6. In-app purchase in another app 7. Shared code with your other apps 8. Shared code with third parties 9. Made for a client.
Close by offering a screen recording or sample files. Reply in App Store Connect; don't resubmit unless something actually changed.

If the honest answer to 5, 6 or 7 is "yes, it overlaps", say so to the user before writing: the fix is product (merge it into the existing app as a feature, or make it different), not wording.

### packet-2.1 template
The six items Apple asks for: screen recording, purpose and audience, setup + credentials + sample files, every external service, regional differences, regulated-industry docs. Paste the same text in the Resolution Center reply and in the Notes field. Then: leave the submission alone, one status inquiry after two weeks at most, and hold other apps until this one is approved.

Recording shot list: start on the home screen of a physical device on the latest iOS, launch, sign up, log in, main feature, user content + report/block, purchase + unlocked content, delete account.

## Example
See `examples/backed-update.md` for a short real note that got an update approved in 1 minute.

## Step 3: pre-submit check
Full checklist and rejection map: `GUIDE.md`.
Print a pass/fail list: own website with privacy/terms/support linked in App Store Connect and in the app, support email on that domain, demo login tested today, account deletion, report/block, every SDK listed, recording link opens signed out, no more than a few similar apps on the account, new account = one app in review at a time.
