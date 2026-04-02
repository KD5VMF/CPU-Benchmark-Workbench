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
- overall benchmark scoring
- workload-fit analysis based on measured results

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
- Run log export for traceable benchmark sessions
- System capability reporting for ISA features and topology hints
- Dynamic benchmark list that matches what the system reports
- Final **overall score** from **0 to 100,000**
- Final **best use case** opinion based on category scoring
- Fullscreen **thread scaling graph** with per-series **Show All / Hide All / individual show-hide**
- Single-series **focused analysis** panel that explains the selected benchmark and interprets the current run
- Scrollable analysis text for longer per-benchmark evaluations
- More benchmark-specific wording so different tests do not all read like the same generic result

## Packaged release progression

This project has been evolving in visible feature steps across the packaged source archives.

### v24 package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v24.zip`  
**Program version:** `24.0.0`

Version 24 established the modern workbench direction:

- broad benchmark family coverage
- Smart Sweep thread sampling
- burn-in support
- overall system scoring
- best-use-case analysis
- Windows desktop Visual Studio project packaging

### v26 package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v26.zip`  
**Program version:** `26.0.0`

Version 26 added the first major fullscreen graph usability upgrade:

- per-series **show / hide** buttons in the fullscreen graph
- quick **Show All**
- quick **Hide All**
- live redraw as series visibility changes
- easier isolation of individual scaling curves

### v27 package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v27.zip`  
**Program version:** `27.0.0`

Version 27 added focused single-series graph interpretation:

- when only one benchmark line is visible, the right side shows a focused analysis area
- the panel explains what the selected benchmark is testing
- the panel describes what a healthy curve usually looks like
- the panel interprets the current run and gives a practical scaling verdict
- version 27 also received a small follow-up UI fix so longer analysis text can be scrolled cleanly

### v28 package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v28.zip`  
**Program version:** `28.0.0`

Version 28 keeps the fullscreen graph layout but makes the right-side analysis substantially smarter and less repetitive:

- stronger benchmark-specific explanations instead of near-duplicate wording
- more detail about the **actual math / kernel style** being used
- better discussion of what hardware resource is really being stressed
- improved interpretation of the **current measured curve**
- more specific “what this says about this PC” commentary by benchmark family
- section labels in the focused analysis area are styled more clearly for readability
- the v28 refinements keep the same overall v28 version while polishing the wording and presentation

For users, v28 is the current “smarter analyst” release: the graph does not just show one line at a time, it gives more benchmark-aware commentary about what that line means for the machine being tested.


## Benchmark families

Core benchmarks currently used by the project include:

- **Integer Mix** — general ALU throughput and thread scaling
- **Bit Twister** — bit operations, rotates, integer data motion
- **Floating Point Mix** — scalar floating-point throughput
- **Floating Point Mix (Peak)** — higher-intensity floating-point stress path
- **Branch Chaos** — branch predictor and mixed control-flow behavior
- **Cache Walker** — cache hierarchy and locality pressure
- **SIMD Vector Math** — runtime portable SIMD behavior
- **AVX2 / FMA Float32** — modern wide-vector floating-point path when available
- **AVX2 / FMA Float32 (Peak)** — higher-intensity AVX2/FMA throughput path
- **AVX-512 Wide Float32** — very wide vector path when available
- **AVX-512 Wide Float32 (Peak)** — higher-intensity AVX-512 throughput path
- **AES Blocks** — hardware-assisted AES throughput when available
- **Memory Stream** — memory bandwidth and cache-friendly streaming behavior
- **Memory Stream (Sustained)** — heavier long-stream bandwidth path
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

The newer fullscreen graph tools also help users isolate one benchmark at a time and read a workload-specific interpretation of what the current scaling curve appears to say about the PC.

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

## Overall scoring

At the end of a completed benchmark session, CPU Benchmark Workbench can produce an **overall system score**.

Scoring features include:

- a normalized score range from **0 to 100,000**
- weighted scoring across benchmark families
- reduced sensitivity to one extreme outlier
- better representation of real mixed-workload CPU behavior
- a scoring model designed to summarize the machine without hiding the per-test details

The score is intended to be useful as a practical overview, while the benchmark tables remain the main source of truth.

## Best use case analysis

After a run completes, the program can also provide an opinion about the system’s strongest likely use case based on the benchmark profile.

Example categories include:

- **General Throughput**
- **Scientific / Simulation**
- **Memory / Data Movement**
- **Encryption / Secure Data**
- **Visual / Creator Math**

This helps users understand not only how fast the CPU is overall, but what kinds of workloads it appears best suited for.

## System awareness

The benchmark suite detects available CPU and runtime features and only enables certain tests when supported.

Examples include:

- SSE / SSE2 / SSE3 / SSSE3
- SSE4.1 / SSE4.2
- AVX
- AVX2
- FMA
- AES
- AVX-512 families when available
- NUMA-related system reporting and placement-aware execution

Because some features depend on both **hardware support** and **runtime exposure**, the exact test list may vary between systems.

On larger systems, placement policy can matter a lot. The workbench can expose behavior differences between compact scheduling and more NUMA-balanced execution.

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
