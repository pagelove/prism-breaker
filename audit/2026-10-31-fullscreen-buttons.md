# Fullscreen from button actions

## FB-PLAN
Actor: Codex
Request: Combine fullscreen with any and all button presses.
Plan: Add one delegated trusted-click handler for phone and installed-app buttons, including dynamically added controls. Keep each action synchronous and unchanged; skip fullscreen/layout toggles and gesture-consuming share/copy/download/install actions using document attributes. Attempt API fullscreen even if the installed window reports fullscreen (the reported Android case can still benefit). Keep fullscreen across return to the start screen once entered through a button; honor an explicit/system exit until a new play action or explicit fullscreen request. Do not request on synthetic events, ordinary desktop browser clicks, or page load. Add behavioral tests for these paths and retain failure/retry handling. Rebuild the offline package and run the suite. Runtime changes are local until the normal release gate and publication complete.
Affected files planned: public/display.js, public/index.html, tests/display.test.mjs, FULLSCREEN-UPGRADE.md, generated PWA artifacts, audit receipts.
Verification: pending.
Plan UTC: 2026-10-31T17:37:57.7925321Z

## FB-IMPLEMENTED
Actor: Codex
Plan reference: FB-PLAN
Changes: Added trusted delegated button handling for phone/installed windows, including explicit API entry in installed fullscreen mode, retained navigation fullscreen, user-exit suppression, and document-authored gesture exclusions. Added nine behavioral regressions, updated fullscreen guide, rebuilt immutable/offline runtime 9344c61c6475cef32ae7 (94 cached assets).
Verification: 237 tests passed, 0 failed after complete build. Local Chromium/IAB 390x844: Settings opened while fullscreen control changed to Exit fullscreen; closing Settings retained Exit; explicit Exit followed by Settings retained Enter; Start adventure restored Exit; pause and Back to start screen retained Exit and checkpoint. This is local browser evidence, not a physical Android/Edge installed-app certification. A read-only browser evaluation exposed fullscreenElement as null while the app's fullscreen API-driven label read Exit; the receipt relies on observed app state, not an unsupported OS-visibility claim.
Failures/corrections: First focused run had 14 pass/1 fail because fake toggle controls lacked getAttribute; completed DOM fixture interface, then full suite passed. One browser Settings click immediately after leaving fullscreen could not resolve its location during resize; refreshed observed state, then the click succeeded. No runtime workaround was introduced for either test-tool issue. An initial search referenced nonexistent public/input.js; corrected inspection used actual app paths.
Affected files: public/display.js, public/index.html, tests/display.test.mjs, FULLSCREEN-UPGRADE.md, public/pwa-release.js, public/sw.js and this audit/evidence. Previous fullscreen-review files are preserved separately and not claimed as part of this change.
Release status: Implemented and tested locally. Not committed, pushed or deployed in this task. Full exact-source release approval and publication remain required before live release.
Verified UTC: 2026-10-31T17:41:39.5397713Z
