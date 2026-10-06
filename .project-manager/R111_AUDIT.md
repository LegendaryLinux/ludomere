# Interactive audit, 2026-10-06

Window: 08:13:55–20:13:55 UTC. Branch: `improvement/interactive-ux-audit-2026-10-06`.
Main fast-forwarded to `5c0d5cb`; no upstream merge, push or new PR.

## Consolidated verification checkpoint

- Atb3f9227 the next private full build gate PASS: formatting, all-target Clippy with warnings
  denied,570 library tests, six integration tests, five Python helper tests and build.69 ignored
  library entries excluded by default; changed GTK paths independently exercised. Log:
  /tmp/ludomere-r111-full-build-8kbq3zr4/build.log. All34 commits have exact post-commit build PASS.

- At6b7328d the private build gate passes cargo fmt, all-target Clippy with warnings denied,
 566 library tests, six integration tests, five Python helper tests and cargo build --locked.
 57 ignored library entries are excluded by default; changed GTK paths were exercised separately.
 Log: /tmp/ludomere-r111-full-build-odjoz3gv/build.log. No exhaustive UI coverage claim.
- Two earlier harness failures retained: symlink helper blocker destination, then absent synthetic
 UID records preventing private D-Bus authentication. Wrapper now resolves/deduplicates blocked
 helpers and mounts only generated current-UID passwd/group/files-only NSS records. No real account
 database, wallet, desktop or external networking exposed; product tests were not weakened.
- Live P343/P345/P346 retest passes: healthy uninstall hides Retry/collapses alternative recovery,
 retains warnings/archive-default, restores blue Download/arrow in place, and source switching in
 the same chooser shows full paths while hiding Depot feedback for offline selections.

## Live testing

- P367 repair presentation independently reviewed and verified: padded scrolling fallback with
  clear Repair/Update title and hidden stopped spinner; reused reinstallation chooser restores
  standard680x620 dimensions/title. Actual mapped constrained-geometry fixture PASS
  (/tmp/ludomere-p367-8jvgzmkd), existing P346 source/destination fixture PASS
  (/tmp/ludomere-p346-r96dc1gv). Initial Clippy test-type complexity corrected with an equivalent
  cfg(test) alias, independently reviewed; final compile/fmt/Clippy PASS. No execution/consent
  changes; live retest still pending and inspection lifecycle addressed separately in P368.

- On695d738 the Account Factory Reset-to-Connection gap is visibly corrected; Connection remains
  Online and authenticated. No reset, sign-in exchange or settings mutation performed.

- Native Gungeon Repair offers reinstall/Browse/reset instead of Depot repair; no files changed.
  Review Reinstallation then remains in420x180 dialog, visibly clipping installer choices while
  Install stays available. Rechecked after loading, cancelled without installing. P367 assigned
  concrete handoff-size/layout fix; do not claim native repair end-to-end PASS from this flow.

- Settings Proton shows full selected runtime path, automatically reports Steam Linux Runtime
  found and disables its unnecessary download action. Public Load releases populates choices and
  enables download selection without changing the installed default or downloading a runtime.
  Account Connection shows Online and authenticated. No sign-out/reset or runtime change tested.

- Coffee Talk Properties onb3f9227 reproduced Switch-on-installed-Master refusal without changing
  branch/password; P363 addresses the verified pointless action. Read-only Cloud storage Check now
  completes with No remote save files/0B, in place. Normal sync setting remains enabled; no export,
  forced sync, cloud deletion or other settings change. Properties closed normally.

- Onb3f9227 initial Offline Installers shows both retained Gungeon archives/checkmarks/638MB.
  Confirmed native removal with archive deletion unchecked reports one game directory removed,
  zero prefixes and two archives retained. Detail changes to Download without reopening; arrow
  offers Install from Offline Installer. Chooser selects downloaded Linux2.1.9 and correct root.
  Cached install completes, Play launches native executable without Windows setup/repair, and
  the fresh marker is schema1/base.operating_system=linux with no UMU field. Game intro and main
  menu render; normal quit ends EtG.x86_64 and restores Play/white title/search in place.
  No extra transfer or deliberate cloud/save deletion; reservation remains9GB of40GB.

- Archive-only Gungeon macOS transfer paused at134.8/260MB. Initial featured trash clicks showed
  no dialog despite responsive navigation; after revisiting Downloads, ordinary clicks show Cancel
  download confirmation. Confirmed cancellation removes that transfer, preserving both completed
  Linux/Windows installers and native payload. Source diagnosis finds no proven dead handler;
  original transition remains unexplained, no speculative product change. Reserve9GB of40GB.

