# Data release: IBM vs IonQ cross-vendor entangling-circuit comparison

Minimal, standalone data backing the paper **"Verify Before You Trust It,
Even Yourself: A Cross-Vendor Quantum Hardware Case Study"** (Lokesh
Pullakandam, Jack Woehr). This repo exists so the paper's physics claims
can be independently checked without needing access to the authors'
broader private research repositories.

**Status: paper is an intermediate/working draft, not yet submitted or
published anywhere.** This data release stands on its own regardless —
every job ID below is independently checkable against IBM's and IonQ's own
job history by anyone with API access, which doesn't depend on this repo,
the paper, or the authors at all.

This release covers only the comparison in this specific paper (the graded
`single`/`ring`/`degree3` entangling circuits run on IBM `ibm_fez` and IonQ
`Forte-Enterprise-1`). It does not cover the earlier, separate Singmaster's
Conjecture search work (27.78x on `ibm_marrakesh`, 178.8x on `ibm_fez`) —
that lives in [`singmasters-conjecture`](https://github.com/Lokesh-2025/singmasters-conjecture).
Any future, unrelated follow-up research (e.g. correlated-error /
"raindrops" characterization) will get its own separate data release rather
than being folded into this one.

## What's here

- `circuits/e1_entangled_lnaa.py` — the circuit construction code (LNAA:
  Lattice-Native Amplitude Amplification).
- `circuits/qasm_ionq/e1_{single,ring,degree3}.qasm` — the exact OpenQASM
  circuits submitted to IonQ hardware.
- `data/job_ids.csv` — all 6 real hardware jobs behind the comparison, with
  real submission timestamps (UTC) pulled directly from each vendor's own
  job record.
- `data/amplification_results.csv` — the headline amplification numbers,
  every run, both vendors.
- `data/target_row_probabilities.csv` — raw per-row measured probabilities
  for the controlled repeat-run pair.
- `data/calibration_snapshots.csv` — real device calibration (2-qubit gate
  error, readout error, T1/T2) around each run date, both vendors.
- `data/entanglement_entropy.csv` — exact entanglement entropy vs. real
  hardware degradation (Table 4 in the paper).
- `figures/` — the 4 figures used in the paper, generated directly from the
  data above.

## How to verify independently

Every job ID in `data/job_ids.csv` can be looked up directly:
- IBM jobs: via IBM Quantum's own job history (`job_status()` /
  `job_results()` for a given job ID).
- IonQ jobs: via IonQ's REST API, `GET /v0.3/jobs/{id}`.

That's the strongest form of verification available — it doesn't depend on
trusting this repo, the paper, or the authors.

## Related

- Verification tool: [quantum-verifier](https://github.com/Lokesh-2025/quantum-verifier)
- MCP server / snapshot pipeline: [quantum-hardware-mcp](https://github.com/Lokesh-2025/quantum-hardware-mcp)
- IBM-side Singmaster's Conjecture work: [singmasters-conjecture](https://github.com/Lokesh-2025/singmasters-conjecture)

## Citation

Paper is pre-publication; a citation (DOI, venue) will be added here once
it's actually submitted/published. Until then, cite this repository's
Zenodo archival DOI directly (added once this repo is archived on Zenodo).
