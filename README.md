# WIOM CSP — NetBox Setup Flow

Visual spec and engineering reference for the **Wiom Channel Service Partner (CSP)** NetBox installation wizard.

This repo is the **single source of truth** for the 31-screen flow an agent walks on-site at the customer's home to install the fibre NetBox. It mirrors the `Install_Flow_Visual_Spec_v2.2.0.md` committed in `wiom-tech/wiom-csp-app-apr09` under `docs/features/install-flow/`, and it is kept in sync with every PR that lands against that path.

## Current spec

- **[Install_Flow_Visual_Spec_v2.2.0.md](./Install_Flow_Visual_Spec_v2.2.0.md)** — authoritative, self-contained.

The spec is self-contained: every surface, component, token, label, navigation rule, and design decision needed to understand or re-implement the wizard is captured inline. No external cross-references.

## Scope

The NetBox setup wizard covers the **on-site installation experience** — from PayG acknowledgement through selfie, Aadhaar, payment, power-on, ISP configuration, placement photos, wiring, optical power, speed test, to the Happy Code handoff. Thirty-one surfaces plus three overlay dialogs.

**Not in scope** — the install drilldown (the pre-wizard Home-screen surface that surfaces the install task and its states) is spec'd separately in `WIOM-CSP-Setup-scenarios-drilldown` (see `Install_Flow_Visual_Spec_v1.5.1.md` there).

## How this repo relates to the source code

| Artefact | Where it lives |
|---|---|
| This spec (v2.2.0) | `Install_Flow_Visual_Spec_v2.2.0.md` — this repo, and also `wiom-tech/wiom-csp-app-apr09:docs/features/install-flow/Install_Flow_Visual_Spec_v2.2.0.md` |
| Kotlin / Compose implementation | `wiom-tech/wiom-csp-app-apr09:feature/installation/src/main/java/com/wiom/csp/feature/installation/redesign/` |
| Shared tokens + validators | `wiom-tech/wiom-csp-app-apr09:core/common/` |
| Flutter production PRD (authoritative for the ISP configuration module) | `installation-supply-view` (internal) — see §3.13 of the spec for the specific file references |

## Authoring rules

- New work on the wizard surface updates the spec in `wiom-tech/wiom-csp-app-apr09` first, and that commit is mirrored here.
- Any amendment to the spec triggers a version bump — the filename always carries the version (v2.2.0 → v2.2.1 → v2.3.0 etc.). No "living latest" file name.
- The spec document must stay self-contained — no delta-only specs, no "see v2.1.1 for unchanged content" references.
- Flutter `installation-supply-view` is the source of truth for functional behaviour in modules where the Kotlin port is catching up (currently: §3.13 configuration module). When the two diverge, Flutter wins unless a product manager has explicitly signed off on a deliberate deviation.

## History

- v2.2.0 (this repo's initial commit) — PRD realignment of the configuration module + cross-cutting system-bar inset rule. Supersedes v2.1.1 and the v2.1 DRAFT.
- v2.1.1 — as-built snapshot of the wizard at PR #41 merge on 2026-04-16 (superseded).
- v2.1 DRAFT — reference-repo-derived draft (superseded).

Earlier draft history is preserved in `wiom-tech/wiom-csp-app-apr09:docs/features/install-flow/` for audit purposes.