- Onc9f5b99, existing native Gungeon installation launches and renders its intro; normal window
  quit ends EtG.x86_64 and restores green Play/white title/search in place. The original mixed
  marker hash remains unchanged before/after launch, proving read-only recovery. No Windows repair
  accepted or deliberate game save/cloud deletion. Intro, not a completed gameplay test, verified.
  Further cached reinstall deferred until P355 saved launch-options preservation is corrected.

- P351 live Collections Tab shows a clear game-card focus ring and Enter opens its detail view.
  Gungeon's temporary favorite was restored; screenshot favorite-restored confirms Removed from
  favorites and an empty star. P353 Storage wording fits the990x700 settings window; normal outer
  scroll reaches lower controls. P350 Recheck completed too quickly to capture its busy appearance;
  deterministic fixture, not the live screenshot, establishes the pending state.

- Additional live controls: Comet manual check shows immediate checking/disabled button and
  returns to up-to-date; downloaded-file index reports one indexed/matched archive without changing
  payloads. Metadata refresh shows Game list500/569 and completes with Library synchronized in
  Notifications. On-demand detail artwork subsequently loads; metadata-search incomplete reflects
  intentionally lazy metadata, not a persistent synchronization spinner.
- Gungeon Logs shows its saved run and successful exit; inner scrolling pauses follow mode with
  an explanation, outer page scrolling exposes the full log panel and installation-log actions.
  No log export, clipboard copy or unrelated desktop inspection performed.

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

### P365a — save launch fields without overwriting unrelated preferences

- Atomic partial SQL updates only executable/arguments/updated timestamp, preserving raw runtime
  and pending-profile JSON, update policies, original creation timestamp and activity. Absent rows
  receive launch defaults and retain marker-based Windows runtime fallback; no schema change.
- Seed initial submitted text so unchanged Enter/focus/unmap does not save. Actual edits and
  failures remain retryable. Register profile activity before queued work and reject old session
  before filesystem/database access. No global operation lock or unrelated-download restriction.
- Independent review, four focused private SQL/actual-entry/old-signal/branch regressions,
  formatting, Clippy and compilation PASS. Evidence p365-qjlangm4, p365-4111ep92,
  p365-9774kct8, p363-w2ixj27h. No real profile changes for these tests.
- Full P365 design was rejected: its global gate would block editing during unrelated downloads,
  and unknown marker data would disable new windows until reopened. Stale installation-specific
  launch fields and broader Properties refresh still need a separate non-disruptive design.

### P366 — collapse unused Factory Reset feedback space

- Bind the reset-status scroller's own visibility to its label, collapsing the empty reserved
  area while retaining real progress and full selectable, capped-height error scrolling.
- Independent review, extended actual Account layout/status/lifetime fixture (p359-anwwrai6),
  formatting, Clippy and compilation PASS. Synthetic feedback expands, scrolls and collapses to
  the original measured height; no Factory Reset action, account change or private data in test.

### P364 — show update-check progress and results inside Settings

- Immediately disable duplicate check activation and show local pending/result/refusal/error text.
  Keep full redacted diagnostics selectable/wrapping, restore deliberate retry after terminal or
  stale sessions, and release weak page controls on close. Background work retains normal behavior.
- Keep pending feedback local so automatic/duplicate checks cannot clear unrelated main progress.
  Main result notifications retain existing policy; already-running does not promise a notification.
  Original click-time epoch/auth/online checks reject stale UI results, not already-queued work.
- Independent review, actual production-dispatch/inert-outcome mapped fixture (p364-17h3duxl),
  existing backend stale test (p364-fls7izo3), formatting/Clippy/compilation PASS. Fixture covers both
  duplicate orderings, reentrant retry, session changes, long redacted errors and destruction; no
  real batch updates run. Initial lint test placement and hidden-main effective-visibility assertion
  corrected in tests only, preserving main sentinel own visibility/text and mapped Settings checks.

### P363 — explain unavailable branch actions

- Branch Switch is disabled for invalid/current branch, Forget Password for invalid/Master, with
  useful tooltips. Preparation disables both actions; selection changes cannot bypass it. After
  handoff Switch stays disabled while named-branch Forget returns. Errors restore current eligibility.
