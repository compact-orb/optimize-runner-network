# optimize-runner-network

A GitHub Action that enables **BBR** TCP congestion control and the **FQ**
queuing discipline on Linux runners.

## What it does

1. **Load kernel modules**: Attempts to load `sch_fq` (Fair Queuing) and
   `tcp_bbr` (BBR) with `modprobe`. Continues if loading fails (for example,
   when built into the kernel).
2. **Set `sysctl` parameters**:
   - `net.core.default_qdisc=fq`
   - `net.ipv4.tcp_congestion_control=bbr`
3. **Apply queuing discipline**: Finds the default route network interface
   and replaces its root queuing discipline with `fq` using `tc`.

## Usage

Add this step to a Linux job in your workflow:

```yaml
steps:
  - uses: compact-orb/optimize-runner-network@v1
```
