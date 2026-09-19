# Documentation Conventions

**Type: Authorial guide**

**Status: Active**

This is the author-facing guide to organizing, writing, and maintaining the vault. Read the relevant sections when creating, editing, moving, or auditing documentation. It establishes no setting canon.

## Corpus Boundary

Agents and LLMs must not directly write, rewrite, or otherwise edit corpus prose, including drafts and equivalent creative text stored elsewhere, as those are meant to be fully user generated and maintained. However, they may read and discuss that material only when requested, providing critique or suggestions without modifying the source.

## Find the Right Home

| Location | Owns |
| --- | --- |
| `Start Here.md` | Short reading routes and links to the main subjects and working tools. |
| `00 Core` | Premise, durable axioms, story intent, working terminology, and inspirations. |
| `01 World` | Environments, histories, regional geography, societies, and contact context. Milky Way references sit together. Andromedan material remains distinct. |
| `10 Technologies/01 Key Concepts` | Broad physical principles, travel constraints, and major infrastructure systems. |
| `10 Technologies/02 Devices and Applications` | Named devices, interfaces, operating vocabulary, and bounded use cases. |
| `11 Ship and Crew` | This vessel's programme, installed systems, condition, complement, and formal organization. |
| `80 Narrative` | Viewpoint choices, characters, relationships, arcs, and planning boards. |
| `90 Corpus` | User-written prose, creative drafts, fragments, and fictional documents. Author-facing story planning belongs in `80 Narrative`. |
| `99 Workshop` | Development order, unresolved decision packages, calculation tools, and inherited alternatives. |

Use fixed `00 Core` and `01 World` first, followed by the project-specific `10 Technologies` and `11 Ship and Crew` domains. Supporting folders follow.

Folders identify subjects and uses, not approval. General physics and a particular device belong in separate technology folders even when they share a mechanism. A vessel reference records what this ship has. The technology reference records how that capability works.

## Ownership and Navigation

- One document owns the detailed answer to a subject. Dependent notes give the context needed to remain readable and link to that owner.
- Put a usable baseline or operational summary first, then mechanics, constraints, consequences, and open questions as needed. Do not force every small note into a large template.
- Landing pages provide short context and descriptive links. A topic overview may own a genuinely broad baseline, but should not repeat each linked reference.
- Use descriptive filenames. Avoid catch-all `General Ideas` files and unqualified `Overview` names. Create a new folder when existing material needs grouping, not as an empty promise of future work.
- Numbering expresses a deliberate reading or browsing order. Preserve or deliberately repair it when moving files. It is not a record of creation order.
- Split sections when readers seek them independently or they have different owners or uses. Merge when they repeatedly answer the same question together. File length alone is not a reason to split. Related equipment may remain together.
- Exact technical vocabulary belongs with its mechanism. The central glossary defines ambiguous shared terms and links to specialized vocabulary.

## Status and Approval

Begin ordinary documents with **Type** and **Status** labels. Use **Scope** when approval applies only at a particular level, **Approval** when canonization explicitly requires it, and **Development** for explicit deferrals. Technology references may also carry **Physical basis** and **Setting role**. Keep each field on its own paragraph so it remains readable in both Markdown and preview.

Use these status values consistently:

- **Current foundation:** existing core, terminology, or reference material whose original document had no explicit approval label. This records continuity, not a new blanket canon approval. Open questions and candidate sections remain unselected.
- **Approved baseline** or **Selected baseline:** retain the author's existing approval wording and state its scope. Neither label settles explicitly open details.
- **Exploring** or **Provisional:** retain the existing distinction between alternatives under development and a provisional working proposal. Preserve any explicit approval requirement.
- **Current direction:** revisable narrative preferences.
- **Active:** a navigation page, guide, or queue in current use. This is not a canon status.

Kanban boards retain their native frontmatter and settings instead of receiving prose labels or a new heading. Document type and status labels apply to ordinary notes, not as extra cards on a board.

Keep these dimensions distinct:

| Dimension | Examples | Meaning |
| --- | --- | --- |
| Authorial approval | Approved baseline, selected high-level baseline, provisional, exploring, rejected | Whether the author has selected the material and at what level. |
| Narrative planning | Current narrative direction, candidate scene or character | Story preferences do not automatically settle broader canon. |
| In-setting availability | Routine, exceptional, undeployed research, theoretical-only | Whether people in the setting can use a capability, separate from authorial approval. |
| Development state | Active, explicitly deferred, superseded | Whether work should proceed now. |

Preserve existing status and approval labels. Do not infer approval from a file's folder, a confident sentence, a catalogue entry, or its presence in a reference. Moving or consolidating text never canonizes it.

An active topical working reference may contain approved constraints and exploratory details if their boundaries are explicit. Use section-level labels when a single file-level label would misrepresent mixed material. Keep incompatible alternatives distinguishable. Preserve provenance, conflicting figures, names, and mechanisms until the author resolves them.

Approved numerical or historical baselines can coexist with an unresolved physical implementation. Identify the actual dependency rather than downgrading every related fact. Where the project has selected a baseline, reopen it only for an identified conflict with a selected mechanism or direct narrative need.

