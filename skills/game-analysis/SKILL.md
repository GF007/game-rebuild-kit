---
name: game-analysis
description: Analyze game logic, animation, physics and rendering; build or audit reconstructions using target evidence. Use for technical investigation, not gameplay advice.
---

# Game analysis

Define a testable question and the evidence needed to support the requested deliverable.

- **Target:** the original game build or artifact being studied.
- **Reconstruction:** the new implementation being compared with the target.
- **Contract:** the inputs, operations, outputs, state and execution conditions supported by target evidence for reproducing a behavior.

## Start

Use supplied material and lightweight read-only checks to establish **target/build, access, deliverable and acceptance level**. Ask one concise question for gaps that change scope, access or acceptance.

If discovery cannot resolve the target or access, ask for the game name, sample path or intended device; request an ADB endpoint or serial only when needed. Discover package IDs, engine names and formats yourself when possible. If several plausible targets remain, ask the user to choose. Confirm identity and version before deeper inspection or changes.

Begin broad requests with a brief technical survey, then clarify the desired outcome. When a larger deliverable is already requested, the survey is a checkpoint; continue toward that deliverable.

For Android targets, prefer a compatible emulator. Install the app, finish updates and resource downloads, then enable and authorize ADB debugging.

## 1. Define the scope of each claim

Record the object, build, state and output. With runtime access, use the selected object and effective bindings to narrow dependencies before broad extraction. Otherwise, follow stable identifiers and references; mark runtime selection as unresolved. Names are clues, not identity evidence.

## 2. Trace cause and effect

Follow `input -> computation -> state update -> write-back or downstream use -> observable result`.

Trace selected execution through resource bindings, computations and downstream processing to the final result. Code or asset presence establishes availability, not execution. Mark missing connections; a failed search does not prove absence.

## 3. Describe the behavioral contract

Record **algorithms, data semantics, parameter origins, execution order and retained state**. Check units, coordinate spaces, representations and timing across stage boundaries.

Static dependencies can constrain ordering without proving the runtime schedule. Matching formulas alone is insufficient.

For reconstructions, use the [pipeline coverage record](references/field-guide.md#check-pipeline-coverage). Record missing inputs and substitutions, their effects and evidence. A working fallback is not a recovered target value.

## 4. Validate independently

Establish the contract from target evidence before judging the reconstruction. Use an independent reference and state its limits. Choose checks that distinguish competing explanations, hold unrelated conditions constant and measure the requested result. Successful execution or visual similarity alone does not establish equivalence.

Preserve reference inputs, candidate versions and comparison conditions. Attribute improvements only through matched comparisons; lower output error can conceal compensating mistakes.

## 5. Match claims to evidence

Distinguish observations, deductions, fitted values and unknowns. Scope each claim. When fitting is authorized, record chosen values, their basis, effects and residuals; do not treat fitting as recovery.

For important unknowns, record the next check and its resolution condition. Revisit assumptions when evidence changes. A revised user goal changes acceptance criteria, not what past evidence proves.

## 6. Choose checks that resolve uncertainty

Use inventories, indexes and targeted searches before expensive decoding or execution. Probe only capabilities needed for the next check. Reuse existing tools and evidence with matching inputs and assumptions; create shared scripts only for repeated work with stable interfaces.

Build a reconstruction only when requested or necessary. On failure, distinguish tool or access problems from target limitations and choose another useful evidence path.

For visual reconstructions, verify target assets, active stages and input semantics, then deliver the agreed visual quality. Use image metrics for diagnosis; pixel-exact matching requires an explicit acceptance target. Prioritize residuals by visible impact, expected benefit and investigation cost. Preserve the last verified result during uncertain refinements.

Continue for unmet acceptance criteria when a useful check is feasible. If blocked, name the evidence gap and minimum missing input while continuing independent work. Deliver when the agreed criteria are supported; test the actual entry point, record limits and complete task-specific cleanup.

## Working loop

`Question -> evidence map -> key unknown -> discriminating check -> revised conclusion -> acceptance`.

Read the [field guide](references/field-guide.md) when selecting tools, designing checks or reporting results. Stay within the task's authorization. Keep samples and environment-specific details in local case records.
