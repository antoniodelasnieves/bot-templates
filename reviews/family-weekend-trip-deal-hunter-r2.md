# Review: Family Getaway Finder (r2)

Overall score: **7/10**. Not ready to publish. The booking promise, children's ages, quiet hours, and storefront copy now agree with each other. Two import hazards remain: the sample settings line is a live `(log)` memory, and getting-started is a 13-to-15 question gate before the first search.

Reviewed file: `templates/family-weekend-trip-deal-hunter.md`. No real names, towns, emails, phones, IDs, company or client names, bot names, or URLs.

## R1 flags

1. Resolved. "Other bots" and "a coordinator bot" are gone. Shortlists and reminders stay in this chat, and health, legal, and money admin are out of scope.
2. Resolved. The bot never books, reserves, holds, or pays, even if the owner says yes. The shortlist closer tells the owner to book on the site.
3. Resolved. Pay-later rates, deposits, no-show fees, and points or credit redemptions count as spending and are never completed by the bot.
4. Resolved. Safety bans in-app messages to hosts, properties, and support, as well as email and DMs.
5. Resolved. The reminder no longer asks "keep or cancel?". It says the bot cannot cancel or change the stay, and the owner cancels on the site.
6. Resolved. Ages are not stored. A search may ask for ages and must not save them. Venue stays in the search. School, team, club, coach, opponents, results, and times are excluded.
7. Resolved. A pasted confirmation is stripped to property name, dates, and free-cancellation deadline. Names, emails, phones, addresses, confirmation codes, loyalty numbers, and payment details are excluded.
8. Resolved. Search may use only search, results, and availability. Saved travellers, payment methods, past trips, inbox, messages, account creation, saved cards, settings changes, and passwords are banned.
9. Resolved. No legal, visa, financial, or insurance advice. No invented government link. No cards, points programs, loans, insurance, or safe-or-unsafe claims.
10. Resolved. The title is the profile name, Family Getaway Finder.
11. Not resolved. Brace placeholders are gone, but the replacement is a `(log)` line. See the judgment below.
12. Resolved. Each getting-started prompt asks one thing. Home base, travel limit, sites, and cancellation window are no longer paired.
13. Resolved. Deadline reminders are a routine, created per booking, at 48 hours and 24 hours, moved earlier out of quiet hours. The weekly scan is asked in getting-started and sends only to this chat.
14. Resolved. Quiet hours are never used for sending. A reminder that would land inside them goes out earlier, not later.
15. Resolved. The bot prefers the free-cancellation deadline closest to arrival, and skips a rate whose deadline is earlier than the saved minimum (default 7 days) unless the owner asks to see it labeled.
16. Not resolved. The paste fallback and the ban on guessed prices, ratings, availability, and travel times are in place. A successful search still does not say what opens the site.
    Suggested fix: "Use web browsing if this bot has it. For each stay, cite the page you opened and the check time. If browsing is off, use the paste fallback and mark the shortlist unverified. Do not add a plugin that can pay, message, or change an account."
17. Resolved. Getting-started runs first and blocks search. Currency is asked. Fewer than 3 matches are shown as-is, with the reason, and the list is not padded. The budget unit is stored with the amount.
18. Resolved. Event questions run only when the settings log says event trips: yes. The skill text stays in the file either way.
19. Resolved. Party size is stored only in the settings log. The profile line is the rule: counts, family room, no ages, names, birthdates, passport or ID numbers, or health details.
20. Resolved. The name is Family Getaway Finder. The description covers weekends, 3 to 4 day breaks, and optional sports trips, and it does not promise discounts.
21. Resolved. The storefront line says the owner books every stay, and the bot only shortlists and never books, reserves, holds, or pays.

## Example settings line

The `(log)` line labeled "example only, not real data" can be imported as real settings. It uses the same memory kind as the live settings log, and the quoted text is a finished record: 2 adults, 2 children, family room, 600 EUR per trip, a 7-day window, Central European time, quiet hours 21:00 to 08:00, event trips on, weekly scan off. "Example only" is a comment beside that record, not a separate kind a loader has to honor. Getting-started says to save answers "in the example format," and the first-run rule treats a saved settings log as the gate. A bot can read this line as the gate already passed, leave event trips on, and search with a household the owner never described. The values are also specific enough to look like a real family rather than blanks.

Suggested fix: delete this line from Memory facts. Show the field order only inside getting-started, as instructions, not as a `(log)` line. Write the log only after the owner answers, and replace any earlier log when you do. If a log still contains "example only", "mid-sized inland city", or "not set", setup is not finished and the bot must not search.

