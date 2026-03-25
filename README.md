# First Proof Benchmark Results

**Autonomous Proof Discovery Pilot — Public Dataset**

Public-language release of an audited pilot run in which a local open-source language model attempted 10 open research-level mathematics problems from the [First Proof](https://firstproof.xyz/) benchmark, running for 8 hours on a consumer laptop with zero human intervention.

---

## What is the First Proof Benchmark?

The First Proof Benchmark is a challenge designed to test whether AI systems can perform genuine mathematical discovery — not routine textbook exercises, but novel proofs of open problems across advanced mathematics. Each problem demands constructing or verifying a proof at the research frontier.

This repository contains the complete, audited results of one pilot run against 10 of those problems, preserving both successful proof steps and failed search routes as a public scientific record.

## Run Configuration

| Parameter | Value |
|---|---|
| **Model** | Local open-source language model |
| **Hardware** | Consumer laptop |
| **Runtime** | 8 hours, unattended |
| **Human intervention** | None during the run |
| **Post-hoc audit** | Independent step-level review of all 85 candidate steps |

## Problems Attempted

The pilot tackled 10 problems spanning 10 distinct areas of mathematics:

| # | Problem | Area | Outcome |
|---|---------|------|---------|
| 1 | Singularity of the &#934;<sup>4</sup><sub>3</sub> measure under smooth translations | Quantum field theory | Partial |
| 2 | Local test vector for Rankin–Selberg integrals on GL<sub>n+1</sub> &times; GL<sub>n</sub> | Automorphic forms | Partial |
| 3 | Markov chain with interpolation ASEP/Macdonald stationary weights at q = 1 | Probability & algebraic combinatorics | Partial |
| 4 | Finite free Stam inequality | Free probability | Partial |
| 5 | O-slice connectivity and geometric fixed points | Equivariant homotopy theory | Partial |
| 6 | Schur-complement certificates for light vertex sets | Spectral graph theory & algorithms | **Accepted** |
| 7 | Obstructions to Q-acyclic universal covers for lattices with involutions | Topology & geometric group theory | Partial |
| 8 | Quadrivalent polyhedral Lagrangian surfaces need not admit Lagrangian smoothings | Symplectic topology | **Accepted** |
| 9 | Complete polynomial certificate for rank-one scaling of determinantal block tensors | Algebraic geometry & tensor methods | **Accepted** |
| 10 | Matrix-free PCG for the mode-k RKHS subproblem with Kronecker structure | Numerical linear algebra & kernel methods | Mixed |

**3 accepted theorem-level proofs, 6 partial proofs with structural progress, 1 mixed result** (algorithmic core accepted, one theoretical dependency remains).

## Key Results

### Step-Level Metrics (85 audited steps)

| Metric | Rate | Description |
|--------|------|-------------|
| **Assumption compliance** | 100% (85/85) | Every step stayed within the stated hypotheses |
| **Inference validity** | 98% (83/85) | Only 2 steps contained a mathematical error |
| **Goal completion** | 76% (65/85) | Most steps are directionally useful but some stop short of closure |
| **Generalization robustness** | 69% (59/85) | The main bottleneck: locally valid steps that fail to transport to the full target |

### Verdict Distribution

| Verdict | Count | Share |
|---------|-------|-------|
| Accepted | 65 | 76% |
| Rejected | 6 | 7% |
| Partial | 6 | 7% |
| Deferred | 6 | 7% |
| Open | 2 | 2% |

### The Core Finding

> **Local correctness is far easier than robust transfer.** The gap between inference validity (98%) and generalization robustness (69%) is the defining signal of this pilot. The model rarely makes outright mathematical errors — most failures occur when a locally valid argument does not survive expansion from a special case to the full target.

## What Makes This Dataset Different

1. **Process, not just answers.** The dataset preserves the full proof-search structure — accepted steps, rejected routes, deferred mechanisms, and explicit open bridges — rather than collapsing everything into a final score.

2. **Negative evidence is first-class output.** Six rejected routes were identified (4 by the model itself, 2 by audit). Each rejection permanently eliminates a proof family and provides reusable boundary information for future work.

3. **Closed-loop measurement.** The same four step-level gates (assumption compliance, inference validity, goal completion, generalization robustness) were tracked during discovery and then reapplied in post-hoc audit. This makes the pilot an auditable inquiry record.

4. **Cross-problem patterns.** The dataset supports falsifiable hypotheses about when AI proof search succeeds or fails — for instance, proofs dominated by rigidity lemmas show the highest robustness, while "base case then stall" is the most common failure mode.

## Proof Highlights

### Accepted Proofs

- **Problem 6 (Schur-complement certificates):** A clean end-to-end proof establishing the canonical variational characterization of light vertex sets, including a counterexample ruling out simpler conditions.

- **Problem 8 (Lagrangian smoothing obstruction):** A local Maslov-index computation at a product vertex yields a nonzero index contradicting the zero-index requirement of any smooth Lagrangian disk — a clean topological obstruction.

- **Problem 9 (Rank-one scaling certificate):** A deep rigidity chain from flattening/slice rank constraints through core tensor rigidity (via projective geometry) to block-scaling collapse. The most robust completion in the pilot.

### Notable Partial Results

- **Problem 1 (&#934;<sup>4</sup><sub>3</sub> singularity):** Four of five steps are clean, including the logarithmic variance divergence. One missing negative-moment bound is the sole remaining gap.

- **Problem 2 (Rankin–Selberg test vectors):** The GL<sub>2</sub> &times; GL<sub>1</sub> base case closes completely via Gauss sums, plus a monomiality criterion that sharpens the target. The higher-rank bridge remains open.

- **Problem 7 (Q-acyclic universal covers):** The Euler-characteristic obstruction chain is strong — integrality from Q-acyclicity combined with index scaling forces contradiction under involution — but an external existence premise (a specific ball-quotient surface) is not established in the proof.

## Cross-Problem Patterns

| Pattern | Type | Evidence |
|---------|------|----------|
| Local topological obstructions close proofs | Positive signal | P7, P8 |
| Rigidity chains produce the most robust completions | Positive signal | P9 |
| Correct rejection permanently shrinks search | Positive signal | P2, P4 |
| Base case closes but mechanism fails to transport | Failure mode | P2, P3, P4 |
| Invalid inferences cluster at generalization moves | Failure mode | P2, P5 |
| Late steps become forced in complete proofs | Structural signal | P8, P9 vs P3 |
| Single-gap conditionals are closer to repair than strategy failures | Structural signal | P1, P7 vs P2–P4 |

## Repository Structure

```
.
├── README.md
├── LICENSE
├── proofs/
│   ├── first_proof_benchmark_solutions_1.pdf    # Phi^4_3 measure singularity
│   ├── first_proof_benchmark_solutions_2.pdf    # Rankin-Selberg local test vector
│   ├── first_proof_benchmark_solutions_3.pdf    # Markov chain construction
│   ├── first_proof_benchmark_solutions_4.pdf    # Finite free Stam inequality
│   ├── first_proof_benchmark_solutions_5.pdf    # O-slice connectivity
│   ├── first_proof_benchmark_solutions_6.pdf    # Schur-complement certificates
│   ├── first_proof_benchmark_solutions_7.pdf    # Q-acyclic universal covers
│   ├── first_proof_benchmark_solutions_8.pdf    # Lagrangian smoothing obstruction
│   ├── first_proof_benchmark_solutions_9.pdf    # Rank-one scaling certificate
│   └── first_proof_benchmark_solutions_10.pdf   # Matrix-free PCG for RKHS
└── datasets/
    └── first_proof_benchmark_results.xlsx       # Full audited dataset
```

## Dataset Workbook Guide

The Excel workbook (`datasets/first_proof_benchmark_results.xlsx`) contains five sheets:

| Sheet | Contents |
|-------|----------|
| **Overview** | Pilot summary, novelty classification, metric dictionary, and reading guide |
| **Tactic Data** | All 85 audited steps with four binary metrics, verdicts, search-role labels, and review notes |
| **Proof Summary** | Formula-driven proof-level rollups: per-metric rates, rejection flags, and overall outcome for each problem |
| **Aggregate Metrics** | Workbook-level counts, rates, verdict distributions, search-role breakdowns, and the key validity-vs-robustness gap |
| **Process Traces** | Curated high-leverage steps showing what each contributed and what boundary information it produced |
| **Cross-Problem Patterns** | Falsifiable hypotheses extracted from the pilot with evidence pointers and testable implications |

## Metric Definitions

| Metric | Definition |
|--------|------------|
| **Assumption compliance** | The step stays within the stated assumptions and target setting |
| **Inference validity** | The mathematics of the step is correct as written |
| **Goal completion** | The local objective of the step is actually achieved, not merely sketched |
| **Generalization robustness** | The step remains useful when expanded from a local/special case to the full target |

### Verdict Labels

- **Accepted** — Valid and goal-complete at the claimed scope
- **Partial** — Promising but with an unresolved subgoal or missing premise
- **Rejected** — Ruled out by counterexample or invalid inference
- **Deferred** — Plausible but insufficiently developed to judge
- **Open** — Explicit unresolved bridge statement or conjecture
- **Mixed** — Algorithmic core accepted; one theoretical dependency remains partial

## Implications

**For AI and mathematics research:**
- A local open-source model can produce auditable proof-search structure, not just candidate final answers
- Route elimination is productive output — the model correctly self-rejected 4 of 6 dead routes
- The validity-to-robustness gap is the primary target for improving AI proof discovery systems

**For future benchmarking:**
- Systems should be scored on route elimination, premise verification, and transport — not only proof completion
- Process-level datasets (preserving search structure) are more informative than binary success/failure labels
- Generalization robustness at mid-proof predicts completion better than inference validity alone

## License

See [LICENSE](LICENSE) for details.
