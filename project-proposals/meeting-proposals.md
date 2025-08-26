# Proposals

## 1) Threat-as-Tests: map MITRE ATT\&CK tactics to executable API tests

**Idea (short):** Build a runner that converts a small library of ATT\&CK-mapped tactics (auth bypass, SSRF, IDOR, exfil) into property-based tests against a REST API. Policies (YAML) define forbidden/required behaviors; the runner generates sequences + oracles and reports “threat coverage.”

**Thesis runway:** expand to (i) multi-step adversary emulation, (ii) coverage metrics tied to ATT\&CK, (iii) CI gating.

**Prior work & gaps:** adversary emulation exists (CALDERA; Atomic Red Team) but targets endpoints/networks more than APIs; little on *API-specific* test generation and measurable “threat coverage” for web services. ([MITRE][1], [arXiv][2], [GitHub][3])

---

## 2) Mutation testing for secure coding rules

**Idea (short):** Implement mutators that inject typical security anti-patterns (string-built SQL, weak JWT checks, unsafe deserialization, missing CSRF). Run the project’s test suite to compute a **Security Mutation Score** and show which rules/tests actually catch security bugs.

**Thesis runway:** (i) operator taxonomy for APIs, (ii) link to fuzzers (mutation adequacy vs. crash-finding), (iii) CI budget optimization.

**Prior work & gaps:** security-oriented mutation has been explored (esp. SQLi, REST APIs), and mutation is a mature testing technique—yet modern stacks lack practical, security-focused operator sets + CI tooling; few studies compare security-mutation scores with fuzzers or code-scanners. ([ScienceDirect][4], [www0.cs.ucl.ac.uk][5], [ACM Digital Library][6], [arXiv][7], [USENIX][8])

---

## 3) Secure-by-Default GitHub Actions linter + auto-fixer

**Idea (short):** Write a static analyzer for workflow YAML that flags risky patterns (untrusted interpolation, unpinned actions, over-broad permissions, secrets exposure) and proposes safe auto-fixes. Evaluate on a corpus of public workflows and your own repos.

**Thesis runway:** (i) sound/complete rule semantics, (ii) fix-synthesis with breakage prediction, (iii) longitudinal ecosystem study.

**Prior work & gaps:** empirical studies show widespread problems and present first analyses/tools (ARGUS; GHAST; large-scale workflow studies), but actionable **auto-fix** with safety guarantees and modern rule coverage (e.g., permissions, artifact trust) is still open. ([USENIX][9], [ACM Digital Library][10], [2024.msrconf.org][11])

---

## 4) Forensic timeline reconstruction for containerized incidents

**Idea (short):** Build a timeline correlator that fuses Docker/Kubernetes events, syscalls/audit logs, app logs, and registry pulls into a single, queryable timeline (CLI/mini-UI). Provide playbooks + datasets; evaluate time-to-root-cause vs. single-log baselines.

**Thesis runway:** (i) eBPF stream integration, (ii) confidence scoring and provenance, (iii) timeline schemas/ontologies.

**Prior work & gaps:** digital-forensic timelines and container/K8s forensics are active areas (DFRWS SoK; SCARF; incident guidance), but **multi-source, container-first correlation** with investigator-centric queries and reproducible datasets is underexplored. ([DFRWS][12], [first.org][13])

---

## 5) Identify insecure logs & enforce privacy-by-design logging

**Idea (short):** Create a policy-driven library + scanner that (a) identifies insecure logs and (b) enforces minimization/redaction at the call-site. Ship a “privacy score” and developer hints; measure leakage reduction vs. debug usefulness.

**Thesis runway:** (i) trainable detectors per domain, (ii) privacy/utility trade-off metrics, (iii) compliance evidence packs.

**Prior work & gaps:** recent studies highlight sensitive data in logs and propose anonymization/sanitization, and approaches appear—yet **developer-facing tooling** that ties policy → code → measurable risk reduction in CI is still scarce. ([ACM Digital Library][14], [ScienceDirect][15], [arXiv][16])

---

## 6) Security-flaky tests identifier

**Idea (short):** Build a CI add-on that detects flakiness with a security lens: classifies failures tied to nondeterministic preconditions (token expiry, clock skew, rate-limits, external IdP, network). Quarantine + generate hardening recipes (e.g., deterministic clock, fake IdP).