- No credential-presence probe, branch backend or password policy changed. Independent review,
  actual mapped controls/lifecycle fixture (p363-0w7fepo0), formatting, Clippy and compilation PASS.
  Fixture invokes no real branch/password worker; no real branch switch claimed.

### P362 — retain notification hover across remapping and clean up on destruction

- Bind manually parented notification popover cleanup to its anchor's destruction, using a weak
  reference and parent check. Surface unrealization no longer permanently detaches the popover;
  never-presented windows now also clean up. History, timers, focus and click behavior unchanged.
- Independent source/lifecycle review PASS. Strict never-presented, mapped detach/reinsert,
  hide/show and pending-timeout teardown fixture PASS, along with unchanged notification action
  and Account status tests. Root verified no children-left/popover/surface warnings in all logs;
  isolated harness's pre-existing GSettings source diagnostics remain separate.
- Evidence p362-xqiig396, p362-cjd5fixj, p359-_vwcgyk0; formatting, Clippy and compilation PASS.

### P361 — explain unavailable Storage moves before clicking

- Move follows current selection and destination: disabled for empty/missing/same-target choices,
  existing Windows-prefix refusal, or active work. Tooltips explain why; changing selection or
  rebuilding rows cannot re-enable active Move. Backend guards and destination choice unchanged.
- Independent source review, mapped actual-controls regression and existing backend destination
  preflight PASS; formatting, Clippy and compilation/build PASS. Initial fixture incorrectly
  requested invalid selection in a nonempty autoselect dropdown. Corrected only the setup to empty
  its real model, explicitly assert no selection, then retain every sensitivity/tooltip/busy check.
  Evidence p361-q5cbyzon (initial), p361-5nevxott (pass), p361-htizftam (backend pass).

### P359 — keep Account session status current

- Refresh the existing GOG session subtitle from in-memory network, token expiry and logout state.
  Weak row/model references stop updates after destruction; unchanged text produces no updates.
  No keyring, database or network probes, identity/action redesign or navigation added.
- Actual mapped-row transition/time-expiry/borrow/focus/destruction fixture, independent review,
  fmt/Clippy/build PASS. Fixture-only nonexistent stack field corrected to real content stack;
  first old-binary run correctly rejected zero tests. Strict assertions retained.
- A separate pre-existing notification-popover teardown warning appeared in this test and is
  assigned P362 diagnosis; do not attribute it to status refresh or claim a clean global teardown.

### P355 — retain launch options through cached reinstalls and source migration

- Fresh cached-offline and offline migration plans now retain saved arguments and full Windows
  runtime preferences while preserving selected source/destination and native independence.
  Empty saved rows remain authoritative; migration uses installed values only when no row exists.
  Existing repair/DLC plans keep explicit current options. Windows completion retains pending
  profile data without applying it or changing active-profile resolution/target-prefix derivation.
- Cached preparation holds profile activity from admission through hydration/save/enqueue, with
  original session checks. Migration reads preferences before backup/removal; returned errors stop
  preparation. No GTK I/O or helper policy change. The shared fresh constructor replaces duplicates.
- Independent review and eight private actual-constructor/save/refused-handoff/completion/native
  regressions PASS; formatting, Clippy and build PASS. No actual source migration was exercised
  by these fixtures. Malformed JSON defaults inside StateStore remain a separate deferred issue.

### P354 — prepare initial downloaded-file rows off GTK

- Files immediately shows an inspection shell while one tracked worker prepares base/owned-DLC
  paths, saved jobs, completeness, historical copies, folder availability and summary values.
  Reuse one connection/jobs scan and prepared rows; no initial per-row GTK DB/stat fallback.
- Keep unknown local state non-actionable, retain prior totals on returned errors and offer Retry.
  Weak view/request/account/auth/local-revision/input guards reject stale results and coalesce
  changes. Revoked sessions stop loading with exact Home-then-reopen guidance; no automatic
  replacement-session work. Ordinary errors keep in-place Retry; later row policies are unchanged.
- Review caught and corrected cached-local fallback totals, cross-kind grouping and stale-session
  loading feedback. Two new actual-entry lock/heartbeat/prepared-data/lifecycle fixtures plus four
  existing archive/queue/summary regressions PASS. Initial existing-test runs refused the wrong
  private prefix; corrected harness invocation passed without weakening guards or product code.
  Independent final review, formatting, Clippy and build PASS. No real-file work in fixtures.
- Existing persistence APIs may suppress malformed row/JSON errors internally; this pre-existing
  limitation remains explicitly deferred. One connection is not an atomic multi-query snapshot.

