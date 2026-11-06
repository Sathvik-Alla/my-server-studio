# Lesson 01 specification

## STUDIO-001 · Launch a tested calculator on an existing server

**Status:** New calculator launch passed and sanitized evidence was reviewed. Local fast checks encountered Windows compatibility errors. Full CI is pending.
**Next step:** Review the local check results and complete the remaining review checkpoints in [Lesson 01](studio/lesson-01.md).
**Instructor implementation:** [issue #9](https://github.com/kaw393939/373_hosting/issues/9).
Create your own issue from the [lesson template](.github/ISSUE_TEMPLATE/studio-calculator.md).

## Agreed result

Launch the supplied published calculator image through your existing Traefik
network and a nonconflicting HTTPS hostname. Preserve unrelated services and
host access. Do not add another proxy/updater or build a substitute image.
The [release selection](studio/calculator-release.json) supplies the expected
commit and multi-platform digest independently of the running website.
An explicitly agreed adoption of a matching existing deployment is recorded
as adoption, not a fresh launch. This bounded lesson does not certify the whole
server baseline or a vulnerability-free image.

- **Agreed public hostname:** `qa-is373-sathvik.duckdns.org`.
- **Intended result:** One new calculator project on the replacement hosting baseline, using the pinned [instructor release](studio/calculator-release.json), the existing Traefik `websecure` entry point, and `hosting-web`. Check for hostname and route conflicts before starting. Preserve the welcome site and Traefik configuration. A conflict or matching existing route requires separate review.
- **Pre-launch browser observation:** The learner reported Chrome displayed `NET::ERR_CERT_AUTHORITY_INVALID` on the calculator hostname before deployment.
- **Post-launch browser observation:** The learner reported that Chrome loaded the calculator without a certificate warning and displayed `42` for `6 × 7`. See [LEARNING.md](LEARNING.md#browser-observation).
- **Own issue / feature branch:** [STUDIO-001 issue #1](https://github.com/Sathvik-Alla/my-server-studio/issues/1) is open and tracked by local branch `codex/studio-001-calculator`.
- **Original server prerequisite gap:** After destroying the previous droplet, the learner confirmed there were no running droplets and no recovery image for it in DigitalOcean Backups & Snapshots. The original server cannot be restored through DigitalOcean backups or snapshots.
- **Replacement baseline:** The learner rebuilt the hosting baseline on Ubuntu 24.04 LTS and verified the SSH host fingerprint, key authentication, and sudo access.
- **SSH hardening complete:** The learner validated and reloaded the SSH configuration, confirmed key login and sudo in a fresh session, and verified that a fresh root login was rejected.
- **Docker installation complete:** The learner copied the course installer over SCP. The first execution failed at `set -euo pipefail` with `invalid option name`. Windows CRLF line endings were suspected. The learner reported that the successful run pulled the `hello-world` image, printed `Hello from Docker!`, reported Docker Compose `v5.7.0`, and returned to the shell without errors.
- **DuckDNS complete:** The learner confirmed that the welcome-site and calculator hostnames resolved to the replacement server.
- **Studio read-only checks passed:** After the Windows SSH transport fix, the learner reported a ready, read-only Studio doctor result with two existing containers and sudo required.
- **Hosting configuration validated:** The learner reported that the course generator created `runtime/compose.yaml` and `docker compose config --quiet` returned without errors. The generated dashboard configuration binds to server loopback for SSH tunnel access.
- **HTTPS hosting baseline complete:** The learner verified that Traefik and the welcome-site container were running on `hosting-web`. Chrome initially returned `NET::ERR_CERT_AUTHORITY_INVALID`, and Traefik logged `contact email has forbidden domain "example.com"`. The learner replaced the placeholder email privately, regenerated and validated Compose, and reapplied the baseline stack. The learner reported that Traefik logged successful Let's Encrypt account registration, HTTP-01 validation, and certificate issuance for `is373-sathvik.duckdns.org`. Windows PowerShell `curl.exe -fsS` succeeded with certificate verification enabled and returned the expected welcome-page HTML.
- **Completed locally:** The clone and Windows studio setup are complete, and the [classroom trial](LEARNING.md#classroom-trial) is recorded.

Private SSH targets and configuration stay in ignored local state. Share only
reviewed, selected evidence; never commit credentials or raw server output.

## Evidence to keep

| Evidence | Actual result / link |
|---|---|
| Prepared Black/Pylint/pytest and real-image browser checks | Windows `studio.py check --fast`: Black passed (8 files). Pylint reported three `E1101` errors for Unix-only `os.geteuid` and `os.chown` in `studio_tools/remote.py`. Pytest stopped at collection because Windows lacks `signal.SIGHUP`. The local Docker engine was unavailable, so real-image Chromium E2E was not run. The Ubuntu GitHub Actions checks are pending. |
| Hosted image/commit, trusted HTTPS, valid and rejected API cases | The saved `launch` report recorded `passed` and `launched`, matched the pinned release, and passed trusted public HTTPS, multiplication, divide-by-zero, and numeric-string rejection checks. See [sanitized launch evidence](studio/evidence.json). |
| Preservation of unrelated services | The launch checks recorded both existing hosting containers as unchanged. |
| Own prediction, check interpretation, browser observation and keep/revise reason | Prediction and browser observation recorded in [LEARNING.md](LEARNING.md). Check interpretation and keep/revise reason pending. |
| Accuracy review before publishing learner excerpts | Learner approved the classroom trial, prediction, and browser observation for publication. |
| Actual PR, latest CI, merge and issue closure | Pending |

Link the exported `studio/evidence.json`, actual CI and issue/PR when available.
CI does not deploy this server. A fixture, green check, timestamp, closed issue
or AI assertion alone does not establish the full result. `status` reports
recorded evidence and readiness for instructor review; it does not grade,
certify authorship or establish understanding.

## Optional instructor history

The records below are background, not steps to repeat. Their original anchors
remain here so earlier links continue to work.

## HOST-001 · Keep the Traefik dashboard private

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-001--keep-the-traefik-dashboard-private).

## HOST-002 · Controlled host maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-002--controlled-host-maintenance).

## HOST-003 · Companion image security maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-003--companion-image-security-maintenance).
