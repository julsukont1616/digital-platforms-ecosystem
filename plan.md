# Thailand Digital Platform Ecosystem — Build Plan

## What we're building

A single-file interactive HTML diagram showing Thailand's digital platform ecosystem as 6 horizontal layers + a Data & AI side column, with 4 togglable flow overlays. Orthogonal connections only (90° turns, 6px corner radius). Figma-quality aesthetics via CSS/SVG.

Output: `ecosystem.html`

## Architecture

All node positions are pre-computed from a grid formula. All connections are orthogonal polylines through explicit waypoints. The LLM never computes layout — it places things at specified coordinates and styles them.

## Build sequence

Each phase has its own file with a self-contained prompt. Feed that file (plus the current HTML from the previous phase) to the CLI. Verify the checkpoint before moving on.

| Phase | File | What it does | Depends on |
|-------|------|-------------|------------|
| 1 | `phase-1-grid.md` | Static grid: 6 layers + side column, all node cards positioned | Nothing |
| 2 | `phase-2-connections.md` | Orthogonal path renderer + 3 test connections | Phase 1 HTML |
| 3 | `phase-3-flows.md` | All 4 flows with connection data + toggle buttons | Phase 2 HTML |
| 4 | `phase-4-interactions.md` | Hover highlight, tooltips, draw-in animation | Phase 3 HTML |
| 5 | `phase-5-badges.md` | Scale badges + layer labels polish | Phase 4 HTML |
| 6 | `phase-6-polish.md` | Dark mode, responsive, final visual tuning | Phase 5 HTML |

## Rules

1. **One phase per CLI session.** Never combine phases.
2. **Attach the current HTML** when starting each phase (except Phase 1).
3. **Verify the checkpoint** visually before proceeding. If it fails, retry that phase — don't move forward with broken output.
4. **Phase files are self-contained.** Each has all data needed. The CLI should not need to reference this master plan or the v4 spec.
5. If a phase produces messy output, retry with the prompt: "Start over on this file. Read the attached plan carefully before writing any code."

## Reference

The full design spec is in `ecosystem-diagram-plan-v4.md` for human reference. The CLI should never be given that file directly — it's too large. The phase files extract exactly what's needed.
