# Adversarial review: Grok Bot template launch

Reviewed `launch/STRATEGY.md` at `01b5346`. This review uses the live schedule, not the calendar inside that file. Nothing here was posted. Templates were not published or edited. `STRATEGY.md` was not modified. Any wording under "Drafts" is for Antonio to approve or reject. It is not cleared to post.

Live facts used: Tuesday 29 September 2026, about 12:03 Europe/Madrid, @antoniostoner posted the hook plus a thread (10 posts). No template is published. Each one still needs his manual confirm, so there is no share link. Madrid is UTC+2 this week.

Real remaining schedule under review:

- Tue 29 Sep 17:30: Promise Tracker: No Proof, Not Done
- Wed 30 Sep 09:30: Daily Habit Check-in
- Wed 30 Sep 17:30: Family Getaway Finder
- Fri 2 Oct 14:30: combined LinkedIn post
- Mon 5 Oct 17:30: X recap
- One X Article per bot. Bot Team Health Check is the fourth template and has no time on this list.

## Score

5/10.

The hook, the claims boundary, the refusal to use engagement bait, and the article drafts are sound. The launch that is actually live breaks the file's own rule: do not post until the first link is real. A giveaway with nowhere to go cannot be imported, bookmarked as a template, or defended when someone replies "where is it?". The real schedule then omits the fourth template, so Friday's "four templates" LinkedIn post is not yet something he can publish honestly.

## Top 5 changes, by impact

### 1. Do not publish another post until that post contains a working import URL

Impact: this is the whole launch. The 12:03 thread already promised four free templates and closed with "link lands with the article." There is still nothing to import.

(opinion) A second linkless post at 17:30 would teach people to ignore the account. The file already says to move the calendar rather than launch with no link. That rule was missed at noon. It should hold at 17:30.

Before 17:15, manually confirm and publish only Promise Tracker. Open the share URL in a private window. If a stranger cannot see the template, it is not a share link, and the 17:30 post does not go out. Do not batch-confirm the other three in a hurry just to fill the thread.

The published For You ranker does not treat "contains a link" as a negative weight. The default `OpenLinkWeight` is 0.2, and the file header says those defaults were last synced 2026-09-28. Weights multiply predicted probabilities, not raw counts, so this is not "one reply equals 25 link clicks." Source: https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/home-mixer/params/param.rs and https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/README.md

(opinion) Hiding the only useful URL in a reply, which `STRATEGY.md` still specifies for the thread index, is the wrong trade. People who do not open the thread never see it. Put the import URL in the 17:30 post body and in the X Article. Also reply on the noon thread with the same URL, so the people already there can finish the job.

### 2. Put Bot Team Health Check on the calendar before LinkedIn

The real list has three bot slots and then a LinkedIn post that, in `STRATEGY.md`, presents all four. Health check is named as the fourth template and has no time. Friday 2 Oct 14:30 cannot say "four templates" unless that link is already real. The file's own gate is correct: LinkedIn waits until all four links exist.

(opinion) Thursday 1 October 2026, 17:30 Madrid, is the empty US-overlap slot (11:30 US Eastern, 08:30 US Pacific). Use it for the Health Check article, not for a reshare. Promise Tracker at Tuesday 17:30 is a reasonable recovery: the noon thread already stated the safety rule, and "no proof, not done" is the line most likely to be repeated. Shipping Health Check fourth is fine. Forgetting it is not.

If Thursday 17:30 slips, move LinkedIn to 14:30 on the next weekday after the fourth link exists. Do not ship a three-link post that still says four.

### 3. Treat the noon thread as a 48-hour object, and repeat every URL in a new post

The published For You pipeline's `AgeFilter` removes posts older than 48 hours. Source: https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/README.md

The noon thread therefore drops out of that candidate set around 12:03 Madrid on Thursday 1 October. A reply added later does not create a new root post. Monday 5 October's recap must contain the four import URLs in the post itself. "Link in the Tuesday thread" will point at a post the For You age filter has already removed.

`STRATEGY.md` still says the first reply is the index that gets edited as links go live. Keep that reply for people who already opened the thread. Do not make it the only place the URLs live. Each bot post, the Friday X note if he still wants one, and the Monday recap should carry the URLs again.

(opinion) Do not delete the noon thread. It is the public record of the promise. Correct it with a reply once a real URL exists.

Author diversity is not a reason to fear a second post today. The README describes a repeated-author decay, but the scorer wired in this commit sets `enable_author_diversity` to false and both the decay and the floor to 1.0, which does not decay anything. Source: https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/home-mixer/scorers/value_model.rs and the README section "Scoring and Ranking." (opinion) The reason to keep Tuesday to one new bot at 17:30 is that he can host only one reply thread well, which the strategy already says. It is not because the checked-in ranker punishes a second post.

