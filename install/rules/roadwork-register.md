---
paths:
  - "**/roadwork-ingest/**"
---
# Roadwork register conventions — roadwork/
- **One register per project, `roadwork/`, at the path the project's own law names — no path under the project carries a register of its own —** with three sibling sub-registers:
  `todo/` (fixes, chores, decisions to take, findings to trace; item file
  `todo.md`), `feature/` (new capabilities; `feature.md`), `spark/`
  (ideas for later; `idea.md` only, no frontmatter, never worked). The test
  that tells the kinds apart: a todo is done once and is then over; a
  feature is built once and reused when built — generally; the Operator's
  naming overrides it (Operator, 2026-09-11/15). One
  folder per item, kebab-case item name, never reused and never a skill name (an item that builds or changes a skill is named for its outcome, not for the command — Operator, 2026-09-11); each item sits under its destination's folder — `todo/<destination-slug>/<item-name>/`, `feature/<destination-slug>/<item-name>/`, an item not yet navigated under `unnavigated/` — and each destination's folder has
  its own `archive/`, a sibling of its items; a navigation should generally exist as soon as a destination is established, and items filed before it inform it, to a degree, and move under it. Beside them, `docs/` (non-transitory documents — among them `docs/terms.md`, one row per glossary term and per git word a person meets: the plain word, the agent's word, the meaning; every glossary term has a row) and
  `destinations/` (one `<destination-slug>.prd.md` per destination, with
  `destinations/archive/` for the built ones) and `maps/` (one
  `<map-slug>.md` per map, with `maps/archive/` for the retired), each with an anchor
  (Operator, 2026-09-15). A todo or feature folder holds exactly four files:
  the item file, `intent.md` (the outcome wanted and why), `plan.md`
  (how, and how verified; "not yet scoped" is valid), `spec.md` (the
  buildable unit; "not yet specified" is valid). No `specs/` folder;
  the item file may carry a `**Paths:**` line under its owner line, as `/roadwork-ingest` §3 gives it.
  Ruling: the Operator's, 2026-09-10.
- **The register.** One per project, a clone of a remote Roadwork repository: fetched from and merged, never pushed to, its commits local. The remote ships the skeleton with its anchors, the docs, the rule and the skills — never a map and never an item; maps and items are the project's own, and in a merge the docs are the remote's to win. The project's law names the register's path and the alias, if any, of its reference prefix. A spec archived shipped graduates to the register's `docs/context/` as a decision record.
- **Frontmatter** opens every `todo.md` and `feature.md`, eight keys,
  always present, empty allowed (a `feature.md` carries nine: `onroad-cohort` eighth — see Cohorts — and `road-level` last); the last key, `road-level`, is the item's level within its destination — `main`, `secondary` or `side` — set by `/roadwork-nav-to-destination` from the destination's requirement, empty until then, the sanity todo `main`; read with the destination's `bucket-list-priority` to keep the loose order, never to rewrite it: `blocker` (yes iff `blocking` is
  non-empty — derived, never set by hand), `blocking` (items this one
  blocks), `blocked-by` (items blocking this one; empty = not blocked),
  `external` (a short sentence naming a dependency outside the roadwork registers,
  e.g. a signup; counts as blocked until the Operator clears it), `group`
  (names shared by items that belong together; an item may carry several;
  groups are never declared; a name carries its formation date,
  `<name>-<YYYY-MM-DD>`), `in-process` (the date `/roadwork-make` put the item on
  the road; empty when not; cleared by `/roadwork-verify-and-archive`), `disposition` (empty
  while open; set by `/roadwork-verify-and-archive` at archiving: `shipped`, `withdrawn`,
  `superseded by <ref>`, `decided`, or `abandoned` — an item never built,
  partly built, or only apparently built may be archived on the Operator's
  word with its shortfall recorded).
- **References.** `todo/<item-name>`, `feature/<item-name>`, `spark/<item-name>`;
  from anywhere, `main/<kind>/<item-name>` — the project's law may alias the
  prefix. No reference contains ` && `: that is the batch separator.
- **Batch invocation.** One skill, many references on one line, separated
  by ` && ` (space, two ampersands, space); a single reference is the one-element case;
  every skill splits its arguments on it. Accepted by
  `/roadwork-verify-and-archive` and `/roadwork-make` — the two that can hold to one
  round for a whole batch; every other skill refuses more than one reference
  and names its reason in one line (Operator, 2026-09-14); `/roadwork-tasksplit`
  among them, one source at a time. One carve-out: `/roadwork-ingest` accepts a
  **spark batch** — sparks only, one home — and converts it into one item; the
  bare `/roadwork-spark` lists the open sparks grouped for it (Operator, 2026-09-15).
