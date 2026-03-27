# Interpreting Results

## Start with single-thread
Single-thread performance still matters for:
- responsiveness
- lightly threaded apps
- many legacy programs
- parts of larger programs that do not parallelize well

## Then look at scaling
Good scaling means the CPU continues to gain as thread count rises.
Poor scaling can happen because of:
- memory bandwidth limits
- cache pressure
- NUMA effects
- thermal throttling
- scheduler behavior
- benchmark design limits

## Compare benchmark families, not just one score
Examples:
- Strong Integer Mix + weak Memory Stream = compute-rich but bandwidth-limited machine
- Strong AVX2/AVX-512 + weak scalar = highly vector-friendly workload profile
- Strong single-thread + modest scaling = great desktop responsiveness but fewer parallel gains
- Strong AES = good crypto path support

## NUMA-aware thinking
On multi-socket or NUMA systems, some benchmarks may flatten or even regress at high thread counts because memory locality becomes harder to maintain.

## Burn-In interpretation
If results fall over time in Burn-In mode, possible reasons include:
- thermal throttling
- power limits
- cooling saturation
- background load

## A healthy comparison workflow
1. Run a single benchmark at 1 thread.
2. Run Smart Sweep.
3. Compare compute-heavy vs memory-heavy benchmarks.
4. Repeat after a long Burn-In if you want to see sustained behavior.
