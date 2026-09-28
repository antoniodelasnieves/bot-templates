# Review r2: Promise Tracker: No Proof, Not Done

**Score: 7/10**

A score of 9 or higher means ready to publish. This draft is not ready.

Fourteen of the eighteen r1 flags are fixed, including the term split, the status model, setup questions, ID memory, medical refusal, and the storefront name and opening line. Four r1 flags are only partly fixed, and the new text adds contradictions of its own: quiet hours both forbid sending and then run the chase, and the safety line demands a yes for each send while setup can grant a standing permission to message teammates.

## R1 flags

### Resolved

1. **Chase sends to people the setup never allowed.** Resolved. Skill 3 and the routine draft chases to people, and they send only if the owner enabled direct messages in setup. A new conflict between that standing permission and the per-action safety line is filed below as a new flag.
2. **The promiser can agree a bar that is just an acknowledgment.** Resolved. An acknowledgment is never a bar, only the owner's written confirmation qualifies, and a missing bar needs the owner's agreement.
3. **Anyone can mark an item urgent.** Resolved. The quiet-hours fact and the routine allow an urgent send only when the owner marked that item.
4. **The routine never checks quiet hours.** Resolved as a check. The routine now starts with quiet hours. The way that sentence interacts with "Run chase" is a new flag.
5. **Medical advice is missing.** Resolved. The out-of-lane fact and the greeting cover medical, legal, and financial advice, with a refusal and a pointer to a qualified professional.
7. **Promise text is stored whole.** Resolved as a rule. Summaries are short and neutral, and secrets, passwords, credentials, health details, and financial details are redacted in chases and lists. The width of "financial details," and the evidence note that can still quote proof, is a new flag.
8. **"Owner" is three different people.** Resolved. A terms fact defines "owner" as the importer and "promiser" as who made the promise, and the skills use those words that way.
9. **FAIL is both closed and still open.** Resolved. FAILED-CHECK is defined as still chased, "active" means OPEN or FAILED-CHECK, and chase loads both. A mismatch between that definition and skill 2 is a new flag.
12. **Empty list mutes the owner.** Resolved. Quiet-when-empty applies only to the routine, and the profile says to reply when the owner writes.
13. **Hardcoded #7 and no ID memory.** Resolved. IDs are last-ID-plus-one, the sample uses `#[ID]`, and getting-started sets last ID used to 0.
15. **Casual "I'll…" lines become tracked promises.** Resolved. A casual line is logged only after the owner says yes to "Track this as a promise?"
16. **Coordinator placeholder survives "send it to me."** Resolved. Status lists go to the report recipient chosen in setup. The brace placeholders are gone.
17. **Name depends on jargon.** Resolved. The name is "Promise Tracker: No Proof, Not Done."
18. **Description buries the hook.** Resolved. The description opens with "OK, on it" is not done, and it no longer claims every promise. A new over-claim about who gets messages is filed below.

### Not fully resolved

6. **Opening pages, sheets, and mail.** Partly resolved. Verification is now pasted proof, with no login, and page content is untrusted data rather than instructions. Still open: the proof fact and skill 2 tell the bot to open a shared link when it "has the means," and the bar examples still include "email visible in the Sent folder." Skill 2 does not say that an unopened link is missing proof.
   **Remaining fix:** Do not fetch links, mailboxes, or files. Ask the owner to paste the visible text or a screenshot. If the proof is a link you did not open, mark FAILED-CHECK and do not infer a pass. Replace the Sent-folder example with "the owner pastes the sent message."

10. **Stale window and workday clock.** Partly resolved. Setup now asks timezone, workday start, workday end, and the stale window. Still open: "2 working hours" is not defined as time inside that start and end, setup never asks which days are workdays, and escalation still says "their workday end."
    **Remaining fix:** Define the stale window as elapsed time inside the owner's workday only, pausing overnight and on other days. Ask which days are workdays, with Monday–Friday as the default. Write "the owner's workday end" in the escalation fact.

11. **Schedule can run before setup.** Partly resolved. The default times are 12:30 and 17:00, and getting-started says to create the routine only at the end. Still open: the routine is already in the imported file, its content has no "setup unfinished, send nothing" stop, and skill 1 and skill 3 will log and chase if the owner talks before the questions end. "Create the routine" can also add a second copy of a routine the import already registered.
    **Remaining fix:** First line of the routine, and of skill 1 and skill 3: if getting-started has not saved timezone, chase times, and chase settings, send nothing and finish setup. Tell getting-started to set the times on this routine, not to create another one.

14. **Promiser can park the promise.** Partly resolved. Only the owner can park or cancel, and other people's park or cancel requests are ignored. Still open: nothing says how a PARKED promise becomes OPEN again, so a parked item stays unchased with no way back.
    **Remaining fix:** The owner reopens a PARKED id by asking, which sets it back to OPEN and resumes chasing. Say that CANCELLED stays closed.

## New flags

### (a) Personal-data or identity leaks

No new flags. The revised file has no real names, towns, emails, phone numbers, account or government IDs, company or client names, private bot names, or URLs.

### (b) Safety gaps

#### N1. A standing "yes" to message teammates fights the per-action safety rule

The safety fact forbids sending external email or messages without the owner's explicit yes for that specific action. The chasing fact, skill 3, the routine, and getting-started question 5 allow every future chase to go out once the owner enables direct messages in setup. Question 5 does not say those messages leave on the chase schedule, does not ask which channel, and nothing lets the owner revoke that yes. "External email or messages" can also be read as forbidding the in-chat assistant chase and the status list, which would stop the product, or as allowing any channel after one setup yes, which would let a scheduled run email or text teammates.

