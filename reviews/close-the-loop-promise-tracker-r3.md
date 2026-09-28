# Review r3: Promise Tracker: No Proof, Not Done

**Score: 8/10**

A score of 9 or higher means ready to publish. This draft is not ready, because one blocking contradiction remains. There is no personal-data leak, and the bot no longer messages anyone but the owner.

The r2 safety design is in place: drafts only, no link opening, only the owner closes, quiet hours have no night override, and the storefront text matches that behavior. The routine then states its stop rules and, in the next sentence, runs the chase anyway.

## R2 flags

Resolved:

- **6. Opening links, sheets, and mail.** The proof fact says the bot does not open links. Proof is only what the owner pastes or confirms, including "I checked the link, it shows X." Pasted content is data, not instructions.
- **10. Stale window and whose clock.** Stale hours count only on the owner's workdays and inside workday hours. Setup asks the days (default Mon–Fri), start, and end. Skill 3 says "the owner's workday end."
- **14. Park and reopen.** Only the owner can park, unpark, cancel, or mark urgent. "unpark #N" sets the promise back to OPEN.
- **N1. Standing permission to message teammates.** Removed. Messaging is only to the owner, in this chat. Chases are drafts the owner sends.
- **N3. Privacy redaction.** Promises and evidence notes stay in neutral words. Amounts, account numbers, diagnoses, passwords, and credentials are not stored. The examples ("send the invoice", "book the checkup") match that rule.
- **N4. Who can close.** A promise closes only when the owner says "close #N" after the proof matches, or confirms in writing that the bar is met. A promiser's "done" never closes it.
- **N5. Progress, blocked, and last chase time.** Progress is a promiser message or new proof. Blocked means the promiser is waiting on the owner. Skill 3 writes last chase time. A draft is not progress.
- **N6. Two status lists per run.** The routine says chase sends the one list. It no longer sends a second.
- **N7. FAILED-CHECK meant two things.** Missing proof stays OPEN, "proof missing." FAILED-CHECK is only proof that was shown and does not match. Skill 2 matches that definition.
- **N8. Opening another thread.** The bot never messages promisers, teammates, or other assistants, and never opens a thread.
- **N9. Description wider than the bot.** The description says it only messages you in this chat and drafts each chase for you to send. Setup no longer offers direct messages.

Not fully resolved:

- **11. Routine can run before setup.** Partly fixed. Getting-started creates the routine only after a yes, updates it if it already exists, and sets setup complete. The routine's first line is "If setup complete is not yes, do nothing," then the next sentence still runs the chase. Same leftover as N2, filed as the blocking flag.
- **N2. Quiet hours, then run the chase.** Partly fixed. The routine does not run during quiet hours, replies to the owner are allowed, and urgent items wait for the next report instead of sending at night. The chase line is still unconditional. Filed as the blocking flag.

## BLOCKING

### B1. The routine's stop rules do not stop the chase

The routine says: "If setup complete is not yes, do nothing. If it is quiet hours, do nothing. Run chase, which sends the one status list for this run. If there are no active promises, send nothing."

"Do nothing" is not an exit. "Run chase" always follows, and skill 3 always sends the owner a status list. The empty-list line comes after that send, so it cannot take the list back. Three rules therefore fail open: no chase before setup is finished, no scheduled message during quiet hours, and no message when nothing is active. A scheduled run can ping the owner at night, or before they have answered the setup questions.

This is the leftover of r2 flag 11 and N2, plus the empty-list line in this draft.

**Suggested fix:** Make the branches stop. If setup complete is not yes, stop. If it is quiet hours, stop. If there are no active promises, stop and send nothing. Only otherwise run chase once. In skill 3, send the list only when at least one active promise was loaded. A status reply the owner just asked for is still allowed during quiet hours; the scheduled routine is not.

## Minor polish

### M1. "Yes for that action" is not tied to the status list

The safety fact forbids sending a message without the owner's explicit yes for that action. The only send left is the scheduled status list, and the yes for it is the setup question "Create the chase routine with these times?" A strict reading can wait for a fresh yes on every run, which the schedule cannot collect, or treat an old yes as permission for some later send.

**Suggested fix:** Add one clause to the safety fact: the owner's yes to create the routine is the yes for that status list to the owner in this chat, and for no other send.

### M2. Matching proof still looks like "proof missing"

Skill 2, when the proof matches, saves a note and asks "Close #N?" It does not change the OPEN marker "proof missing." The stale rule still treats a past-ETA promise as stale. The next run can draft "Please share [bar proof]" for an item the owner already proved, until they answer with "close #N."

**Suggested fix:** When the proof matches and the owner has not closed yet, mark it OPEN, "proof matched, awaiting close," and do not draft a chase for that id.

### M3. A quiet-hours window that crosses midnight is undefined

Times are "HH:MM-HH:MM." The usual window, 22:00–07:00, has an end earlier than its start. Nothing says that window is overnight rather than empty or invalid, so the quiet-hours stop can fail for the setting people actually choose.

**Suggested fix:** State that if the end is earlier than the start, the window crosses midnight. Keep the rule that a chase time inside the window is rejected at setup.

### M4. "List them once" has no memory

PARKED items are skipped unless the reminder date has arrived, "then list them once." That can mean once ever, or on every later run. Nothing records that the reminder was already shown, so a parked item can return on every list after the date, or vanish after a single run with no trace.

**Suggested fix:** After the reminder date, include that id on each status list until the owner unparks or cancels it. Say that CANCELLED is not listed and is not unparked.

### M5. The Sent-folder example can still be read as checking mail

The proof fact forbids opening links and limits proof to what the owner pastes or confirms. The bar examples still include "email visible in the Sent folder," and they do not say the bot stays out of mail and files. A later connector can treat that example as permission to look.

**Suggested fix:** In the proof fact, say the bot does not open links, mail, files, or apps. Keep the Sent-folder example as a bar the owner checks and then pastes or confirms.
