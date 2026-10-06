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
- Test game transfer budget used: 0 GB so far. No intentional cloud deletion, real uninstall,
  installed-game modification or helper execution performed yet.

## Fixes

### P325 — retain search while changing library filters

- Preserve the query for boolean, language and metadata filters; keep search visible/enabled
  beside active chips. Preserve explicit Clear Filters behavior and view selection.
- Production change removes 20 lines from library/window; actual GTK regression exercises both
  input orders, all filter handler types, matching grid/sidebar counts, focus/widget identity,
  chip removal and Clear Filters without starting metadata workers or creating a real database.
- Independent UI review PASS. Focused private Broadway/DBus test PASS, formatting and all-target
  Clippy PASS. Build verification recorded with the commit in the status record.

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
