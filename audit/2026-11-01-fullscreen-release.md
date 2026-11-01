# Fullscreen button release

## FBR-PLAN
Actor: Codex
Request: Commit, push, deploy the fullscreen button changes.
Plan: Review the pending diff and authoring records, regenerate runtime-bound browser acceptance in native Edge, commit exact source on a codex branch, run the release gate, push and integrate only after required CI passes, publish through the existing owner DAV release tool, verify all public assets and the update path, then commit publication evidence. Preserve score records and platform policies. Physical Android installed launch remains separately unverified.
Verification: pending.
UTC: 2026-11-01T18:09:18.6031391Z

## FBR-ACCEPTANCE
Actor: Codex
Plan reference: FBR-PLAN
Result: Fresh Edge 156 browser acceptance passed all six required browser categories against runtime digest c58319f174a0e9595cd5c0e3339ac521a9b118a356bb5e472f01105c7f9ffcfa. All 44 playback cases and 13 lifecycle cases passed. Sustained 3600-frame p95 interval 17.1ms, maximum 18ms and p95 CPU submission 1.2ms; all 22 sampled scene flash checks passed. Thresholds unchanged. Repository and generated-asset checks pass. Receipt: audit/2026-11-01-fullscreen-browser.json and review/evidence/handbook-browser.json.
Actions: Regenerated the ignored QA fixture; refreshed the required version-controlled acceptance receipt; reviewed the pending fullscreen diff without further runtime edits. Native Edge coordinate input was used after accessibility-click geometry was unavailable. Immediate snapshots after navigation/input could precede its completion; observed state was refreshed before continuing. Initial workflow inspection used a nonexistent ci.yml name, then located quality.yml; no workflow change.
Scope: Local browser/fixture evidence, not physical Android installed-window validation. The prior fullscreen inspection receipts are included, including the preserved byte-array parsing failure and corrected readback.
Next: Commit exact release inputs, run release gate and required remote CI, merge and deploy.
UTC: 2026-11-01T18:17:10.5627306Z

## FBR-PUBLISHED
Actor: Codex
Plan reference: FBR-PLAN
Source: b72eada76df7bc7508a9f39239e75d3a0f7f7e7c, integrated normally via PR #25 as 0e206a016ad1dc07e169a95eca7b44da1c422415 after both required Bun/CI checks passed. Local exact-merged-source gate passed all 237 tests, repository, generated package and browser requirements.
Deployment: Runtime 9344c61c6475cef32ae7 published at 2026-11-01T18:20:26.879Z through the pinned owner-DAV publisher. All 103 publication paths completed; 94 public cached assets, entry graph, worker and fullscreen manifest verified. Score records/policies, authored world documents and catalogs preserved. Publisher session quit after completion.
Client verification: Existing client moved from f6395c37345e39f49387 to 9344c61c6475cef32ae7 using Settings Update game; Ready to play offline returned, displayed personal best 5,300 and Prism Garden 0-point checkpoint preserved. A Settings tap at 390x844 changed the API-driven fullscreen label to Exit fullscreen while opening Settings; close retained fullscreen. No score submitted. Receipt and screenshot included. This is local Chromium evidence, not a physical Android guarantee.
Test-tool correction: Unscoped Update game matched three controls; selected the observed settings-update control, which completed the update. No application change was needed. Native Edge acceptance window was task-created; cleanup requested its closure. The local preview and browser viewport override are cleaned up after verification.
Files: Dated deployment, merged release gate, public live, client update and screenshot receipts; this appended log; publication hashes/patch. Audit-only follow-up does not alter the deployed runtime and requires no second deployment.
UTC: 2026-11-01T18:22:06.4442211Z
