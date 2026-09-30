# Phase 1 gate review, second opinion (Claude Opus 5.5)

Independent review of the four recipes as of 30 September 2026, against the six-point rubric in `launch/LAUNCH_PLAN_V2.md`, plus the checks a stranger importing the template would make. Pass is 9 or higher. I read the recipes fresh and did not use the earlier scores in `launch/PHASE1_REVIEW.md`.

This file scores and flags. It does not change a template or a live bot, publish, or post. The templates are free. No metrics are used.

Checked against the 29 September versions: the only change is the Promise Tracker storefront (the hook moved to sentence 2). The other three recipes are byte-identical. No real names, towns, companies, emails, handles or URLs appear in any recipe. All four files are plain ASCII.

## Scores

- Promise Tracker: No Proof, Not Done: 9. Pass.
- Daily Habit Check-in: 9. Pass.
- Family Getaway Finder: 9. Pass.
- Bot Team Health Check: 9. Pass.

All four meet all six rubric points, so the Phase 1 gate can close once Antonio accepts the wording. None is a 10. Each has at least one issue a stranger would hit that the rubric does not test.

Fix before Phase 2 (my recommendation, not a rubric fail):

- Promise Tracker issues 1 and 2
- Habit Check-in issues 1 and 2
- Family Getaway Finder issue 1
- Health Check issue 1

These close a contradiction between the card and the rules, or an undefined skip. They are wording only and add no power. They narrow what the bot may do, so they do not reopen the rubric. Everything else is optional polish.

---

## 1. Promise Tracker: No Proof, Not Done. Score 9

Rubric: 1 pass, 2 pass, 3 pass, 4 pass, 5 pass, 6 pass.

The new first sentence states the job, so point 2 now passes. The card still has a safety limit ("I only message you"). The hello fits one screen and ends on the first question, which is the best opening in the set. Setup asks one thing at a time. Every clock question shows HH:MM with an example or a default. A fake walk reaches "Create the chase routine with these times?", and that routine is the only thing created. A stranger still hits four problems. "The bar" and "the chase" are undefined. The card does not say whose promises. The Safety line lets a yes unlock messages to other people, which contradicts both the card and the Messaging rule. Skipping the timezone, the workday hours or the quiet hours has no defined behavior, and the chase routine cannot run without them.

Issues, highest impact first:

1. Safety contradicts Messaging and the card. Messaging says the bot never messages promisers. Safety says it may with the owner's yes. A model can resolve this toward sending the chase itself.
   - Current: `- (profile) Safety: the setup yes covers only the scheduled status list to the owner. Never spend, buy, post, delete anything, or send any message to anyone else without the owner's explicit yes for that specific send or action. The bot never does the promised work and never invents a status.`
   - Replace: `- (profile) Safety: the setup yes covers only the scheduled status list to the owner. Never send a message to anyone but the owner, even with a yes; the owner sends every chase. Never spend, buy, post or delete anything without the owner's explicit yes for that specific action. The bot never does the promised work and never invents a status.`

2. Questions 2, 4 and 5 have no default and no skip rule.
   - Current: `If the owner skips question 3, 6 or 8, use its default.`
   - Replace: `If the owner skips question 3, 6 or 8, use its default. If the owner skips question 1 or 7, save none. Questions 2, 4 and 5 have no default: if one is skipped, say "I need this one before I can schedule anything." and ask again.`

3. The card uses in-product words ("the bar", "the chase") and does not say whose promises.
   - Current: `I keep each promise open until you confirm proof that matches the bar, and I draft the chase for you to send. "OK, on it" is not done. I only message you, in this chat.`
   - Replace: `I track the promises your assistants and teammates make, and keep each one open until you confirm proof that it is really done. I draft the follow-up for you to send. "OK, on it" is not done. I only message you, never them.`

4. Privacy mismatch. Setup asks for promisers by role, but the log confirm prints `[name]`, and nothing stops a person's name being stored.
   - Current: `- (profile) Neutral words: store promises and evidence notes in neutral words (for example "send the invoice", "book the checkup"). Never store amounts, account numbers, diagnoses, passwords or credentials.`
   - Replace: `- (profile) Neutral words: store promises and evidence notes in neutral words (for example "send the invoice", "book the checkup"). Store each promiser by role or bot name, not by a person's name. Never store amounts, account numbers, diagnoses, passwords or credentials.`
   - Current: `Confirm in one line: "#[ID] OPEN, promiser: [name], bar: [bar], ETA: [time]."`
   - Replace: `Confirm in one line: "#[ID] OPEN, promiser: [role or bot name], bar: [bar], ETA: [time]."`

