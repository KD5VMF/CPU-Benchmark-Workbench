# Benchmark Guide

This guide explains what each benchmark is meant to stress and how to think about the results.

## Integer Mix
Stresses general-purpose integer arithmetic and simple throughput scaling.

Best for:
- ALU throughput
- comparing general CPU strength
- checking whether many threads scale cleanly

## Bit Twister
Uses bit operations and data mixing patterns.

Best for:
- integer pipeline behavior
- rotate/shift-heavy work
- comparing older CPUs to newer ones outside pure vector math

## Floating Point Mix
General scalar floating-point workload.

Best for:
- scalar FP throughput
- seeing whether a machine is strong even before SIMD specialization

## Branch Chaos
Introduces branch-heavy and mixed instruction-flow behavior.

Best for:
- branch predictor behavior
- workloads with irregular control flow

## Cache Walker
Walks memory with locality pressure to highlight cache behavior.

Best for:
- cache hierarchy sensitivity
- data locality differences
- spotting cases where scaling stalls because data movement dominates

## SIMD Vector Math
Uses the runtime's portable SIMD path.

Best for:
- portable vector behavior
- comparing runtime-managed SIMD versus ISA-specific paths

## AVX2 / FMA Float32
Appears when the platform exposes AVX2 and FMA.

Best for:
- dense floating-point math
- modern workstation and desktop vector throughput
- seeing how well wide vectors scale across threads

## AVX-512 Wide Float32
Appears when the platform exposes AVX-512.

Best for:
- very wide vector throughput
- workstation and server-class CPUs with AVX-512
- seeing whether frequency or thermal behavior changes under very wide vectors

## AES Blocks
Appears when hardware AES is exposed.

Best for:
- crypto-oriented throughput
- storage, security, and networking-adjacent comparisons

## Memory Stream
Focuses on streaming memory behavior.

Best for:
- bandwidth-bound workloads
- seeing when additional threads stop helping because memory is saturated

## Matrix Multiply
Sustained compute with meaningful cache reuse.

Best for:
- combined compute plus locality behavior
- real-world “dense math” style comparisons

## Prime Scan
Branch-heavy integer workload.

Best for:
- lightly cached integer work
- thread scaling on irregular math

## Mandelbrot
Independent-pixel floating-point plus branch behavior.

Best for:
- mixed floating-point and control-flow testing
- visually familiar workload style

## Smart Sweep
Smart Sweep samples a few thread counts instead of all of them. This gives a fast picture of scaling behavior.

## Burn-In Run
Burn-In is for longer duration testing. Use it to observe:
- thermal soak effects
- stability over time
- whether results drift under heat
