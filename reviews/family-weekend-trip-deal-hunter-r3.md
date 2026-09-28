# Review: Family Getaway Finder (r3)

Overall score: **8/10**. Not ready to publish. No personal-data leak remains, and the booking, payment, deletion, and nationality rules hold. One contradiction in the cancellation filter still breaks the shortlist.

Reviewed file: `templates/family-weekend-trip-deal-hunter.md`. No real names, towns, emails, phones, IDs, company or client names, bot names, or URLs. Asking for adult and child counts in one question is fine.

## R2 flags

11. Resolved. The example settings line is gone. Nothing in Memory facts is a pre-filled `(log)`.
16. Resolved. Searching uses whatever browsing the bot has, cites the source and check time, shares only links from pages it opened or the owner gave, and falls back to pasted listings labeled unverified.
22. Resolved. The sample household (party, 600 EUR, Central European time, sports on) is gone. "21:00 to 08:00" is only an example of how to say quiet hours.
23. Resolved. Nothing is deleted without an explicit yes, except expiring that booking's own deadline reminder after the deadline passes. The owner saying to keep the stay is a yes to stop reminding.
24. Resolved. Search forms may take dates, party counts, and room count. The bot stops at names, contact details, payment, or an account login.
25. Resolved. The bot must not ask for or guess nationality, and it must not supply a government link.
26. Resolved. Getting-started is six questions, then search may start. Sites, travel limit, event trips, and the weekly scan are asked only when needed.
27. Resolved. The weekly scan does not exist until the owner gives a day and time outside quiet hours, a destination list or region, and a date window. It asks nothing, guesses no prices, and does not use the booking closer.
28. Resolved. Timezone is checked by reading back the current local time for the owner to confirm. Quiet hours use a 24-hour example. An early reminder goes out 30 minutes before quiet hours. The weekly time must sit outside quiet hours.
29. Resolved. The bot writes the settings log from the owner's answers, replaces the old entry, and later changes it only when the owner says to.
30. Resolved. The reminder is filled in with the property name and the deadline date and HH:MM in the owner's timezone.
31. Resolved. Ordinary trips drop anything outside the budget, must-haves, or cancellation window, then sort by total price, lowest first. Event trips use that filter and then sort by travel time to the venue. Rating is shown and does not re-rank the list.

## Blocking

1. The cancellation rule skips a rate whose free cancellation "ends fewer than" the saved minimum days before arrival (default 7). A deadline 1 day before arrival is fewer than 7, so it is dropped. A deadline 14 days before arrival is kept. That is the reverse of question 6 ("at least how many days before arrival must free cancellation last?"), of the tie-break ("prefer the later free-cancellation deadline"), and of the storefront line "free cancellation first." The flexible rates this bot exists to find are the ones it discards.
   Suggested fix: "Skip a rate whose free-cancellation deadline is earlier than N days before arrival (default N = 7). A deadline on the day before arrival qualifies. When prices tie, prefer the later deadline. Show a non-refundable rate only if the owner asks, and label it."

## Minor

2. The budget is collected per night, while the filter only says "miss the budget" and the job talks about total price. A 3-night total can be compared with a per-night cap, which drops every weekend stay.
   Suggested fix: "Drop a stay whose price per night is over the saved budget. Sort the ones that remain by total price, lowest first."

3. Getting-started says "Never ask for ... ages." Privacy says to ask ages inside the current search when room pricing needs them, and not to save them.
   Suggested fix: "Do not ask ages during setup, and do not save them. A search may ask ages when the price depends on them, and must not write them into memory."

4. The bot stops at an account login, and the paste fallback applies when it cannot open a site. A login wall is neither path, so the search can die without a next step. The same stop does not mention a terms page, which the booking rule forbids accepting.
   Suggested fix: "On a login or terms page, stop. Do not type credentials or accept terms. Tell the owner to sign in themselves if they want. If prices are still blocked, use the paste fallback."

5. Every option must show travel time, and search forms may be filled with a room count, but neither value is collected and both can be invented. The timezone step can also invent the clock it reads back. Honesty forbids invented distances.
   Suggested fix: "If travel time does not come from a page you opened, say it is unknown. If a form needs a room count and the owner has not given one, ask once; do not guess. If you cannot read the clock in the owner's timezone, do not invent the time; ask what time it is there."

## Storefront

No new flags. The name and the description match a shortlist the owner books themselves, including weekends, 3 to 4 day breaks, and optional sports trips.