5. The hello has a clunky clause ("promises you ask me to track open") and an off-lane advice line. It also says "a few" for eight questions. The advice rule stays in memory under Out of lane.
   - Current: `"Hi, I'm Promise Tracker. I keep the promises you ask me to track open until you confirm proof, and I draft chases for you to send. I only message you, here. I don't give medical, legal or financial advice. A few quick questions, one at a time.`
     `First question: Who makes promises I should track? Please list the assistants and teammates by role."`
   - Replace: `"Hi, I'm Promise Tracker. I track the promises you give me and keep each one open until you confirm proof. I draft follow-ups for you to send. I only message you, never the people or assistants I track. Eight quick questions, one at a time.`
     `First question: Who makes promises I should track? List the assistants and teammates by role, for example 'my designer'."`
   - Current: `1. "Who makes promises I should track? Please list the assistants and teammates by role." (Asked in the hello. Do not repeat it.)`
   - Replace: `1. "Who makes promises I should track? List the assistants and teammates by role, for example 'my designer'." (Asked in the hello. Do not repeat it.)`

6. "Run the chase" is internal jargon.
   - Current: `8. "What times should I run the chase on workdays, as HH:MM? The default is 12:30 and 17:00."`
   - Replace: `8. "At what times on workdays should I send you the status list and drafted follow-ups, as HH:MM? The default is 12:30 and 17:00."`

7. The confirm step has no read-back, unlike the other two confirms, and a default chase time can fall outside a short workday.
   - Current: `If a chase time falls in quiet hours, ask for a new one. Save the answers, set last ID used to 0, then ask: "Create the chase routine with these times?"`
   - Replace: `If a chase time falls in quiet hours or outside the workday, ask for a new one. Save the answers, set last ID used to 0, read back the workdays, workday hours, quiet hours and chase times, then ask: "Create the chase routine with these times?"`

---

## 2. Daily Habit Check-in. Score 9

Rubric: 1 pass, 2 pass, 3 pass, 4 pass, 5 pass, 6 pass.

The hello is warm, fits one screen, and states the advice limit and the only-you rule. Crisis text stays out of the screenshot. Setup is one ask per question, and every clock time shows HH:MM and an example. The examples are labelled as not defaults, and the confirm reads back exactly the two routines it creates. The crisis rule itself is sound. It has specific triggers, pauses all routines, saves no details, never discusses methods, gives a minor-specific line, and ends only on "resume coaching" after a safety question. The gaps are these. Safety says a yes can unlock messaging other people, but the card says "I only message you". A skipped timezone has no rule. The setup line that introduces "crisis pause" is the first time the user hears the word, and it reads awkwardly. "Each with a narrow limit" means nothing to a stranger. "Evening review" is easy to confuse with "weekly review".

Issues, highest impact first:

1. Safety allows messaging others with a yes, which contradicts the card and the first clause of the same line.
   - Current: `- (profile) Safety: message only the owner, in this chat. Never spend money, make reservations, send messages to anyone else, or delete anything without the owner's explicit yes for that action.`
   - Replace: `- (profile) Safety: message only the owner, in this chat, and never anyone else, even with a yes. Never spend money, make reservations or delete anything without the owner's explicit yes for that action.`

2. A skipped timezone is not covered, and every routine depends on it.
   - Current: `If the owner skips a time or the quiet hours, say "No time is preset, so I need one from you." and ask again.`
   - Replace: `If the owner skips the timezone, a time or the quiet hours, say "Nothing is preset, so I need this one from you." and ask again.`

3. Controls line: "crisis pause" arrives undefined, and "works, after I ask if you are safe" is awkward.
   - Current: `Then say: "You can say pause, resume, weekly only or stop at any time. Plain 'resume' restarts only after a normal pause. After a crisis pause, only 'resume coaching' works, after I ask if you are safe."`
   - Replace: `Then say: "You can say pause, resume, weekly only or stop at any time. If I ever pause for your safety, only 'resume coaching' restarts me, and I will ask if you are safe first."`

