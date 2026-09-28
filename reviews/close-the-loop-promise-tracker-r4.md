# Review r4: Promise Tracker: No Proof, Not Done

**Score: 8/10**

A score of 9 or higher means ready to publish. B1 is fixed. One new contradiction keeps the scheduled run alive after there is nothing left to say, so this is not ready.

No names, contacts, or other identity leaks. The bot still messages only the owner, in this chat, and still does not spend, post, or delete on its own.

## B1

Resolved. The routine now checks three stop conditions first and ends the run when any of them is true: setup is not complete, the current time is inside quiet hours, or there is nothing to report. Chase runs only if all three checks are clear. "If any is true, end the run" is an exit, not a note that the next sentence ignores. Quiet hours may cross midnight, which keeps that exit meaningful for a 22:00–07:00 window.

## New blocking issue

### B2. A parked reminder that has already been shown keeps the run alive

Stop condition 3 ends the run only when there are no active promises and no parked reminder date has arrived. "Has arrived" stays true on every later run. Skill 3 says to list that reminder once and then hide it until the owner unparks it or sets a new date, and it still says to send the status list whenever chase runs.

After the one list, a day with no active promises still fails the stop: the old date has arrived, so the routine runs chase, and chase sends the owner another status list. The empty-run silence from B1 does not hold for any parked item whose reminder date is in the past. If "hide" is not stored, the same reminder is listed on every run, which breaks "list it once."

**Suggested fix:** End the run when there is nothing new to show: no active promises, and no parked reminder that is due and not yet listed. When a due reminder is listed, record that it was shown. Later runs send nothing until the owner unparks it, cancels it, or sets a new reminder date.

## Checked, not blocking

The safety line now limits the setup yes to the scheduled status list for the owner, and it still refuses other sends without a yes for that send. Matching proof is marked "proof found, awaiting close" and is not chased. The Sent-folder bar opens mail only if the owner connected mail and said yes to that check; that does not send, spend, or delete, and pasted proof remains the normal path.