### P357 — track Storage inspection during profile reset

- Both choice-list and selected-library inspection open SQLite, so both now acquire profile
  activity before spawning and check originating sessions before reads/reconciliation. Reset
  draining accounts for delayed work; results still require current request/account/session.
- Independent review caught a new page-lifetime session snapshot that prevented reuse after
  sign-in. Corrected to per-admission snapshots; a deliberate current-session Recheck works in
  the same Settings page, while old results cannot paint or start stale profile reads.
- Actual delayed-worker/activity-drain/stale-no-database/same-page-retry and existing P350 feedback
  regressions PASS in private profiles/displays. Independent re-review, fmt/Clippy/build PASS.
  No actual profile reset or credential deletion used for this test.

### P352 — separate native installs from retained Windows preferences

- Real Linux Gungeon reinstall inherited a saved UMU profile, wrote a contradictory marker and
  incorrectly offered Windows prefix repair. Explicit Linux preparation, completion, marker
  construction and reconciliation now keep native runtime state independent of Windows settings.
- Preserve complete durable Windows preferences, including pending profile, when native executable
  discovery saves preferences. Windows marker fallback and missing-prefix installedness remain.
  Recover only the identified native/offline/managed-UMU marker shape in memory; future and other
  contradictory markers stay strict. No prefix deletion, on-read rewrite or schema change.
- Independent source review and four private regressions PASS, covering multipart preparation,
  both native completion points, exact recovery/rejected counterexamples and repeated full/targeted
  reconciliation with activity/preferences/raw-file preservation. Formatting/Clippy/build PASS.
  Live native retry remains pending; original failed marker is retained for that check.

- The first live retry found Storage's separate protected marker reader still called strict
  validation directly, blocking launch. Follow-up shares the exact pure normalization after each
  reader's existing checks; storage no-follow, bounded regular-file reads and strict writes remain.
  Actual launch-admission/readiness fixture plus the four prior regressions PASS, including rejected
  symlink/oversized/malformed/future metadata and unchanged raw bytes. Independent review and
  fmt/Clippy/build PASS. This corrects missing admission coverage; real launch still to be retried.

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

### P333 — keep Downloads actions visible with long failures

- Full selectable archive/Depot diagnostic labels scroll inside a capped viewport, leaving
  Retry/Cancel outside. Preserve existing cancellation/session behavior and all diagnostic text.
- Independent review and four focused GTK tests PASS. Mapped real-CSS fixture at1100x600 kept
  archive/Depot headers at210/241px for roughly16KB errors; inner scrolling leaves actions and
  outer scroll fixed. Formatting, all-target Clippy and build PASS.

### P335 — reuse the cached-library database connection

- Startup Metadata/Acquisition readiness reuses one store and at most one cached-product
  reconstruction per game. Preserve independent observation errors, strict TTL boundaries,
  malformed-product handling, immediate game-list delivery and existing receiver guards.
- Source-derived connection opens drop from1+2N to1; observations remain2N and maximum product
  reconstructions drop from2N toN. This is not a measured whole-application timing claim.
- Independent review, two focused private regressions, formatting, all-target Clippy and build PASS.

### P337 — retain search and selection after game exit

- Release the mutable model borrow before synchronous alphabetical filter invalidation; otherwise
  callbacks fall back to admitting every row despite the actual query/count. Clear GTK's selected
  flags before detaching retained sidebar rows so reorder can restore the selected row correctly.
- The strict mapped regression initially exposed the retained-row selection defect after its
  baseline was established; production correction now passes both sorts, real row/card filters,
  selection, activity ordering, current detail, focus and scroll. No assertion was weakened.
- Live Coffee Talk normal exit returned to green Play/white sidebar title with only Coffee Talk
  shown for the active query. Mapped regression, formatting, all-target Clippy and build PASS;
  independent final re-review PASS before commit.
- Live Home no-match guidance verified. Test-driver xdotool type consumed subsequent words in
  one attempt; corrected by separate invocation. No product defect inferred from that input error.

### P339 — identify archive size honestly

- Label the game detail, DLC catalog and refreshed subtitle byte count as Downloaded files;
  a remaining installed game no longer has an unexplained0B value after deleting its archive.
- No byte-counting or traversal changes. Independent review, existing async-summary regression
  extended through nonzero/zero/repeated refresh, formatting/all-target Clippy/build PASS.

### P341 — clear stale transfer colors

