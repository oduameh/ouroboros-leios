---
sidebar_position: 3
---

# How it works

Leios is a high-throughput overlay protocol designed to enhance blockchain scalability—such as for Cardano’s Ouroboros—by managing a structured flow of transactions.

## Key stages

1. **Creating Input Blocks (IBs)**  
   Stake pool operators (SPOs), acting as validators, bundle transactions into input blocks every 0.2–2 seconds. These IBs are broadcast across the network for parallel processing.

2. **Proofs of data availability**  
   Validators check that IBs contain valid and accessible transaction data. This is later confirmed via endorser blocks (EBs) and a voting mechanism, ensuring no data is missing or malformed.

3. **Generating Endorser Blocks (EBs)**  
   EBs aggregate multiple verified IBs, grouping them for validation and proposing their inclusion in the blockchain’s final ledger.

4. **Pipelined processing**  
   The protocol uses a seven-stage endorsing pipeline (explained below) to process IBs, EBs, and votes in parallel—maximizing throughput and bandwidth efficiency.

5. **Voting and certification**  
   Validators use stake-weighted BLS signatures to vote on EBs. This certifies both their correctness and data availability, allowing only compliant IBs to proceed.

6. **Final inclusion in the blockchain**  
   Certified EBs are referenced by a certificate included in a ranking block (RB)—a Praos-style block minted roughly every 20 seconds. These RBs finalize transactions on-chain, preserving both efficiency and auditability.

## Leios architecture

Leios uses a pipelined architecture to achieve high throughput. Each pipeline instance includes the following seven stages:

### 1. Propose

- Validators propose IBs containing transaction data.
- Proposals target frequent output (every 0.2–2 seconds).
- These IBs initiate the current pipeline instance.

### 2. Deliver1

- IBs are disseminated across the network using a freshest-first strategy.
- This ensures that honest nodes receive IBs within a bounded delay (e.g., Δₕᵈᵣ), even during adversarial message bursts.

### 3. Link

- Validators create EBs that reference the proposed IBs.
- EBs group and order IBs for validation and inclusion.

### 4. Deliver2

- Additional time is allocated for any adversarial IBs to propagate.
- Ensures all honest nodes have the necessary data before voting.

### 5. Vote1

- Validators vote using stake-weighted BLS signatures on EBs from the link stage.
- EBs become vote1-certified once a threshold of signatures is reached.

### 6. Endorse

- New EBs reference vote1-certified EBs across pipeline instances.
- This reinforces confirmation and supports high throughput.

### 7. Vote2

- Validators cast final votes on EBs from the endorse stage.
- EBs are vote2-certified if they reference a majority of vote1-certified EBs and are ready for RB inclusion and ledger finality.


## Network resilience

Leios addresses adversarial tactics with:

- **Freshest-first diffusion**  
  Nodes prioritize receiving the most recent IBs and EBs based on VRF-based timestamps. This limits delays from adversarial bursts.

- **Equivocation proofs**  
  If a validator double-signs (e.g., sends conflicting EBs), honest nodes detect and broadcast proofs. This ensures only one valid block per slot is processed, preserving bandwidth.

## Integration with Ouroboros

Leios enhances [Ouroboros Praos](https://iohk.io/en/research/library/papers/ouroboros-praos-an-adaptively-secure-version-of-ou/) by overlaying its Ranking Blocks (RBs) with high-throughput IB and EB processing:

- RBs are minted every ~20 seconds and anchor ledger security.
- The Leios pipeline enables continuous IB generation and certification without altering Praos' core settlement guarantees.

---

By combining pipelined architecture with parallel processing and robust confirmation, Leios achieves near-optimal throughput (For example, up to (1−δ) of network capacity) while resisting adversarial strategies such as message flooding and equivocation.