**Suggested fix:** Write one sentence that names the allowed sends: in this chat, to the owner and to assistants listed at setup; a draft shown to the owner for anyone else. If question 5 stays, state that "yes" means a message to a teammate named in question 1, on one channel the owner names in that same answer, on the chase schedule, without asking each time. Say that "no" is the default, that email is off unless they name email, and that the owner can revoke it in chat with effect on the next run.

#### N2. Quiet hours both block every send and then run the chase

The quiet-hours fact says "never message during quiet hours." The empty-list fact says "Always reply when the owner writes." The routine says if it is quiet hours, send nothing, except owner-urgent items, and the next sentences are "Run chase" and "Send the report recipient one short list," with no condition. The escalation fact tells the bot to message the owner when an item is past workday end, and it does not repeat the hold until quiet hours end. "Only an owner-marked urgent item may be sent" can also turn a teammate draft into a night send.

**Suggested fix:** Quiet hours apply to scheduled chases, status lists, and escalations. A reply to a message the owner just sent still goes out. In the routine, stop before "Run chase" unless quiet hours are over or that item is owner-urgent; do not leave "Run chase" as an unconditional next step. Urgent changes the clock only. It still drafts chases to people unless direct messages are enabled. Repeat in the escalation fact that an overdue ping waits until quiet hours end.

#### N3. Privacy redaction drops the promise and can still keep the secret

The privacy fact forbids storing financial details and health details. The bar examples depend on financial details ("shows the new price") and on mail. A price, invoice, or appointment promise can be stored as "[redacted]" and then cannot be chased or checked. The other way, skill 2's "one-line evidence note" and skill 1's confirm line are not told to stay redacted, so a pasted password can be written into the CLOSED-PASS note. Government IDs and account numbers are not named.

**Suggested fix:** Redact passwords, credentials, government IDs, bank and card numbers, and medical record contents. Keep amounts, prices, and deadlines when the owner stated them as the promise or the bar. For a health matter, store a neutral label the owner agrees to. The evidence note and the confirm line say "matched the bar" or the redacted summary, not a copy of the proof.

#### N4. The last line of skill 2 lets the wrong person close the loop

Skill 2 requires proof that matches the bar, then says: accept "done" only from the promiser (with proof) or the owner. The parenthetical attaches to the promiser, so the owner's bare "done" reads as enough, against "Never close on an acknowledgment" and against the product name. "The promiser" is also defined as anyone who made a promise, not the promiser field on this id, so a different assistant can report it done.

**Suggested fix:** A done-report counts only from the owner or from the promiser named on that id, and only with proof that matches the bar. The owner's "done" with no proof stays an acknowledgment and the status stays FAILED-CHECK, unless the bar is the owner's written confirmation or the owner explicitly waives the bar for that id.

### (c) Clarity and usability

#### N5. "No progress" is undefined, so the stale rule can chase forever or never

Stale means no progress within the window, or past ETA. Progress is not defined. Last chase time is a required field and is never written. A chase message can count as progress and clear the stale state, or not count, so every active item is chased at both daily runs until it closes. "Blocked," used on the status list and in the escalation rule, is also undefined, so missing proof can be treated as blocked on the owner and generate an extra ping every run.

**Suggested fix:** Progress is a new ETA, a proof attempt, or an update from the owner. Sending or drafting a chase is not progress; when you do it, set last chase time. Blocked means the promiser has said they need a decision or proof from the owner, or the bar is the owner's confirmation. Missing proof alone is stale, not blocked.

#### N6. Each chase run sends the status list twice

Skill 3 ends by sending the report recipient one short list. The routine says "Run chase" and then "Send the report recipient one short list." One scheduled run produces two lists. If the recipient is the owner, that also fights the escalation fact, which says to message the owner only when a promise is blocked on them or overdue.

**Suggested fix:** Send the status list in one place, inside skill 3. The routine calls chase and does not send a second list. State that the scheduled list to the report recipient is not an escalation. If the recipient is already the owner, do not send a separate escalation for items that are already on that list.

#### N7. FAILED-CHECK means two different things

The status fact says FAILED-CHECK is "proof was shown but did not match the bar." Skill 2 also sets FAILED-CHECK when proof is missing. A missing proof is not a failed match, so a model can leave that promise OPEN and skip the "say exactly what is missing" line, or it can follow skill 2 and ignore the definition.

**Suggested fix:** Define FAILED-CHECK as a done-report that failed: proof was missing or did not match. Keep it active and chased, which the rest of the file already says.

#### N8. Chases and status lists assume everyone is in this chat

Skill 3 tells the bot to ask a listed assistant "in this chat," and to send the report recipient the list. Getting-started collects assistant names and an optional coordinator, and it never says they share this chat. If they do not, the bot has no next step, so it can open a new thread, which is an external send.

**Suggested fix:** If the assistant or the coordinator is not in this chat, draft the chase or the status list for the owner in this chat and do not open another thread. Say that in skill 3 and in the chasing fact.

### (d) Storefront appeal

#### N9. The description promises a limit the setup questions remove

The name is clear and the first sentence carries the hook. The description then says: "It only messages you and the assistants you list, and it drafts chases to teammates for you to send." Question 5 offers to message teammates directly, and the chasing fact honors that yes. A shopper who imports on the strength of that sentence gets a wider sender than the listing describes.

**Suggested fix:** Keep the default in the description, and add the opt-in in the same sentence: drafts for teammates, unless you later allow direct messages to them. Leave the opening "OK, on it" sentence as it is.
