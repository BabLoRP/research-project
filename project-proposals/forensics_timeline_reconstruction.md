# Forensic Timeline Reconstruction (system-centric or mobile/app-centric)

## Deliverables

Build a tool that collects heterogeneous logs, normalizes them into a shared event model, and reconstructs an analyst-friendly, searchable timeline that can also surface suspicious activity post-incident.

## Problem

Investigators and defenders drown in siloed logs (auth, OS, app, DB, cloud/mobile). Reconstructing who did what, when, and via which components is slow and error-prone (clock skew, partial data, noisy events). Existing tools either (i) do great low-level parsing but weak correlation, or (ii) do strong attack reconstruction for specific OS audit streams but lack broad, analyst-centric timeline UX.

## Predicted Issues & Questions

- mobile (application or device) or system?
- integrated or included/deployed in the context after the fact
- find the suspicious behaviour or enable manual recounstructing?

### Scope options (choose one later; same architecture)

1. System-centric (default): Linux/Windows endpoints + containers/K8s + app/auth logs. Focus on post-incident reconstruction and triage. Anchors: OS audit (auditd/ETW), auth (OAuth/OIDC/SSH), app logs, container/K8s events.
2. Mobile/app-centric: Android app + backend (server/API/CDN) artifacts: app logs/SQLite, notifications, file metadata, plus server-side access/auth logs that involve the app’s users.

## Draft research questions (RQs)

RQ1 (Effectiveness). Compared to a strong manual baseline, how much does the pipeline improve time-to-valid-story and precision/recall of event linking (actor-action-resource)?

RQ2 (Uncertainty). Which uncertainty handling (clock-skew correction, partial orders, confidence scores) most reduces investigator mistakes without hiding useful detail?

RQ3 (Suspicion scoring). Post-incident, do lightweight rules (e.g., provenance/causal tags, ATT&CK-like patterns) materially help analysts find the right slice of the timeline faster than search-only?

## Prior work & gaps

Strong, peer-reviewed foundations show how to reconstruct attack scenarios from OS audit logs using dependency graphs and tag propagation; it is possible reuse these ideas but generalize to a breadth of log types and put an analyst-first timeline UX on top.
See SLEUTH (real-time attack reconstruction from audit logs) and HOLMES (provenance-based APT correlation). Both are well-cited and freely available.

Classic timeline reconstruction work demonstrates low-level to high-level event building and motivates partial orders over naive time sorting.

If mobile track, recent open-access surveys and case studies map the artifact landscape (SQLite/app data, logs, cloud ties) and highlight repeatability challenges the normalization/uncertainty handling directly address.