### 4. Add one real screenshot to each X Article, and use the LinkedIn carousel as the bundle

The article drafts are text only. They describe safety rules a stranger cannot see. The available proof is the bot's own words after he confirms it: the opening line, and the line that it only messages him and drafts the chase. No other person's data, no tokens, no made-up chat.

Photo expand and video open are scored actions. Defaults in the same params file: `PhotoExpandWeight` 0.05, `VideoOpenWeight` 0.07, `ContDwellTimeWeight` 0.004, `ContClickDwellTimeWeight` 0.4. Source: https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/home-mixer/params/param.rs

(opinion) Those weights are small next to a reply (default `ReplyWeight` 5.0). A screenshot will not "beat the algorithm." It will show the product. One still image of the Promise Tracker intro is enough for 17:30. A short screen recording is optional and only if it is the real confirm screen. Do not invent a UI.

Secondary guides say an X Article can carry a title, headings, and images, and that it needs X Premium. This review did not get a copy of the official help page (help.x.com returned a challenge), so treat the formatting details as secondary: https://tweetloft.com/blog/how-to-use-twitter-x-long-form-posts-notes

LinkedIn: Buffer's 2026 study of 4.8 million posts found Friday at 3 p.m. and Friday at 4 p.m. local time among the strongest slots, and reported that carousel (document) posts generated up to 596% more engagement than text-only posts in that dataset. Source: https://buffer.com/resources/best-time-to-post-on-linkedin/

(opinion) Friday 14:30 Madrid is 30 minutes before Buffer's cited Friday 3 p.m. peak, and other 2026 writeups still prefer European morning. Do not move LinkedIn for that half hour. Do use the carousel outline already in `STRATEGY.md`, with the real URLs on the last slide. The 596% figure is Buffer's result, not a forecast for this post. Other timing studies disagree with Buffer; the honest claim is "Friday afternoon local is a supported slot in one large dataset," not "14:30 is optimal."

### 5. Reply on the live thread during this window, and do not fish for engagement

The file schedules the launch reply block for 17:30 because it assumed the launch was at 17:30. The launch was at 12:03. The useful replies are the ones happening now.

Answer a real question with the rule from that template, in two or three sentences. If someone asks where the link is, the true answer is that nothing is importable yet and Promise Tracker is planned for 17:30 only if the confirm succeeds.

Do not ask for a like, repost, follow, bookmark, or a keyword reply. X's Original Content Rewards Program, as reported in September 2026, can disqualify creators who repeatedly ask for likes, reposts, replies, bookmarks, or follows in order to raise engagement. That is a payout rule, not a published ranker weight. Source: https://www.complex.com/pop-culture/a/markelibert/x-original-content-rewards-program-creator-payouts

(opinion) The no-bait rules already in `STRATEGY.md` are the right ones to keep. The noon hook does not break them. Leave the hook up. Do not post a new "viral" variant today.

Social proof: do not add a user count, a saved-hours claim, or a testimonial. The file's ban on invented numbers is correct. The screenshot in change 4 is the proof that exists.

## Next 6 hours (about 12:15 to 18:15 Madrid, Tuesday 29 September 2026)

All times Europe/Madrid. 17:30 is 11:30 US Eastern and 08:30 US Pacific (CEST is 6 hours ahead of EDT and 9 hours ahead of PDT).

1. 12:15 to 12:40. Read the live thread and every reply. Note impressions, bookmarks, replies, and profile visits for the 12:03 post. Link clicks should be zero. That row is the baseline. Pin the thread if it is not pinned. Do not delete it. (opinion) Deleting a launch that people may already have seen looks worse than a plain correction.

2. 12:40. If there are questions, reply with the template rule only. If someone asks for the link, use the status draft below only after approving that exact text. If there are no questions, one status reply is still worth posting, same condition: his yes on the exact text first.

3. 12:50 to 16:15. Manually confirm and publish only Promise Tracker. Load the share URL logged out. If it fails, stop. The 17:30 slot is cancelled, not replaced with another teaser. Do not confirm Habit, Getaway, or Health Check in this window unless Promise Tracker is done and there is spare time that does not risk a bad confirm. Those three are not today's posts.

4. 16:15 to 16:45. If the URL works, capture one screenshot of the bot's own opening text. Crop out names, emails, and any other person's details. If the confirm screen cannot be captured cleanly, ship the post without an image. Do not draw a mock.

5. 16:45 to 17:15. Read the 17:30 draft below and the noon-thread follow-up. Change whatever is wrong. Nothing posts until he has said yes to the exact characters, including the real URL pasted in place of the bracket.

