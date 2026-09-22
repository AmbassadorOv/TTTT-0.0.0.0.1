# GOLEM TRVM — C1/C2 Resolution Core

Status: SPECIFIED

## Scope

This document consolidates the current Golem compiler boundary:

- C1 Attribution / Provenance
- C2 Temporal Revision
- Shev Shmaitta prior weights as a bounded uncertainty input
- Provenance + Trace
- Neural network as Proposal Only
- FOL as Fallback Only
- Causes 3–7 blocked with E_SCOPE

The network proposes. The processor decides.

## Runtime

CLAIM + SOURCE_REFERENCE
→ PROVENANCE GUARD
→ C1 AttributionResolver
→ C2 TemporalRevisionResolver
→ Conflict Classification
→ COMMIT / FOL Fallback
→ STATE + TRACE

## Claim state

S(C) = (T, P, A, V)

T = Truth: FALSE | TRUE | UNKNOWN
P = Proof: UNTESTED | PROVISIONAL | SUPPORTED | COMMITTED
A = Attribution: MISSING | PARTIAL | RESOLVED
V = Version: SINGLE | SUPERSEDED | CHRONOLOGY_OK

## C1

C1 resolves whether apparent conflict is attributable to distinct authorities or insufficient attribution.

Different authors:
RESOLVED / NO_DIRECT_CONTRADICTION

Same author:
pass to C2.

## C2

C2 resolves whether statements belong to distinct temporal stages or represent a recognised revision/retraction.

Different stage or retraction:
REVISION

Same stage:
pass to conflict classification.

## Commit condition

K_COMMIT ⇔ (A = RESOLVED) ∧ (V ∈ {SUPERSEDED, CHRONOLOGY_OK})

Commit does not follow from neural confidence.

## Shev Shmaitta

The current mathematical specification supplied for this stage uses:

W_Shev = diag(0.18, 0.15, 0.16, 0.12, 0.14, 0.10, 0.09, 0.06)

These values are priors/weights for uncertainty classification. They do not determine truth and do not override C1/C2.

W_Cause = diag(0.60, 0.40)

Components:
1. Cause 1 — aggregation without attribution
2. Cause 2 — retraction/change of earlier opinion

Causes 3–7 are outside the active scope and return E_SCOPE.

## Neural boundary

GNN/SNN output is a proposal vector:

N = softmax(U)

M_gate filters the proposal space to the currently open channels.

Candidate → TYPE-CHECK → Opcode → PRECONDITION → Execute / Fail

The neural substrate may generate candidate relations, similarity/anomaly signals, or candidate attribution/temporal links. It cannot write authoritative truth directly to State.

## Provenance

Every executable claim transition requires SourceReference and traceable provenance.

No Claim without SourceReference.

## Status lifecycle

SPECIFIED → PROVISIONED → IMPLEMENTED → TESTED → VERIFIED → ACTIVE

No status may skip a stage.

## Mishnaic knowledge object

For Mishnaic material, the Mishnah is treated as a canonical knowledge object, not as the reasoning engine.

The active compiler questions are:

1. C1 — Whose statement is this?
2. C2 — Is this an earlier/later formulation or recognised revision of the same authority?

Gemara-style dialectical expansion and causes 3–7 remain outside the current scope.
