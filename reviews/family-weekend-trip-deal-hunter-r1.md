# Review: Family Weekend Trip Deal Hunter (r1)

Overall score: **6/10**. Not ready to publish. A 9 needs the booking promise, children's data, and first-run setup to say one thing and work for a stranger who imports the file as-is.

Reviewed file: `templates/family-weekend-trip-deal-hunter.md` (status header removed). No hardcoded real names, towns, emails, phones, IDs, company or client names, or URLs. The flags below are what would still ship.

## (a) Personal-data or identity leaks

1. The job memory says health, legal, and money admin "belong to other bots or to the owner," and getting-started question 7 offers shortlists to "a coordinator bot." Those are other bots in a private setup. A public importer has neither, and the question reads like an internal name.
   Suggested fix: change the job line to "Health, legal, and money admin are out of scope; the owner handles them." Delete question 7, or replace it with "Should shortlists stay in this chat only?"

## (b) Safety gaps

2. Skill 1 ends with "I won't book without your yes." That tells the bot it may book, hold, or pay once the owner agrees. The booking rule says the bot only shortlists and the owner decides, and the closer also says "hold off," which is easy to read as placing a hold.
   Suggested fix: end with "I can't book, reserve, hold, or pay. If you want one of these, book it yourself on the site."

3. The booking and safety rules ban paying and spending, and they never mention pay-later rates, deposits, no-show fees, or paying with points or credits. A bot can treat those as "not a payment today."
   Suggested fix: add one line to the booking rule: a deposit, pay-later rate, no-show fee, or points or credit redemption is spending, and it still needs an explicit yes for that option and price. The bot does not complete it.

4. Safety bans email and DMs. Booking sites confirm stays through in-app messages to a host, property, or support. That channel is open.
   Suggested fix: add "Never message a host, property, or support channel."

5. Deadline-watch tells the owner "keep or cancel?" The same skill says never cancel or change a booking. The question offers a cancel action the bot is not allowed to take.
   Suggested fix: remind with "I can't cancel or change this. If you want out, cancel it yourself on the site before the deadline. Reply 'keep' and I won't mention it again."

6. Children's ages are written into durable log memory when the owner shares them. Event-trip stores the venue and only forbids results, times, and club details. School, team, coach, and opponent are not forbidden. Ages plus home base plus venue and dates can identify a child.
   Suggested fix: do not store ages, school, team, club, coach, or opponent. Ask ages only inside the current search. For events, store city and dates, and keep the venue in that search thread only.

7. Deadline-watch invites "confirmation details" and says what to keep, not what to drop. A pasted confirmation usually includes guest names, email, phone, address, and a confirmation code.
   Suggested fix: "If a confirmation is pasted, store only the property name, the dates, and the free-cancellation deadline. Do not store guest names, emails, phones, addresses, confirmation codes, loyalty numbers, or payment traces."

8. The booking-site rule says not to create accounts, save cards, or change settings. A session the owner already signed in can still open saved travelers, cards, past trips, and the inbox.
   Suggested fix: add "Do not open payment methods, saved travelers, past bookings, or the inbox. Never ask for a password."

9. The honesty rule says the bot gives no legal, visa, or financial advice, then says to "point to the official government source." That is how a model invents a government URL. Credit cards, insurance, loans, and "this area is safe for kids" are not banned.
   Suggested fix: "Do not interpret entry rules. Do not recommend cards, points programs, loans, or insurance. Do not call a neighborhood safe or unsafe. Do not invent a government URL. Name the agency and tell the owner to look it up."

## (c) Clarity and usability for a stranger importing it

10. The title is still "Template draft: Family Weekend Trip Deal Hunter," so the packed file looks unpublished.
    Suggested fix: title the file with the profile name only.

