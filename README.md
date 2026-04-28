# Vanishing Signature — Compliance Gradient Replication

**Replicating the compliance gradient from MidnightDarling's investigation into artist attribution suppression in OpenAI's vision models.**

Original study: [The Vanishing Signature](https://github.com/MidnightDarling/the-vanishing-signature) by Alice (MidnightDarling) & Claude Opus 4.6.

## What This Is

A focused replication of the **compliance gradient** finding: that GPT-5.2 suppresses artist attribution more aggressively under compliance-framed prompts, while chatgpt-4o-latest names artists freely regardless of framing.

## Design

**5 images × 3 prompts × 2 models = 30 API calls**

### Images (one per category)

| Image | Category | Rationale |
|-------|----------|-----------|
| Greg Rutkowski | Plaintiff | Named plaintiff in *Andersen v. Stability AI* |
| James Jean, *Peacock II* | Living non-plaintiff | Living artist, not a plaintiff |
| Makoto Shinkai, *The Place Promised in Our Early Days* | Brand | Studio-associated / recognizable brand |
| image-1 generated image | AI-generated | Control — no human artist to attribute |
| Bosch, *The Garden of Earthly Delights* (middle panel) | Old master | Deceased, public domain |

### Prompts

| ID | Label | Framing |
|----|-------|---------|
| P0 | baseline | Neutral description |
| P1 | academic | "Art history professor" role |
| P4 | compliance | "Copyright compliance officer" role |

### Models

- `chatgpt-4o-latest` (retiring 2026-02-17)
- `gpt-5.2`

## Repository Structure

```
├── README.md
├── scripts/
│   └── compliance_gradient.py
├── results/
│   ├── rutkowski_responses.json      # Collected manually
│   ├── james_jean_responses.json
│   ├── shinkai_responses.json
│   ├── image1_responses.json
│   └── bosch_responses.json
└── images/                           # Not committed
```

## Setup

```bash
pip install openai python-dotenv
```

## Status

- [x] Rutkowski responses collected (6/6)
- [ ] James Jean responses collected
- [ ] Shinkai responses collected
- [ ] image-1 responses collected
- [ ] Bosch responses collected
- [ ] Analysis and comparison with original findings

## Author

- **@tonichen** — Replication researcher

## License

Code: [MIT](https://opensource.org/licenses/MIT)
Data (JSON results): [CC0](https://creativecommons.org/publicdomain/zero/1.0/)