4. The card's first sentence has no verb and does not say "habits". "Each with a narrow limit" is opaque.
   - Current: `A one-minute daily check-in and a five-minute weekly review. Areas: health habits, career and learning, family and relationships, and money habits, each with a narrow limit. I only message you, and I do not give medical, mental-health, legal, tax, or financial advice.`
   - Replace: `A one-minute daily check-in and a five-minute weekly review that help you keep a few small habits. Pick from four areas: health habits, career and learning, family and relationships, and money habits. I only message you, and I do not give medical, mental-health, legal, tax, or financial advice.`

5. "Evening review" versus "weekly review" can be confused.
   - Current: `3. "Do you want a morning plan check-in or an evening review?"`
   - Replace: `3. "Should your daily check-in be in the morning, to plan the day, or in the evening, to look back on it?"`
   - Current: `(If the owner chose the evening review, use the example 21:00 instead.)`
   - Replace: `(If the owner chose the evening, use the example 21:00 instead.)`

6. The crisis number list runs regions together, and it does not lead with "if you are in danger now". Same numbers, clearer order.
   - Current: `Urge them to contact emergency services or a crisis line, for example 112 in the EU, 911 in the US, or call or text 988 in the US and Canada, or your local emergency number.`
   - Replace: `Urge them to contact emergency services now if they are in danger: their local emergency number, for example 112 in the EU or 911 in the US and Canada. For suicidal thoughts in the US or Canada, they can also call or text 988.`

7. Question 5 reads as translated ("Time as HH:MM, for example Sunday 18:00").
   - Current: `5. "Which day and time for the weekly review? Time as HH:MM, for example Sunday 18:00."`
   - Replace: `5. "Which day and time should the weekly review be, with the time as HH:MM? For example Sunday 18:00."`

8. Question 6 does not say more than one area is allowed.
   - Current: `6. "Which areas do you want to work on: Health habits, Career and learning, Family and relationships, Money habits?"`
   - Replace: `6. "Which areas do you want to work on? Pick one or more: Health habits, Career and learning, Family and relationships, Money habits."`

9. Optional: the hello ends without a question, so the screenshot has no next step. Promise Tracker's pattern converts better (opinion).
   - Current (end of hello): `A few quick questions, one at a time."`
   - Replace: `Six quick questions, one at a time.` followed by a new line `First question: What's your timezone?"`
   - Current: `1. "What's your timezone?"`
   - Replace: `1. "What's your timezone?" (Asked in the hello. Do not repeat it.)`

---

## 3. Family Getaway Finder. Score 9

Rubric: 1 pass, 2 pass, 3 pass, 4 pass, 5 pass, 6 pass.

The public name has no "deal". The card and hello both carry the booking refusal, and the card says it never promises a discount. The hello is short and fits one screen. Its six-question count matches the skill and the memory ("six answers"). Point 6 is met because this recipe creates no routine at setup. The walk ends at "Any dates coming up you'd like me to look at?", and asking to create a routine would invent one. Privacy is the strongest in the set: counts only, no ages saved, no nationality, and pasted confirmations are stripped. The gaps are wording. Only question 6 has a default, and nothing says what to do if another answer is skipped, yet search waits for all six. Question 6 reads backwards. "The party" and "3 to 4 day breaks" read as translated. "Free cancellation first" suggests a sort order, but the rule filters: non-refundable rates appear only when the owner asks.

Issues, highest impact first:

1. There is no skip rule for questions 1 to 5, and the memory says search starts only once all six answers are saved.
   - Current: `Save the answers in the settings log. Booking sites, travel time, event trips and the weekly scan are asked later, only when they come up.`
   - Replace: `Only question 6 has a default. If the owner skips any other question, say "I need this one before I can search." and ask again. Save the answers in the settings log. Booking sites, travel time, event trips and the weekly scan are asked later, only when they come up.`

2. Question 6 is hard to parse ("how close ... at least 7 days before").
   - Current: `6. "How close to arrival do you want to be able to cancel for free? The default is at least 7 days before."`
   - Replace: `6. "How many days before arrival should you still be able to cancel for free? The default is 7 days."`

3. The hello says "the party" and "free cancellation first".
   - Current: `"Hi, I'm your Family Getaway Finder. I shortlist family breaks, free cancellation first. I never book or pay; you do. I store the party as counts of adults and children, not names. Six quick questions, one at a time."`
   - Replace: `"Hi, I'm your Family Getaway Finder. I shortlist family stays with free cancellation. I never book or pay; you do. For your family, I save only how many adults and children travel, never names. Six quick questions, one at a time."`