11. Profile memory still contains `{your cancellation window, default 7 days}`, `{your timezone}`, `{your preferred booking site(s)}`, `{number of travellers...}`, and `{your quiet hours}`. Getting-started says "replace the placeholders" and gives no example of a finished log line, so an importer cannot tell when setup is done.
    Suggested fix: add "Text in {braces} is a setup slot. Replace it with the owner's answer before the first search, and never show the braces." Add one example: `(log) Home base: city the owner named. Travel radius: 3 hours by train. Budget: 800 in the currency they named, per trip. Party: 2 adults, 1 child. Sites: site they named. Cancellation window: 7 days. Quiet hours: 21:00–07:00 in their timezone.`

12. The intro says "one at a time," then question 1 asks for home base and travel distance, and question 4 asks for booking sites and the cancellation window.
    Suggested fix: split those into four questions and wait for each answer.

13. Routines are "None by default," while deadline-watch promises reminders 48 hours and 24 hours before a deadline. The routines section also offers a weekly "weekend deals" scan "during getting-started," and getting-started never asks about that scan. Nothing tells the importer what fires the reminders.
    Suggested fix: delete the weekly-scan sentence, or add a getting-started question that creates it and state that the scan only sends this owner a shortlist. Add one routine: once a day at a fixed local time outside quiet hours, remind only if a stored deadline falls inside 48 hours or 24 hours; otherwise send nothing.

14. Quiet hours may be broken when a free-cancellation deadline is inside 24 hours. Deadline-watch says both reminders happen outside quiet hours.
    Suggested fix: pick one rule. Use "Never message during quiet hours. If the 24-hour mark falls inside quiet hours, send that reminder at the last allowed minute before quiet hours."

15. "Cancelled for free until at least 7 days before arrival" and "free to cancel until the day before are best" pull in opposite directions. Question 4 ("how many days before arrival should free cancellation last?") can mean either a latest deadline or a minimum notice period.
    Suggested fix: "Prefer the latest free-cancellation deadline. Skip a rate whose free-cancel deadline is earlier than N days before arrival. Default N is 7. A deadline on the day before arrival is the best match."

16. Plugins are none, the shortlist skill says "Search the preferred site(s)," and honesty forbids invented prices. An importer cannot tell how a live price is fetched, or what to do when the bot cannot open the site.
    Suggested fix: "If this bot can browse, search the preferred site and cite the page and the check time. If it cannot, ask the owner to paste listings and label the shortlist unverified. Never guess a price, a rating, or a travel time."

17. Getting-started is skill 4, with no statement that it blocks search. Budget is "per night or per trip," so two answers cannot be compared. Currency is never asked. There is no rule for fewer than 3 matching stays, so the "give 3–5 options" line invites padding.
    Suggested fix: "On first run, use only getting-started. Do not search until each answer is saved." Ask for one budget unit (total for the stay) and the currency. "If fewer than 3 rates qualify, show only those and say how many matched. Do not pad with non-refundable or over-budget stays."

18. Question 6 says the bot will "turn on event-trip planning," and the wrap-up says to turn that skill on or off. The file does not say the platform can disable a skill. An importer who leaves the text in place will still get sports questions after the owner said no.
    Suggested fix: "If the owner says they do not travel for sports, do not ask event questions. Leave the skill text in the file."

19. Party size lives in a profile placeholder and again in the log line ("party makeup"), so it is unclear which one search should read.
    Suggested fix: keep the profile party line as the rule only (counts the owner chooses to share; no names, birthdates, passport or ID numbers, or health details). Keep the numbers only on the log line.

## (d) Storefront appeal of name and description

20. "Family Weekend Trip Deal Hunter" sounds like a Saturday–Sunday bargain bot. The body is a free-cancellation shortlist for weekends, 3–4 day trips, and optional sports travel. "Deal Hunter" promises a bargain the skills never define.
    Suggested fix: name it "Family Short-Break Finder." Description: "Shortlists a few family stays for weekends and 3–4 day breaks, free cancellation first. Kids' sports trips are optional. You book every stay yourself."

21. The storefront line "nothing is booked, held or paid for without your explicit yes" still means the bot books after a yes. That fights the shortlist-only rule and is the weaker promise.
    Suggested fix: put the stronger line on the label: "You book every stay yourself. This bot only shortlists and never pays, reserves, or holds."
