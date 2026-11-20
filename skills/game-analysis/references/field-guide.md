# Field guide

Read when selecting the next action, designing a check or preparing a report. Tool choices below are optional; they are not a required sequence.

## Select the next check

State three things: **the question, the competing explanations, and the observation that would distinguish them.** Use these to select the evidence and tool.

| Unknown | Evidence to seek | Suitable methods |
|---|---|---|
| What is being examined? | Identity, format, version and dependencies | File headers, archive listings, hashes, package or device metadata |
| How are objects connected? | References, bindings and data origins | `rg`, object indexes, a compatible resource parser |
| How is a result computed? | Relevant operations, field semantics and inputs/outputs | Small Python analyses, targeted source inspection or disassembly |
| When does a path run? | Selected branches, effective parameters, update order and prior state | Call traces, logs, state inspection or frame captures |
| Does a reconstruction match? | Independent reference results under matched conditions | Numerical comparisons, controlled interventions, browser or graphics-state inspection |

Shell commands, `rg` and Python cover routine inspection. ADB supports Android device access; resource parsers interpret formats; disassemblers and CPU emulators support native-code analysis; shader reflection and translation expose graphics interfaces and computations; browser tools observe a reconstruction running in a browser.

Use an available tool only when it addresses the current unknown. Record the tool version and the input on which it succeeded. Confirm compatibility with the sample rather than assuming it from the tool name. Availability checks, documentation reads and execution are separate observations.

Official entry points, when needed: [ADB](https://developer.android.com/tools/adb), [UnityPy](https://github.com/K0lb3/UnityPy), [Unicorn](https://github.com/unicorn-engine/unicorn), [SPIRV-Cross](https://github.com/KhronosGroup/SPIRV-Cross).

## Connect claims to evidence

Retain this locator chain:

`sample identity -> object, field or code location -> reproducible check -> observed result -> scoped claim`.

| Evidence layer | What it can establish |
|---|---|
| `static` | Data, algorithms or capabilities present in a specified target artifact |
| `target-function` | Outputs of an isolated target function for specified inputs; not proof that the game invoked it |
| `independent-reference` | Outputs of a separately validated model or implementation; not by themselves proof of target behavior |
| `target-runtime` | What the target selected or executed in a specified environment and interval |
| `reconstruction-runtime` | What the reconstruction itself produced |

Record evidence layer separately from claim status:

- **Confirmed:** evidence establishes the claim within the stated scope.
- **Hypothesis:** an explanation has supporting evidence but still needs a distinguishing check.
- **To-verify:** evidence is missing or insufficient to assess the claim.

Parameter origin is separate again: a **recovered** value comes from a cited target artifact or observation; a **fitted** value is chosen to meet a stated objective. Record any transformation between a recovered field and its effective value. A chosen value does not resolve an unknown target value.

## Match validation to the claim

- **Mechanism:** vary the relevant input or state and observe the requested result when execution is needed to distinguish explanations. Static claims may be resolved from artifacts alone.
- **Reconstruction:** align semantics and conditions before comparing outputs. Check where data crosses stage boundaries.
- **Dynamic behavior:** compare state evolution over time, including initialization, sustained input, input removal and relevant state transitions.
- **Rendering:** trace produced data through sampling and composition to the requested output. Check representations, resource state and execution conditions separately.
- **Equivalence to the target:** use independent target results under matched conditions and a stated error criterion. Set the criterion before evaluating the candidate.

With static evidence only, report the supported contract, deductions and unresolved runtime questions. A local pass does not establish system equivalence. If a check cannot change a conclusion or resolve an acceptance condition, choose a more useful check.

## Report and stop

For a small question, a concise answer with evidence locators is sufficient. For a longer investigation, maintain one record:

```text
Question and scope: object, conditions, requested deliverable
Sources: sample identifiers/hashes, tool versions, evidence locators
Contract: inputs, operations, parameters, schedule, retained state, outputs
Validation: independent reference, checks, observations, error and coverage
Conclusion: established claims, deductions, fitted values, unknowns
Open items: responsible role, next check, observable resolution condition
```

Lead with the answer, then give evidence, scope and the smallest reproduction procedure. Stop when the agreed deliverable is supported; report unresolved conditions that prevent completion. Keep sample-specific addresses, layouts, parameters, scripts and assets in local case records.