- **`ordering.md`** — one ordered list, top is next; a line is
  `- <ref> — <why it sits here>`; a group is an indented block under one
  line and moves whole; archived items are struck. Loose by design: an
  order, not a schedule; maintained by agent judgment. One per register,
  the project's whole. It is what the session agent answers "what should we do
  next?" from. **`working.md`** beside it records the items in process,
  same scope; written by `/roadwork-make`, drained by `/roadwork-verify-and-archive`.
- **Filing from the Operator's notes** (only through `/roadwork-ingest`): the
  item file carries the notes **verbatim** under a dated heading (later
  notes as dated addenda, verbatim), then the filer's reading under its
  own heading, marked as the filer's and pending the Operator's
  correction, then a numbered "not decided by this filing" list — the open
  questions the notes leave, each with the filer's reading, which seeds
  the interview's first round. `intent.md` is filed as a placeholder and
  written only by `/roadwork-intentify`; `spec.md` and `plan.md` stay placeholders
  until `/roadwork-specplan`. Never a paraphrase in place of the notes; never
  an interpretation passed off as the notes.
- **Destinations.** A programme of work is a destination: one product
  requirements document, `destinations/<destination-slug>.prd.md` in the
  register, made by
  `/roadwork-destination` — bare, the destinations with their
  navigation state; `<new-slug> <description>`, an interview in
  `/roadwork-intentify`'s pattern writing the fixed form (the destination,
  numbered requirements, Out, Success); `<existing-slug>`, an update with a
  dated changelog line; a pasted document or path, saved verbatim as
  `destinations/<slug>.source.md` and then interviewed. `/roadwork-nav-to-destination
  <destination-slug>` (a slug only; anything else refused) turns it into a
  group: every derived item cites the destination by path and carries the
  line **Destination:** `<destination-slug>` — one destination per item,
  the group's; no frontmatter key — carries the group
  `<destination-slug>-<YYYY-MM-DD>`, and is `blocked-by` the sanity todo
  `todo/<destination-slug>-sanity` the skill creates last — the Operator's
  check of the decomposition and its completeness, worked by
  `/roadwork-navsanity`, archived on the Operator's word. Nothing in the
  group starts before that. A built destination moves to
  `destinations/archive/` by hand (Operator, 2026-09-15). `/roadwork-tasksplit <source>`
  is the small sibling: any document or list into a dated group of todos,
  one per unit the source delineates, the source's words verbatim, no
  sanity todo (Operator, 2026-09-15).
- **Maps.** A map is a primitive of the way to a destination — before
  agents, process, tools, judgements, inputs — one `maps/<map-slug>.md` per
  map in the register, in the fixed form `/roadwork-map` writes
  (bare, the maps with the count of items naming each; `<new-slug>
  <description>`, the interview; `<existing-slug>`, an update with a dated
  changelog line; a pasted document or path, saved verbatim as
  `maps/<slug>.source.md` and then interviewed). An item names its map by
  one line, **Map:** `<map-slug>`, under its owner line — one map per item,
  no frontmatter key — written by `/roadwork-intentify` when the Operator
  names one, or by `/roadwork-nav-to-destination` when the destination
  names one (its optional Map line, inherited by the group).
  `/roadwork-intentify` and `/roadwork-specplan` read the item's map; no
  skill enforces one. A retired map moves to `maps/archive/` by hand
  (Operator, 2026-09-15).
- **Naming.** Every roadwork register skill's name begins with `roadwork`
  (Operator, 2026-09-11): `roadwork-ingest`, `roadwork-spark`, `roadwork-destination`, `roadwork-nav-to-destination`, `roadwork-help`, `roadwork-map`,
  `roadwork-navsanity`, `roadwork-intentify`, `roadwork-specplan`,
  `roadwork-verify-and-archive`, `roadwork-tasksplit`, `roadwork-subagentifygroup` — with one exception:
  every lifecycle skill begins with `roadwork-`, the go included: `/roadwork-make` (Operator, 2026-09-16). `unlazy` is not one.
- **Cohorts.** `/roadwork-subagentifygroup <group>` finds subgroups of a
  group's features that can be built in parallel by sub-agents, by a
  **rubric** every criterion of which must pass (no dependency edge
  between members, disjoint file ownership, accepted spec and plan with
  gates, no external and not in process, self-contained builds), read
  back before any cohort is declared. Each cohort gets a
  **cohortmeister** `feature/cm-<group>-<cohort>` — a pseudo-feature the
  skill files itself, blocking every member, whose plan is unlazy's
  orchestrated PLAN form: one sub-agent per member, the CM's ledger as
  the results checker. `onroad-cohort` (features only) names the cohort.
  `/roadwork-make <CM>` runs the cohort; a member alone is refused
  unless the Operator says proceed (the **override**, unrecorded). A
  failed member **reverts** to standalone with a dated note sending it
  through `/roadwork-specplan` again; `/roadwork-verify-and-archive <CM>` archives the
  met members with it (the **cascade**: members `shipped`, the CM
  `decided`). Cohorts sit last in the group's block. Sits after
  `/roadwork-nav-to-destination`, before `/roadwork-navsanity` (which checks cohorts).
