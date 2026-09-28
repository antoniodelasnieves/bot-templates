# Review r1: Doc – Team Doctor

Overall score: **6/10**

Not ready to publish (9+ is the bar). The ask-first list, the default of approving every patch, quiet hours, and the ban on medical, legal, and financial advice are the right fences. A stranger still cannot tell how Doc sees other bots, the weekly job can fire on unresolved placeholders, and two paths (exact-text patches to a coordinator, and "apply Doc patches") can move private text or edit a live bot without a yes for that action.

Reviewed file: `templates/doc-team-doctor.md` (status header removed).

## (a) Personal-data or identity leaks

No flags. The packed file has no real names, towns, emails, phones, account or government IDs, company or client names, private bot names, or URLs. `{your coordinator bot}`, `{your quiet hours}`, and `{your timezone}` are generic. "Doc" is this template's public persona. The draft status line that pointed at an internal `published.md` is not in this copy.

## (b) Safety gaps

1. **"Apply Doc patches" is a standing yes for live edits, and "wording or clarity" is undefined.** Memory fact "Fix levels" lets the target bot apply a quiet fix on its own once the owner has flipped that preference. Skill 3 then skips approval whenever the toggle is on. A duty added or removed can be labeled clarity. The profile safety line asks for an explicit yes for that specific action; question 5 of getting-started replaces that with one blanket answer.
   Suggested fix: Keep "approve every patch" as the only path. Every patch is shown to the owner and applied only after they reply yes to that patch. In the same sentence, state that creating, merging, renaming, removing, pausing, permissions, safety lines, connectors, spending, buying, booking, posting, email, DMs, file shares, and deletes are ask-first even if a future toggle exists. Define a quiet fix as a rephrase that leaves the bot's duties and bans unchanged.

2. **Exact before/after text is sent to the coordinator and can carry personal data.** Skill 1 forbids pasting personal data into the update and gives a generic example. Skill 3 still requires "the exact current text" and "the exact replacement text", then says to send that patch to the owner or the coordinator. The privacy fact forbids copying IDs, health, finances, family details, or credentials into reports or into another bot. Those two instructions disagree, and the coordinator is another bot.
   Suggested fix: Any quote that contains an ID, health or money detail, family detail, credential, token, or message body is rewritten as "private detail removed" before it is stored or sent. The coordinator receives only the generic line. The owner, in this chat, is the only recipient of a patch that still quotes instruction text.

3. **"Urgent" is not defined, so quiet hours bend whenever Doc decides they should.** The quiet-hours fact and getting-started question 2 both allow a message during quiet hours for an urgent issue. Overlap, a stale routine, or a missing bot could all be called urgent.
   Suggested fix: Name the one urgent case: a bot on the roster has no line that forbids spend, post, send, or delete without the owner's yes. That case gets one line to the owner. Every other finding waits until quiet hours end.

4. **The checkup's safety test is thinner than Doc's own safety rule.** Doc itself must not spend, buy, book, post, email, DM, share files, or delete without a yes for that action. Skill 1 only checks other bots for "no spend/post/send/delete", medical/legal/financial advice, and quiet hours. A bot that can book or share files passes the checkup.
   Suggested fix: Put one canonical sentence in the memory fact, skill 1's check, skill 2's intake, and the weekly routine: no spend, buy, book, post, email, DM, file share, or delete without an explicit owner yes for that action, and no medical, legal, or financial advice.

5. **A needs-you item can still be carried out by the coordinator.** The report format is problem, proposed fix, who acts, needs-you. Nothing in the update text tells the recipient to stop. The weekly routine forbids create, merge, remove, and permission changes inside the routine, and is silent on rename, pause, connectors, spend, post, send, and delete.
   Suggested fix: End every update with this fixed line: "Needs-you items wait. Do not create, merge, rename, remove, pause, change permissions, add a connector, spend, buy, book, post, email, DM, share files, or delete until the owner replies yes to that numbered item." Repeat that ban in the weekly routine's content, and limit the routine's own send to the in-desk update.

6. **Skill 2's ban is shorter than the ask-first list, and "Afterwards" writes the roster even when the owner said no.** The skill says Doc never creates, merges, or removes a live bot. It does not repeat rename, pause, permission changes, or connectors. The last sentence adds the bot to roster memory after the proposal, with no "only if they said yes and the bot is installed."
   Suggested fix: Copy the full ask-first list into the skill. Add a roster line only after the owner confirms the bot is installed. On a no, leave the roster unchanged and say so.

7. **Doc can quiet-patch its own safety, privacy, honesty, and ask-first lines.** Nothing says Doc is off limits to itself. With "apply Doc patches" on, a later checkup can weaken the fences in this file.
   Suggested fix: Doc never edits its own safety, privacy, honesty, or ask-first text. Those edits are ask-first, and only the owner applies them.

8. **Work-versus-home separation has no setup step, so a private lane can leak into the shared report.** The privacy fact says to keep lanes separate, with work versus home as the example. Getting-started never asks which bots are in which lane, and every finding otherwise goes to one coordinator.
   Suggested fix: Add one setup question: "Which bots should stay off the shared report? Name them." Findings about those bots go only to the owner in this chat, in the generic form from flag 2.

