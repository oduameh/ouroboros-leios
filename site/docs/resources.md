---
sidebar_position: 4
---

# Resources

This page collects key resources on **Ouroboros Leios**, including technical
papers, presentations, and videos.

## Technical documentation

### Leios CPS

- [Leios CPS](https://github.com/cardano-foundation/CIPs/blob/master/CPS-0018/README.md)

**Summary**

Cardano’s mainnet periodically faces congestion, with block utilisation
exceeding 90 percent, delaying transactions and harming user experience for
airdrops, DEXs, oracles, and dApps. As new applications and bridges (for
example, Cardano–Midnight and Cardano–Bitcoin) add demand, current throughput
(~12 TPS maximum) lags far behind competitors such as Solana (7 229 TPS).  
In Ouroboros Praos, security constraints—specifically, the need to relay a block
within a 20-second slot—limit block size and script execution, leaving network
resources under-used. This CPS calls for research into scaling solutions such as
Ouroboros Leios to boost transaction volume, size, and execution units while
keeping processing times predictable for time-sensitive workloads.  
Goals include defining stakeholder needs, safely increasing limits, and
leveraging unused resources—without compromising security or raising node
costs. Historical data show frequent near-full blocks and Plutus bottlenecks,
highlighting the urgency as Cardano targets nation-state-scale usage by 2030.

### Leios CIP

- [Leios CIP (CIP-0079)](https://github.com/cardano-foundation/CIPs/pull/379)  
  — Cardano Improvement Proposal by Duncan Coutts, November 2022.

**Summary**

CIP-0079 introduces Ouroboros Leios as a long-term solution to raise Cardano
throughput beyond the limits of Ouroboros Praos. The CIP explains the rationale
and provides a high-level protocol design.

### Leios research paper

- *High-Throughput Blockchain Consensus under Realistic Network Assumptions*  
  (May 31, 2024) — Sandro Coretti, Matthias Fitzi, Aggelos Kiayias,
  Giorgos Panagiotakos, and Alexander Russell.  
  <https://iohk.io/en/research/library/papers/high-throughput-blockchain-consensus-under-realistic-network-assumptions/>

**Summary**

The paper presents Leios, a protocol overlay that transforms low-throughput PoW
or PoS systems into high-throughput chains, achieving near-optimal throughput of
(1 − δ) σ_H (where σ_H is the honest-stake fraction and δ > 0). Leios addresses
adversarial tactics such as message bursts and equivocations via:

1. Concurrent input-block (IB) generation.  
2. Endorser blocks (EBs) with data-availability proofs.  
3. A seven-stage pipeline for uninterrupted processing.  
4. Freshest-first diffusion with VRF-based timestamps.  
5. Equivocation proofs to cap malicious spam.

Applied to Ouroboros, Leios yields a scalable, secure layer-1 for Cardano while
maintaining settlement guarantees and supporting dynamic participation.

## Videos

- **Scaling Cardano with Leios** — Prof. Aggelos Kiayias  
  <https://www.youtube.com/watch?v=Czmg9WmSCcI>

- **Understanding Leios** — Giorgos Panagiotakos  
  <https://www.youtube.com/watch?v=YEcYVygdhzU>

**Monthly Leios meetings**

- [October 2024 meeting](https://drive.google.com/file/d/12VE0__S0knHqXXpIVdXGWvDipK0g89p_/view)  
- [November 2024 meeting](https://drive.google.com/file/d/1W4iu4MwOXILXes1Zi43MeM505KAOHXso/view)  
- [December 2024 meeting](https://drive.google.com/file/d/1F07oKxBgdOEasGcstxEavkPCgr58sbIO/view)  
- [January 2025 meeting](https://www.youtube.com/live/6ovcWDCdqFU?si=-dgnvO7353tUyiDZ&t=120)

## Presentations

- **Leios overview slides** — Sandro Coretti-Drayton  
  <https://docs.google.com/presentation/d/1W_KHdvdLNDEStE99D7Af2SRiTqZNnVLQiEPqRHJySqI/edit>

**Monthly slide decks**

- [October 2024 slides](https://docs.google.com/presentation/d/1KgjJyP6yZyZKCGum3deoIyooYUOretA9W6dTtXv1fso/edit)  
- [November 2024 slides](https://docs.google.com/presentation/d/11LHQeUuv-TQfiy9GwXkrffSimFjSq8tdTB8qIB-Pk3U/edit)  
- [December 2024 slides](https://docs.google.com/presentation/d/1LwpcXnXLgrYTSDalJY1SfpeyU_4lIkYhyMy5Kv0Huzw/edit)  
- [January 2025 slides](https://docs.google.com/presentation/d/1qKXe3CvAvJGVWAssjrKpRrRABMT6I39E1FxUWQ_PZzo/edit)

## Tools and simulations

- **Throughput simulation** — interactive model of Leios capacity  
  <https://www.insightmaker.com/insight/5B3Sq5gsrcGzTD11GyZJ0u/Cardano-Throughput-v0-2>

## Development resources

- **GitHub repository** — official Leios implementation  
  <https://github.com/input-output-hk/ouroboros-leios>  

- **Cost estimator** — interactive tool for resource-cost estimation  
  <https://leios.cardano-scaling.org/cost-estimator/>
