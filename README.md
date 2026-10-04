# State of agent markdown, September 2026

The dataset behind [State of agent markdown, September 2026](https://markdownregistry.com/reports/state-of-agent-markdown-2026-09), a report from [markdownregistry.com](https://markdownregistry.com) on 69,119 instruction files for AI agents (SKILL.md, AGENTS.md, CLAUDE.md, DESIGN.md, llms.txt and Cursor rules) from 2,887 public GitHub repositories. Data frozen September 27, 2026 from the registry's own crawl.

The report page is the canonical source: https://markdownregistry.com/reports/state-of-agent-markdown-2026-09

## Files

| File | What it is |
|---|---|
| `data/state-of-agent-markdown-2026-09.json` | The exact JSON the report page renders, as downloaded from [https://markdownregistry.com/reports/state-of-agent-markdown-2026-09.json](https://markdownregistry.com/reports/state-of-agent-markdown-2026-09.json) |
| `data/state-of-agent-markdown-2026-09.csv` | The same figures, one per row, as downloaded from [https://markdownregistry.com/reports/state-of-agent-markdown-2026-09.csv](https://markdownregistry.com/reports/state-of-agent-markdown-2026-09.csv) |

Both files are byte-for-byte copies of the downloads published on the report page.

## Key findings

In the report's own words (the `findings` array in the JSON):

- In the registry's corpus, roughly one in five agent markdown files changed within two weeks of being indexed. Of 47,724 files watched for at least 14 days, at least 9,487 (19.9%) received a new upstream commit within 14 days and at least 6,745 (14.1%) within 7. Without the ten most active repositories of each kind, the 14 day share is at least 17.8%.
- In the corpus, llms.txt files changed most often: at least 41.2% (106 of 257) changed within 14 days, followed by AGENTS.md at 27.8%, CLAUDE.md at 23.2%, SKILL.md at 19.4%, Cursor rules at 12.2%, DESIGN.md at 5.4%, each a lower bound.
- In the registry, copies of Anthropic's skills can fall behind their source. For 5 skills from the anthropics/skills repository (skill-creator, frontend-design, docx, pptx and xlsx), chosen because they change often, 75 files in other repositories are byte-for-byte copies of a recorded upstream version, and 47 of them (62.7%) match an older version rather than the current one.
- About one in ten SKILL.md files in the registry breaks the Agent Skills specification's frontmatter rules. Of 60,844 SKILL.md files inside a skill directory, 54,836 (90.1%) conform; the most common failure is a name that does not match its directory (3,858 files, 6.3%).
- The audit flags 194 of 69,119 files (0.3%) on at least one critical check. The checks are deliberately broad, so emoji joiners, stray zero-width spaces, Persian text, the example access key from Amazon's documentation, code that reads environment variables, security guidance that quotes an attack and security test fixtures trip them too; a flag means read this file, not that it is malicious.
- In the registry, 458 files contain a curl or wget command piped straight into a shell, 395 of them SKILL.md files.
- In the registry, 5.7% of SKILL.md files (3,487 of 61,170, across 254 repositories) are byte-identical to a file in another repository. DESIGN.md reads 53.3%, but 540 of its 555 copies sit in four repositories that carry the same template set.

Every figure above describes the registry's corpus, not a random sample of GitHub. The change figures are lower bounds.

## Methodology

Definitions, quoted from the `definitions` object shipped in the JSON:

- `observed`: files first indexed at least 14 days before the data was frozen
- `within7`: of those, files with an upstream commit dated within 7 days after first indexing (a lower bound)
- `within14`: the same within 14 days (a lower bound); the page's change figure
- `rest_files`: observed files outside the 10 repositories of that kind with the most changes within 14 days
- `rest_w14`: within14 for those files
- `cross_repo_dup`: files of at least 200 bytes whose bytes equal a file in another repository; the page's copy figure
- `copy_repos`: repositories holding at least one such copy
- `top4_copies`: copies held by the four repositories holding the most
- `distinct_contents`: NOT used on the page: distinct SHA-256 contents among the live files of that kind
- `drift_repos`: NOT used on the page: repositories with at least one observed file of that kind
- `changed`: NOT used on the page: files with any commit after first indexing, over each file's whole, unequal watch period
- `changed3`: NOT used on the page: files with three or more such commits, same unequal period
- `dup_files`: NOT the page's copy definition: files with any byte-identical twin, same repository and any size included
- `vendored.current`: files in other repositories byte-identical to the current recorded upstream version
- `vendored.older`: files in other repositories byte-identical to an older recorded upstream version
- `vendored.other`: files sharing the skill's name that match no recorded upstream version; left out of the page's figures

Audit grades (the `a`, `b`, `c`, `f` columns per kind), as the report defines them: "A passes everything, B fails one advisory check, C fails two or more, and F fails a critical check."

Kind keys in `data.kinds`: `skill` is SKILL.md, `agents` is AGENTS.md, `claude` is CLAUDE.md, `design` is DESIGN.md, `rules` is Cursor rules, `llmstxt` is llms.txt.

The full method (how repositories are found, what counts as a change, the 14 day window, what counts as a copy, audit versions) is on the [report page](https://markdownregistry.com/reports/state-of-agent-markdown-2026-09), under Method.

## Guides that use these figures

[markdownregistry.com/guides](https://markdownregistry.com/guides): how to pin an agent skill, AGENTS.md vs CLAUDE.md vs SKILL.md, skill security, where to find skills, the SKILL.md frontmatter rules, and agent skills for a team.

## Studies, October 2026

Four shorter studies counted from the same crawl, each with its method on its page. The files in `data/studies/` are byte-for-byte copies of the JSON each post publishes beside it (the post's address with `.json` added).

| Study | Data |
|---|---|
| [AGENTS.md and CLAUDE.md in one repo: what 1,203 folders do](https://markdownregistry.com/blog/agents-md-and-claude-md-in-one-repo) | `data/studies/agents-md-and-claude-md-in-one-repo.json` |
| [How projects write Cursor rules: 557 files counted](https://markdownregistry.com/blog/how-projects-write-cursor-rules) | `data/studies/how-projects-write-cursor-rules.json` |
| [How llms.txt files follow the format: 438 files counted](https://markdownregistry.com/blog/how-llms-txt-files-follow-the-format) | `data/studies/how-llms-txt-files-follow-the-format.json` |
| [DESIGN.md files against the official linter: 1,162 checked](https://markdownregistry.com/blog/design-md-files-against-the-official-linter) | `data/studies/design-md-files-against-the-official-linter.json` |

In each post's own words (its opening paragraph):

- **AGENTS.md and CLAUDE.md in one repo: what 1,203 folders do.** Keep the instructions in AGENTS.md and start CLAUDE.md with an @AGENTS.md line. That is what Claude Code's docs show, and the most common single setup in the 1,203 folders the registry has collected from public GitHub that hold both files: 28.8% use the import, 23.8% a symlink and 3.2% identical copies. Another 8.8% only mention the other file in words, and 35.4% keep two separate files.
- **How projects write Cursor rules: 557 files counted.** Most projects now write Cursor rules as .mdc files in .cursor/rules: 510 of the 557 rule files the registry has collected, against 47 legacy .cursorrules files. Of the .mdc rules, 32.7% load in every chat, 32.2% attach to matching files and 28.8% let the agent decide. And 46 set a narrow file pattern that Cursor ignores, because they also say alwaysApply: true.
- **How llms.txt files follow the format: 438 files counted.** Most llms.txt files get the top of the format right and drift below it. Of 438 files named llms.txt in public GitHub repositories, 96.6% open with an H1 and 85.2% follow it with a summary blockquote. But only 30.6% follow the whole structure the llms.txt proposal sets out: in 52.7% of files, at least one section under an H2 heading holds prose, not the list of links the proposal describes.
- **DESIGN.md files against the official linter: 1,162 checked.** Most DESIGN.md files keep their design values in the markdown body, not in tokens a tool can check. Of 1,162 DESIGN.md files in public GitHub repositories, 78.1% have no YAML design tokens, which the format leaves optional, though 747 of those still spell out three or more hex colors in their text. Of the 254 with tokens, 88.6% pass the format's own linter with no errors, and only 8.3% with no warnings either.

Like the report, every study describes the registry's corpus, not a random sample of GitHub. The study data is licensed the same way as the rest of this repository; attribute each to its post.

## Cite

markdownregistry, "State of agent markdown, September 2026", September 27, 2026, https://markdownregistry.com/reports/state-of-agent-markdown-2026-09

A `CITATION.cff` is included, so GitHub shows a "Cite this repository" button.

## License

The data is licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0). Attribution: markdownregistry.com, with a link to https://markdownregistry.com/reports/state-of-agent-markdown-2026-09.

## Related

- [markdownregistry.com](https://markdownregistry.com): a registry of agent markdown, every file versioned by content hash and audited
- [mdr, the CLI](https://markdownregistry.com/cli): install agent markdown pinned to a content hash
- [How to pin an agent skill to an exact version](https://markdownregistry.com/guides/pin-agent-skills)

Contact: jack@dotcomjack.com
