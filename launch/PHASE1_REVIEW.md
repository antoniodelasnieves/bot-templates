# Phase 1 gate review

Adversarial score of the 29 September 2026 polish against the six-point rubric in `launch/LAUNCH_PLAN_V2.md`. A pass is 9 or 10. A 9 needs all six points. This file scores and flags. It does not rewrite a template, publish, or post. The templates are free. No metrics are invented.

Reviewed: the four polished recipes (Promise Tracker, Daily Habit Check-in, Family Getaway Finder, Bot Team Health Check), the polish note, and the four diffs against the pre-polish drafts. Public name means the profile name and the storefront, not the file slug.

Scores:

- Promise Tracker: No Proof, Not Done: 8. Fail. Point 2.
- Daily Habit Check-in: 9. Pass.
- Family Getaway Finder: 9. Pass.
- Bot Team Health Check: 9. Pass.

Phase 1 gate: not passed. The gate needs all four at 9 or higher. This is the first fail for Promise Tracker, so that step returns once. Steps 2, 3 and 4 stay passed. Phase 2 does not start.

## 1. Promise Tracker: No Proof, Not Done. Score 8

Points: 1 pass, 2 fail, 3 pass, 4 pass, 5 pass, 6 pass. No personal identifiers.

The name matches the profile name, and the card does not say "deal" or promise a discount. The hello is the screenshot, about 60 words, and it says the bot only messages you and gives no medical, legal or financial advice. Questions are one ask each: timezone, workdays, then start and end together as the plan's third ask, with HH:MM and the examples 09:00 and 18:00. Quiet hours, the stale default of 2 hours, and the chase default of 12:30 and 17:00 are visible. The diff adds no send, spend, book, or outward message. A fake walk still reaches "Create the chase routine with these times?" The first sentence of the storefront is `"OK, on it" is not done.` That is the hook. It does not state the job. The job is sentence 2, and the safety limit is sentence 3, so the card is not empty, but point 2 requires the first sentence to state the job. Joining the hook and the job with a colon leaves the same opening clause, so that join does not pass. One replacement, the profile description only:

`I keep each promise open until you confirm proof that matches the bar, and I draft the chase for you to send. "OK, on it" is not done. I only message you, in this chat.`

## 2. Daily Habit Check-in. Score 9

Points: 1 pass, 2 pass, 3 pass, 4 pass, 5 pass, 6 pass. No personal identifiers.

The name matches. The first storefront sentence is the job, a one-minute daily check-in and a five-minute weekly review, and the card says it only messages you and gives no medical, mental-health, legal, tax, or financial advice. The hello fits one screen, states those limits, and does not include the crisis rules. Timezone and quiet hours are split. Quiet hours, the check-in time, and the weekly review each show HH:MM and one example, and the examples are labelled as not defaults. A skipped time is asked again. Question 5 asks for day and time as one schedule answer, the same pattern as a workday window, with one example (`Sunday 18:00`). That meets point 4. The new read-back and "Create the daily check-in and the weekly review with these times?" sit before routine creation. The pre-polish recipe created both routines with no yes. Point 5 forbids adding the power to send, spend, book, or message anyone else. This confirm removes an unconfirmed create. It does not add that power. Point 6 is met because the walk now reaches that yes. Keep the confirm.

## 3. Family Getaway Finder. Score 9

Points: 1 pass, 2 pass, 3 pass, 4 pass, 5 pass, 6 pass. No personal identifiers.

The public name is Family Getaway Finder, matching the profile name. The slug still contains "deal". The card does not. The card says it never promises a discount, which is a refusal, not a promise. The first sentence states the job: shortlisting family stays for weekends and 3 to 4 day breaks, free cancellation first. The card also says you book, and that the bot never books, reserves, holds or pays. The hello is short, includes "I never book or pay; you do." and the party-as-counts line, and has no hotel, price, or child's name. Quiet hours use HH:MM-HH:MM and the example 21:00-08:00. The diff does not add search, booking, or messaging power. This recipe creates no routine at setup. Reminders are created later, only after the owner has booked a stay themselves and shared it. Point 6 allows the confirm already in the recipe. That end point is "Any dates coming up you'd like me to look at?" A fake walk reaches it. Adding "Create the routine?" would invent a routine this template does not have. Point 6 is met. Do not add that question.

## 4. Bot Team Health Check. Score 9

Points: 1 pass, 2 pass, 3 pass, 4 pass, 5 pass, 6 pass. No personal identifiers.

The name matches. The first storefront sentence states the job, one numbered list of fixes, and the card says it does not edit, create, or remove another bot, and that sending, spending, posting, and deleting need a yes. The hello is the plan's two lines, states what it will not do, and puts `Say "get started".` on its own line. Nothing runs before that. There are still seven questions. Timezone is the only one with no default. Quiet hours show HH:MM-HH:MM and 22:00-07:00. Question 5 asks for frequency, day, and time as one schedule answer, with one example: `weekly, Monday 09:00`. The pre-polish question already asked those three together. Splitting it would make eight questions and make the hello false. One schedule slot is one thing under point 4, and the clock form is now on the question. The diff adds no power to edit another bot or to send, spend, post, or delete. The walk still reaches "Shall I create the checkup routine with these settings?" Keep question 5 as one ask.

## Identifiers

Searched the four recipes and the four diffs for names, towns, companies, emails, and handles (Antonio, Yerbabuena, Trust3, Madrid, Spain, an @ handle, an email). None are in the template text. "Deal" appears only in the family file slug. "Discount" appears only as "never promises a discount" or "never promises discounts." The polish note's fake answers (a city, a timezone, a sample bot name) are in that note, not in a recipe.

## Out of scope

A duplicated word in the health-check powers line ("read read-only") is pre-polish. It is not a rubric point and was not introduced by this diff. It does not change the score.
