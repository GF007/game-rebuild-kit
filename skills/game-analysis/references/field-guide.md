# Field guide

Choose tools by the uncertainty they resolve. The methods below are not a required sequence.

## Select the next check

State **the question, competing explanations and the observation that would distinguish them** before selecting a tool.

| Unknown | Evidence to seek | Suitable methods |
|---|---|---|
| What is being examined? | Identity, format, version and dependencies | File headers, archive listings, hashes, package or device metadata |
| How are objects connected? | References, bindings and data origins | `rg`, object indexes, a compatible resource parser |
| How is a result computed? | Relevant operations, field semantics and inputs/outputs | Small Python analyses, targeted source inspection or disassembly |
| When does a path run? | Selected branches, effective parameters, update order and prior state | Call traces, logs, state inspection or frame captures |
| Does a reconstruction match? | Independent reference results under matched conditions | Numerical comparisons, controlled interventions, browser or graphics-state inspection |

Use shell commands, `rg` and Python for routine inspection. Probe only needed capabilities; record the tool version, input and result. Installation or device connectivity alone does not establish compatibility.

Record failed operations and observed errors. Try useful alternative paths; request only the input needed to unblock progress. Keep environment failures separate from target limitations.

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

- **Confirmed:** evidence establishes the scoped claim.
- **Hypothesis:** supported explanation awaiting a distinguishing check.
- **To-verify:** insufficient evidence to assess the claim.

Parameter origin is separate: **recovered** values come from cited target evidence; **fitted** values are chosen to meet an objective. Record transformations to effective values. Fitting does not resolve an unknown target value.

## Check pipeline coverage

For each stage relevant to the requested reconstruction, record:

| Field | Required detail |
|---|---|
| Stage | Operation and conditions under which the target selects it |
| Target evidence | Build and asset, code or runtime locator; distinguish presence from execution |
| Inputs | Origins, representations, resource state and retained history; identify missing, substituted or fitted values |
| Output | Produced data, downstream consumer and verification result |

Follow the chain to the final displayed or consumed output. Missing core stages and unexplained substitutions remain technical gaps regardless of visual similarity.

## Match validation to the claim

- **Mechanism:** vary relevant inputs or state when execution is needed to distinguish explanations; static claims may be resolved from artifacts.
- **Reconstruction:** align semantics and conditions; check data crossing stage boundaries.
- **Dynamic behavior:** compare initialization, sustained input, input removal and relevant state transitions over time.
- **Rendering:** use the pipeline coverage record; align camera, state, resolution and presentation conditions for visual comparisons.
- **Equivalence:** compare independent target results under matched conditions, using an error criterion set before evaluating the candidate.

With static evidence only, leave unsupported runtime questions open. A local pass does not establish system equivalence. Choose checks that can resolve a claim or acceptance condition.

Retain comparison inputs, candidate versions, masks and measurement methods. If these change, repeat matched comparisons before attributing improvement. Keep numerical error separate from pipeline correctness.

## Diagnose the final image

For visible defects, trace `source assets -> sampling -> post-processing -> composition -> screen display`. Inspect effective resources, state and intermediate outputs along the affected path before choosing a fix. An enabled anti-aliasing option does not establish final-image coverage.

Use a matched camera, pose, lighting, temporal convergence and display scale; vary one suspected cause at a time. For edge defects, distinguish source geometry or texture detail, sampling and mip selection, temporal filtering, alpha coverage and blending, and actual output dimensions. Temporally filtered RGB can still acquire hard edges from a later binary alpha mask. Check color and coverage separately, including premultiplication at composition boundaries; a resolution change is a separate intervention from an asset upgrade.

Measure the affected region and an unaffected control region where useful. Retain the last verified delivery, rerun the old reference path and representative new paths, and isolate browser checks from the user's active camera or controls. Record which conditions support the diagnosis; a fix under one condition does not explain every later complaint.

## Verify assets and variant contracts

When quality is requested, distinguish these claims and report missing evidence:

| Quality claim | Evidence needed |
|---|---|
| Highest locally available | Inventory of the installed resources and compatible candidates actually compared; unavailable optional downloads remain unknown |
| Native default | Target defaults and their conditions; these do not establish the current runtime choice |
| Configured upper limit | Declared quality or LOD limits for the relevant build and configuration; these do not prove selection |
| Observed runtime selection | Effective target resources, bindings and settings for the measured device and state |

