# AutoScribe Control

Git is the authoritative forensic record for AutoScribe Control. The live server catalogue is rebuilt from the current validated `main` snapshot.

## End-to-end smoke plan

Plan: `AutoScribe End-to-End Smoke Test` (`pln_AXB4JQC9BKXF9481`)

The plan deliberately contains exactly two steps:

1. `LLM Smoke Test` (`stp_GAPSW1HRDDH0AXN2`) — calls the `chatgpt` engine with model label `luna`, resolves one role, one context and one task instruction, and requires a deterministic five-line response.
2. `Verify Smoke Test Output` (`stp_FHZ0AYS2BX3YDZEK`) — passes the first step's output through the registered local `smoke-test` extension. The extension fails non-zero unless the LLM output is exactly correct.

### Test input

Use a source whose body/input presented to the plan is exactly:

```text
AUTOSCRIBE_SMOKE_INPUT_V1
```

Surrounding whitespace is allowed because the LLM instruction explicitly trims it for comparison.

### Expected LLM intermediate output

```text
AUTOSCRIBE_LLM_SMOKE_V1
ROLE=PASS
CONTEXT=PASS
TASK=PASS
INPUT=AUTOSCRIBE_SMOKE_INPUT_V1
```

### Expected final response

```text
AUTOSCRIBE_SMOKE_PASS_V1
llm=pass
role=pass
context=pass
task=pass
input=pass
chaining=pass
script=pass
```

### What a successful run proves

A successful final response verifies the Control snapshot was ingested; the plan resolved both reusable steps; role/context/task identities were resolved and materialized; the ChatGPT worker path and API credential worked; the fixed input reached the LLM; the first-step output became the second-step input; the local extension registry resolved `smoke-test`; the script executed successfully; and the final step was persisted as the call response for normal export/writeback.

The test is intentionally strict. Any extra LLM text, missing instruction sentinel, wrong input sentinel, broken step chaining, missing extension registration, or non-zero script result causes the smoke run to fail rather than produce a false positive.
