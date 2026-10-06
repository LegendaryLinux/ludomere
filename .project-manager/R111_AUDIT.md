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
  launched, sidebar turned green and Stop appeared. Root removed its X11 game window afterward;
  later checked xdotool's manual and corrected that this destroys the window rather than requesting
  normal process exit. Do not infer game exit/stop defects from that automation action.
- Measured Gungeon payload339,363,121 B, prefix355,554,544 B and archive382,662,456 B: about1.078 GB
  on disk. Coffee Talk Depot preparation succeeded after wallet activation; component/install consent
  accepted through UI. Track subsequent transfer/disk changes before adding more test games.
- Test game transfer budget initially0.383 GB, then Coffee Talk Depot (557 MB installed payload).
  Measured combined payload/prefix/archive plus dependency cache approximately2.15 GB; reserve
  a conservative4 GB of the40 GB allowance including download overhead until exact totals settle.
  No intentional cloud
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

### P330 — discover the credential service before reading a saved login

- Saved-login reads reuse existing bounded Secret Service discovery/advertised provider activation.
  Standard providers remain preferred; KDE compatibility activation is used only when advertised.
  No wallet settings changed, new provider hardcoding, plaintext fallback or token cache added.
- Preserve original authentication generation and durable sign-out barriers before discovery,
  before credential read and after read. Discovery itself does not request unlock or collection
  access; the keyring's existing credential-read behavior still applies afterward.
- Independent security/lifecycle review PASS. Seven focused synthetic/private-bus regressions,
  formatting, all-target Clippy and cargo build --locked PASS. User-unlocked real provider remains
  running; no forced wallet restart/lock was used to claim a cold-start integration test.

### P329 — refresh managed-file summaries without blocking GTK

- Move refreshed archive counts/sizes and legacy-file metadata reads to workers. Share one refresh
  callback per files page/product, discard older requests and detached/account-stale results,
  and reserve profile activity before worker entry so reset cannot race profile recreation.
- Keep prior summary on read failure and update existing labels in place. Initial page construction
  still has older synchronous reads; this does not claim every Files path is now asynchronous.
- Independent source/lifecycle review PASS. Three private regressions PASS: summary equivalence,
  SQLite-lock/GTK heartbeat with stale/reset cases, and existing archive arrival/deletion controls.
  First existing-test invocation stopped at its required fixture-prefix guard; corrected isolated
  invocation passed. Formatting, all-target Clippy and cargo build --locked PASS.

## Further findings
### P331 — finish native installer restart requirements

- Coffee Talk's .NET vendor log confirms successful setup with HRESULT0x80070BC2 and restart
  request. Its Windows3010 status became Unix194 and Ludomere incorrectly rejected it.
- Recognize documented3010/1641 low-byte results only for native MSI and the exact official
  dotNet45/NDP452 installer. Other executables, Winetricks and interpreters remain strict.
- Drain installer children, then run the selected prefix's Wine restart routine through normal
  tracked UMU execution before recording completion. Also finalize after zero success, ensuring
  a retried already-installed component cannot bypass an interrupted restart. No host reboot.
- Independent source/security review PASS. Seven focused private regressions PASS, including
  explicitly synchronized inert process/drain/cancel checks, receipt/retry, strict failures and
  existing durable guard/MSI-path tests. Formatting, all-target Clippy and build PASS.
  Real Coffee Talk retry remains pending the rebuilt binary; no live success claimed yet.

### P332 — keep setup outcomes visible while reading diagnostics

- Pin concise sanitized failure/status above a diagnostics-only scroller, keep Close outside it,
  hide finished progress bars, and title terminal states Setup complete/failed/stopped using the
  existing structured outcome. Put full selectable error before operation/stage history.
- No process, retry, launch or background-window behavior changed. Independent review PASS;
  formatting/error test and mapped400px GTK scrolling/control regression PASS. Initial GTK test
  looked for a collapsed expander child too early; corrected fixture only, then passed.
- Formatting, all-target Clippy and cargo build --locked PASS. Live retry on new code next.

### P327 — confirm and track permanent Depot cancellation

- Confirm Downloads cancellation, retain Keep as default, and show Cancelling while cleanup runs
  off GTK. Preserve published payloads and current temporary-file safety checks; full errors become
  terminal failures with retry controls instead of stale busy state or silent refusal.
- Retain cleanup ownership/profile activity through terminal publication and reject competing
  resume/pause/cancel admissions. Independent review found two races; corrected recovery admission
  ordering and preserve an installation's proven success if it beats a late cancellation request.
- Three focused backend and one GTK regression PASS, including protected-directory refusal,
  journal preservation/retry, held-gate responsiveness, stale admission and late completion.
  Fixture-only AlertDialog API/unnamed-widget lookup issues corrected before successful run.
  Independent UI/backend re-review, formatting, all-target Clippy and build PASS.
- Coffee Talk real retry completed setup, updated Play/installed title in place, enabled normal
  cloud sync and rendered language/title/profile-selection screens. No game save was deliberately
  created or cloud file deleted. Root used Ludomere Stop after discovering X11 windowclose does
  not end the game process; this is a test-driver correction, not a product defect.

### P334 — explain empty library search results

- Show no-match and hidden-games guidance in the existing Home view, without clearing filters,
  replacing cards or navigating from another page. Preserve existing empty-account guidance.
- Independent review PASS; mapped empty/filter/scroll/focus regression and existing search/filter
  regression PASS. Formatting, all-target Clippy and build PASS before commit.
- Coffee Talk Stop returned to Play and no Coffee Talk/Gungeon process remained. Live Stop exposed
  a separate search/sidebar inconsistency, assigned P337. Normal game exit was not simulated by
  destroying its X11 window; no automatic post-exit cloud-sync success is inferred from that action.

## Remaining findings

### P333 — keep Downloads actions visible with long failures

- Full selectable archive/Depot diagnostic labels scroll inside a capped viewport, leaving
  Retry/Cancel outside. Preserve existing cancellation/session behavior and all diagnostic text.
- Independent review and four focused GTK tests PASS. Mapped real-CSS fixture at1100x600 kept
  archive/Depot headers at210/241px for roughly16KB errors; inner scrolling leaves actions and
  outer scroll fixed. Formatting, all-target Clippy and build PASS.

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
