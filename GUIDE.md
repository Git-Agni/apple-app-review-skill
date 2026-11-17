# How to avoid an App Store rejection (2026)

Everything we could find on getting an iOS app approved and keeping the developer account alive, in one file. Guideline numbers are from Apple's [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/), checked on 2026-11-17. Long version with screenshots: [annayal.com/blog/app-store-rejection](https://annayal.com/blog/app-store-rejection/).

- [How App Review actually works](#how-app-review-actually-works)
- [The rejection map](#the-rejection-map)
- [Guideline 4.3 spam and the 9 questions](#guideline-43-spam-and-the-9-questions)
- [Guideline 2.1: the new-account gate](#guideline-21-the-new-account-gate)
- [Section 3.2(f): account termination](#section-32f-account-termination)
- [Writing the Notes for Review](#writing-the-notes-for-review)
- [Pre-submit checklist](#pre-submit-checklist)
- [After a rejection: reply, resubmit or appeal](#after-a-rejection-reply-resubmit-or-appeal)
- [Sources](#sources)

## How App Review actually works

From Phillip Shoemaker, who ran App Review from 2009 to 2016 ([Substack](https://phillipshoemaker.substack.com/p/who-is-actually-reviewing-your-app)):

- A reviewer gets roughly **13 minutes for a new app and 6 for an update**, on an iPhone and an iPad, on the latest OS, under a quota.
- Most reviewers came from Apple retail. Teams are split by the app's **primary language**; every localization gets read.
- The reviewer sees **every previous rejection**, the earlier reviewer's notes and screenshots, and **every account linked to yours**. Once something is found, the next reviewer looks for it again.
- New reviewers look for reasons to reject. Experienced ones let minor issues pass. You can't pick, so leave nothing minor.
- Anything that can change after approval (server switches, remote flags, content loaded later) makes reviewers suspicious. Guideline 2.5.19 now bans hidden or dormant features outright.
- Shoemaker's estimate: about 15% of calls are wrong either way. Reduce how much depends on the reviewer's judgment.

Apple says 90% of submissions are handled within 48 hours. In the UK, Apple's commitments to the CMA promise 90% within 24 hours.

## The rejection map

| Guideline | What triggers it | How to avoid it |
|---|---|---|
| **2.1 App Completeness** | Crashes, placeholder text, broken links, login wall with no demo account, backend on staging or down | Test on a physical device. Demo account that never expires in the Sign-In fields. Backend live during review. Remove debug menus and test content |
| **2.1(b) In-app purchases** | A configured purchase the reviewer can't find or buy | Every IAP visible and working in sandbox. If one can't be reached, explain why in the notes |
| **2.3.1 Accurate metadata** | Features in the description or screenshots that aren't in the build. Generic notes for new features | Describe every new feature specifically in Notes for Review (generic descriptions are rejected) |
| **2.3.3 Screenshots** | Splash screens, login screens or title art as screenshots | Show the app in use |
| **2.3.7 Name and keywords** | Name over 30 characters, competitor names or trademarks in keywords, prices in the name | Unique name, honest keywords |
| **2.3.10 Platform focus** | Android or other store names and imagery in the app or listing | Keep everything about Apple platforms |
| **2.5.2 / 2.5.19 Code and hidden features** | Downloading code that changes features, dormant or undocumented features | Ship what you show. Declare anything remote-configured in the notes |
| **3.1.1 In-app purchase** | Unlocking digital content with license keys, QR codes, crypto or outside payment | Use In-App Purchase for digital goods |
| **3.1.2 Subscriptions** | Unclear price, period or what's included, subscriptions under 7 days, value that isn't ongoing | Show price, period and what the user gets on the paywall, plus restore and terms/privacy links |
| **3.2.2 Unacceptable business models** | Forcing ratings, reviews or downloads to unlock features | Never gate features behind a review |
| **4.1 Copycats** | Another app's name, icon, look or brand | Your own design and name |
| **4.2 Minimum functionality** | A thin web wrapper, a repackaged website | Native features a website can't do |
| **4.2.6 Template apps** | App built from a template or app generation service and submitted by the service, not the content owner | The content owner submits under their own account |
| **4.3 Spam** | Multiple bundle IDs of the same app, a copy of a crowded category, many near-identical apps on one account | One app with options instead of many apps. A real difference you can describe in numbers |
| **4.8 Login services** | Social login as the main account with no private-email option | Offer Sign in with Apple or an equivalent that limits data to name and email |
| **1.2 User-generated content** | UGC with no filter, report, block or published contact | Filter, report, block, and a contact in the app |
| **1.5 Developer info** | No working support contact | Support URL and email that work, on the app's own domain |
| **5.1.1 Privacy** | No privacy policy link in metadata and in the app, data collected without consent, data you don't need | Privacy policy in both places, consent, collect only what the feature needs |
| **5.1.1(v) Account deletion** | Account creation with no in-app deletion | Delete account inside the app |
| **5.1.2 Data use** | Undisclosed sharing, including with third-party AI. Tracking without ATT | Disclose every SDK and AI provider. Ask ATT before tracking |

## Guideline 4.3 spam and the 9 questions

Guideline 4.3 (Spam): "Don't create multiple Bundle IDs of the same app" (4.3(a)) and "Don't submit apps that are indistinguishable from what's already widely available" (4.3(b)). In 2026 it often arrives together with 4.2.6 (App Generation Services).

The letter gives you two paths. If the description applies, make significant changes before resubmitting. If you believe the app already meets 4.3(a), 4.3(b) and 4.2.6, **do not resubmit**. Reply to the message and answer all of these in full:

1. Describe in detail what this app does and the primary problem it solves for users. Do not use the App Store marketing description as your response.
2. Who is the intended user of this app? Provide a detailed description of the specific target audience.
3. What need or gap in the market does this app address that existing apps do not currently address, or address less effectively?
4. What beta testing did you conduct before submitting? Provide examples of user feedback from beta that was applied to the production build.
5. Is this app a standalone product, or part of a suite of related apps under your developer account? If part of a suite, how does its scope differ from each other app?
6. Could this functionality be delivered as an in-app purchase, feature expansion, or content addition within another app on your account? If so, why wasn't it consolidated?
7. Does the binary share significant code, frameworks, or assets with any other app on your account, beyond standard third-party frameworks? Identify each shared component.
8. Does it share any codebase, SDK, or content library with any third-party app, beyond standard frameworks? Identify it and the original functionality this app adds.
9. Was this app created for a client, partner, or third party who provided the content, concept, or branding? If so, why is it submitted under your account rather than theirs?

How to answer (from [Rasty Turek's approved reply](https://x.com/synopsi/status/2122380692747411566)):
- Plain explanation of the user problem, with outside proof (press links), not store copy.
- Named user groups.
- The gap with a date and a count ("I searched the US App Store on 2026-11-13 and found ten; the biggest has 14 ratings").
- Beta testing with build numbers, dates and the specific changes feedback caused.
- Name every app on the account and say in one line how each differs.
- State your frameworks and SDKs honestly. Say who wrote the core logic.
- Say who owns it and which company publishes it.
- Offer a screen recording or sample files.

If the honest answer to 5, 6 or 7 is "yes, it overlaps", the fix is product, not wording: merge it into the existing app or make it genuinely different.

Shoemaker on the threshold: reviewers were trained to flag a developer at **9 similar apps; at 10 the door closed** ([post](https://x.com/pbsIdentity/status/2048794298955501805)). It was never written into 4.3.

## Guideline 2.1: the new-account gate

New accounts can get a 2.1 Information Needed notice that opens with "This app has been submitted by a developer account that has a limited App Review history." It asks for:

1. A screen recording on a physical device, latest OS, from launch: sign up, login, account deletion, UGC reporting and blocking, paid content.
2. The app's purpose, audience, problem and value.
3. Setup instructions, login credentials, sample files.
4. Every external service: data providers, auth, payments, AI services.
5. Regional differences, or a statement that there are none.
6. Documentation for regulated industries or protected third-party material.

Send it before you're asked: put the full packet in the Notes field of your first submission. Host the recording on a link that opens signed out. After replying, leave the submission alone; one status inquiry after two weeks at most. **Hold your other apps until the first one is approved**, because several pending apps from a new account reads as volume. ([Shoemaker](https://phillipshoemaker.substack.com/p/prove-yourself-first))

## Section 3.2(f): account termination

Section 3.2(f) of the Apple Developer Program License Agreement lets Apple terminate an account for "a pattern of manipulative or misleading behavior". Every app comes down. Shoemaker reports App Review issuing these since mid-2026 for submission behavior, not only fraud: too many submissions, too many app name changes, repeated 1.1 rejections ([Substack](https://phillipshoemaker.substack.com/p/apple-approved-the-fix-then-it-called)).

Prevention:
- Treat every submission as having a cost. Don't fire off rapid resubmissions to test a reviewer.
- Don't rename apps repeatedly.
- After a content rejection (1.1, 1.2), fix the cause fully, including what a prompt or server could still produce, and say exactly what you changed.
- Never hide features behind server switches.
- Keep every rejection, every reply and screenshots outside App Store Connect.

Appeal: Apple expects an apology where something was wrong, an explanation of how it happened, and a plan to prevent it, in that order.

## Writing the Notes for Review

Apple's rules for the field: up to **4,000 bytes**, any language. New features described with specificity (2.3.1(a)). Demo account in the Sign-In fields must not expire; extra accounts go in Notes. Explain non-obvious features and in-app purchases. If an IAP can't be reviewed, say why (2.1(b)).

Use [`SKILL.md`](SKILL.md) to generate them from your code, or the template in it by hand. A real 615-character example that got an update approved in 1 minute: [`examples/backed-update.md`](examples/backed-update.md).

## Pre-submit checklist

**Every submission**
- [ ] Tested on a physical device, latest iOS, no crashes, no placeholder text, no debug menus
- [ ] Backend points at production and stays live during review
- [ ] Demo account in Sign-In fields works today and won't expire
- [ ] Notes for Review: what it does, how to test step by step, every new feature specifically, every outside service, under 4,000 bytes
- [ ] Every in-app purchase visible and buyable in sandbox; paywall shows price, period, what's included, restore, terms and privacy
- [ ] Privacy policy linked in App Store Connect and inside the app; privacy labels match every SDK
- [ ] Account deletion in the app (if accounts exist)
- [ ] Report, block and filter (if user content exists)
- [ ] Screenshots show the app in use; description matches the build
- [ ] No other platform names, no competitor names in keywords

**New app or new account, also**
- [ ] The app has its own website with privacy, terms and support, linked in App Store Connect and in the app
- [ ] Support email on that domain
- [ ] Screen recording from launch on a real device, link opens signed out
- [ ] 2.1 packet already in the notes
- [ ] Only one app in review from this account
- [ ] You can answer all 9 4.3 questions with numbers before you submit

## After a rejection: reply, resubmit or appeal

1. Read the whole message. If it says reply instead of resubmit, reply.
2. Resubmitting the same build unchanged adds a rejection to your history.
3. If you fix something, resubmit with a note that says exactly what changed and where.
4. If you disagree after replying, appeal to the App Review Board from the Contact Us form in App Store Connect.
5. Save everything.

## Sources

- Apple, [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/) and [App Review Information](https://developer.apple.com/help/app-store-connect/reference/app-review-information/)
- Phillip Shoemaker (ran App Review 2009-2016): [X](https://x.com/pbsIdentity), [Substack](https://phillipshoemaker.substack.com)
- Rasty Turek's public 4.3 rejection and approved reply: [X](https://x.com/synopsi/status/2122380692747411566)
- An Nayal's two approvals and the Backed notes: [annayal.com/blog/app-store-rejection](https://annayal.com/blog/app-store-rejection/)
- Scanners that pair well with this: [app-store-preflight-skills](https://github.com/truongduy2611/app-store-preflight-skills), [app-store-compliance](https://github.com/mjmirza/app-store-compliance)
