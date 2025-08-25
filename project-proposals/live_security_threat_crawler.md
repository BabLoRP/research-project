# Live Security Threat web crawler

## Deliverables

A focused crawler + decoy (“honeypot”) presence that continuously harvests, fingerprints, and summarizes malicious bot activity and threat chatter across the clear/social/dark web—surfaced in a live dashboard.

## Predicted Issues & Questions

## Draft research questions (RQs)

RQ1. Can a multi-surface crawler (clear/social/dark) discover actionable threat indicators (IOCs, botnet campaigns) earlier than curated feeds?

RQ2. What are the precision/recall trade-offs of social-honeypot infiltration for identifying malicious accounts/bots at scale?

RQ3. Which normalization and scoring features best rank emerging threats by operational risk (volume, novelty, propagation)?

## Prior work & gaps

There’s peer-reviewed work on multi-surface threat crawling (clear/social/dark), social honeypots for spam/bot discovery (highly cited SIGIR’10), and modern honeypot deployments (Scientific Reports 2023) that inform both crawler scope and deception techniques.

Missing contribution: unify these with near-real-time scoring and rigorous lead-time/precision metrics.
