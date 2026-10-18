# Content Publish Lifecycle · 内容发布全流程

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.md)
[![Local & Network-free](https://img.shields.io/badge/provenance-local--zero%20network-2ea44f.svg)](#)
[![Deterministic Radar](https://img.shields.io/badge/radar-deterministic%20SVG-blue.svg)](security-radar.svg)
[![Evidence-chain](https://img.shields.io/badge/evidence-chain-logged-orange.svg)](#)
[![Bilingual](https://img.shields.io/badge/docs-EN%2FZH-brightgreen.svg)](README.md)

> **From "design done" to "shipped with evidence":** a reusable publish pipeline that turns publishing from guesswork into an auditable process — 设计 → 落地 → 检查 → 验证 → 发布 → 沉淀.

## One-line positioning

A publish pipeline is most likely to fail not at "writing" but at "nobody checks before it goes out, and nothing is checkable after." This skill splits publishing into six stages, each with a clear deliverable and checkpoint. Every external claim must be pinned to real evidence.

## The six stages

| Stage | What it solves |
|---|---|
| **Design** | Decide what to publish, where, and the version; split the goal into executable stages and checkpoints. |
| **Implement** | Adapt content to channel specs (title / tags / format / length); decouple the artifact from the source. |
| **Inspect** | Check channel \| content \| version \| scheduled-time before anything goes out; confirm-then-act. |
| **Verify** | Locally, network-free, generate a provenance attestation (ATTESTATION) and a security radar. |
| **Publish** | Land to the target repo / channel through a controlled path; record link, time, status. |
| **Consolidate** | Feed records, versions and fingerprints back for retrospectives and rollback. |

## Differentiators

- **Evidence-chain logging** — every artifact carries version, fingerprint and receipt.
- **Local, network-free provenance** — `publish_attest.py` computes SHA-256 and a package fingerprint offline.
- **Deterministic security radar** — `gen_skill_security_radar.py` renders `security_results.json` to SVG with no randomness and no timestamp.

## Quick start

```bash
# install via the skill manager
openclaw skills install @zhaoxinghua09-cell/content-publish-lifecycle

# or clone and drop SKILL.md into your skills directory
git clone https://github.com/zhaoxinghua09-cell/content-publish-lifecycle.git

# local, network-free provenance attestation
python publish_attest.py

# deterministic security radar
python gen_skill_security_radar.py --results security_results.json
```

## License / 许可

Released under the **MIT** license — see [LICENSE.md](LICENSE.md). Vendor-neutral.
Authorship: SynomosAI · 诺声(Logos). Cite with the repo URL
`https://github.com/zhaoxinghua09-cell/content-publish-lifecycle`.
Any external claim must be pinned to real evidence; not a medical device / no clinical claim.

Security: report privately per [SECURITY.md](SECURITY.md). Contributions: [CONTRIBUTING.md](CONTRIBUTING.md). Agent guidance: [AGENTS.md](AGENTS.md).

Contact: zhaoxinghua06@126.com ｜ ORCID `0009-0001-0512-1237`
