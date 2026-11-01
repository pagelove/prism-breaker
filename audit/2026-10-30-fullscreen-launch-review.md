# Installed fullscreen launch review

## FS-PLAN
UTC: 2026-10-31T02:29:26.9166415Z
Actor: Codex
Request: Make the PWA launch fullscreen by default.
Plan: Inspect manifest, startup controller and existing regression coverage; compare the public manifest; check current platform requirements. Change runtime only if a missing or incorrect setting is found. Preserve user exit behavior and do not attempt to bypass gesture requirements.
Initial observations: Repository manifest already uses display fullscreen. Phone start/resume requests API fullscreen. Web search could not retrieve the public manifest, so direct public HTTP readback is pending. Initial rg globs were rejected by PowerShell/rg; corrected searches used explicit files. No runtime changes made.
Affected files: this audit and its evidence receipt.
Verification: pending public readback and focused existing tests.

## FS-VERIFIED
UTC: 2026-10-31T02:29:59.0197411Z
Actor: Codex
Plan reference: FS-PLAN
Result: Live manifest returns HTTP 200 and display=fullscreen, id=/, scope=/, start_url=/?source=installed. Nine focused display/PWA checks pass, zero failures. No missing launch setting was found; no runtime edit or deployment is warranted. Device-specific installed-window behavior remains unverified.
Readback correction: The first PowerShell response exposed application/manifest+json as a byte array. Passing it directly to ConvertFrom-Json yielded null fields; this was a probe parsing error, not a live manifest error. Original receipt is preserved. Explicit UTF-8 decoding produced the verified receipt.
Platform evidence: https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/display documents the browser-controlled requested launch mode. https://developer.mozilla.org/en-US/docs/Web/API/Element/requestFullscreen requires transient user activation. Consequently no script can guarantee tap-free fullscreen when the installed browser declines the manifest mode. Existing phone start/resume taps are the supported fallback.
Affected files: audit/2026-10-30-fullscreen-launch-review.md, audit/2026-10-30-fullscreen-launch-live.json (failed parser receipt), audit/2026-10-30-fullscreen-launch-verified.json. The JSON receipts include SHA-256 hashes of reviewed source. Reviewable change evidence is the additive audit files; application source is unchanged.