- Neutral empty/preparing/downloading archive rows clear earlier error styling and tooltip;
  actual failures remain red and verified completion green. Active archive Pause gets operational
  blue styling, with paused/failed/complete paths restoring normal idle styling.
- Independent review and three focused GTK regressions PASS, covering real row-event transitions,
  deletion/retry/error/complete and existing library-selection queue proxies. Fixture recreated a
  deleted inert parent for simulated transfer completion; production deletion was not changed.
- Formatting, all-target Clippy and build PASS. Live evidence originally reproduced both colors.

### P338 — batch installer chooser polling

- Keep one lazy job index per poll, preserving canonical artifact identity, newest/last-tie
  selection, managed-file precedence, completed-file validation and independent read fallbacks.
  Empty malformed artifact records cannot panic the new index. No timer/session/UI receiver changes.
- Source-derived job reads fall fromU to at most1 forU groups requiring fallback; all-managed
  groups perform no job read. Saved-job identity work falls fromU×J toJ per pass.
- Independent review, three private pure/file regressions and actual-row GTK regression PASS;
  formatting, all-target Clippy and build PASS.

### P342 — keep free-space inspection read-only

- Only compatible existing destinations start a read-only free-space query; opening the chooser
  no longer creates missing directories or replaces an unavailable diagnosis with free bytes.
- Reject missing/non-directory/symlink leaves in the query boundary. No new mount assumptions or
  folder-creation workflow. Independent review, private no-write regression, formatting/Clippy/build PASS.

### P340 — native Home grid keyboard activation and accessible titles

- Use one native FlowBox activation path for mouse/keyboard, preserve secondary context menus,
  label each retained grid cell with its full title, and restore visible keyboard focus styling.
  Reject hidden, detached, stale-model and logout-pending activation without background navigation.
- Independent review, native activation/cursor/accessibility fixture and three existing filter/
  empty/exit regressions PASS. Fixture waits for actual layout and enters native focus handling;
  strict cursor/activation assertions retained. Formatting/all-target Clippy/build PASS.
- Live restarted app: Tab/Shift-Tab shows a clear card focus ring; Enter and Space each open the
  focused Gungeon detail, preserving its search; grid right-click retains the normal action menu.
  Private screenshots home-keyboard-focus5, home-keyboard-enter, home-keyboard-space-confirmed,
  home-context-menu under the audit evidence directory. Collection game tiles remain unchanged.

### P344 — explain external uninstaller prompts

- All existing uninstall stage-message writers and UI fallback now say to follow any prompts in
  the uninstaller window. This addresses the real Gungeon Yes/No/OK prompts without detecting
  windows, stealing focus or altering helper execution. Independent review/fmt/Clippy/build PASS.

### P343 — simplify normal uninstall confirmation

- Hide Retry until a removal check fails; collapse alternative file-reset choices for healthy
  installations and expand them on failure. Browse, prefix/save warnings, optional archive cleanup,
  default Cancel and explicit destructive consent stay visible and unchanged.
- Independent review, two private mapped recovery/preview regressions, formatting/Clippy/build PASS.
  Initial fixture compilation used private marker APIs and an incorrect label return type; corrected
  fixture only before execution. No protection or destructive-confirmation assertion weakened.

### P345 — restore idle colors and subsequent transfer controls

- Synchronize Download/Install/Update versus Play container styling for both main and arrow buttons;
  reuse the idle helper on paused/failed archives. Completed archive resets its active visual latch,
  allowing a later download to show Pause instead of retaining idle content.
- The expanded strict repeated-operation test first failed, proving that existing latch defect.
  Minimal correction, independent re-review and the unchanged six-case regression now PASS;
  formatting/all-target Clippy/build PASS. No timers, execution or download states changed.

### P348 — refuse busy cancellation promptly

- Capture/check recovery generation with one nonblocking admission attempt instead of waiting on
  another operation's journal persistence. Hold successful admission through owner registration;
  preserve profile activity, protected-file cleanup and late-completion semantics.
- Both cancellation surfaces explain busy/refreshed state and allow retry. A rejected permanent
  Depot cancellation cannot fall through to unrelated offline cancellation.
- Independent review and five private regressions PASS, including actual GTK callback/heartbeat
  while another admission is held, unchanged owner on refusal, retry, stale generation, late success,
  protected cleanup and confirmation. Formatting/all-target Clippy/build PASS. Initial test-local
  missing glib import fixed without adding a production GTK dependency.