**Thesis runway:** (i) root-cause classification models, (ii) auto-repair templates, (iii) effect on MTTR/dev-throughput.

**Prior work & gaps:** flaky tests are well studied overall (causes, prediction, CI impact), but **security-specific flakiness** (auth/permission/time/secrets) is largely uncharted—clear gap for taxonomies, detectors, and fixes. ([ACM Digital Library][17], [mir.cs.illinois.edu][18], [ScienceDirect][19])

---

* **Fastest to ship + publishable:** #3, #2
* **Most novel gap:** #1 (API-oriented adversary-as-tests), #6 (security-flaky)
* **Forensics bent:** #4
* **Privacy/compliance angle:** #5

[1]: https://www.mitre.org/sites/default/files/2021-11/prs-18-0944-1-automated-adversary-emulation-planning-acting.pdf?utm_source=chatgpt.com "Automated Adversary Emulation: A Case for Planning and ..."
[2]: https://arxiv.org/abs/2408.15645?utm_source=chatgpt.com "Red Team Redemption: A Structured Comparison of Open- ..."
[3]: https://github.com/redcanaryco/atomic-red-team?utm_source=chatgpt.com "redcanaryco/atomic-red-team"
[4]: https://www.sciencedirect.com/science/article/abs/pii/S0065245818300305?utm_source=chatgpt.com "Mutation Testing Advances: An Analysis and Survey"
[5]: https://www0.cs.ucl.ac.uk/staff/mharman/tse-mutation-survey.pdf?utm_source=chatgpt.com "An Analysis and Survey of the Development of Mutation ..."
[6]: https://dl.acm.org/doi/10.1145/2610384.2610403?utm_source=chatgpt.com "Automated testing for SQL injection vulnerabilities: an input ..."
[7]: https://arxiv.org/pdf/2403.03701?utm_source=chatgpt.com "arXiv:2403.03701v1 [cs.CR] 6 Mar 2024"
[8]: https://www.usenix.org/system/files/usenixsecurity23-gorz.pdf?utm_source=chatgpt.com "Systematic Assessment of Fuzzers using Mutation Analysis"
[9]: https://www.usenix.org/system/files/sec22-koishybayev.pdf?utm_source=chatgpt.com "Characterizing the Security of Github CI Workflows"
[10]: https://dl.acm.org/doi/pdf/10.1145/3560835.3564554?utm_source=chatgpt.com "Automatic Security Assessment of GitHub Actions Workflows"
[11]: https://2024.msrconf.org/details/msr-2024-technical-papers/4/Quantifying-Security-Issues-in-Reusable-JavaScript-Actions-in-GitHub-Workflows?utm_source=chatgpt.com "Quantifying Security Issues in Reusable JavaScript Actions ..."
[12]: https://dfrws.org/wp-content/uploads/2025/05/SoK-Timeline-based-event-reconstruction-for-digital-forensics-Terminology-methodology-and-current-challenges.pdf?utm_source=chatgpt.com "SoK: Timeline based event reconstruction for digital forensics"
[13]: https://www.first.org/resources/papers/amsterdam25/FIRST-Incident-response-in-Kubernetes-Mahdi-Alizadeh.pdf?utm_source=chatgpt.com "Incident Response in Kubernetes"
[14]: https://dl.acm.org/doi/10.1145/3715779?utm_source=chatgpt.com "Protecting Privacy in Software Logs: What Should Be ..."
[15]: https://www.sciencedirect.com/science/article/abs/pii/S2214212621001915?utm_source=chatgpt.com "Log pseudonymization: Privacy maintenance in practice"
[16]: https://arxiv.org/abs/2505.14976?utm_source=chatgpt.com "SDLog: A Deep Learning Framework for Detecting Sensitive Information in Software Logs"
[17]: https://dl.acm.org/doi/abs/10.1145/3476105?utm_source=chatgpt.com "A Survey of Flaky Tests | ACM Transactions on Software ..."
[18]: https://mir.cs.illinois.edu/marinov/publications/LamETAL20LongitudinalFlakyTests.pdf?utm_source=chatgpt.com "A Large-Scale Longitudinal Study of Flaky Tests"
[19]: https://www.sciencedirect.com/science/article/pii/S0164121223002327?utm_source=chatgpt.com "Test flakiness' causes, detection, impact and responses"
