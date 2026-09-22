# Neural Substrate Update to the Existing Network

Status: SPECIFIED

## Architectural decision

The GNN + SNN layer is an update to the existing Agent Fabric / Golem runtime, not a replacement network.

Existing orchestration and symbolic control remain authoritative.

## Updated pipeline

EXISTING AGENT FABRIC
→ NEURAL SUBSTRATE
→ PROVENANCE GUARD
→ C1 ATTRIBUTION GATE
→ C2 TEMPORAL GATE
→ CONFLICT CLASSIFIER
→ TRACE / FOL FALLBACK
→ STATE / PROOF

## Neural role

Proposal Only.

The neural layer may propose:

- candidate claim relations
- candidate attribution links
- candidate temporal relations
- graph-neighborhood signals
- anomaly or similarity signals

These are candidates, not facts.

## Processor role

The deterministic processor performs:

- type checking
- provenance validation
- C1 attribution resolution
- C2 temporal resolution
- precondition checks
- conflict classification
- state transition
- commit or fail

The processor is the only component authorised to commit State.

## Drift boundary

Probabilistic neural output must terminate at the Candidate boundary.

No softmax score, spike pattern, embedding similarity, or learned ranking is itself a proof.

This preserves the existing rule:

Network writes Candidate.
Processor writes State.

## Compatibility

The update preserves the prior network's orchestration, provenance, evidence, and verification contracts. It adds a proposal-generating substrate before the authoritative resolution gates.
