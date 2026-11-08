---
name: daily-study
description: Runs the user's daily Bible routine in WordGuide — today's chapters from a one-year reading plan, the day's devotional, keeping track of which plan days they have read, and memorizing verses with spaced review. Use when the user asks for today's Bible reading or devotional, where they are up to in the plan, to mark a day as read, to memorize a verse, or to review or manage their memory verses — and before calling any WordGuide reading-plan, devotional, or memory-verse tool, so a review never gives the verse away. The reading and devotional need no account; progress and memory verses need the user to sign in to WordGuide.
---

# Daily Study

A daily rhythm of reading and memorizing Scripture, kept in the user's own WordGuide account.

## The user's local date

WordGuide's server keeps time but does not know the user's time zone, so it cannot tell which
calendar day it is for them. Every tool here that takes a date gets the user's own date, as
YYYY-MM-DD: `date` for `get_daily_reading` and `get_daily_devotional`, and `local_date` for
`list_my_memory_verses`, `add_memory_verse`, `record_memory_review`, `mark_reading_complete`, and
`get_my_study_stats`. Work it out from the current date and what you know of where they are, and go
with your best estimate rather than asking.

## The reading plan

- **Today's reading**: `get_daily_reading` with today's date. It returns four chapters on two
  tracks, group study and individual study, which together cover the Bible in a year. The readings
  share no theme for the day, so do not invent one. The full text comes back; no second call is
  needed.
- **Where they are up to**: `get_daily_reading` with today's date and `next` set to true. For a
  signed-in user this shows their next unread day of the plan.
- **Marking a day read**: only when the user says they have finished it. Call
  `mark_reading_complete` with `plan_day` set to the plan day the reading result showed (its `date`,
  as MM-DD) and `local_date` set to their local date. Never mark a day because you showed it.
  Marking a day that is already complete does no harm.
- **Undoing a day**: `unmark_reading_complete` changes their plan position and streak. Confirm with
  the user before calling it.
- **The devotional**: `get_daily_devotional` with today's date. It names the classic devotional it
  comes from; mention the source.

## Memory verses

- **Adding a verse**: `add_memory_verse` with the reference and their local date, when the user asks
  to memorize it. Adding a verse already on their list keeps its progress.
- **Reviewing**: call `list_my_memory_verses` with `status` set to `due` and their local date. Do
  not show or hint at a due verse's text before the user has tried it: your reply must not contain
  any of its words, not even the opening words as a prompt. The result appears as WordGuide's memory
  card: one verse at a time, reference first, the text hidden until the user reveals it, then
  buttons for "I recalled it" and "I missed it" that record the review. Let the card run the review:
  tell the user their verses are on the card, and record nothing yourself, because you cannot see
  what they tap and a review recorded twice moves a verse on twice. If they type an attempt here
  anyway, tell them how it compares and leave the marking to the card.
- **Nothing due**: say so, and give the next review date the result names.
- **Removing a verse**: `delete_memory_verse` also deletes its review history. Confirm with the user
  before calling it.

## Signing in

The reading plan and the devotional work without an account. Plan progress and memory verses need
the user to sign in to WordGuide. If a tool cannot run because they have not signed in, Claude
offers them WordGuide's sign-in; do not retry the call in a loop. Carry on with what needs no
account, and once they have signed in, do what they asked.

## Ground rules

- Record nothing as a side effect, and do not assume the user would want something recorded: no day
  marked read, no verse added, and no review recorded unless the user said so.
- Use identifiers exactly as a WordGuide result returned them in this conversation: a
  `memory_verse_id` from `list_my_memory_verses` or `add_memory_verse`, and a plan day from
  `get_daily_reading`, or one the user names. Never guess or construct one; look it up first.
- Quote Scripture exactly as WordGuide returned it, cite the reference, and include any
  `attribution` credit line the result carries. Never cite a reference that no tool call returned.
