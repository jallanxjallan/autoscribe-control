# Book manuscript preflight and mechanical proofreading

**Status:** Control catalogue plan ready for Codex review and later deployment. This document is an implementation boundary and test checklist, **not** an assertion that a source-conversion validator has already been installed.

## Contract

The publication renderer consumes approved manuscript-sourced text as letter-perfect. It may set type, paginate, and change purely visual presentation, but it must not correct words, normalize punctuation, silently repair Markdown source, or rewrite text. Ambiguous or invalid input must be reported upstream rather than guessed at render time.

All text changes happen in manuscript sources *before* publishing and are author-approved through review/diffs. Neither the new Control plan nor its presence in the repository changes production until the user arranges deployment.

## Two separate passes

1. **Raw Markdown conversion preflight (not implemented here).** Audit the actual `.md` file *before Pandoc or other parsing*. Catch conversion artifacts and structural ambiguity in source, correct them once upstream, and keep reviewable diffs. Protect legitimate Markdown structures. Some rules can be deterministic; ambiguous cases must be flagged rather than automatically rewritten.
2. **AutoScribe mechanical proofreading.** Use `Book — Mechanical Proofreading` on one already structurally valid passage BODY. It returns a complete candidate corrected body and nothing else. The author reviews the resulting diff and accepts or rejects it using the existing conflict/writeback mechanism. It is not an automatic manuscript rewrite or a literary editing pass.

The Control plan does not itself implement stage 1 or prove that stage 2 output is character-for-character unchanged outside corrections. Codex should test preservation and failure behavior before production use.

## Preflight cases to test

| Raw source | Risk / expected treatment |
| --- | --- |
| `The sky---and the city` | Likely an em dash; repair in source when context confirms it, rather than rely on rendering-time smart punctuation |
| `---` on its own line | Could be a thematic break, separator, or import artifact; do not blindly replace |
| `1998. The city changed.` at the start of a paragraph | Markdown may parse this as an ordered list; when prose is intended, escape the source period as `1998\. The city changed.` and preserve the printed text |
| `1. First item` in a genuine list | Preserve the legitimate list |
| Footnotes, Obsidian links, emphasis, layout directives, local-language terms | Preserve syntax and intentional manuscript language exactly |
| Passage without mechanical faults | Proofreader returns it unchanged |
| Uncertain quotation, date, colloquialism, proper name, or historic spelling | Leave the text unchanged and do not speculate |

A future deterministic preflight can report suspicious patterns and fail closed on source ambiguity; it must not be hidden inside the renderer. Keep the initial implementation simple and use genuine manuscript passages for acceptance tests.

## Instruction input clarification — 6 November 2026

Raw Markdown is the ingest transport contract. Plan instructions operate on the
prepared `content` received, which earlier stages may have extracted or
transformed. They must not assume an original file format, remove presumed
frontmatter, or reconstruct raw source. The existing plan and step IDs remain.
Raw-source conversion preflight stays separate and is not implemented here;
neither pipeline processing nor renderer behavior changes. Synthetic model
substitution qualifies wiring only, not provider availability or proofreading
quality.