## Fifteen getting-started questions

Fifteen is too long. With no children and no weekly scan the owner still answers 13 questions; with both, 15. The greeting calls that "a few quick questions," and the first-run rule refuses every search until all of them are saved. A stranger who wants one weekend list has to finish timezone, quiet hours, sports travel, and a weekly scan first. Most will abandon, or paste one reply the bot cannot map onto 15 slots.

Suggested fix: make the first run six questions: home base, travel limit, party counts plus family room, budget in one reply (amount, currency, and per night or per trip), booking sites, and cancellation window (default 7 if they say default). Default the rest and do not block a search on them: event trips off, weekly scan off, quiet hours 22:00 to 07:00. Ask the timezone only before the first reminder. Offer "use defaults" for anything still unasked.

## (a) Personal-data or identity leaks

22. The sample settings publish a plausible household: two adults, two children, a family room, 600 EUR, Central European time, quiet hours 21:00 to 08:00, and kids' sports trips on. There is no town name, and the city is only "a mid-sized inland city," but the rest is a fingerprint, and it sits in a public template as a `(log)` memory.
    Suggested fix: do not ship filled values. If a shape example is needed outside memory, use "not set" for every field.

## (b) Safety gaps

23. Safety now says never delete "anything outside its own reminders." That drops the old requirement of an explicit yes, and it never defines which memories are the bot's reminders. A bot can treat the settings log or a booking note as one of its reminders and delete it.
    Suggested fix: "Never delete settings, bookings, or other memories. The only thing you may delete is the reminder for one stay, and only after its deadline has passed or the owner tells you to stop reminding them about that stay."

24. The booking rule says to stop if a site asks for payment or guest details. Normal search forms ask how many guests. The bot can treat the party-size field as guest details and refuse every search, or it can type past that field into names and contact details.
    Suggested fix: "Party counts may be entered on a search form. Stop before any name, email, phone, payment, or ID field. Do not type those."

25. The honesty rule tells the owner to check the official travel site "for their nationality." Nationality is not a setting, so the bot will ask for it or infer it from home base. That is identity data, next to a rule that already bans passport and ID questions.
    Suggested fix: "Do not ask nationality, citizenship, or passport country, and do not infer them. Say entry rules are outside this bot, and that the owner should check the foreign office of the country that issued their passport."

## (c) Clarity and usability for a stranger importing it

26. The weekly scan "runs trip-shortlist for the next two weekends." Trip-shortlist starts by confirming dates and must-haves, and it has no destination. A scheduled run cannot hold that interview, so it will stall, ask questions at the scheduled time, or pick places the owner never named. It also ends by asking the owner to report a booking they did not make.
    Suggested fix: "The weekly scan does not ask questions. It searches stays within the saved travel limit of home base, for the next two weekends, using saved budget, cancellation window, and must-haves if any. It sends one shortlist, or one line that the site could not be opened. It runs only after setup is finished. It does not use the booking-reminder closer."

27. Quiet hours and the early reminder need a real timezone and a start time. Question 11 asks "What's your timezone?" and the sample answer is "Central European," which is not a zone a clock can use. Question 15 does not say the weekly time must fall outside quiet hours. "Just before quiet hours start" has no number of minutes.
    Suggested fix: ask for a zone such as Europe/Madrid, and for quiet hours as a 24-hour start and end. If the weekly time falls inside quiet hours, ask again. Send an early reminder 15 minutes before quiet hours start.

28. Settings are "changed only by the owner," and getting-started also tells the bot to write that same log. Read literally, the bot is not allowed to save the answers.
    Suggested fix: "Write the settings log from the owner's answers during getting-started. After that, change it only when the owner asks, and replace the old log rather than adding a second one."

29. The reminder says "this stay" and "the stored deadline" without the property name or the clock time. Two bookings produce the same message, and the owner can cancel the wrong stay on the site.
    Suggested fix: "Include the property name and the deadline in the owner's timezone. Do not include guest names, confirmation codes, or payment data."

30. The job says good value is the lowest total price, "weighed against" travel time and rating. Skill 1 puts free-cancellation options first. Event-trip ranks by travel time to the venue, then price. Those are three different lists.
    Suggested fix: "Drop stays that miss the budget, the must-haves, or the cancellation window. Ordinary trips: sort by total price, lowest first. Event trips: sort by travel time to the venue, then price. Show the rating; do not re-rank by it. When prices tie, prefer the later free-cancellation deadline."

## (d) Storefront appeal of name and description

No new flags. Family Getaway Finder matches the wider job, and the description leads with shortlists, free cancellation, optional sports trips, and the owner booking every stay.
