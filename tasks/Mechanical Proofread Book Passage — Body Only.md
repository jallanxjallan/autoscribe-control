---
identity: tsk_Q4R8V2M7H9N5X3KC
---
Perform ONE conservative mechanical-proofreading pass on the supplied raw passage. If an opening YAML frontmatter block is present, treat it as read-only coordination and exclude it from the returned manuscript body. Do not copy or rewrite metadata.

Correct only errors for which the intended reading is unambiguous:
- Misspellings and obvious typographical substitutions, including wrong-but-valid words where context makes the correction certain.
- Accidental repeated words, missing small words, and agreement or syntax slips with a single clear repair.
- Clear punctuation, spacing, capitalization, and quotation-pair mistakes.
- Obvious inconsistent spelling or hyphenation within this passage, without imposing a new style.
- An inline `---` ONLY when it is unmistakably an em dash in the prose; never change a standalone thematic break or uncertain Markdown construct.
- A date-like paragraph prefix such as `1998. The city changed.` ONLY when context unambiguously means a year and prose rather than a numbered list: escape the source period as `1998\. The city changed.`. Preserve legitimate numbered lists; leave ambiguity unchanged for upstream review.

Do NOT perform literary editing. Do not rephrase for elegance, fix perceived awkwardness, change sentence order, edit dialogue into formal grammar, harmonize dialect or historically situated spelling, replace imagery, add explanation, alter claims, change names/dates/figures, or resolve ambiguous references. Preserve the original prose even where another wording would read more smoothly. If a suspected error has more than one defensible correction, leave it unchanged.

Preserve all existing Markdown and Obsidian structures exactly, including paragraph breaks, links, footnote labels, formatting delimiters, directives, and inline code. Never change text inside a code span or code fence. Do not insert or remove headings, legitimate lists, block quotes, manuscript metadata, or frontmatter. Apart from the explicit unambiguous raw-source conversion repairs above, preserve structure. The renderer must never make these repairs. A deterministic preflight and actual-model behavior remain separately unqualified.

Return ONLY the complete corrected passage BODY as ordinary Markdown, with no explanatory text, comments, markup highlighting, change log, code fences around the answer, or editorial notes. If you find no unambiguous faults, reproduce the input body unchanged.
