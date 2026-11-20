# game-analysis-kit

**Analyze game logic, animation, physics and rendering through traceable evidence.**

[![A character shown in five synchronized views: final composite, rig and motion, character color, normal buffer, and bloom.](media/character-debug.webp)](media/character-debug-1080p.mp4)

[Watch the 1080p video](media/character-debug-1080p.mp4)

16 seconds, 1920 x 1080, 30 fps, silent. The views share one animation state and camera. Buffer views use actual outputs from the reconstructed renderer; display transforms are labeled.

## Case: character animation and rendering

The example traces character resources into animation, secondary motion and rendering. The recording shows:

- **Final composite:** character shading and post-processing.
- **Rig / motion:** live rig transforms, animation time and a rotation trace.
- **Character color:** the first character color attachment (MRT0).
- **Normal buffer:** stored RGB values from the normal attachment (MRT3).
- **Bloom:** the composed bloom buffer, displayed at 2x gain.

This is a package-based reconstruction with fitted parameters, not verified native-game equivalence.

## Quick start

1. Ask your agent to read [SKILL.md](skills/game-analysis/SKILL.md).
2. Provide the game build or sample, the question, and the result you need.

> Use game-analysis to investigate this game behavior. State the question, choose the smallest useful evidence path, and explain what is established and what could change the conclusion.

For reuse, copy the entire `skills/game-analysis/` directory into a skill directory supported by your agent. Load the [field guide](skills/game-analysis/references/field-guide.md) when selecting tools, designing checks or reporting results.

## Scope and requirements

| Item | Scope |
|---|---|
| Focus | Game logic, animation, physics, rendering and reconstruction audits |
| Requirements | No runtime dependencies for the skill itself; analysis tools depend on the target and question |
| Included | Analysis instructions, a field guide and representative media |
| Not included | Extracted game assets, format decoders, a viewer runtime or an automated reconstruction system |
| Current evidence | Distilled from one Android / Unity investigation; usefulness across games needs further evaluation |

Keep samples and task-specific scripts in local case directories. Select existing tools as needed; add shared code only when repeated use justifies it.

## Method

1. Define the scope of each claim.
2. Trace inputs through computation and downstream use to the result.
3. Describe the supported behavioral contract; mark unknowns.
4. Validate against an independent reference.
5. Distinguish observations, deductions and fitted values.
6. Choose checks that resolve uncertainty; stop when the requested goal is met.

The game-specific focus is on **resource references, state over time, and downstream use of computed results**.

## Attribution

Inspired by the direct-CLI approach in [leanrea](https://github.com/aicodeking/leanrea), reviewed at commit `09ba4aa`. Upstream benchmark results are not performance claims for this repository.

The skill text is [MIT licensed](LICENSE). Third-party game content shown in the media and external tools retain their respective rights and licenses.
