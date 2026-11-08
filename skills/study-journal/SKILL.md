---
name: study-journal
description: Keeps the user's own Bible study in WordGuide — notes and highlights anchored to verses, study notebooks, finding what they wrote, study statistics, and what is recorded about them. Use when the user asks to save, find, edit, file, tag, or delete a note or highlight, to start, rename, or delete a notebook, to read a passage together with their own notes, to see how their study is going, or to turn reading tracking on or off — and before calling any WordGuide note, highlight, notebook, statistics, or settings tool. Requires the user to sign in to WordGuide.
---

# Study Journal

The user's notes, highlights, and notebooks live in their own WordGuide account. This skill keeps
them the way the user wants them: saved when asked, found when needed, and never lost by surprise.

## Signing in

Every tool here acts on the user's own WordGuide account. If one cannot run because they have not
signed in, Claude offers them WordGuide's sign-in; do not retry the call in a loop. Carry on with
anything that needs no account, and once they have signed in, do what they asked.

## Save only what the user asks you to save

- Create a note, highlight, or notebook only when the user asks for it in so many words. Never
  record anything as a side effect of a conversation, and do not assume they would want it saved. If
  saving seems useful you may offer once, then wait for a yes.
- Save the user's own words. Do not rewrite or expand a note they dictated. If they ask you to draft
  one, show it to them before saving it.
- Anchor each note or highlight to the passage the user means. If it is unclear, ask.
- In Claude's chat, WordGuide's passage view has its own buttons for highlighting a verse and adding
  a note, and you cannot see what the user taps. If they say they saved something there, do not save
  it again.

## Choosing the tool

| The user wants | Tool |
| --- | --- |
| To save a note on a verse or passage | `create_note`, optionally into a notebook and with tags |
| Their notes on a passage, in a notebook, with a tag, or from a period | `list_my_notes` — for a period, give `created_from` and `created_to` as their local dates and `utc_offset_minutes` for their time zone |
| A note found by what it says | `search_my_notes` |
| To change a note's text, tags, or notebook | `update_note` (the passage it is anchored to cannot change) |
| To highlight a passage | `create_highlight`, in yellow, green, blue, pink, or orange |
| Their highlights | `list_my_highlights` |
| To start, list, or rename notebooks | `create_notebook`, `list_my_notebooks`, `update_notebook` |
| To read a passage with their own notes and highlights | `get_passage` — when they are signed in, their notes and highlights for that passage come back with the text |
| How their study is going | `get_my_study_stats`, with their local date (YYYY-MM-DD) so it can count memory verses due |
| What is recorded about them | `get_my_study_settings` |
| To start or stop tracking which passages they read | `update_my_study_settings` |
| To remove a note, highlight, or notebook | `delete_note`, `delete_highlight`, `delete_notebook` |

## Use the identifiers WordGuide gives you

Editing or deleting takes an identifier: `note_id`, `highlight_id`, or `notebook_id`. Use one that a
WordGuide result returned in this conversation. If you do not have it, find it first with
`list_my_notes`, `search_my_notes`, `list_my_highlights`, or `list_my_notebooks`. Never guess or
construct an identifier.

## Confirm before anything is lost

- Before `delete_note`, `delete_highlight`, or `delete_notebook`, say exactly what will be removed —
  quote the note, or name the highlighted passage and its colour, or name the notebook — and wait
  for the user to confirm.
- Deleting a notebook does not delete its notes; they become unfiled. Say so when you ask.
- Turning tracking off with `update_my_study_settings` deletes the reading records already
  collected. Say so, and wait for the user to confirm before turning it off. Turning it on needs
  only their request.
- Afterwards, report what WordGuide says happened, such as how many notes became unfiled or how many
  records were removed.

## Quoting Scripture

When you show Scripture beside the user's notes, quote it exactly as WordGuide returned it, cite the
reference, and include any `attribution` credit line the result carries. Never cite a reference that
no tool call returned.

## Their data

If the user asks how to see, export, or delete everything WordGuide holds about them, point them to
https://wordguide.app/account/data, where they sign in with the same email address.
