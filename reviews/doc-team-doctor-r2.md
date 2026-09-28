# Review r2: Bot Team Doctor

Overall score: **7/10**

Not ready to publish (9+ is the bar). The ask-first list, the off-by-default auto-apply, the advice ban in the greeting, the three cadences, and the paste fallback are real fixes. The scheduled checkup still contradicts its own send ban, skip still stores a device timezone the owner never confirms, and a few r1 holes are only narrowed.

Reviewed file: `templates/doc-team-doctor.md` (replaced verbatim with the revised draft).

## r1 flags

1. **Not resolved.** Quiet fix is now a typo, grammar, or ambiguous-phrasing change that must not change what the bot does, when it runs, or who it contacts, and auto-apply is off unless the owner names a bot. The standing write remains: "When on, Doc applies only quiet fixes to that bot" with no yes on that patch. "Ambiguous-phrasing" is still Doc's judgment, and question 7 asks the owner to allow "typo and phrasing fixes," which is wider than spelling.
   Remaining fix: Quiet fix means spelling and punctuation only. Any change a reader could take as a different instruction is a report item. Auto-apply still waits for the owner's yes on that patch, then the owner pastes it. Doc does not write another bot's text.

2. **Not resolved.** Patches, logs, and reports now replace names, IDs, health, money, family details, addresses, and credentials with generic words. Skill 3 says to redact both texts. The patch is still "sent for approval" with no recipient, so the coordinator can receive instruction quotes. The list omits phone numbers, email addresses, and message or file contents. Redacting every "name" either strips roster bot names or keeps a person-named bot in the shared report.
   Remaining fix: Approval is the owner's yes in this chat. The coordinator gets the generic finding only. Add phone numbers, email addresses, and message or file contents to the redact list. Keep roster bot names; redact people.

3. **Not resolved.** Urgent is now defined, and only the owner is messaged. The definition still includes "a bot is about to spend, send, post or delete something wrongly," which Doc cannot see and can stretch. Buy, book, and share files are outside that sentence.
   Remaining fix: Urgent means one case: a roster bot's text no longer forbids spend, buy, book, post, send, file share, or delete without the owner's yes. One line to the owner. Every other finding waits.

4. **Resolved.** Skill 1 now checks spending, buying, booking, posting, sending, sharing files, deleting, medical/legal/financial advice, and quiet hours.

5. **Not resolved.** The profile says the report recipient may not act on the ask-first list, and the routine says the coordinator's yes never counts. The update the coordinator actually reads still has no fixed stop line. "Who acts" may be the coordinator (flag 17).
   Remaining fix: End every update with: "Needs-you items wait for the owner's yes. Do not create, merge, rename, remove, pause, change permissions or safety lines, add or change a connector, spend, buy, book, post, email, message, share files, or delete."

6. **Resolved.** Skill 2 now waits for an explicit yes before creating, merging, renaming, removing, pausing, changing permissions or safety lines, or adding a connector, and it adds a roster row only after the owner confirms the bot exists.

7. **Resolved.** Doc never patches its own safety, privacy, honesty, or ask-first lines, and every change to Doc is ask-first. A new clash with setup and with naming Doc for auto-apply is flag N2 below.

8. **Not resolved.** Question 6 now asks which lanes to keep separate, and shared reports are supposed to carry summaries only. A summary still crosses to the coordinator. The r1 bar was owner-chat only for those bots.
   Remaining fix: Name the bots in the answer. Findings about them go only to the owner in this chat, in the generic form from flag 2.

9. **Resolved.** The greeting says Doc does not give medical, legal, or financial advice, and that nothing big changes without a yes.

10. **Resolved.** The file starts at `## Profile name`. The draft title and the pack note are gone.

11. **Not resolved.** Skill 1 and getting-started now say to ask for a paste when Doc cannot read a bot, and skill 3 can confirm from a paste. "If you cannot read a bot directly" still treats direct access as normal, auto-apply still has Doc write the other bot, and the routine "refreshes the roster" for bots Doc believes it can see.
    Remaining fix: The log roster is the only desk list. Doc diagnoses a bot only from text the owner pasted in this chat. If the paste is missing, say so and skip that bot. Change the roster only when the owner names an add or a removal. The owner copies an approved patch in.

12. **Not resolved.** Getting-started says no routine exists until it finishes, and the routine stops to run getting-started if setup is unfinished. The file still ships the routine. Nothing tells the importer to say "getting started." The last setup step tells Doc to create or enable the routine itself. Monday 09:00 is not checked against the owner's quiet hours.
    Remaining fix: Under the profile description, add: "After import, open this bot and say: getting started." While timezone, quiet hours, or report recipient is still a placeholder, Doc only runs that interview. Tell the owner which schedule control to set, to a time outside quiet hours. If the chosen hour falls inside quiet hours, ask for a different hour before saving.

13. **Resolved.** Question 4 offers weekly, every two weeks, or monthly, and the routine schedule states Monday 09:00, every 14 days, and the first Monday for those three.

14. **Not resolved.** Question 5 stores one line (default) or silence, and skill 1 follows it. The routine content always sends one numbered update.
    Remaining fix: The routine uses the saved choice. Silence means send nothing when there are no new items and no still-open items.

15. **Not resolved.** New items are capped at 5 to 7, then one line counts and names still-open items. The open ask-first detail is gone, so a safety item from last week is a name without its fix or its needs-you flag.
    Remaining fix: Repeat every still-open needs-you item in full. Cap new findings at 7. If anything is held, the last line is "N more held for next time."

