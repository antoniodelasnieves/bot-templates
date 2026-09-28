# Review r3: Bot Team Health Check

Overall score: **9/10**

Ready to publish. No blocking flags: no personal-data leak in the file, no path that spends, posts, emails, deletes, or edits another bot without a yes on that item, and the checkup can run. What is left is polish.

Reviewed file: `templates/doc-team-doctor.md` (replaced verbatim with the round-3 draft).

## r2 flags

1. **Resolved.** Auto-apply is gone. Every patch, including a typo, is needs-you. This bot never edits another bot. The owner applies the patch, or tells that bot to apply it.
2. **Resolved.** Patches go to the owner. Reports redact people's names, emails, phones, addresses, IDs, account numbers, health, money, and message contents, and they keep bot names. Tokens in a quote are a minor remainder (M1).
3. **Resolved for the buy/book/share gap.** Urgent now includes spend, buy, book, post, send, share files, and delete, and it is one short message. "About to" is a minor remainder (M2).
5. **Resolved.** Every update ends with the stop line, and skill 1 says to end with it. Report recipients and other bots must not act on needs-you items.
8. **Resolved.** Separate-lane findings go only to the owner in this chat, never to a shared recipient. Naming which bots are in the lane is a minor remainder (M3).
11. **Resolved.** The roster changes only when the owner confirms. Text comes from a paste or a read-only read. This bot does not edit, create, pause, or remove another bot.
12. **Resolved.** The first message tells the owner to say "get started." Nothing runs before that. No routine is created until they confirm a timezone and say yes to the summary. Checkup time must sit outside quiet hours.
14. **Resolved.** The routine sends nothing when the desk is healthy, nothing is open, and the owner chose silence. One line when they chose one line.
15. **Resolved.** Every still-open item is listed, each with a one-line needs-you ask, not dropped. A shorter-than-full line is a minor remainder (M4).
16. **Resolved.** The device timezone is gone. Question 2 asks for a city or timezone, reads back the zone and the local time, and requires confirmation. No confirmed zone means no routine.
17. **Resolved.** Who-acts is the owner, or a named bot only once the owner tells it. Needs-you items are always the owner.
18. **Resolved.** The name is Bot Team Health Check. The storefront description says it reviews Grok Bot assistants and gives no medical, legal, or financial advice.
N1. **Resolved.** Reports and replies are the messages it may send, and it never messages anyone else. Email, post, spend, and delete stay on the needs-you list. The urgent line is a minor remainder (M5).
N2. **Resolved.** Saving the setup answers is the only unprompted change to itself. The checkup routine is created only after a separate yes. Auto-apply cannot target it because auto-apply is gone.
N3. **Resolved.** Every new-bot draft includes the safety lines, quiet hours, and no medical, legal, or financial advice. The owner creates the bot.
N4. **Resolved.** Quiet hours limit only messages it starts. Replies to the owner are never held, so setup and a first checkup they just accepted continue.
N5. **Resolved.** The voice says "bot team health checker." The name Doc is gone.
N6. **Resolved.** The description names sending, posting, email, spending, deleting, and creating or removing a bot as actions that need a yes, and it says this bot never edits another bot.

## Blocking

None. Nothing in the packed file is a real name, place, email, phone, ID, company, client, private bot name, or URL. The scheduled report does not contradict the send ban. A yes is required before a patch, a new bot, a connector, a permission change, or any spend, post, email, file share, or delete.

## Minor polish

### (a) Leaks

No identity leaks in the file.

M1. Passwords, tokens, and keys are "never asked for or stored," and they are not in the replacement list, so a key already sitting in pasted instructions can be quoted in a report.
Suggested fix: Add passwords, tokens, and keys to the Privacy replacement list, next to account numbers.

### (b) Safety

M2. Urgent still means a bot "is about to" spend, buy, book, post, send, share, or delete. This checker cannot see another bot's next action, so the exception either never fires or treats any missing safety line as imminent.
Suggested fix: Urgent means one case only: pasted or read-only text has lost the line that forbids those actions without the owner's yes. One short message to the owner. Everything else waits.

M5. Quiet hours allow that one urgent message, and the Messages fact does not list it. "The only messages" are reports and replies.
Suggested fix: Add the same sentence to Messages: the one urgent line to the owner is allowed, and no other started message is.

### (c) Clarity

M3. Question 7 asks which lanes to keep separate and does not ask which bots are in each lane. "Work and home" with no names leaves the owner-only rule with nothing to match.
Suggested fix: Ask "Name the bots in each lane." If they name a lane and no bots, ask once more before saving.

M4. Still-open items are carried as a one-line ask. The problem and the proposed fix from the earlier update are not repeated. New items stop at 5 to 7 with no count of what was held.
Suggested fix: Repeat each still-open item as problem, proposed fix, who acts, needs-you. If new items are cut, end with "N more held for next time."

M6. The storefront line "Sending ... always need your yes" can be read as a fresh yes before every weekly report. The Messages fact allows that report.
Suggested fix: In the description, call the scheduled checkup the one send it makes on its own, and keep post, email, spend, delete, and create or remove as the actions that need a yes each time.

M7. The routine block is in the file, and its content never says to send nothing when getting-started has not finished. "Every 7 days" is also looser than the Monday 09:00 default collected in question 5.
Suggested fix: First line of the routine content: if getting-started has not finished, send nothing. State the weekly default as Monday 09:00 in the confirmed timezone.

### (d) Storefront

No remaining storefront flag. The name and the description say what it reviews, the advice ban, and the actions that need a yes.
