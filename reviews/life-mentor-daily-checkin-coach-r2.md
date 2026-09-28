# Review r2: Daily Check-in Life Coach

## Overall score

**8 / 10**

Not ready to publish. A publishable template scores 9 or higher. This revision fixes the r1 ship-blockers: no named companion bots, no work/home memory bridge, no third-party weekly send, no income-growth pitch, no specialist bot standing in for a professional, one 90-day clock, one pair of question caps, and a storefront name and description that match the "this chat only" rule. What is left is smaller and still real. Crisis help still has no named crisis line and no path for a minor. Health still says "keeping appointments on the calendar" while privacy forbids appointment details. Money still includes "learning about money." The pause rule and the missed-check-in script disagree about whether a paused routine can speak. Those are text fixes, not a new design, which is why this is an 8 and not another 6. They are enough to hold it under 9.

Reviewed file: `templates/life-mentor-daily-checkin-coach.md`, replaced verbatim with the revised draft. The template was not rewritten.

## R1 flags

### Resolved

1. **Named companion bots.** Question 5 now says "another assistant" for appointments or paperwork, with no bot names.
2. **Work-bot / home-bot split.** That sentence is gone. Privacy now says not to import other tools or assistants unless the owner pastes into this chat.
3. **Third-party weekly send.** Question 6 and the summary recipient are gone. Safety, the label, and the weekly review all say this chat, owner only.
4. **Tracking how other people are doing.** The job fact now limits family to the owner's actions and time, and says the coach does not track other people. Skill 1 matches. The "each kid" example is gone.
6. **Specialist bot as a professional.** Out-of-lane advice is a qualified professional only. Question 5 does not hand topics off.
8. **Abuse and a child at risk left inside goal-setting.** The crisis fact now names abuse, violence, and a child at risk, and it says to stop coaching.
11. **Quiet hours losing to the clock.** "Quiet hours always win," a time inside them is not saved, and routines "never run during quiet hours."
13. **Replacing goals without a yes.** Skill 1 shows the current list and continues only on a clear yes to "Replace these with new goals?"
14. **"Template draft" title.** The H1 is the public name.
15. **Brace placeholders.** No `{your quiet hours}` or `{your timezone}` tokens.
16. **Weekly time never asked.** Question 3 asks for day and time, with a default, and the weekly schedule uses both.
18. **Evening check-in asked three things.** Evening mode is two quoted questions, and the two-question cap is repeated on the rhythm fact, the skill, and the routine.
19. **Goal count disagreed.** Structure and skill 1 both say one goal per area, and a second only if the owner asks, never more than two.
21. **Area labels disagreed.** The label, the job fact, and question 4 use the same four names.
22. **Profile vs log unexplained.** The first memory fact says profile rules do not change and log facts hold setup, goals, and progress.
23. **Slash name.** One name, "Daily Check-in Life Coach," in the H1 and the profile name.
24. **Description overclaimed "never sends" and omitted the weekly review.** The label now includes the weekly review, the full advice ban, and "only messages you, in this chat."

### Not resolved

5. **Money still teaches finance.** Income-growth is now banned, and so are investment ideas. The same job line adds "a saving routine, budgeting check-ins and learning about money." That is advice about how much to save, what to pay first, and which products to learn. The out-of-lane list covers tax and investment only, so a model can treat a budget lecture as in-lane. **Remaining fix:** Money habits are only the habit the owner already named, such as "review spending every Sunday." Do not teach saving rates, debt order, accounts, products, or courses. Do not judge a purchase, a debt, or a job move.

7. **Crisis handling is still incomplete.** The new rule does stop coaching, pauses routines, refuses to store the incident, and gives 112 and 911 as emergency examples. It still says "or a local crisis line" with no name. There is no 988 (call or text) for the United States and Canada. There is no line for an owner who may be under 18. It does not say to refuse methods, means, or plans. **Remaining fix:** Lead with "contact your local emergency number now." If they are in the United States or Canada, also say they can call or text 988. Do not present 112 and 911 as the only numbers. If they might be under 18, tell them to contact a trusted adult as well. Send only that help message: do not discuss methods, means, or plans, and do not problem-solve the crisis.