16. **Not resolved.** Skip defaults and the example "22:00-07:00" are in place. The timezone default is the device zone, with no city example, no read-back, and no retry when 09:00 sits inside the hours they chose. See the device-timezone check below.
    Remaining fix: Example answer: "22:00–07:00 America/Los_Angeles." Read back the saved hours, zone, and checkup time. If the checkup time is inside quiet hours, ask for another hour.

17. **Not resolved.** Who-acts is now owner, coordinator, a named bot, or Doc for a quiet fix. That adds the coordinator, and needs-you is still not tied to the owner. A named bot can be told to act on an ask-first item.
    Remaining fix: Who-acts is `owner`, `Doc`, or one roster bot name. `needs-you: yes` means the owner acts. Doc's unprompted action is writing the update.

18. **Not resolved.** The name is now "Bot Team Doctor," and the description leads with "Checks your Grok Bot desk." "Doctor" is still the noun a shopper reads, and the storefront description never says this is not medical advice. The disclaimer is only in the greeting, which the storefront does not show.
    Remaining fix: Use a name such as "Bot Desk Checkup." Put "for your Grok bots" and "no medical advice" in the first sentence of the description.

19. **Resolved.** The description sends the list to "you," and it no longer ends on create, merge, or remove. "Nothing big" is vague; that leftover is flag N6.

## Device timezone

The default "22:00-07:00 in the timezone your device reports" is **not sound**.

The hours and the Monday 09:00 checkup are in the same zone, and 09:00 falls outside 22:00-07:00, so the default pair does not collide with itself. The source of the zone is the failure. This bot runs on the owner's behalf, and the device that "reports" a zone may be the host, a UTC server clock, a laptop on a VPN, or a phone in another city. Skip on question 2 saves that zone with no confirmation and no read-back. "If unknown, I'll ask again" asks the same empty source again; it does not ask for a city. A fixed offset or a three-letter abbreviation drifts or flips across daylight saving. Once saved, quiet hours and the checkup move together to the wrong wall clock: the owner's real night stays open, and Monday 09:00 arrives in their evening or night.

Suggested fix: Do not save a device zone on skip. Show the detected value and ask "Should quiet hours use {zone}?" If nothing is reported, or the value is UTC, a numeric offset, or a three-letter abbreviation, ask for a city or region (example: America/Los_Angeles). Read back "Quiet hours 22:00–07:00 in {zone}. Checkup Monday 09:00, outside those hours." If 09:00 is inside their hours, ask for a different checkup time before creating the routine.

## (a) Personal-data or identity leaks

No new flags. The revised file has no real names, towns, emails, phones, IDs, company or client names, private third-party bot names, or URLs. The placeholders are `{your report recipient}`, `{your quiet hours}`, and `{your timezone}`. "Doc" is the in-template nickname; the dual name is a clarity flag (N5), not a customer leak.

## (b) Safety gaps

N1. **The checkup is a send, and the same routine forbids sending.** The ask-first list and the safety fact require an explicit yes for each email or message. The routine then says never do anything on that list, including sending messages, and also says send one update to the report recipient. The urgent quiet-hours line is a second send with the same clash. A strict reading either blocks the product or treats "sending messages" as allowed whenever Doc is doing its job.
Suggested fix: Carve out two sends in the ask-first list, the safety fact, and the routine, in the same words: the numbered checkup to the saved recipient on the saved cadence outside quiet hours, and one urgent line to the owner. Every other email, message, post, or file share stays ask-first, one yes per action.

N2. **"Every change to Doc is ask-first" covers setup, and it also covers auto-apply if the owner names Doc.** Getting-started saves log memories and creates the routine without a separate yes. Question 7 can name Doc, which then "applies" quiet fixes to Doc's own text, including the lines skill 3 says never to patch, if a typo is found inside them.
Suggested fix: State the only setup writes that are already allowed: the seven saved answers, and the one checkup routine after the owner has picked the cadence and the hour. Doc is never an auto-apply target. No other change to Doc's instructions, skills, or routines runs without a yes for that change.

N3. **A new bot's draft instructions are unchecked.** Skill 2 says to propose a paragraph with the job and draft instructions. It does not require those drafts to include the safety lines and quiet hours, and it does not forbid medical, legal, or financial advice inside the draft the owner is asked to approve.
Suggested fix: Every new-bot draft includes the canonical safety sentence and the saved quiet hours. The draft contains no medical, legal, or financial advice. Doc waits for the owner's yes before any create.

## (c) Clarity and usability

N4. **Quiet hours also freeze a conversation the owner already started.** "Doc may message the owner about urgent items only" during quiet hours. Setup question 2 can be answered at 23:00, and the next question, or the first checkup they just accepted, then waits until morning.
Suggested fix: Quiet hours delay Doc starting a checkup or any other outbound note. They do not delay replies while the owner is in this chat, including the rest of getting-started and a first checkup the owner just accepted.

N5. **The storefront name and the speaking name differ.** The profile name is "Bot Team Doctor." The job, the skills, and the greeting say "I'm Doc."
Suggested fix: Use Bot Team Doctor in the greeting. If the short name stays, define it once: "Bot Team Doctor (you can call me Doc)."

## (d) Storefront appeal

N6. **"Nothing big" does not tell a shopper what is fenced.** The description is clearer than r1 and addresses the owner directly. It never names email, post, or delete, and it never says the bot is not a physician. Someone buying "Bot Team Doctor" can still read a medical product that will rearrange their bots.
Suggested fix: First sentences in this shape: "Weekly checkup for your Grok bots, not medical advice. It sends you a short list of overlaps, missing jobs, and unsafe rules. You approve every change. It does not email, post, or delete anything unless you say yes to that item."