Inspect payloads rather than names or triangle counts alone. Compare topology, vertex attributes used by the shaders, skin weights and bone/bind-pose compatibility; verify material bindings and required passes. For textures, inspect native dimensions, format, channel semantics and the full mip chain, then check sampler and mip selection when runtime access exists. Enlarging an image does not recover missing source detail. Record which candidates were selected, rejected or remain unavailable and why.

For character or outfit collections, keep a compact per-variant record of identity, resource dependencies, pose/skeleton assumptions, material/pass differences and readiness. Reuse the validated pipeline where contracts match. Check one representative of each new shader family or rendering path before batch expansion, then smoke-test every delivered variant for selection, loading and rendering. Estimate work by new dependencies and behavioral differences as well as count. A higher-quality mesh can require additional attributes or passes; a static pose check does not establish animation compatibility.

## Inspect executed work

Apply this when the requested deliverable includes an interactive renderer inspector. Generate the stage list and metadata from actual execution: order, inputs and outputs, resource identities, dimensions/formats and relevant draw, depth, blend or sampling state. Distinguish current outputs, retained history and cached or substituted inputs. A reconstruction trace establishes its own execution, not the target game's schedule.

Capture stage outputs before reused buffers overwrite them. Label whether a stage control displays a recorded result or actually stops execution. Make depth/channel visualization and display conversions explicit; presentation views are not raw buffer values.

Preserve rendering behavior while observing it: restore graphics state changed by inspection and avoid advancing or resetting temporal history merely to view a buffer. Disclose unavoidable redraws or resets and re-establish matched state before comparing the final result with inspection enabled and disabled: hold render/output dimensions fixed and let temporal history converge. Test layout-driven resizing separately. Record any instrumentation cost separately from rendering performance.

## Deliver an inspectable viewer

Use the relevant parts for HTML/viewer deliverables; an inspector, dark background or particular resolution is not a universal requirement.

- **Resolution:** distinguish internal render targets, output/drawing-buffer dimensions and CSS display size, including device pixel ratio. Define whether presets control height, total dimensions or render scale. Report requested and actual dimensions and capability limits. Preserve the selected quality semantics when panels change layout, resize dependent targets and invalidate affected temporal history when dimensions change.
- **Presentation:** keep backdrop, ground, grid and display shadows configurable and label their provenance. Separate viewer additions from recovered target materials, lighting and scene behavior; a display floor or fitted shadow does not establish original-scene equivalence.
- **Portable delivery:** build from declared runtime dependencies, including optional variants and their material paths. Check reference closure, archive contents and integrity, then launch the delivered entry point using only package contents in an isolated location or server. Detect reliance on development paths, browser caches or undeclared network resources. Exercise the default and representative additional paths. Report package-integrity and runtime-startup results separately; neither substitutes for the other.

## Choose the delivery checkpoint

For requested reconstructions, distinguish these outcomes:

| Checkpoint | Condition |
|---|---|
| Runnable result | A minimal execution path runs and can be inspected; unresolved inputs are listed |
| Usable delivery | Agreed technical and visual criteria are met; intended interactions work and residual differences are disclosed |
| Precision follow-up | Explicitly requested scope, reference conditions and error criteria govern further refinement |

Advance only as required by the requested deliverable. A runnable checkpoint does not close unmet acceptance items; an optional residual does not automatically extend a completed task.

## Report, resume and close

For a small question, a concise answer with evidence locators is sufficient. For a longer investigation, maintain one record:

```text
Question and scope: object, conditions, requested deliverable
Sources: sample identifiers/hashes, tool versions, evidence locators
Contract: inputs, operations, parameters, schedule, retained state, outputs
Validation: independent reference, checks, observations, error and coverage
Conclusion: established claims, deductions, fitted values, unknowns
Progress: current checkpoint, verified artifact paths, unmet criteria
Open items: responsible role, next check, observable resolution condition
Environment: task-created tools or processes, changes and cleanup status
```

On resumption, verify that target identity, artifacts and conditions match the record before reusing evidence. Runner interruptions are not target limitations.

Deliver the result, supported scope, residuals and minimal reproduction steps. Test the delivered entry point and package, not only a development preview. Restore temporary changes to the target; remove only task-created temporary tools or processes. Retain evidence and user data. Keep sample-specific details in local case records.
