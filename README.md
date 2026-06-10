# optimize-runner-network

A GitHub Action that optimizes the runner's network performance by enabling the **BBR** TCP congestion control algorithm and the **FQ** queuing discipline.

## What it does

1. **Loads kernel modules**:
   - `sch_fq`: Fair Queueing traffic control scheduler.
   - `tcp_bbr`: BBR congestion control algorithm.
2. **Sets system controls**:
   - Sets default queuing discipline (`default_qdisc`) to `fq`.
   - Sets TCP congestion control (`tcp_congestion_control`) to `bbr`.
3. **Applies queuing discipline** — Replaces the root queuing discipline of the `eth0` network interface with `fq`.

## Usage

Add the action as a step in your GitHub Actions workflow:

```yaml
steps:
    uses: compact-orb/optimize-runner-network@v1
```
