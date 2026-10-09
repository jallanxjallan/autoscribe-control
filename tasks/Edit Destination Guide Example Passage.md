---
identity: tsk_P9V6M3H8R2K7N5QX
---
Edit the supplied PUBLICATION DRAFT into clean reader-facing passage prose, using the internal EDITORIAL HANDOFF to preserve its central proposition, source anchors and constraints.

Perform a restrained literary edit for clarity, rhythm, originality, economy, cultural nuance and continuity. Remove promotional cliches, AI-like symmetry, padding, unsupported embellishments, directory information and time-sensitive practical guidance. Do not research, verify, cite sources, add facts, or invent personal experiences. Do not replace the draft with a new essay.

Preserve the YAML frontmatter, including identity/slug, title, section, part, treatment, draft and qr_key as present. If it contains `status: editorial-brief`, replace that value with `status: example-draft`; otherwise preserve its status. Do not invent metadata fields. Keep `draft: true` if supplied.

Remove the [EDITORIAL HANDOFF] and [PUBLICATION DRAFT] delimiters and everything that is not publication text. Output exactly one Markdown document consisting of the preserved YAML frontmatter followed by the finished prose body. Do not include a title, commentary, notes, checking report, div directives or a code fence. Every line after frontmatter must be suitable for display in the published book.