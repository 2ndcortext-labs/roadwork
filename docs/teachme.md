# Teach me the road plans

This file is a walk-through of how work is planned and recorded in this project, written for a person first. It uses plain names; the word the session agent [the agent running your session] uses for the same thing follows in brackets the first time. When you answer a "tell me more" offer with yes, this file is what the session agent reads to answer you. If you want one thing explained, type `/roadwork-help <thing>`. The plain word for every term the session agent uses, and for the git words, is in `docs/terms.md`, one row per term; read that table first.

## Where work is recorded

Your project has one work-plans folder [road plans, the `roadwork/` folder — the register], at the path your project's law names; no folder under the project carries its own. It is a copy of a remote [a clone: fetched from and merged, never pushed to; its commits stay local]; the remote supplies the folder's skeleton, the docs, the rule and the skills, never a map and never an item — maps and items are yours, and when the copy is updated the remote's docs win. Inside, three sub-folders: `todo/` for fixes, chores, decisions to take and findings to trace; `feature/` for new capabilities; `spark/` for ideas parked for later, never worked. Inside each, one folder per goal [a destination] holds that goal's items and an `archive/` where its finished items go, whole, never deleted; an item filed before its goal is navigated waits in `unnavigated/`. Beside them: `docs/` for documents that outlast any one item (this file lives there), and `destinations/` for the larger goals — one product requirements document [a destination, `<slug>.prd.md`] per goal, made with you and later broken into items. Beside them too, `maps/` holds the ways destinations are reached, one map per way [a map: the process, the tools, the judgements, the inputs, and how it was done before agents were in the picture].

## One item, four files

A todo or a feature is a folder of exactly four files. The item file (`todo.md` or `feature.md`) holds your notes as you gave them, word for word, the session agent's reading of them marked as its own, and a numbered list of what the filing did not decide. `intent.md` says what is wanted and why, in your words, after an interview. `spec.md` says exactly what changes and how anyone checks it. `plan.md` says in what order it is built and the gates the build must pass. A spark is one file, `idea.md`, and nothing else.

## The lifecycle

Work moves through skills, each one a command you type. In order:

- `/roadwork-destination` — makes a destination with you: a bare call lists the destinations you have; with a name and a description it interviews you and writes the document; a pasted document is saved as it came and interviewed from.
- `/roadwork-map` — makes a map with you: how a destination is reached — the process, the tools, the judgements, the inputs, and how it was done before agents; the interview and spec skills follow the map an item names.
- `/roadwork-nav-to-destination <slug>` — turns one destination into a group of items and a sanity todo you check before anything in the group starts. `/roadwork-navsanity <group>` is that check, thorough, six kinds.
- `/roadwork-ingest` — files one item from your notes: decides todo or feature and says why, places it in the order, prepares the first questions. `/roadwork-tasksplit` files many todos from a list at once.
- `/roadwork-intentify <ref>` — the interview. It reads your notes back, asks two questions, then works the design tree in rounds until nothing is left assumed. Writes `intent.md` when you confirm.
- `/roadwork-specplan <ref>` — writes `spec.md` and `plan.md` from the accepted intent, has fresh reviewers check both, and hands them back. Accepting a spec is not a go.
- `/roadwork-make <ref>` — the go. Only this, or your word "build", starts work. It puts the item in process and builds under the gates, one after another; a bare call lists what could be built now.
- `/roadwork-verify-and-archive <ref>` — evaluates what was built, asks you what to do with anything short, and on your word moves the item to its goal's `archive/` with its resolution recorded.

Beside the chain, `/roadwork-help` answers: with nothing after it, the map; with a skill, an item or a term, that one thing. It writes nothing.

Every skill ends by offering the next step as a command you can copy, never by running it.

## The loose order and the in-process list

`ordering.md` is the list of what comes next, top first, kept loose by judgement, with one clause per line saying why it sits there. Groups are indented blocks. `working.md` lists what is in process right now, one line per item, dated; a line is removed when the item is archived.

## The kind test

A todo is done once and is then over. A feature is built once and reused when built. That is the test, generally; your naming overrides it.

## How to name a thing

In the plans: `todo/<item-name>`, `feature/<item-name>`, `spark/<item-name>`; from anywhere, `main/<kind>/<item-name>` [the register's prefix; your project's law may alias it]. Item names are kebab-case, in your words, chosen at filing, never reused.

## How offers look

Anything the session agent suggests you type is printed in its own code box, nothing else in the box, so you copy it in one gesture. One plain sentence before the box says what typing it does. Several commands that run as one line share one box, joined with ` && `. The glossary entry **Offer form** in every skill carries this rule. Where your session can show a list you tick, the offers come as that list instead, with a free-text choice for anything else; a tick is the same as typing the command.

## The bare calls

Some skills, typed with nothing after them, list instead of act. `/roadwork-spark` lists the open ideas, grouped by which could become one item together. `/roadwork-destination` lists the register's destinations and whether each has been turned into items. `/roadwork-make` lists what could be built now. A bare call writes nothing.

## One item, start to finish

Say a thought crosses your mind: the greeting the tool prints is stale. You type `/roadwork-spark the greeting is stale, fix the wording`. A spark is filed as `spark/greeting-is-stale`, your words kept, one round of questions asked, and it rests.

A week later the bare `/roadwork-spark` lists it. You type the ingest command it offers. `/roadwork-ingest spark/greeting-is-stale` files `todo/fresh-greeting` — a todo, because it is done once — places it in `ordering.md`, and moves the spark to its archive as converted. It offers the interview.

`/roadwork-intentify todo/fresh-greeting` reads your notes back, asks whether you have anything to add, then a round: which wording, where it prints, whether the old text is referenced anywhere else. You answer; it confirms the shared understanding; `intent.md` is written and accepted.

`/roadwork-specplan todo/fresh-greeting` writes the spec — one requirement: the new wording, printed at start, nowhere else — and the plan with one gate that checks it. Five reviewers read the spec, four the plan; what holds is folded in. You say "spec accepted".

`/roadwork-make todo/fresh-greeting` is your go. The item goes on `working.md`, the gate becomes its ledger, the build runs, the gate passes, the change sits in the project's held batch. It offers the archive.

`/roadwork-verify-and-archive todo/fresh-greeting` reports the gate met and the change landed or not yet, asks whether to archive now or wait for landing, and on your word moves the folder to `todo/archive/` with "shipped" recorded. It offers the next item from the top of the order.