9. **Appointments still sit in the health job.** Stress and energy are gone, and the greeting now lists the same bans as the out-of-lane fact. Health habits still include "keeping appointments on the calendar." Privacy says never store appointment details, and safety says never book without a yes for that booking. A calendar entry is an appointment detail, and Plugins is None, so the bot cannot actually touch a calendar. **Remaining fix:** Cut calendar and appointment-keeping from the health area. Health goals are a sleep schedule, movement, or hydration target the owner chooses. Any reminder is a line in this chat with no clinic, clinician, place, or reason. Booking still needs a separate explicit yes, and this bot does not book.

10. **Silence, pause, and the control words still do not line up.** After three missed check-ins, skill 2 says "pause the daily routine and ask once." The pause fact says a paused routine "sends nothing" until the owner says "resume." Pausing first means the one question is never sent. "Switch to weekly" and "stop" are not defined, so weekly can keep firing after "stop." Getting-started never teaches the controls. **Remaining fix:** Send the one question, then pause the daily routine. No reply means stay paused and do not ask again. "Switch to weekly" pauses daily and leaves the weekly routine on. "Stop" pauses both routines and does not delete goals or routines. In the last line of getting-started, tell the owner: "You can say pause check-ins, resume daily, switch to weekly, change my time, or reset goals."

12. **Progress notes can still hold the banned details.** The privacy list now forbids sleep numbers, symptoms, stress levels, appointment details, diagnoses, and details about other people, and the example note is "done, short walk." Skill 2 still saves "a few neutral words" from the reply. "What got done today?" will often include a symptom, a mood, a name, or an amount, and nothing says to drop those words before saving. **Remaining fix:** A note is the habit name plus done or not done, nothing else. If the reply includes symptoms, mood, sleep numbers, amounts, balances, account data, or another person, do not write those words into the note.

17. **Default routines can still be armed on import.** Routines are "created only at the end of getting-started," which is the right rule, and delivery is this chat. The file still contains both routine blocks with "default 08:00" and "default Sunday 18:00." A host that schedules from the file will not obey the prose. Neither routine says "if the time is not saved yet, send nothing and continue getting-started." **Remaining fix:** On each routine, add that sentence. Remove the default clock times from the schedule lines. Keep 08:00 and Sunday 18:00 only as spoken fallbacks inside questions 2 and 3, after quiet hours are known.

20. **The goal is still called quarterly.** The clock is a 90-day cycle from the setup date in the structure fact, skill 1, skill 3, and the weekly routine. Skill 1 and the structure fact still say "quarterly goal," which readers take as a calendar quarter. **Remaining fix:** Replace "quarterly goal" with "90-day goal" in the structure fact and in skill 1. Do not use "quarter."

## New flags

### (a) Personal-data or identity leaks

No real name, town, email, phone, ID, company, client, bot name, or URL. One privacy hole remains.

25. **Family goals can still store other people.** Privacy says never store details about other people. The job example is "calling a relative or planning time together," so the saved goal will often be "call Sam on Sunday." That is another person's name in the log, and a later "what got done" note will collect how the call went. **Suggested fix:** Examples and saved goals name only the owner's time block, such as "Sunday 16:00 set aside for family." If the owner includes a name, do not write the name into goals, notes, or archives. Do not ask how the other person is.

### (b) Safety gaps

26. **Archived goals can never be deleted, even when the owner asks.** Skill 1 says to move replaced goals to the archived log and "never delete them." Safety says not to delete without an explicit yes for that action, which means a yes does allow a delete. An archive that cannot be removed will keep names, health habits, and money habits the owner wanted gone. **Suggested fix:** Archive on replace, after the replace yes. If the owner explicitly says to delete a named goal, note, or archive entry, delete that item only. "Never delete" should not override that yes.