4. The card's first sentence is long, and "optional trips around kids' sports events" is unclear.
   - Current: `Shortlists a few family stays for weekends and 3 to 4 day breaks, with free cancellation first and optional trips around kids' sports events. You book every stay yourself. This bot only shortlists and never books, reserves, holds or pays. It never promises a discount.`
   - Replace: `Shortlists a few family stays with free cancellation for weekends and 3- or 4-day breaks, and can plan around a kids' sports event if you ask. You book every stay yourself: it never books, reserves, holds or pays. It never promises a discount.`

5. Question 1 stores a home location. Say that a coarse answer is fine.
   - Current: `1. "Which city or region do you usually start from?"`
   - Replace: `1. "Which city or region do you usually start from? A nearby city is enough."`

6. Optional: add a first question to the hello (same pattern as Habit issue 9): `First question: Which city or region do you usually start from?`, plus `(Asked in the hello. Do not repeat it.)` on question 1.

---

## 4. Bot Team Health Check. Score 9

Rubric: 1 pass, 2 pass, 3 pass, 4 pass, 5 pass, 6 pass.

The card's first sentence is the job, and it has a safety limit. The hello is two lines, fits one screen, and keeps the "say get started" gate. "Seven questions" and "timezone is the only one with no default" both match the skill exactly, and so does every stated default. The confirm, "Shall I create the checkup routine with these settings?", matches the one routine it creates. Question 5 packs frequency, day and time into one answer, with one example and one default. I accept that as one scheduling decision; splitting it would make the hello's count false. The main problem is how a stranger reads the card and hello. "Sending, spending, posting, and deleting need your yes" and "I never ... spend, delete ... without your yes" both imply this bot can do those things once you agree. Its Safety fact says it never does them at all. The second hello line is a fragment.

Issues, highest impact first:

1. The card and hello imply powers the bot does not have.
   - Current (card): `Reviews how your Grok Bot assistants are set up and returns one numbered list of fixes. It does not edit, create, or remove another bot. Sending, spending, posting, and deleting need your yes.`
   - Replace (card): `Reviews how your Grok Bot assistants are set up and returns one numbered list of fixes. It never edits, creates, or removes another bot, and never spends, posts, emails, or deletes anything. Every fix waits for your yes.`
   - Current (hello line 1): `Hi, I'm your bot team health checker. I review how your assistants are set up. I never edit another bot, and I never send, post, email, spend, delete, or create or remove a bot without your yes.`
   - Replace (hello line 1): `Hi, I'm your bot team health checker. I review how your assistants are set up and suggest fixes. I never edit, create, or remove another bot, and I never spend, post, email, or delete anything. Every fix waits for your yes.`

2. The second hello line is a fragment.
   - Current: `Say "get started". Then seven questions, one at a time. Timezone is the only one with no default.`
   - Replace: `Say "get started" and I'll ask seven quick questions, one at a time. Only the timezone has no default.`

3. "Read read-only" appears twice and reads as a typo.
   - Current: `it works only with text the owner pastes or text it can read read-only.`
   - Replace: `it works only with text the owner pastes or text it can open read-only.`
   - Current: `Use each bot's text as pasted by the owner or read read-only.`
   - Replace: `Use each bot's text as pasted by the owner or opened read-only.`

4. The Privacy rule covers patches and reports, not pasted bot text that is saved to the roster.
   - Current: `- (log) Roster, report recipient, timezone, quiet hours, cadence, checkup time, healthy-desk choice and separate lanes are saved here during getting-started.`
   - Replace: `- (log) Roster, report recipient, timezone, quiet hours, cadence, checkup time, healthy-desk choice and separate lanes are saved here during getting-started. Before saving any pasted bot text, apply the Privacy rule to it.`

No change proposed for question 5.

---

## Across the set (opinion, no change required)

- The cards mix voices: Promise and Habit say "I", Family says "This bot" and "it", and Health says "It". The replacements above keep each card's voice. A single voice would read more like one family of templates.
- Promise Tracker's acceptance-bar example mentions opening mail if the owner connected it, while Plugins is None. It is conditional and adds no power. Leave it.
- Spelling is mixed British and US ("Summarise", "travellers", "breaks"). That is not an error. Pick one before the storefront copy is final if Antonio cares.
