# Documentation Conventions

**Type: Authorial guide**

**Status: Active**

This is the author-facing guide to organising, writing, and maintaining the vault. Read the relevant sections when creating, editing, moving, or auditing documentation. It establishes no setting canon.

## Find the Right Home

| Location | Owns |
| --- | --- |
| `00 Start Here.md` | Short reading routes and links to the main subjects and working tools. |
| `00 Core` | Premise, durable axioms, story intent, working terminology, and inspirations. |
| `01 Technologies/01 Key Concepts` | Broad physical principles, travel constraints, and major infrastructure systems. |
| `01 Technologies/02 Devices and Applications` | Named devices, interfaces, operating vocabulary, and bounded use cases. |
| `02 World` | Environments, histories, regional geography, societies, and contact context. Milky Way references sit together; Andromedan material remains distinct. |
| `03 Ship and Crew` | This vessel's programme, installed systems, condition, complement, and formal organisation. |
| `04 Narrative` | Viewpoint choices, characters, relationships, arcs, and planning boards. |
| `05 Corpus` | Story ideas and actual prose drafts. |
| `99 Workshop` | Development order, unresolved decision packages, calculation tools, and inherited alternatives. |

Folders identify subjects and uses, not approval. General physics and a particular device belong in separate technology folders even when they share a mechanism. A vessel reference records what this ship has; the technology reference records how that capability works.

## Ownership and Navigation

- One document owns the detailed answer to a subject. Dependent notes give the context needed to remain readable and link to that owner.
- Put a usable baseline or operational summary first, then mechanics, constraints, consequences, and open questions as needed. Do not force every small note into a large template.
- Landing pages provide short context and descriptive links. A topic overview may own a genuinely broad baseline, but should not repeat each linked reference.
- Use descriptive filenames. Avoid catch-all `General Ideas` files and unqualified `Overview` names. Create a new folder when existing material needs grouping, not as an empty promise of future work.
- Numbering expresses a deliberate reading or browsing order. Preserve or deliberately repair it when moving files; it is not a record of creation order.
- Split sections when readers seek them independently or they have different owners or uses. Merge when they repeatedly answer the same question together. File length alone is not a reason to split; related equipment may remain together.
- Exact technical vocabulary belongs with its mechanism. The central glossary defines ambiguous shared terms and links to specialised vocabulary.

## Status and Approval

Begin ordinary documents with **Type** and **Status** labels. Use **Scope** when approval applies only at a particular level, **Approval** when canonisation explicitly requires it, and **Development** for explicit deferrals. Technology references may also carry **Physical basis** and **Setting role**. Keep each field on its own paragraph so it remains readable in both Markdown and preview.

Use these status values consistently:

- **Current foundation:** existing core, terminology, or reference material whose original document had no explicit approval label. This records continuity, not a new blanket canon approval; open questions and candidate sections remain unselected.
- **Approved baseline** or **Selected baseline:** retain the author's existing approval wording and state its scope. Neither label settles explicitly open details.
- **Exploring** or **Provisional:** retain the existing distinction between alternatives under development and a provisional working proposal. Preserve any explicit approval requirement.
- **Current direction:** revisable narrative preferences.
- **Active:** a navigation page, guide, or queue in current use; this is not a canon status.

Kanban boards retain their native frontmatter and settings instead of receiving prose labels or a new heading. Document type and status labels apply to ordinary notes, not as extra cards on a board.

Keep these dimensions distinct:

| Dimension | Examples | Meaning |
| --- | --- | --- |
| Authorial approval | Approved baseline; selected high-level baseline; provisional; exploring; rejected | Whether the author has selected the material and at what level. |
| Narrative planning | Current narrative direction; candidate scene or character | Story preferences do not automatically settle broader canon. |
| In-setting availability | Routine; exceptional; undeployed research; theoretical-only | Whether people in the setting can use a capability; separate from authorial approval. |
| Development state | Active; explicitly deferred; superseded | Whether work should proceed now. |

Preserve existing status and approval labels. Do not infer approval from a file's folder, a confident sentence, a catalogue entry, or its presence in a reference. Moving or consolidating text never canonises it.

An active topical working reference may contain approved constraints and exploratory details if their boundaries are explicit. Use section-level labels when a single file-level label would misrepresent mixed material. Keep incompatible alternatives distinguishable; preserve provenance, conflicting figures, names, and mechanisms until the author resolves them.

Approved numerical or historical baselines can coexist with an unresolved physical implementation. Identify the actual dependency rather than downgrading every related fact. Where the project has selected a baseline, reopen it only for an identified conflict with a selected mechanism or direct narrative need.

Keep detailed open questions with their topic. [[99 Workshop/00 Revision Priorities|Revision Priorities]] owns their work order and explicit deferrals, linking to the detailed questions. Completed decisions belong in their owners, not repeated at length in the queue or a workbook.

## Writing and Knowledge Layers

Use Canadian spelling and established setting vocabulary. Reference prose should be clear, precise, and conscise . Explain mechanisms, operating constraints, consequences, and uncertainty, while avoiding mystical hand-waving.

The reference writer may use an omniscient view of the setting. That does not make the complete authorial model common knowledge among characters. Distinguish objective reality, institutional knowledge, common practice, common belief, and narrative revelation using [[99 Workshop/01 Development Method and Order|Development Method and Order]].

Keep authorial design, calculations, and narrative planning distinct from in-setting exposition. Mark a document's purpose explicitly when it is an author-facing tool. In an otherwise in-setting reference, put necessary external analogies, comparisons, or design commentary in a final `#META` section rather than presenting them as diegetic fact.

Avoid usage of semicolons and em-dash whenever possible, and opt instead for commas, periods, and "joining words" ( "while", "but", "and", etc ) based on suitability. Avoid statement like "this is not only X, but also Y" and "This is A, and therefore not B", unless they add meaningfuly novel information or context to the statement. If a sentence can be trimmed out without losing useful information, try to do so.

## Links and Markdown

- Use concise Obsidian links at the first useful occurrence of a concept; avoid linking every repetition. Prefer explicit vault-relative targets for cross-folder links and plain-language display labels.
- Link directly to the relevant section when the reader needs a specific answer. Update the link if that heading changes.
- Outside tables use `[[File Name|display text]]`. Inside tables escape the internal pipe exactly once: `[[File Name\|display text]]` or `![[Image.png\|200]]`. Keep ordinary table separators unescaped. Adjust escaping when moving text into or out of tables; never double-escape links or put alignment spaces inside targets or labels.
- Use one descriptive document title and a coherent heading hierarchy. Check table cell counts, code fences, and mathematical blocks when restructuring.
- Keep Kanban board frontmatter, settings, and card syntax intact when moving boards.

## Editing and Handoff

When changing a foundational concept, trace direct and likely second- or third-order effects through affected references. Remove, revise, or explicitly defer dependencies on superseded assumptions. Surface substantive contradictions instead of inventing a resolution.

`VALIDATE` markers are author-maintained review prompts, not instructions to delete text automatically. Keep review proportionate to the affected concepts.

Treat Legacy folders as obsolete and leave them alone unless the task explicitly needs them. Do not modify source guides, inherited material, or empty idea files unless the task calls for it. Preserve useful source provenance and unresolved alternatives when consolidating notes.

For moves and merges, update inbound links, section targets, navigation lists, and ownership statements together. Remove a superseded wrapper only after its useful material has a destination. Keep summaries short enough that they do not become competing versions of the answer.

Before handoff, inspect the diff for information loss and unintended changes, check Markdown structure and links, and verify that status and deferral boundaries survive. `git diff --check` checks diff whitespace only; it is not a content or link audit.