27. **Question 5 invites a paste from another assistant.** It says the coach will not read the other assistant, and "if you want me to know something from it, just paste it here." It does not say what must not be pasted. Owners will paste health records, account numbers, and notes about other people, and the log will be tempted to keep them. **Suggested fix:** Add to question 5: "Do not paste health records, account numbers, IDs, balances, or anything about other people. A one-line habit is enough." If they paste those anyway, do not write them into memory; say you cannot store that and continue setup.

28. **"Resume" after a crisis is the same word as ordinary unpause.** Crisis pauses "all routines until the owner says to resume." The pause fact turns any "resume" back on. A later check-in reply of "resume" restarts habit coaching with no sign that the pause was a crisis pause, and the crisis rule's "not in that conversation" does not cover the next day. **Suggested fix:** Keep a crisis pause separate from an ordinary pause. Restart after a crisis only if the owner clearly asks to resume coaching. The first reply repeats the emergency-number nudge in one sentence and does not continue the crisis topic or the old goal talk. Ordinary "resume" must not clear a crisis pause.

29. **The bot can invent health targets.** Health habits include a sleep schedule and hydration. Nothing says the owner must choose the target. The model will fill in hours of sleep or glasses of water, which is medical advice under a habit label. Out-of-lane also says "coach only the habit side" of a medical or psychological topic, so a disclosed condition becomes a plan ("walk more for that"). **Suggested fix:** The owner states the habit and the target. Do not invent durations, amounts, or frequencies, and do not say whether a target is healthy. If the topic is medical, psychological, legal, tax, or investment, suggest a professional and do not design the habit from the disclosed condition. A habit continues only from a target the owner states without tying it to that condition.

### (c) Clarity and usability for a stranger

30. **The morning default is attached to evening review.** Question 2 asks for morning or evening, then "At what time? (Default 08:00.)" An owner who says "evening" and accepts the default gets an 08:00 evening review. Quiet hours will not catch that, because 08:00 is often outside them. **Suggested fix:** Default a morning check-in to 08:00 and an evening review to 21:00. Use only the default that matches the chosen mode, say that clock time back, and save it only after the owner confirms.

31. **Quiet hours and clock times have no required shape.** The quiet-hours test ("if a chosen time falls in quiet hours") needs two comparable clocks. The questions accept "mornings," "8," or "after work," and the log line does not say what was stored. Routines then cannot know whether they are inside quiet hours. **Suggested fix:** Save quiet hours as a start time and an end time, and save each routine as a weekday plus HH:MM, all in the owner's timezone. If a reply does not parse, ask again. Do not create routines until timezone, quiet hours, and both times parse. Store the setup date as that timezone's calendar date, and count the 90 days from that date.

32. **The greeting name does not match the profile name.** The H1 and profile name are "Daily Check-in Life Coach." The first spoken line is "I'm your daily check-in coach." A stranger cannot tell which string is the product. **Suggested fix:** Use "Daily Check-in Life Coach" in the greeting as well, unless the storefront name is changed (flag 33). Then use that exact string in the H1, the profile name, and the greeting.

### (d) Storefront appeal

33. **"Life Coach" overclaims the shelf.** "Daily Check-in Life Coach" is one name and it is readable, and it no longer looks like a path. "Life coach" is what people hire for therapy-adjacent and money advice, which this bot must refuse. The habits-only limit shows up only after the name. **Suggested fix:** Publish as "Daily Check-in Coach" or "Daily Habit Check-in." Keep the four area names in the description, not in a professional title.

34. **The label never says how long this takes.** Question 3 promises a 5-minute weekly review, and skill 2 says the daily check-in stays under a minute. The storefront label says "short" and nothing else, so a shopper cannot see the burden. The boundary sentence is now accurate; it does not need to get longer, but the cadence should be specific. **Suggested fix:** In the first sentence, state "about a minute each day and about five minutes once a week," using the same numbers as the skill and question 3.

35. **"Books" in the label is ambiguous.** "Never spends, books or sends anything for you" uses "books" as "makes a reservation." Next to a coach that talks about reading, it also reads as "does not use books" or as a missing word. **Suggested fix:** Write "never spends, makes reservations, or contacts anyone for you."
