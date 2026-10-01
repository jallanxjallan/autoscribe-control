---
identity: tsk_Z83XXHS37EXM3F6K
---
Return exactly five non-empty lines and nothing else.

Line 1: `AUTOSCRIBE_LLM_SMOKE_V1`
Line 2: the mandatory line required by the role instruction.
Line 3: the mandatory line required by the context instruction.
Line 4: `TASK=PASS`
Line 5: `INPUT=AUTOSCRIBE_SMOKE_INPUT_V1`

If the input is not exactly `AUTOSCRIBE_SMOKE_INPUT_V1` after trimming surrounding whitespace, return only `AUTOSCRIBE_SMOKE_BAD_INPUT`.