## Remaining gates and live evidence

### P353 — explain drive capacity versus library contents

- Add compact Drive usage label and wrapping explanation that managed categories count this
  library while capacity/free/Other cover the containing drive. Short Other legend avoids widening
  the category row. No calculation, scan, selection or action behavior changes.
- Independent source/layout review and formatting/Clippy/build PASS; no new wording-only test.
  Live narrow-window visual confirmation follows the next app restart.

### P351 — keyboard access within Collections

- Native game-grid activation and full-title accessibility now match Home; preserve collection
  index Buttons and secondary context actions. Use exact collection membership, not Home filters;
  refuse hidden/removed/busy-model/stale-grid/account/logout activation and retain focused children.
- Independent review, strict private mapped native-focus/cursor/activation/accessibility/lifecycle
  regression, formatting/Clippy/build PASS. Physical-key live corroboration remains pending.

### P350 — visible Storage recheck state

- Disable/relabel Recheck while its selected inspection is pending; clear old legend totals with
  the old chart. Restore only current request outcomes; keep library switching available and no-
  library Recheck disabled. Preserve worker/reconciliation semantics and recovery actions.
- Independent review, actual-receiver private GTK success/error/disconnect/stale/account/switch/
  empty regression, formatting/all-target Clippy/build PASS. No real filesystem workers in fixture.

### P349 — bound repeated grid-scroll work

- Coalesce adjustment notifications into one75ms trailing pass reading the latest viewport;
  weak grid references reject hidden/destroyed work. Preserve immediate map/rebuild updates,
  visible-first/nearby order and existing exact bounds; filtered/unmapped rows skip geometry work.
- Independent review, strict private500-card geometry/burst/filter/lifecycle/focus regression and
  formatting/Clippy/build PASS. A burst of20 changes produces one deferred publication instead of
 20 scans. Each scan remains linear; no measured frame-rate or virtualization claim.

### P346 — accurate install destinations and source-specific feedback

- Show full configured Game Files roots and the actual existing installation folder or chosen
  root/slug. Remove chooser-only mount-point lookup and its now-unused helpers. Long paths wrap.
- Keep Galaxy preflight/preparation feedback scoped to Depot while generic/offline errors remain
  visible; preserve source choice, preparation ownership and multipart queue behavior.
- Strict mapped and existing multipart tests PASS, final independent reviews and fmt/Clippy/build
  PASS. Gate caught and corrected a new hidden-parent visibility loop and widget ownership cycle;
  fixture now waits for destination allocation without weakening geometry assertions.

- P346 install chooser final runtime and review gates pass.
  P349 grid-priority coalescing and P350 Storage feedback pass source review, runtime gates pending.
  P351 Collections keyboard parity is isolated. Consolidated build suite has not yet run.
- P347 cross-check's cancellation issue is corrected in P348; no new material auth/session/setup
  issue was found in that bounded source review. This is not an exhaustive security assessment.
- Gungeon Depot launch rendered the actual game menu; normal window-close ended EtG.exe. Details
  displayed completed setup history and Close remained accessible. Planned/recorded counter totals
  differ; potential clarification is deferred rather than treating approximate counters as corruption.

- Gungeon's Depot reinstall completed all declared prerequisite setup successfully before the
  attempted cancellation interaction; this is successful reinstall evidence, not a cancellation pass.
  Conservative transfer/storage budget reservation7GB of40GB after repeated Gungeon acquisition.

- Gungeon uninstall completed through its own Yes/remove, Yes/keep-saves and final OK prompts.
  Ludomere restored Download without reopening details and retained its offline archive; external
  prompt guidance and stale green Download styling are corrected in P344/P345; live retest pending.

- Real Gungeon archive-only deletion/re-download verified: one confirmation removes one archive,
  restores single Download/counts while preserving installed Play; explicit library Download
  transfers/registers382.7MB, restores archive menu/checkmark/counts, and does not run installation.
  Subsequent Depot tests raise the conservative aggregate reservation to7GB of40GB.

- Deferred proposals: clearer drive-wide capacity wording, same-destination Move enablement,
  nested Genre scroll discoverability, initial Files page synchronous reads and grid size rebuilds.
  Missing-library creation needs mount-identity evidence; no speculative automatic recreation added.

Source findings are proposals until assigned, implemented and verified. Full interactive or game
coverage is not claimed from source review alone. Reports: `/tmp/ludomere-r111-{ui-critic,performance,reliability,depot-auth}.md`.
