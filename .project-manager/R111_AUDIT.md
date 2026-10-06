# Interactive audit, 2026-10-06

Window: 08:13:55–20:13:55 UTC. Branch: `improvement/interactive-ux-audit-2026-10-06`.
Main fast-forwarded to `5c0d5cb`; no upstream merge, push or new PR.

## Live testing

- Root launched Ludomere on the real KDE desktop with X11 for scoped automated input.
  User reports wallet already unlocked. No passwords or tokens captured or shared with agents.
- Reproduced search deletion/hiding when enabling Installed; zero-result Home pane is blank.
  App-only screenshots retained privately under `/tmp/ludomere-r111/`.
- Enter the Gungeon Depot preparation failed before game transfer with a credential-service
  D-Bus disconnect. Desktop metadata checks report no standard Secret Service owner and KWallet
  disabled, despite its service owning a bus name. User was notified; wallet settings unchanged.
  Source review identifies redundant keyring reads during Depot preparation despite UI-held token.
  Follow-up corrected the initial diagnosis: the legacy wallet compatibility API being disabled
  does not establish the user's actual Secret Service wallet is disabled. Activating the advertised
  org.kde.secretservicecompat provider restored org.freedesktop.secrets and the user unlocked.
  Existing discovery already supports that provider during explicit sign-in, but saved-token reads
  bypass it. P330 addresses that path; no wallet settings changed or credentials reset.
- Missing configured installer/extras directories created explicitly by root; existing files untouched.
- Enter the Gungeon Windows offline installer (about 382 MB) downloaded through the detail action,
  automatic installation completed, and Play appeared without reopening details. Game process/window
  launched, sidebar turned green and Stop appeared. Root closed its game window normally afterward.
- Measured Gungeon payload339,363,121 B, prefix355,554,544 B and archive382,662,456 B: about1.078 GB
  on disk. Coffee Talk Depot preparation succeeded after wallet activation; component/install consent
  accepted through UI. Track subsequent transfer/disk changes before adding more test games.
- Test game transfer budget used: approximately 0.383 GB so far (under40 GB). No intentional cloud
  deletion or real uninstall performed. Installation used the application's normal helper flow.

## Fixes

### P325 — retain search while changing library filters

- Preserve the query for boolean, language and metadata filters; keep search visible/enabled
  beside active chips. Preserve explicit Clear Filters behavior and view selection.
- Production change removes 20 lines from library/window; actual GTK regression exercises both
  input orders, all filter handler types, matching grid/sidebar counts, focus/widget identity,
  chip removal and Clear Filters without starting metadata workers or creating a real database.
- Independent UI review PASS. Focused private Broadway/DBus test PASS, formatting and all-target
  Clippy PASS. Commit717e8da and exact post-commit cargo build --locked PASS.

### P326 — show active downloads and retain full errors

- Featured transfer selection prefers active Depot/archive work over paused/failed history.
- Show full wrapped, selectable archive and Depot failures separately from changing ETA labels;
  retain Depot row errors through progress updates and refresh changed error text in the same state.
- Failed archive header action is labeled Retry download. Existing pause/resume/delete behavior
  and navigation are preserved.
- Independent source/UI review PASS. Two focused unit tests and two private GTK regressions PASS;
  formatting, all-target Clippy and cargo build --locked PASS. Fixtures prove control/text behavior;
  exhaustive visual clipping or real failure cases are not claimed from unmapped GTK widgets.

### P328 — use the authenticated session for Depot actions

- Carry the current token and original auth/online generations through direct Depot preparation,
  review and admission; avoid redundant saved-login reads. Reject expiry, account mismatch and
  stale sessions before new cache/observation/queue stages. Tokens remain absent from journals.
- Protected branch keyring work runs outside SQLite writes; revalidate before persistence.
  Migration restores once before its installation boundary, with original-session guards.
- Independent security/lifecycle review PASS; eight focused private regressions, formatting,
  all-target Clippy and cargo build --locked PASS. Existing updater API still captures its auth
  generation at worker entry; this change does not claim broader dispatch-provenance repair.
- Coffee Talk real Depot setup exposed a separate .NET4.5.2 exit194, queued as P331. DirectX
  setup completed; retain downloaded game files and investigate before retrying or resetting.

## Findings queued

- Explain zero-result Home searches rather than showing blank content.
- Downloads must feature active work before past failures and show featured error details.
- Depot cancellation needs confirmation, off-thread cleanup and terminal cleanup error feedback.
- Remove repeated keyring reads for already-authenticated Depot actions without weakening session
  revocation or storing credentials in serialized operation requests.
- Move managed-file summary database/stat work off GTK; batch repeated archive state reads.
- Avoid opening SQLite twice per game during cached metadata readiness load.
- Enable keyboard activation for game tiles; improve nested Genre list scroll discoverability.

Source findings are proposals until assigned, implemented and verified. Full interactive or game
coverage is not claimed from source review alone. Reports: `/tmp/ludomere-r111-{ui-critic,performance,reliability,depot-auth}.md`.