- **Lifecycle skills, in order:** `/roadwork-ingest` (ingest: kind decided,
  duplicates refused by judgment across the register, item placed in
  `ordering.md`; never archives), `/roadwork-intentify <ref>` (read-back first, then
  the prepared round, then the design tree; roadwork-register-aware across
  the register; writes cross-notes and frontmatter into
  related items), `/roadwork-specplan <ref>` (`spec.md` with concerns first,
  `plan.md` with gates; on an existing accepted spec and plan a
  reconsideration run — dated changelog, proven gates kept, the previous
  go ended, the spec proposed again; every spec under the Operator's
  spec-writing guidelines, tagged requirements, and two fresh-sub-agent
  verification rounds, one on the spec and one on the plan), `/roadwork-make <ref>` (the Operator's go: one item,
  refused while blocked; writes `in-process`, the `working.md` line and
  the item's `GATES.md` from the plan, then builds under `/unlazy`),
  `/roadwork-verify-and-archive <ref>` (archiving: evaluates concerns, unmet gates and landing
  by ancestry, interviews the Operator, then on their word the six-place
  act — resolution and `disposition`, move to `archive/`, strike from
  `ordering.md`, `working.md` and `in-process` cleared, dependents'
  `blocked-by` cleared — and offers the next item, group first). Beside the chain, not a step: `/roadwork-help [<skill> | <ref> | <term>]` — the map with no argument, one thing with one; read live from `docs/teachme.md`, the glossaries and the register; writes nothing (Operator, 2026-09-15). Each stops and hands back; none starts the next — an
  accepted spec is not a go, only `/roadwork-make` or the Operator's word is
  (ruling 2026-09-10). **Every skill in the chain ends by offering the
  next logical skill and item** — the next step for this item, or, after
  archiving, the next item from `ordering.md` — as an offer in one line,
  never an invocation (Operator, 2026-09-10) — printed as the invocation itself, in its own fenced code block (three backticks, no language tag), so the Operator may copy and run it; every offered block is preceded by one plain sentence naming the item, what is waiting on it, and what typing the block does — the state folded into the sentence, never a heading; one sentence for a batch, every item named (Operator, 2026-09-15); related offers combine into one invocation with the separator ` && `; the skill still never invokes it (Operator, 2026-09-14). The interrupting skills — `/roadwork-ingest`, `/roadwork-spark`, `/roadwork-verify-and-archive`, `/roadwork-specplan` — also end with the **back offers**: up to five open lifecycle steps in flight, most recent first, read from the roadwork register at that moment, never from memory. (Operator, 2026-09-11). A spark's exit is conversion only, on the
  Operator's word.

## Glossary

- **Roadwork register** — the project's `roadwork/`: the one place its work is recorded. Three **sub-registers**: `todo/` (fixes, chores, decisions, findings), `feature/` (new capabilities), `spark/` (ideas; never worked); the test: a todo is done once, a feature is reused when built — the Operator may name the kind against it.
- **Item** — one folder under its destination's folder in a sub-register (`unnavigated/` until a navigation cites it): `todo.md` or `feature.md` (the **item file**) plus `intent.md`, `plan.md`, `spec.md`; a spark holds only `idea.md`.
- **Home** — the register an item lives in: the project's one register, at the path the project's law names; a clone of a remote, fetched and merged, never pushed.
- **Reference (ref)** — `todo/<item-name>`, `feature/<item-name>`, `spark/<item-name>`; from anywhere, `main/<kind>/<item-name>` — the project's law may alias the prefix.
- **Frontmatter** — the YAML block opening an item file: `blocker`, `blocking`, `blocked-by`, `external`, `group`, `in-process`, `disposition`, `road-level` (the item's level within its destination — `main`, `secondary`, `side` — or empty), a feature's `onroad-cohort` before it.
- **`ordering.md`** — the register's loose priority list; top is next. **`working.md`** — the register's dated list of items in process.
- **Operator** — the human owner; every decision is theirs. **Session agent** — the agent running the session that invokes the skill.
- **Project scope** — everything at and under the root the project's law names; the paths an item touches are its **Paths:** line.
- **Batch** — the coherent bundle a project's changes ship in as one PR; the register's own commits are local and never a PR.
- **Lifecycle** — `/roadwork-destination` → `/roadwork-nav-to-destination` (a destination into a group) → `/roadwork-ingest` (or `/roadwork-tasksplit`, many at once) → `/roadwork-intentify` → `/roadwork-specplan` → `/roadwork-make` (the only go; builds under `/unlazy`) → `/roadwork-verify-and-archive`. Every skill ends by offering the next. Beside the chain, `/roadwork-help` answers.
- **PRD** — a product requirements document, `destinations/<destination-slug>.prd.md`, made by `/roadwork-destination` and the source of a group of items made by `/roadwork-nav-to-destination`; cited by path in every derived item.
- **Destination** — one `destinations/<destination-slug>.prd.md`: what is wanted, in a fixed form (a frontmatter block with `bucket-list-priority`, 1–10, 10 the highest; the destination, numbered requirements, Out, Success); its slug categorises the register's items — one destination per item, the group's, written on the item by `/roadwork-nav-to-destination`; archived to `destinations/archive/` by hand when built.
- **Map** — one `maps/<map-slug>.md`: a primitive of the way to a destination — before agents, process, tools, judgements, inputs — in a fixed form, made by `/roadwork-map`; named on an item by its **Map:** line, one per item, read by `/roadwork-intentify` and `/roadwork-specplan`; a pattern to follow or improve, enforced by nothing; retired to `maps/archive/` by hand.
- **Sanity todo** — the todo `/roadwork-nav-to-destination` creates last, `todo/<destination-slug>-sanity`: the group list and the requirement↔item mapping both ways; blocks every other item in the group until the Operator says the group is right.
- **Check types** — the six sanity checks `/roadwork-navsanity` runs over a group: completeness, provenance, shape, dependencies, order, scope.
- **Run** — one pass of `/roadwork-navsanity` over a group: six checks, ten questions, the changes made; recorded as a dated section in the group's sanity todo.
- **Hand-made group** — a group not born of a PRD; its requirements are its members' own claims plus the group's line in `ordering.md`.
- **Cohort** — a subgroup of a group's features that can be built in parallel by sub-agents: the rubric passes on every criterion; named in each member's `onroad-cohort`.
- **Cohortmeister (CM)** — `feature/cm-<group>-<cohort>`: the pseudo-feature that blocks a cohort's members, is onroaded in their place, and whose ledger is the results checker; archives them by cascade.
- **Rubric** — the five pass/fail criteria a subgroup must meet to be a cohort: no dependency edge, disjoint ownership, accepted spec and plan with gates, no external and not in process, self-contained builds.
- **Reconsideration** — `/roadwork-specplan`'s second mode: on an item whose accepted spec and plan already exist, re-read them against everything dated since; a dated `Reconsidered` changelog, proven gates carried, the previous go ended, the spec proposed again.
- **Verification round** — `/roadwork-specplan`'s fresh-eyes check: five predefined questions on the spec, four on the plan, one fresh reader each — run as one workflow where the harness runs workflows, on the top model of the tier one step below the session's (or the session's own where no lower tier exists) at an effort the dispatcher sets, findings in one bounded shape (file, line, one sentence, an empty disposition slot; at most eight; "clean" as none), sub-agents the fallback — findings incorporated or rejected with a reason and recorded in the document by the session agent; one round per document.
- **Back offers** — the second offer line of the four interrupting skills: up to five open lifecycle steps in flight, most recent first, read from the roadwork register; offers, never invocations; each preceded by one sentence saying what typing it does.
- **Item name** — the kebab-case folder name of an item, chosen at ingest in the Operator's words, and its reference (`todo/<item-name>`, `main/<kind>/<item-name>`); never reused; never a skill name. "Slug" is a generic word, not the register's term; the register names one, a destination's `<destination-slug>`.
- **Batch invocation** — one skill, many references on one line, separated by ` && `; accepted by `/roadwork-verify-and-archive` and `/roadwork-make`, and by `/roadwork-ingest` for a spark batch only (sparks of one home, converting into one item — the bare `/roadwork-spark` lists them grouped), refused by the rest with a reason; offers are printed as invocations in code blocks, related ones combined.
- **Bare call** — a lifecycle skill invoked with no argument lists instead of acting — `/roadwork-spark` the open sparks grouped for conversion, `/roadwork-destination` the destinations with their navigation state, `/roadwork-make` the make-eligible items with their goes and the ineligible with their reasons; a bare call writes nothing.
- **Fact suffix** — after the last offer of a lifecycle hand-back, when the machine's minute is a multiple of six: two blank lines, then the title line "A 2ndcortex/roadmap system detail you should know about:" plain, then one fact from `docs/facts.md`, picked by the seconds modulo the count of its numbered facts — never a heading, then "Typing this explains it:" and `/roadwork-help <term>` in its own code block; never after `/roadwork-help`; no state, no script.
- **Tasksplit** — `/roadwork-tasksplit <source>`: any document or list into a dated group of todos, one per unit the source delineates, the source's words verbatim and no reading added; no sanity todo, no cohort.
