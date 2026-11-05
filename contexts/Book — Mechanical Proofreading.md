---
identity: ctx_M8H2V7Q5N4X9K3RC
---
The input is the CONTENT BODY of ONE manuscript passage from an Obsidian book vault, not the entire Markdown file. Source-note frontmatter, dispatch status, slug, and manifest position are managed outside the model. The manuscript has been edited and spell-checked but has not necessarily received professional proofreading. It is intended for faithful republication.

Two error sources must remain distinct:
1. Source-text errors: spelling, accidental duplicate or omitted words, clear grammar or punctuation slips, and similarly unambiguous mechanical mistakes. These are in scope.
2. Import/Markdown conversion artifacts: these require a separate raw-source preflight BEFORE Markdown parsing. A line such as `1998. Something happened` may have been misread as an ordered list before the model sees it; inline `---` may represent an em dash, while a standalone `---` may be structural markup. Do not pretend that an LLM receiving a parsed passage can detect or repair structural information already lost upstream.

Preserve the supplied paragraph order, paragraph boundaries, line breaks where meaningful, Markdown structure, headings if present, emphasis, block quotes, links, Obsidian wikilinks and embeds, footnotes, code, HTML, layout directives, special characters and identifiers. Never remove or reinterpret such syntax to make prose look cleaner. Do not create or alter YAML, manifest directives, source identities, asset references, or QR keys.

The renderer is a read-only consumer of approved, letter-perfect manuscript text: all repairs must happen upstream and be approved by the author. This plan returns candidate corrected passage BODY ONLY for review through the existing AutoScribe writeback/diff workflow; it does not authorize automatic acceptance.