6. 17:30. Post the Promise Tracker pointer with the URL in the body, plus the screenshot if he has one. If an X Article is ready, publish it in the same slot with the URL and the image inside the article, and let the pointer tweet carry both the article and the import URL. If the article is not ready by 17:15, post the short tweet anyway. Do not miss a working link in order to finish formatting. (opinion)

7. 17:31 to 17:40. Reply on the noon thread with the same URL, using the follow-up draft only if he approved it. Edit the thread's link-index reply so Promise Tracker shows the URL and the other three still say they are not up.

8. 17:40 to 18:15. Stay in the new post's replies. Correct a factual miss once: it does not message the promiser, it does not close on "done," and it does not spend. Do not post Habit Check-in, Getaway Finder, or Health Check today. Do not post a second hook.

If the confirm is not done by 17:15: do not post at 17:30. Approve the status draft if it is not already on the thread, and move Promise Tracker to Wednesday 30 Sep 09:30. Move Habit Check-in to Wednesday 17:30. Move Getaway Finder to Thursday 1 Oct 17:30. Health Check then needs a new slot before LinkedIn, or LinkedIn moves. Never stack two new bots into Wednesday 17:30 to catch up.

## Drafts for approval

These are not posted. Replace the brackets with the real URL. If the URL does not work, do not post draft B or draft C.

Draft A, reply on the noon thread, for use only while no template is live:

"Nothing is importable on this thread yet. I still have to confirm each template before it can be shared. Next up is Promise Tracker, aimed at 17:30 Madrid today, and only if that confirm works. I will put the link in that post and back on this thread. The other three are not up."

Draft B, Tuesday 29 Sep 17:30 post:

"Free Grok Bot template: Promise Tracker. 'OK, on it' stays open until you confirm proof that matches the bar. It drafts the chase. You send it. It only messages you, in its chat.

[REAL URL]"

Draft C, reply under the noon thread immediately after draft B is live:

"Promise Tracker is the first one you can import: [REAL URL]. A promise stays open until you confirm the proof. I send the chase myself. The other three templates are not published yet."

## What should stay

- The hook that is already live. It does not invent a count of assistants, and "on their own" does not claim the trip bot will book if he says yes. (opinion) It is the right launch sentence. The miss was posting it before a link existed.
- One bot per slot. Wednesday 09:30 and Wednesday 17:30 are far enough apart to host separately. (opinion) 09:30 Madrid is 03:30 US Eastern, so it is a Europe morning post. That fits a Spain-based account. It is a weak US slot. Do not also expect US follow-through on the habit bot until a later pointer, which this schedule does not have. That is acceptable if Thursday and Friday carry the set again.
- The ban on fake metrics, medical or money claims, and "the getaway bot finds discounts."
- The ban on reply-to-unlock, tag-a-friend, and like-if-you-agree.
- LinkedIn as one professional bundle with a carousel, after all four URLs exist, not a paste of the X thread. (opinion) Friday 14:30 can stay.
- Monday 5 Oct 17:30 as the recap, with the URLs repeated in the post, because of the 48-hour For You filter above.

## Measurement that matches this week

`STRATEGY.md` tells him to compare a Thursday 08:30 Family article with a Thursday 17:30 pointer. That pair is not on the real schedule. Family Getaway Finder is Wednesday 17:30 only. He will not learn the clock from a test he is not running.

(opinion) The comparison that is already running is the noon thread (no link) versus the 17:30 Promise Tracker post (link in the body), scored on bookmarks and link clicks at 24 hours. Write both rows down. Rank the four import URLs only after all four exist. Do not change today's claims based on likes.

## Sources

Published X ranking code, commit `a707cc27`, last sync stamp in `param.rs` 2026-09-28:

- https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/README.md
- https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/home-mixer/params/param.rs
- https://github.com/xai-org/x-algorithm/blob/a707cc27ba36d3fa79450c9cffcc48a82d080b02/home-mixer/scorers/value_model.rs
- https://github.com/xai-org/x-algorithm/commit/a707cc27ba36d3fa79450c9cffcc48a82d080b02

Other:

- https://buffer.com/resources/best-time-to-post-on-linkedin/
- https://www.complex.com/pop-culture/a/markelibert/x-original-content-rewards-program-creator-payouts
- https://tweetloft.com/blog/how-to-use-twitter-x-long-form-posts-notes

Every sentence in this file that is not tied to those URLs, to the templates, or to the live schedule above is marked (opinion). Blog posts that claim a large percentage reach cut for links were not used. Those cuts are not in the published default weights cited here.
