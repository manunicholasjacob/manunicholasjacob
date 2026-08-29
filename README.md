<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/manunicholasjacob/manunicholasjacob/main/assets/banner-dark.png">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/manunicholasjacob/manunicholasjacob/main/assets/banner-light.png">
  <img alt="Manu Nicholas Jacob. Edge AI, computer architecture, LLM inference." src="https://raw.githubusercontent.com/manunicholasjacob/manunicholasjacob/main/assets/banner-light.png">
</picture>

I measure where the bottleneck actually is, on hardware I can put an ammeter on, and I publish the data whether or not it agrees with me.

[Website](http://manunicholasjacob.com/) · [ORCID 0009-0007-6589-6572](https://orcid.org/0009-0007-6589-6572) · [Google Scholar](https://scholar.google.com/citations?user=inrrUQIAAAAJ&hl=en)

Electrical and computer engineer (UMass Amherst), based in Austin. Hardware engineer at Dell by day, working on enterprise AI-server platforms, GPU and PCIe subsystems, and root-cause work. The research below is my own, run on my own hardware.

---

### Tools

| | |
|---|---|
| [**llama‑roofline**](https://github.com/manunicholasjacob/llama-roofline) | Is your `llama.cpp` decode memory-bandwidth-bound? Measure it in one command. Reports the operating point next to every fitted bandwidth, and refuses to quote a number for silicon it has not measured. [`10.5281/zenodo.21842493`](https://doi.org/10.5281/zenodo.21842493) |
| [**ml‑systems‑lab**](https://github.com/manunicholasjacob/ml-systems-lab) | One YAML config drives `llama.cpp` and ONNX Runtime sweeps across laptops, a Raspberry Pi over SSH, and GPUs, with TTFT, throughput and per-rail telemetry. [`10.5281/zenodo.21867055`](https://doi.org/10.5281/zenodo.21867055) |
| [**qgemv‑roofline**](https://github.com/manunicholasjacob/qgemv-roofline) | A quantized GEMV kernel ladder measured against its own bandwidth roof: 12 CUDA kernels plus Triton for batch-1 LLM decode over ggml `q8_0`/`q4_0`, across five NVIDIA GPUs from sm_60 to sm_89. [`10.5281/zenodo.22164007`](https://doi.org/10.5281/zenodo.22164007) |

### Measurement studies

Each of these is a reproducible artifact with its data, its harness and a DOI, not a figure in a PDF.

| | |
|---|---|
| [**The memory wall at the edge of language**](https://github.com/manunicholasjacob/edge-llm-memory-wall) | Edge LLM decode is bandwidth-bound with R² = 0.994, and the KV cache hits a capacity wall before compute does. [`10.5281/zenodo.21844855`](https://doi.org/10.5281/zenodo.21844855) |
| [**The break-even parallel speedup**](https://github.com/manunicholasjacob/edge-breakeven-speedup) | Multithreading saves energy exactly when parallel speedup beats the power ratio. 831 PMIC-measured runs showing the power ratio is a board constant while the speedup is a model property. [`10.5281/zenodo.21987261`](https://doi.org/10.5281/zenodo.21987261) |
| [**Your quantization format is not free**](https://github.com/manunicholasjacob/edge-format-tax) | Same-size, same-label GGUF files decode very differently on edge CPUs. Provenance changes layout, and format rankings do not transfer across cores. [`10.5281/zenodo.21938812`](https://doi.org/10.5281/zenodo.21938812) |
| [**The cold-start tax**](https://github.com/manunicholasjacob/edge-cold-start-tax) | What duty-cycled wake actually costs, and the eviction cliff behind it. [`10.5281/zenodo.21844857`](https://doi.org/10.5281/zenodo.21844857) |
| [**gguf-faultscope**](https://github.com/manunicholasjacob/gguf-faultscope) | What one flipped bit does to a quantized language model, and where in the file it has to land to matter. [`10.5281/zenodo.22163327`](https://doi.org/10.5281/zenodo.22163327) |

Full list of artifacts and manuscripts: [manunicholasjacob.com](http://manunicholasjacob.com/) · [ORCID](https://orcid.org/0009-0007-6589-6572)

---

### Upstream

Merged into [NVIDIA/garak](https://github.com/NVIDIA/garak): a config-root fix in `goodside.RileyIsnt`, an ASCII-selection guard in `badchars`, and a restored unreachable-error path in `load_plugin`. The first shipped in garak v0.16.0.

Open in [ai-dynamo/aiperf](https://github.com/ai-dynamo/aiperf): making the `crick` dependency optional so `pip install aiperf` needs no C toolchain on aarch64, a host-telemetry collector category with a RAPL backend, and two defects found by building against the code rather than reading it.

Also filing measurement-backed issues against [llama.cpp](https://github.com/ggml-org/llama.cpp) and [vLLM](https://github.com/vllm-project/vllm), and reviewing for the [Journal of Open Source Software](https://joss.theoj.org/).

---

### How I work

Measure on real hardware. State the operating point. Publish the rejected hypotheses next to the confirmed ones, and retract in public when a result does not survive re-checking.
