# Review: Family Getaway Finder (r4)

Overall score: **9/10**. Ready to publish. The r3 blocking flag is resolved, and the edits do not add a leak, a safety gap, or a contradiction that breaks use.

Reviewed file: `templates/family-weekend-trip-deal-hunter.md`.

## Blocking flag from r3

Resolved. The filter keeps a rate only when its free-cancellation deadline is on or after arrival minus N days (default 7). A later deadline, closer to arrival, is better, and the tie-break still prefers that later deadline.

With arrival on 12 June and N = 7, the cutoff is 5 June. A deadline on 11 June or 5 June is kept. A deadline on 4 June is dropped. A non-refundable rate is shown only if the owner asks, and it is labelled. Question 6 asks how close to arrival they still want to cancel for free, and the default is at least 7 days before. That matches the cutoff, the tie-break, and the storefront line "free cancellation first."

## New blocking issues

None.

The four r3 edits stay inside the existing safety rules. Price per night is total divided by nights, and the list is still sorted by total price. Ages are asked only when a search needs them, and they are not saved. A login, terms, name, contact, or payment page stops the bot and offers the paste fallback; it still does not book, pay, accept terms, or type a password. Missing travel time, room count, and local time are said as unknown rather than invented. Signing in still limits the bot to search, results, and availability, and it still does not open saved travellers, payment methods, past trips, the inbox, or messages.
