---
name: game-analysis
description: Investigate game logic, animation, physics and rendering through resource references, causal data flow and independent validation. Use to explain mechanisms or audit reconstructions, not for gameplay advice.
---

# Game analysis

Turn the requested behavior into a testable question. Establish what would count as a sufficient answer before expanding the investigation.

Terms used throughout this skill:

- **Target:** the original game build or artifact being studied.
- **Reconstruction:** the new implementation being compared with the target.
- **Contract:** the inputs, operations, outputs and execution conditions required to reproduce a behavior, as supported by target evidence.

## 1. Define the scope of each claim

Identify the object, version, operating conditions and result to explain. Establish identity and relationships through stable identifiers and references; names are search clues. Record conditions that could change the conclusion.

Check available material before asking for missing context. Ask only when the gap affects scope, authorization or acceptance.

## 2. Trace cause and effect

Follow `input -> computation -> state update -> write-back or downstream use -> observable result`.

The presence of code or an asset establishes availability, not execution. To explain a particular behavior, determine which path was selected, what it consumed and how its output reached the result. Connect resource references, execution logic and temporal state. Mark missing connections explicitly; a failed search does not prove absence.

## 3. Describe the behavioral contract

Account for **algorithms, data semantics, parameter origins, execution order and state retained across updates**. Check units, coordinate spaces, representation changes and update timing at each boundary. Mark parts not established by evidence as unknown.

Static dependencies can establish required ordering, but not the actual execution schedule. Matching a formula is insufficient if inputs, state or downstream use differ.

## 4. Validate independently

Establish the contract from target evidence before judging the reconstruction. Choose checks that distinguish competing explanations. Hold unrelated variables constant and measure the requested result directly.

Expected results must not come solely from the implementation under test. Use an independent reference and state its limitations. Choose data, function, system or runtime checks to match the claim. A passing check supports only its tested scope; successful execution or visual similarity alone does not establish equivalence.

## 5. Match claims to evidence

Distinguish observations, deductions, fitted values and unknowns. State the object and conditions for each conclusion. Keep unknown parameters unresolved. When fitting is authorized, record chosen values, their basis, their effects and remaining differences.

When evidence changes, identify the affected assumption or scope. For important unresolved questions, record the next check and the result that would resolve them. Update acceptance criteria when the user changes the goal; do not change what existing evidence proves.

## 6. Choose checks that resolve uncertainty

Start with inventories, indexes and targeted searches. Decode, disassemble or execute only where needed. Each step should address a specific unknown. Reuse evidence whose inputs and assumptions still match the task.

For Android targets, prefer a compatible emulator. Install the app, finish updates and resource downloads, then enable and authorize ADB debugging.

Prefer existing tools. Extract a shared script only for repeated work with stable inputs and outputs. Stop when the requested question has sufficient evidence. Build a reconstruction only when requested or necessary to answer that question.

## Working loop

`Question -> evidence map -> key unknown -> discriminating check -> revised conclusion -> acceptance`.

Scale this loop to the task. Read the [field guide](references/field-guide.md) when selecting tools, designing checks or reporting results. Use tools within the task's existing authorization. Keep original samples and environment-specific details in local case records.
