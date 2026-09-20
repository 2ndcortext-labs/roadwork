# Terms — the plain word, the agent's word, the meaning

_One row per term the session agent uses, and one per git word a person meets; read this before the teach-me. The plain word is yours; the agent's word is the one in the skills' glossaries; the meaning is one line._

| Plain word | Agent's word | Meaning |
|---|---|---|
| the work-plans system | Roadwork | The work-plans system by 2nd Cortex Labs: the plans and the skills that work them. |
| work-plans folder | Road plans | Your project's `roadwork/` folder, the one place its work is recorded; todos, features and sparks each in their own sub-folder. |
| a work item | Item | One folder holding a todo or feature file plus its intent, plan and spec; a spark holds one idea file only. |
| where an item lives | Home | Your project's one work-plans folder, at the path its law names; a copy of a remote, updated from it and never updating it. |
| an item's name-with-path | Reference (ref) | How an item is pointed at: `todo/<name>`, `feature/<name>`, `spark/<name>`, or `main/<kind>/<name>` from anywhere. |
| the item's header keys | Frontmatter | The block at the top of an item file: blocker, blocking, blocked-by, external, group, in-process, disposition. |
| the order file | `ordering.md` | The loose list of what comes next, top first; beside it `working.md` lists what is in process now. |
| you, the owner | Operator (user) | The human owner of the project; every decision is yours. |
| the agent in your session | Session agent | The agent running the session that typed the command. |
| everything in the project | Project scope | Everything at and under the root the project's law names; an item's Paths line says which of it the item touches. |
| one shipment | Batch | The coherent bundle a project's changes ship in as one pull request; the work-plans' own records stay local. |
| the chain of steps | Lifecycle | Goal, then group, then filing, then interview, then spec and plan, then the go, then verify and archive; the help skill answers beside it. |
| product requirements document | PRD | A document that says what a goal is: the goal, numbered requirements, what is out, how success is seen. |
| a goal | Destination | One product requirements document per goal, made with you and later broken into a group of items. |
| a way to a goal | Map | A written way of reaching a kind of goal: the process, the tools, the judgements, the inputs, and how it was done before agents. |
| the group's check item | Sanity todo | The todo created last for a group, holding the group list; nothing in the group starts until you say the group is right. |
| the six checks | Check types | The six checks run over a group: completeness, provenance, shape, dependencies, order, scope. |
| one check pass | Run | One pass of the six checks over a group, recorded as a dated section in the group's check item. |
| a group made by hand | Hand-made group | A group with no goal document; its requirements are its members' own claims and the group's line in the order file. |
| a build-together set | Cohort | Features in one group that helper agents can build at the same time because none depends on or shares files with another. |
| the stand-in for a cohort | Cohortmeister (CM) | A stand-in feature that blocks its cohort's members, is built in their place, and archives them when they all pass. |
| the five tests | Rubric | The five pass-or-fail tests a set of features must meet to be built together. |
| a rethink | Reconsideration | Running the spec skill again on an accepted spec that events have overtaken; the old go ends. |
| the fresh-eyes review | Verification round | Five fresh readers on a spec and four on a plan, one question each, before you see it. |
| the way-back offers | Back offers | After an interruption, up to five open steps offered, most recent first. |
| the item's folder name | Item name | The kebab-case name chosen when the item is filed, in your words, never reused. |
| several at once | Batch invocation | Several references on one line joined with ` && `, run as one command where the skill allows it. |
| a list-only call | Bare call | A skill typed with nothing after it lists instead of acting and writes nothing. |
| how offers look | Offer form | Anything you are invited to type is printed in its own code box with one sentence saying what typing it does, or offered as a choice to tick. |
| the fact at the end | Fact suffix | Now and then a hand-back ends with one fact about the system and a box that explains it. |
| a list into todos | Tasksplit | Any document or list turned into a dated group of todos, one per unit, the source's words kept. |
| your notes, word for word | Notes verbatim | Your words quoted exactly under a dated heading, never paraphrased; the agent's reading is marked as its own. |
| an item already filed | Duplicate | An open item that already carries the ask; judged, never matched by string. |
| the read-back | Read-back | Before any question, your notes and the agent's reading are read back to you and two questions asked. |
| a related item | Crossing / cross-note | Another item this one overlaps, shares a group with, or depends on; noted in that item's file, dated. |
| a concern | Area of concern | A clash between rules or a constraint that cannot be met, recorded with who decides it; never settled silently. |
| a pass-or-fail check | Gate | One observable outcome with a command that fails without it; the list of them is the ledger. |
| the go | The go | Your authorisation to build: the make command or your word; accepting a spec is not it. |
| the ledger | Ledger / `GATES.md` | The item's gates in the checker's form, kept in the item folder; a handoff is the hand-back when any gate is unmet. |
| one evaluated fact | Finding | One fact found at archiving (a concern, an unmet gate, a landing state, a dependent) put to you as a question. |
| how it was closed | Disposition | How an item was archived: shipped, withdrawn, superseded, decided, or abandoned. |
| an idea parked for later | Spark | One idea file, never worked; nothing waits on it; its only exit is conversion on your word. |
| a spark becoming work | Conversion | The one move a spark makes: turned into a todo or a feature on your word, the spark moved to its archive. |
| a spark's related line | Related | The one line of references written when a spark is filed; the only cross-item note a spark gets. |
| a saved record | commit | One saved snapshot of files with a message; what the checker reads as the record of a change. |
| a line of work | branch | A named line of saved records that can be worked apart from the main one. |
| a request to merge | PR | A pull request: asking that a line of work be brought into the main one; a shipment is one. |
| bringing lines together | merge | Bringing one line of work into another so both sets of records are in it. |
| getting the remote's records | fetch | Downloading the remote's records without changing your own files. |
| a local copy of a remote | clone | A full copy of a remote's records on your machine, linked to that remote. |
| sending records to the remote | push | Uploading your saved records to the remote; the work plans never do this. |
| the latest record | tip | The newest saved record on a line of work. |
| descends from | ancestry | Whether one record is in the history of another; how landing is proven, never by matching names. |
| a project's record store | repo | A folder whose history git keeps; a project, its work plans, or a remote. |
