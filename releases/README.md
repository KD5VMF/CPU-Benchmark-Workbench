# CPU Benchmark Workbench Release Files

This folder contains packaged source archives for **CPU Benchmark Workbench**.

## Current package

**File:** `CpuBenchmarkWorkbench_Windows11_VisualStudio_v17.zip`  
**Program version:** `17.0.0`

CPU Benchmark Workbench is a Windows desktop benchmark application for testing CPU performance across multiple workload types, including:

- Integer and bit-manipulation workloads
- Floating-point workloads
- SIMD workloads
- AVX2 / FMA workloads when supported
- AVX-512 workloads when supported
- AES acceleration workloads when supported
- Memory and cache behavior
- Matrix math
- Prime-number scanning
- Mandelbrot compute
- Smart thread scaling
- Burn-in runs

## What is inside the zip

The zip is intended for people who want to **open, build, and modify the project in Visual Studio**.

Typical contents include:

- `CpuBenchmarkWorkbench.sln`
- `src/CpuBenchmarkWorkbench/`
- C# source files
- project file
- license and documentation files

## Requirements to compile

To build this project, you should have:

- **Windows 10 or Windows 11**
- **Visual Studio 2022**
  - Community, Professional, or Enterprise edition is fine
- **.NET 8 SDK**
- Visual Studio workload:
  - **.NET desktop development**

Recommended:
- latest Visual Studio 2022 updates installed
- latest .NET 8 updates installed

## How to compile

1. Download and extract `CpuBenchmarkWorkbench_Windows11_VisualStudio_v17.zip`
2. Open `CpuBenchmarkWorkbench.sln` in **Visual Studio 2022**
3. Let Visual Studio restore dependencies if prompted
4. Select:
   - **Debug** or **Release**
   - **x64** preferred
5. Build the solution:
   - **Build > Build Solution**
6. Run it:
   - **Debug > Start Without Debugging**
   - or press **Ctrl+F5**

## Runtime notes

The program is a Windows Forms desktop application built for modern .NET on Windows.

Depending on how it is built and published, users may need:

- **.NET 8 Desktop Runtime**

If building directly in Visual Studio with the included project, the proper runtime and SDK should be enough.

## CPU feature support

The benchmark suite detects available CPU features and only enables certain tests when supported by the system/runtime.

Examples include:

- SSE / SSE2 / SSE3 / SSSE3
- SSE4.1 / SSE4.2
- AVX
- AVX2
- FMA
- AES
- AVX-512 families when available
- NUMA-related system reporting

Because some features depend on both **hardware support** and **runtime exposure**, the exact test list may vary between systems.

## Smart Sweep behavior

The **Smart Sweep** mode does not test every thread count from 1 to maximum.

Instead, it automatically samples:

- 1 thread
- 25%
- 50%
- 75%
- 100%

Example on a 48-thread system:

- 1
- 12
- 24
- 36
- 48

This gives a much faster scaling picture without excessive test time.

## Burn-In mode

The program also includes a **Burn-In Run** mode for longer stress-style benchmark cycling.

Use it to:

- run selected tests repeatedly
- observe sustained performance
- compare behavior over time
- check stability during long workloads

## Notes for contributors and builders

- Version in this archive: **17.0.0**
- About dialog should match the application version
- Some benchmarks use hardware intrinsics, so older compiler/runtime combinations may behave differently
- If your system does not support a feature, that benchmark may not appear

## License

This project is released under the **MIT License** unless otherwise noted in the repository.

## Main repository

For the full project, documentation, and updates, see the main repository root.
