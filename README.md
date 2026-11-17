# app-review-notes

A free Claude Code skill that fills the App Store Connect **Notes for Review** so the reviewer never has to guess, answers Apple's **9 questions** after a Guideline 4.3 / 4.2.6 rejection, and builds the **Guideline 2.1** packet new developer accounts now get asked for.

It reads your app's code first (screens, purchases, account deletion, every SDK and AI service), then asks you only for what code can't tell it.

Why it exists: [App Store rejection: the 9 questions Apple asks, and the answers that got apps approved](https://annayal.com/blog/app-store-rejection/).

## Install

```bash
mkdir -p ~/.claude/skills/app-review-notes && curl -sL https://raw.githubusercontent.com/Git-Agni/app-review-notes/main/SKILL.md -o ~/.claude/skills/app-review-notes/SKILL.md
```

## Use

In your app's repo, ask Claude Code:
- "write my App Review notes for this update"
- "Apple rejected us under 4.3, here's the message, answer the 9 questions"
- "we got the limited App Review history notice, build the packet"

It drafts. You check every claim before pasting it into App Store Connect.

Made by [An Nayal](https://annayal.com). Sources: Phillip Shoemaker's [Substack](https://phillipshoemaker.substack.com), Rasty Turek's [public reply](https://x.com/synopsi/status/2122380692747411566), Apple's [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/).
