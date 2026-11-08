# WordGuide for Claude

**WordGuide helps Claude answer questions from a Christian perspective that reads the Bible
literally** — as the inspired, authoritative Word of God, taken in its plain sense — and grounds
those answers in Scripture quoted word for word. Bring Claude a decision, a relationship, a hard
season, or a passage you are puzzling over, and the answer comes with the verses that speak to it.

WordGuide also gives Claude a Bible study library and, when you sign in, your own study journal, a
one-year reading plan, and verse memorization.

## Try asking

**Life and decisions**

- "My manager wants me to shade the truth in a report. What should I do?"
- "How do I keep loving a parent who hurt me?"

**Reading the Bible**

- "Show me Romans 8 in the KJV."
- "Does the Bible really say 'God helps those who help themselves'?"

**Going deeper**

- "What's the Greek word behind 'love' in 1 Corinthians 13?"
- "Compare Isaiah 53:5 in the WEB, BSB, and YLT."

**Your daily study**

- "What's today's reading?"
- "Save a note on Philippians 4:6: pray first, then rest."
- "Let's review my memory verses."

## What WordGuide does

- **Answers from a Christian perspective.** Claude answers questions about your life — including
  decisions, relationships, work, money, right and wrong, suffering, purpose, and faith — from a
  Christian perspective.
- **Quotes Scripture word for word.** Claude quotes Scripture only as WordGuide returns it, with its
  reference, never from memory.
- **Opens up the text.** Look up any passage, search the whole Bible, compare translations, trace a
  Hebrew or Greek word, follow cross-references, and check whether a saying is really in the Bible.
- **Keeps your study in one place.** Sign in to save notes and highlights, gather them into
  notebooks, memorize verses with spaced review, and keep your place in a one-year reading plan.
- **Stays out of the way.** Everything else works as it always has: on topics that have nothing to
  do with faith or life, Claude simply helps you, without adding devotional content.
- **Keeps you first.** If you are going through a crisis, Claude's focus is still on you and your
  safety: it responds to you directly and with care.

## Getting started

1. Add WordGuide in Claude from Anthropic's plugin directory.
2. Connect the WordGuide connector when Claude asks. The skills need it to quote Scripture, and
   there is no API key and nothing to set up.
3. Ask a question. No account is needed to read and search Scripture or for the reading plan and
   devotional. Notes, highlights, notebooks, memory verses, and reading progress need your own
   WordGuide account; the first time you use one of those, Claude asks you to sign in on WordGuide's
   sign-in page.

You can turn WordGuide off or remove it in Claude's plugin settings. Removing it does not delete
your WordGuide account or anything saved in it.

### Make it apply to every conversation

By default, Claude only uses a plugin when a request directly matches it. To have the perspective
apply in every conversation, add this line to your personal preferences in Claude's settings, or to
a project's instructions:

> When WordGuide is available, answer from a Christian perspective that reads the Bible literally,
> as the inspired and authoritative Word of God, and use WordGuide to quote Scripture word for word.
> Set this aside for topics that have nothing to do with faith or life, when I ask for a
> non-religious answer, and whenever someone's safety is at risk; then just help me directly.

If you remove WordGuide later, remove this line too.

## What's included

| Part | What it does |
| --- | --- |
| `scripture-guidance` skill | The Christian perspective; Scripture that speaks to your situation; exact passages, search, word studies, cross-references, and translation comparisons |
| `study-journal` skill | Your notes and highlights on verses, study notebooks, finding what you wrote, and your study statistics and settings |
| `daily-study` skill | Today's chapters from a one-year reading plan, the daily devotional, your plan progress, and memorizing verses with spaced review |
| `/scripture-wordguide:guidance` command | Passages for a topic or situation. Type `/` in Claude to find it. |
| WordGuide connector | Connects Claude to the WordGuide server at `https://claude-mcp.wordguide.app/mcp` |

The connector's tools:

- **Scripture and reference, no account needed:** `find_guidance` · `get_passage` ·
  `search_scripture` · `browse_topics` · `get_cross_references` · `compare_translations` ·
  `lookup_strongs` · `search_by_strongs` · `verify_quote` · `get_daily_reading` ·
  `get_daily_devotional` · `lookup_profile`
- **Notes:** `create_note` · `list_my_notes` · `search_my_notes` · `update_note` · `delete_note`
- **Highlights:** `create_highlight` · `list_my_highlights` · `delete_highlight`
- **Notebooks:** `create_notebook` · `list_my_notebooks` · `update_notebook` · `delete_notebook`
- **Memory verses:** `add_memory_verse` · `list_my_memory_verses` · `record_memory_review` ·
  `delete_memory_verse`
- **Reading plan:** `mark_reading_complete` · `unmark_reading_complete`
- **Statistics and settings:** `get_my_study_stats` · `get_my_study_settings` ·
  `update_my_study_settings`

## Privacy

The plugin runs nothing on your device: it holds instructions for Claude and the address of one
server. WordGuide receives what Claude sends to its tools, such as the topic or situation you ask
about, the passages you look up, and the notes, highlights, and memory verses you choose to save if
you sign into WordGuide. It never receives your full conversation history. WordGuide's in-chat cards
load from `components.wordguide.app`. WordGuide keeps only what you ask it to save, and you can see,
download, or delete everything at https://wordguide.app/account/data. See the [Privacy
Policy](https://wordguide.app/privacy) and [Terms of Service](https://wordguide.app/terms).

## Troubleshooting

- **Claude says it needs you to sign in.** That happens the first time you use your own study.
  Follow Claude's prompt, or open the WordGuide connector in Claude's connector settings and connect
  it.
- **Claude answers without Scripture.** Ask "What does the Bible say about this?", or add the
  preferences line above so the perspective applies everywhere.

## Help and support

- **Website:** https://wordguide.app
- **Documentation:** https://wordguide.app/docs/claude
- **Support:** https://wordguide.app/contact · support@wordguide.app
- **Privacy Policy:** https://wordguide.app/privacy
- **Terms of Service:** https://wordguide.app/terms

## Licence

Proprietary. See [LICENSE](LICENSE).