9. **The first words the owner hears do not state the advice ban.** The ban on medical, legal, and financial advice lives in a profile memory fact. The greeting is "I'm Doc, your team doctor. I keep your bots healthy."
   Suggested fix: Open the greeting with: "I check your bots. I do not give medical, legal, or financial advice, and I will not add that advice to any bot."

## (c) Clarity and usability for a stranger

10. **The packed file still starts with author notes.** The H1 is "Template draft: Doc – Team Doctor", and the next paragraph tells the importer it "ships on its own" and can drop into a "multi-bot pack". Someone pasting the file loads that as the bot's voice.
    Suggested fix: Start the file at `## Profile name`. Delete the H1 and the Reusable paragraph.

11. **The skills assume a desk Doc can see and buttons Doc can press.** Skill 1 says "List every bot on the desk." Skill 3 says re-read the bot's instructions and confirm the change is there. Getting-started talks about "apply Doc patches" as if the other bots already have that switch. None of these steps tell the importer where the list, the instruction text, or the switch comes from. The honesty rule says not to invent a status, and the list instruction pushes the other way.
    Suggested fix: State that the log roster is the only desk list, filled from names the owner types or pastes. A checkup diagnoses a bot only from instruction text the owner pasted in this chat. If the text is missing, say "I don't have this bot's instructions" and skip it. State that Doc cannot change another bot: the owner copies an approved patch in themselves.

12. **The weekly routine is armed before setup, on a placeholder clock, and getting-started is easy to miss.** The schedule is "Monday 09:00 {your timezone}". Reports go to `{your coordinator bot}` until the interview replaces the placeholders. Skill 4 says to run once right after import, and it does not say what the owner types to start it, or that the routine stays off until then. "Set the weekly-checkup routine" also assumes Doc can edit the product's schedule control.
    Suggested fix: Put a start line under the profile description: "After import, open this bot and say: getting started." While the timezone, quiet hours, or report recipient is still a placeholder, Doc only runs that interview. Tell the owner the routine clock is set in the product UI, to a weekday time outside quiet hours. Leave the routine disabled until those three answers exist.

13. **Checkup cadence is promised as a free choice and specified as weekly.** Question 4 asks how often, with weekly as the default, then says to set the weekly routine to the chosen cadence. The only routine is weekly. Daily or monthly has nowhere to go.
    Suggested fix: Ask: "Weekly, Monday, outside quiet hours. Keep that?" On a no, tell them the one schedule field to edit. Delete the sentence that says Doc sets the routine to an arbitrary cadence.

14. **A healthy desk has two endings.** Skill 1 says send one line that everything is healthy, or send nothing if the owner prefers silence. The weekly routine says stay silent when nothing changed and nothing is open. Getting-started never asks which they want.
    Suggested fix: Use the routine rule everywhere: if nothing changed and nothing is open, send nothing. Delete the "one line" branch.

15. **The 5–7 cap fights the "still open" rule.** Skill 1 keeps the top 5–7 items. The routine includes every item still open. A safety item ranked 8th disappears, or the two rules disagree in the same run.
    Suggested fix: New findings are capped at 7, most important first. Every still-open needs-you item is repeated even past 7. If anything is held back, the last line is "N more held for next time."

16. **A skipped answer has no default, and quiet hours have no shape.** The interview waits for each answer. It does not say what happens if the owner says "skip", and question 2 does not show a valid reply. Monday 09:00 can land inside the quiet hours they then type.
    Suggested fix: On skip, use: empty roster, reports to the owner, approve every patch, weekly Monday outside quiet hours. Show the example in the question: "22:00–07:00 America/Los_Angeles". If the chosen checkup time falls inside quiet hours, ask for a different hour before saving.

17. **"Who acts" has no allowed set.** The report format requires the field and never says whether it means Doc, the owner, the coordinator, or the bot under review.
    Suggested fix: Allow only `owner`, `Doc`, or the roster name of one bot. Doc's unprompted action is writing the update. `needs-you: yes` means the owner is the one who acts.

## (d) Storefront appeal

18. **The name reads as a clinician.** "Doc – Team Doctor" does not say bots, desk, or checkup. A shopper who wants a doctor and a shopper who wants a bot audit will both misread it.
    Suggested fix: Rename to a literal label such as "Bot Desk Checkup" or "Team Doctor for Your Bots". Put "for your Grok bots" in the first words of the description, and include "no medical advice" in that same sentence.

19. **The description assumes a coordinator and closes on create, merge, and remove.** "Reports to your coordinator bot" leaves out the owner-only case this template already supports. The last clause is the bot offering to create, merge, or remove live bots, which is the scary reading of an otherwise careful product.
    Suggested fix: Use this shape: "Once a week it reviews the Grok bots you name, then sends you a short list of overlaps, missing jobs, and unsafe rules. You approve every change. It will not create, rename, remove, email, post, or delete anything unless you say yes to that item."
