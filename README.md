# clinical-computer-use

A specialized computer-use agent for clinical EMR automation. Outperformed Google Gemini 2.5 by 28 percentage points on specialized clinical forms — demonstrating that domain-specific agents beat general-purpose models where precision matters.

## Benchmark Results

| Metric | Result |
|---|---|
| Success rate — trained EMRs | **97%** |
| Success rate — unseen EMRs | **73%** |
| vs. Google Gemini 2.5 (specialized forms) | **+28 points** (97% vs 69%) |
| Processing time per form | 30–45 seconds |
| API calls per form | 2–3 (optimized) |
| Clinical files tested | 131 |

The 28-point gap against Gemini 2.5 on specialized clinical forms is the core finding: a domain-specialized agent with semantic clinical understanding outperforms a general-purpose computer-use model with broader web capabilities. Clinical depth beats web breadth in healthcare contexts.

## What It Does

The Clinical Browser is a Gemini-powered computer-use agent that automates clinical EMR form completion end-to-end:

1. Ingests a session transcript and patient data
2. Analyzes the EMR form layout via visual perception
3. Extracts and maps clinical data to the correct fields
4. Executes form completion with 2–3 optimized API calls
5. Submits and validates the result

It operates across EMR systems it has never seen before (73% agnostic success rate), making it practically deployable beyond its training set.

## Architecture

The V3.1 browser uses a hybrid perception approach:

- **Visual layer** — Gemini vision analyzes the EMR screen state and identifies interactive elements
- **Semantic layer** — Clinical NLP maps transcript data to EMR field types (SOAP sections, MSE dropdowns, ICD-10/CPT codes, insurance fields)
- **Execution layer** — Coordinates parallel field population to minimize API round-trips

The system was built and tested against 3 production EMR environments (MedFlow, HealthBridge, Care Connect) across 131 real-world clinical files.

## Project Scale

- ~100 hours of development over 14 days
- 9 Python modules
- 4 testing platforms
- 19-file test suite (8 transcripts, 7 insurance cards, 2 EMR templates)
- 6 EMR form variants (HTML + production TXT)

## Roadmap

- **Phase 1:** Expand validation to 15–20+ unseen EMRs to harden the agnostic success rate
- **Phase 2:** Production hardening — database, API wrapper, monitoring, HIPAA compliance docs
- **Phase 3:** Integration with pixel-precision computer-use models to combine semantic clinical depth with visual precision

## Related

**[therapy-emr-dashboard](https://github.com/Talexandra-cyber/therapy-emr-dashboard)** — The EMR interface built as a target for this agent. Instrumented with `data-testid` attributes and a `postMessage` bridge for programmatic control.

**[DynamicClinicalAgent_v4](https://github.com/Talexandra-cyber/DynamicClinicalAgent_v4.py)** — V4 of the same system, refactored into a full CLI + desktop GUI with a two-agent architecture (orchestration + browser execution).
