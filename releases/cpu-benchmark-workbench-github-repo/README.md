# CPU Benchmark Workbench

A Windows desktop benchmark workbench for exploring **how a CPU behaves**, not just producing a single score.

CPU Benchmark Workbench focuses on:
- scalar integer and floating-point throughput
- branch-heavy behavior
- cache and memory behavior
- portable SIMD behavior
- ISA-specific paths such as **AVX2/FMA**, **AVX-512**, and **AES** when detected
- thread scaling from single-thread to many-thread systems
- longer **burn-in** runs for thermal and stability testing

It is intended to be useful on:
- older home PCs
- modern gaming desktops
- workstations
- multi-socket servers
- NUMA systems

## Highlights

- Clean WinForms desktop UI for Windows
- Built-in **Help Guide** with benchmark descriptions
- Built-in **About + MIT** dialog
- **Smart Sweep** mode that samples thread counts intelligently instead of testing every thread count
- **Burn-In Run** mode for longer stress sessions
- CSV export for later comparison and charting
- System capability reporting for ISA features and topology hints
- Dynamic benchmark list that matches what the system reports

## Benchmark families

Core benchmarks currently used by the project include:

- **Integer Mix** — general ALU throughput and thread scaling
- **Bit Twister** — bit operations, rotates, integer data motion
- **Floating Point Mix** — scalar floating-point throughput
- **Branch Chaos** — branch predictor and mixed control-flow behavior
- **Cache Walker** — cache hierarchy and locality pressure
- **SIMD Vector Math** — runtime portable SIMD behavior
- **AVX2 / FMA Float32** — modern wide-vector floating-point path when available
- **AVX-512 Wide Float32** — very wide vector path when available
- **AES Blocks** — hardware-assisted AES throughput when available
- **Memory Stream** — memory bandwidth and cache-friendly streaming behavior
- **Matrix Multiply** — sustained compute with cache reuse
- **Prime Scan** — branch-heavy integer scaling
- **Mandelbrot** — floating-point plus branch behavior on independent pixels

See [docs/benchmark-guide.md](docs/benchmark-guide.md) for the full detailed guide.

## Why this project exists

Many benchmark tools compress a machine into one number. This project is different.

CPU Benchmark Workbench is meant to show **what kind of work a machine is good at**:
- wide-vector math
- memory-heavy workloads
- branch-heavy workloads
- crypto-heavy tasks
- cache-sensitive work
- scaling on many-core and multi-socket systems

That makes it more useful for comparing machines that are very different from each other.

## Smart Sweep

Smart Sweep detects the selected thread ceiling and samples:
- **1 thread**
- **25%** of the selected ceiling
- **50%** of the selected ceiling
- **75%** of the selected ceiling
- **100%** of the selected ceiling

Examples:
- 8 threads → 1, 2, 4, 6, 8
- 16 threads → 1, 4, 8, 12, 16
- 48 threads → 1, 12, 24, 36, 48

This gives a useful scaling curve without creating dozens of nearly redundant runs.

## Burn-In mode

Burn-In repeatedly cycles through the selected benchmarks for a chosen number of minutes, or until stopped.

Use it for:
- long thermal runs
- checking stability at sustained load
- testing cooling changes
- observing clock behavior over time
- comparing “cold” vs “soaked” performance

## Current tech stack

- **.NET 8**
- **Windows Forms**
- C# intrinsics and runtime feature detection where supported
- Windows-focused desktop UX

## Repository layout

```text
.
├─ .github/
│  ├─ ISSUE_TEMPLATE/
│  └─ workflows/
├─ assets/
│  └─ screenshots/
├─ docs/
├─ releases/
├─ src/
│  └─ CpuBenchmarkWorkbench/
├─ CpuBenchmarkWorkbench.sln
├─ LICENSE
├─ README.md
├─ CHANGELOG.md
├─ CONTRIBUTING.md
├─ CODE_OF_CONDUCT.md
└─ SECURITY.md
```

## Getting started

1. Add the application source tree to `src/` and the solution file to the repository root.
2. Open `CpuBenchmarkWorkbench.sln` in Visual Studio.
3. Build and run the project.
4. Start with a single benchmark and a low thread count.
5. Use **Smart Sweep** for quick scaling checks.
6. Use **Burn-In Run** for longer thermal or stability sessions.

## GitHub release layout

This repository is designed so you can:
- keep source in the repo
- attach ready-to-run zip builds to **GitHub Releases**
- keep screenshots in `assets/screenshots/`
- store sample exported CSV results in `docs/` or release assets

The `releases/` folder in this template is only a placeholder with instructions; actual release archives are usually better attached to GitHub Releases.

## Screenshots

Add screenshots here:
- `assets/screenshots/main-window.png`
- `assets/screenshots/help-guide.png`
- `assets/screenshots/about-dialog.png`

Then reference them from this README.

## Interpreting results

A few general rules:
- High **Integer Mix** usually means strong general-purpose throughput.
- High **Branch Chaos** often indicates good branch prediction and instruction-flow handling.
- High **Memory Stream** matters for bandwidth-bound work.
- High **AVX2** or **AVX-512** matters for vector-heavy numeric work.
- Strong single-thread results matter for responsiveness and lightly threaded programs.
- Strong scaling matters for compile jobs, simulation, rendering, analysis, and server-style workloads.

See [docs/interpreting-results.md](docs/interpreting-results.md).

## License

This repository uses the **MIT License**. See [LICENSE](LICENSE).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See [SECURITY.md](SECURITY.md).

## Roadmap ideas

- affinity-aware and NUMA-aware modes
- charts and comparison views
- richer export reports
- live rolling burn-in charts
- per-benchmark advanced settings
- machine-to-machine comparison packs
