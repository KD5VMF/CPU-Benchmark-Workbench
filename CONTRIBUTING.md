# Contributing

Thanks for your interest in improving CPU Benchmark Workbench.

## Before you open an issue

Please include:
- OS version
- .NET SDK version
- CPU model
- thread count
- whether the machine is single-socket or multi-socket
- whether the machine is NUMA
- the benchmark preset used
- whether the issue happens in single-run, Smart Sweep, or Burn-In mode
- screenshots if the issue is visual
- the exported CSV if the issue is performance-related

## Before you open a pull request

Please try to keep changes focused:
- one UI fix
- one benchmark fix
- one new benchmark family
- one documentation improvement

## Coding guidelines

- Prefer readability over cleverness
- Keep benchmark kernels deterministic enough for repeatable comparison
- Preserve CSV compatibility when possible
- Avoid breaking older supported systems without documenting it
- Be careful with intrinsics and overload differences across SDK/compiler versions
- Validate high-DPI and smaller-screen behavior for UI changes

## Benchmark changes

When adding or changing a benchmark, document:
- what it measures
- what hardware features it uses
- expected bottlenecks
- whether it is memory-bound, compute-bound, branch-bound, or mixed
- whether the benchmark should appear only when a feature is detected

## Pull request checklist

- [ ] Builds in Visual Studio
- [ ] README updated if behavior changed
- [ ] Help Guide updated if benchmark catalog changed
- [ ] About dialog version/license text still correct
- [ ] CSV export still works
- [ ] Smart Sweep still behaves correctly
- [ ] Burn-In still behaves correctly
