# Review r3: Daily Habit Check-in

## Overall score

**8 / 10**

Not ready to publish. A publishable template scores 9 or higher, and this round would clear that bar if it had no blocking flag. The draft is now one product: the name, greeting, and label agree; the 90-day clock is the only clock; health, money, notes, archives, quiet-hour format, and routine defaults match the rules around them. No real name, place, email, phone, ID, company, client, bot name, or URL is in the file. One safety contradiction is still on the page. The controls taught at setup restart every routine on the word "resume," and the crisis rule restarts only on the exact phrase "resume coaching," which the crisis message never tells the owner. That is a real safety gap, so the score stays under 9. The other leftovers are polish.

Reviewed file: `templates/life-mentor-daily-checkin-coach.md`, replaced verbatim with the revised draft. The template was not rewritten.

## R2 flags

### Resolved

5. **Money advice.** The job is limited to noticing spending and a check-in on the owner's own plan. The limits fact forbids rates, debt, products, investments, and building a financial plan.
7. **Crisis script content.** The rule stops coaching, pauses routines, saves nothing, refuses methods and plans, names 988, points at local emergency services, and tells a minor to contact a trusted adult. Wording nits are minor flag 3 below, not an open hole in the script.
9. **Appointments and calendar.** Health is sleep schedule, movement, and hydration only.
10. **Missed check-ins and ordinary controls.** The nudge is sent, then the routine pauses. "pause," "resume," "weekly only," and "stop" are defined. Getting-started tells the owner those words. "stop" keeps saved goals unless the owner asks to delete them.
12. **Progress notes.** A note is only "done" or "not done" plus the habit name. Nothing from the reply text is saved.
17. **Default clocks on import.** The routine section says no routine exists until setup finishes, and no default clock ships.
20. **"Quarterly."** Goals and the cycle are 90 days from the setup date. The word quarterly is gone.
25. **Family examples.** Examples are a phone-free dinner and Sunday family time. Privacy forbids storing other people's names. The goal-wording residual is minor flag 1.
26. **Archives.** Replaced goals are archived, and they are deleted only if the owner asks.
27. **Paste prompt.** The other-assistant paste question is gone.
29. **Invented health targets.** The bot may not suggest numeric health targets, and it may not build a plan around a condition, symptom, or medication.
30. **Evening default of 08:00.** There is no default clock. The owner gives the time as HH:MM.
31. **Time shape.** Profile and questions require 24-hour HH:MM and quiet hours as HH:MM-HH:MM. The setup date is the owner's local date. Parse and overnight leftovers are minor flag 4.
32. **Greeting name.** The greeting is "I'm Daily Habit Check-in," matching the H1 and the profile name.
33. **"Life Coach."** The public name is Daily Habit Check-in.
34. **Time cost on the shelf.** The label says a one-minute daily check-in and a five-minute weekly review.
35. **"Books."** The label says "makes reservations," not "books."

### Not resolved

28. **Crisis restart still uses a different word from ordinary "resume."** See blocking flag 1. The special phrase exists, and it is still contradicted by the control the owner is taught.

## Blocking

1. **"resume" restarts coaching after a crisis.** The controls fact says the owner can say "resume" at any time and routines then run again. Getting-started teaches that word. The crisis fact says routines resume only when the owner writes exactly "resume coaching," then the bot asks whether they are safe. The crisis message never tells them that phrase. Two failures follow from the same lines. If the controls win, the word they were taught restarts habit coaching with no safety check. If the crisis line wins, "resume" does nothing and they are not told the only phrase that works. "Are you safe now?" also has no branch: a "no," or a new mention of danger, is not sent back through the crisis script. **Suggested fix:** In the controls fact, state that "resume" does not clear a crisis pause. In the crisis message, include one line: the bot will stay quiet until they send a message that only asks to resume coaching. On that message, ask whether they are safe now. If they say yes, start the routines again and do not return to the crisis topic. If they say no, or describe danger, stay paused and repeat only the emergency and crisis-line message. Do not treat the single word "resume" as that request.

## Minor polish

1. **Goals can still copy a name or an amount.** Skill 1 saves a goal "in their own words and numbers." Privacy says never store other people's names or amounts. Notes already drop the reply text; goals and archives do not. **Suggested fix:** Before saving or archiving a goal, drop other people's names and any amounts. Keep the habit. Do not ask who the other person is.

2. **The label fights the daily check-in.** It says the bot never "sends messages ... without your yes," and it also messages the owner every day. The safety fact already says to message only the owner in this chat and not to message anyone else. **Suggested fix:** In the label, say it only messages the owner in this chat, and that it never spends, makes reservations, messages anyone else, or deletes anything without a yes for that action.

3. **Emergency numbers can be read as a closed list.** The crisis line says "local emergency services (112 in the EU, 911 in the US)" and "988 in the US, or the local equivalent." The parentheses do not say "for example," and Canada is left off 988 even though that is the Canadian line too. **Suggested fix:** Say "your local emergency number, for example 112 in the EU or 911 in the US," and "call or text 988 in the US and Canada, or your local crisis line."

4. **A bad clock still becomes a routine, and overnight quiet hours are undefined.** The questions demand HH:MM, but they do not say to reject "evenings" or "8" and ask again, or to wait until timezone, quiet hours, and both times all parse before creating routines. A range such as 22:00-07:00 is the usual quiet-hours case, and nothing says it runs across midnight. **Suggested fix:** If a reply does not parse, ask again and do not create routines. Treat a quiet-hours start later than its end as overnight.

5. **The missed-check-in menu does not use the control words, and "stop" plus "resume" is unspoken.** The nudge offers "switch to weekly only," while the control is "weekly only," and it offers "resume" before a pause exists. Skill 2 then pauses "until the owner answers," so an off-menu reply can end the pause and bring daily messages back. "stop" removes routines; "resume" says they run at the saved times, but never says a removed routine is recreated from the log. **Suggested fix:** Use only the exact words "resume," "weekly only," "pause," and "stop" in that one message. If the reply is none of those, stay paused and do not ask again. State that "resume" after "stop" recreates both routines from the saved times and does not delete goals.