Keep detailed open questions with their topic. [[99 Workshop/00 Revision Priorities|Revision Priorities]] owns their work order and explicit deferrals, linking to the detailed questions. Completed decisions belong in their owners, not repeated at length in the queue or a workbook.

## Writing and Knowledge Layers

Follow [[Writing Style|Writing Style]] for Canadian English, this project's -ize and -ization preference, clear prose, and restrained punctuation. Use direct author-facing reference language by default. Explain mechanisms, constraints, consequences, and uncertainty. An in-world narrator or META section is not required.

Keep objective reality, institutional knowledge, common practice, common belief, and narrative revelation distinct using [[99 Workshop/01 Development Method and Order|Development Method and Order]]. A complete authorial reference does not establish what characters know.

Distinguish sourced facts, scenario assumptions, inferred consequences, and selected fiction. Record source details and limitations when they affect a claim or calculation. Keep historical draft feedback distinguishable from current assessments, and identify its source when known.

## Links and Markdown

- Use concise Obsidian links at the first useful occurrence of a concept. Avoid linking every repetition. Prefer explicit vault-relative targets for cross-folder links and plain-language display labels.
- Link directly to the relevant section when the reader needs a specific answer. Update the link if that heading changes.
- Outside tables use `[[File Name|display text]]`. Inside tables escape the internal pipe exactly once: `[[File Name\|display text]]` or `![[Image.png\|200]]`. Keep ordinary table separators unescaped. Adjust escaping when moving text into or out of tables. Never double-escape links or put alignment spaces inside targets or labels.
- Use one descriptive document title and a coherent heading hierarchy. Check affected tables, code fences, and mathematical blocks when restructuring them.
- Keep Kanban board frontmatter, settings, and card syntax intact when moving boards.

In Markdown tables, escape every pipe belonging to a cell’s content with exactly one backslash: `\|`. This includes ordinary text, inline code, wikilink aliases, and embed options. Backticks do not protect a pipe from splitting a cell. Keep structural column separators unescaped, and never double-escape content pipes. After editing a table, check that its rows retain their intended cell counts.

## Editing and Handoff

When changing a foundational concept, trace direct and likely second- or third-order effects through affected references. Remove, revise, or explicitly defer dependencies on superseded assumptions. Surface substantive contradictions instead of inventing a resolution.

`VALIDATE` markers are author-maintained review prompts, not instructions to delete text automatically. Keep review proportionate to the affected concepts.

Treat Legacy folders as obsolete and leave them alone unless the task explicitly needs them. Do not modify source guides, inherited material, or empty idea files unless the task calls for it. Preserve useful source provenance and unresolved alternatives when consolidating notes.

For moves and merges, update inbound links, section targets, navigation lists, and ownership statements in editable author-facing documentation together. Exclude corpus text from automated rewriting, including link repair. Report known affected corpus references for the author to update. Remove a superseded wrapper only after its useful material has a destination. Keep summaries short enough that they do not become competing versions of the answer.

Before handoff, apply the validation scope below and verify affected approval, provenance, and deferral boundaries. Check new files as well as existing edits. Report checks and limitations accurately. `git diff --check` checks whitespace only. File comparisons can verify changes without using Git.

## Validation Scope and Stopping Rule

Validate changed material and dependencies that the change could affect. Do not revalidate unrelated content by default. Review the relevant diff or before/after comparison, including new files, for unintended changes and information loss.

| Change | Check |
| --- | --- |
| Ordinary prose correction | Review the edited prose. Skip link checks if targets, headings, paths, and link syntax are unchanged. |
| Link added or target changed | Resolve that link and any heading target. |
| Display label changed | Check syntax and escaping. Recheck the destination only if its target or resolution context changed. |
| Heading renamed or removed | Find and check references to that heading. |
| File moved, renamed, or deleted | Find inbound references and check affected relative links, embeds, navigation, and stale path mentions. |
| Table or structural Markdown edited | Check the affected table's cell counts and pipe escaping, or the affected headings, fences, and surrounding structure. |
| Numerical or foundational content changed | Check the affected values, interpretations, and dependent references within the authorized scope. |

An affected link may be in an otherwise unchanged file. Use a targeted search across editable documentation to find inbound references when needed. This is not a reason to validate every unrelated link. Corpus protection still applies, including during dependency searches.

Batch related edits before checking them. Once a relevant check passes, stop. Repeat only checks whose inputs or dependencies changed, checks needed to investigate an unresolved failure, or checks justified by new evidence or an explicit request. One successful check can satisfy several workflow steps. Do not repeat it merely to produce another handoff summary or report a larger check count.

Broaden validation only when requested or when the actual change or evidence warrants it, such as widespread path changes or failures suggesting a systemic problem. State the reason and limit the scope accordingly. A bootstrap checks the new starter and its local dependencies, not neighbouring projects.

Check portability when guidance is first adopted or when paths, dependencies, or instruction routing change. Inspect the affected guidance and local dependencies first. Use a temporary isolated copy only when it would resolve a concrete uncertainty about external dependencies or when explicitly requested. Ordinary wording edits do not require an isolated copy.

Report the checks actually performed and any relevant limits. Do not maintain validation logs, version fields, or recurring audit dates solely to support this rule.
